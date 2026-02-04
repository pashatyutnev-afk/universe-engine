FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/08__MUS__PROMPT_PACKAGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.PROMPT_PACKAGER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PROMPT_PACKAGER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.PROMPT_PACKAGER.001

---

## [M] PURPOSE
Собирает итоговый PROMPT_PACK для генератора музыки из MUS_BRIEF + STYLE_ROUTE_TOKEN + LYRICS_FINAL и фиксирует ограничения так, чтобы:
- генерация была детерминированной (стабильный стиль/темп/инструменты),
- соблюдались запреты и SOURCE_POLICY_TOKEN,
- соблюдалась пунктуационная политика (запрет восклицаний),
- выдача была готова к step-run пайплайну (draft → revise → final),
- QA мог проверить комплектность и воспроизводимость результата.

---

## [M] OPERATING_PRINCIPLES
- OUTPUT-FIRST: PROMPT_PACK должен быть готов для прямой вставки в генератор.
- CONSTRAINT-LOCK: любые жёсткие ограничения фиксируются в NOTES и не “плавают” между итерациями.
- SAFE-PUNCT: исключить символ `!` в любых полях (lyrics, prompts, notes). Если встречается — заменить на `.`, `—` или `…` без потери смысла.
- NEGATIVE-FIRST: запреты не прячем в “голове” — они отдельным NEGATIVE_PROMPT блоком.
- TOOL-AGNOSTIC: pack содержит общий формат + адаптеры под популярные тулзы (если нужно).

---

## [M] INPUTS / OUTPUTS

### Inputs
- MUS_BRIEF (required)
  - mood, theme, energy, vocal_pref, language, content_bans, references(optional)
- STYLE_ROUTE_TOKEN (required)
  - genre, substyle, bpm_target_or_range, groove, instrumentation, mix_targets, era, vocal_style
- LYRICS_FINAL (optional-by-brief)
  - required если: brief требует вокал/lyrics
- SOURCE_POLICY_TOKEN (optional, but recommended)
  - allowed_sources, prohibited_sources, legal_flags, sampling_rules
- CONSTRAINTS (optional)
  - platform/tool, duration, structure, explicit_instrument_list, must_avoid_list
- MODE_HINT (optional)
  - FAST | RELEASE_READY | MASTERPIECE

### Outputs
- PROMPT_PACK
  - MAIN_PROMPT
  - NEGATIVE_PROMPT
  - LYRICS (optional)
  - VARIANTS (optional)
  - NOTES (constraint lock + render hints)
  - METADATA_HINTS (optional)
- FAIL_CODE (optional)

---

## [M] PROMPT_PACK SCHEMA (canonical)
PROMPT_PACK:
- MAIN_PROMPT:
  - style_core
  - instrumentation
  - rhythm_groove
  - bpm
  - harmony
  - vocals
  - structure
  - mix_master_targets
  - vibe_imagery (short)
- NEGATIVE_PROMPT:
  - banned_content
  - banned_style_artifacts
  - banned_lyrics_markers
  - legal_bans
- LYRICS:
  - final_text (only if required)
- VARIANTS:
  - V1 (safe alternative)
  - V2 (more aggressive/modern)
  - V3 (more minimal/clean)
- NOTES:
  - constraint_lock
  - iteration_instructions
  - punctuation_policy
  - source_policy_summary

---

## [M] STEP-RUN BEHAVIOR
Пакет обязан поддерживать step-run.

### Step mapping
- DRAFT:
  - MAIN_PROMPT краткий, но полный по опорам (genre/bpm/instrument/vocal/structure)
  - NEGATIVE_PROMPT обязателен
  - LYRICS если required
- REVISE:
  - добавляется уточнение “keep same style/bpm/instruments” (lock)
  - добавляются микс-таргеты и структура
- FINAL:
  - максимально конкретный MAIN_PROMPT
  - фиксируются mix/master ориентиры и финальные запреты

### Deterministic locks (must)
- genre + substyle (1–2 строки, без “каши”)
- bpm (число или узкий диапазон)
- key/scale только если MUS_BRIEF это требует
- primary instruments (3–7 пунктов)
- vocal gender/style/language если вокал есть
- structure (например: intro → verse → chorus → verse → chorus → bridge → final chorus → outro)

---

## [M] ALGORITHM (packaging)
S0) Normalize inputs
- trim spaces, normalize lists
- remove `!` everywhere (replace with `.`, `—` or `…`)
- resolve “lyrics required” flag from MUS_BRIEF

S1) Build style_core
- genre + substyle + era + vibe
- keep it short but specific (1–2 lines)

S2) Build instrumentation
- choose primary set from STYLE_ROUTE_TOKEN
- add 1–2 “signature” timbres максимум

S3) Build rhythm_groove + bpm
- bpm_target or tight range
- groove words: swing/straight/half-time/double-time/latin/etc.

S4) Build vocals (if needed)
- vocal style (clean/raspy/airy/aggressive)
- language
- delivery (melodic rap/sung/spoken)
- no “artist name imitation” by default

S5) Build structure
- if MUS_BRIEF has structure → use it
- else use default by genre from STYLE_ROUTE_TOKEN

S6) Mix/master targets
- energy balance, punch, clarity, low-end control
- avoid deep technical LUFS numbers unless brief asks (keep “streaming-ready” language)

S7) Build NEGATIVE_PROMPT
- banned content from MUS_BRIEF
- banned sonic artifacts (muddy mix, harsh sibilance, clipping, distorted vocals) as checklist
- legal bans from SOURCE_POLICY_TOKEN
- lyrics bans: profanity/explicit names/etc (as provided)

S8) Build VARIANTS (optional)
- only if MODE_HINT != FAST OR if MUS_BRIEF requests variants
- each variant changes 1 dimension max (instrumentation OR energy OR era), everything else locked

S9) Assemble NOTES
- constraint_lock list
- iteration_instructions (what can change, what can’t)
- punctuation policy summary
- source policy summary (high level)

---

## [M] TOOL ADAPTERS (optional output blocks)
Если CONSTRAINTS.platform задан, добавляется adapter section в NOTES:

### SUNO-like adapter
- keep MAIN_PROMPT 350–600 chars (если нужно — уплотнить)
- NEGATIVE_PROMPT кратко списком
- LYRICS отдельным блоком

### UDIO-like adapter
- emphasis on scene/vibe + instrumentation + vocal
- “avoid” list отдельным списком

### Generic adapter
- full descriptive MAIN_PROMPT + constraints lock

(Если platform не задан — эти адаптеры не добавляются.)

---

## [M] PUNCTUATION POLICY (hard)
- Запрещён символ `!` в любом поле PROMPT_PACK.
- Если во входах встречается `!`:
  - заменять на `.` / `—` / `…`
  - не усиливать агрессию текста, смысл сохранить
- Не начинать строки с командных междометий, особенно с `!`.

---

## [M] FAIL CONDITIONS
- FAIL_CODE: MUS.FAIL.PACKAGER.MISSING_STYLE
  - нет STYLE_ROUTE_TOKEN или пустые genre/bpm/instrumentation
- FAIL_CODE: MUS.FAIL.PACKAGER.MISSING_LYRICS
  - MUS_BRIEF требует lyrics, но LYRICS_FINAL отсутствует
- FAIL_CODE: MUS.FAIL.PACKAGER.SOURCE_POLICY_BLOCK
  - SOURCE_POLICY_TOKEN запрещает ключевой референс/подход, а альтернативы не заданы
- FAIL_CODE: MUS.FAIL.PACKAGER.INVALID_PUNCT
  - после нормализации остались `!` (недопустимо)

---

## [M] GATES
PASS если:
- MAIN_PROMPT содержит: genre/substyle + bpm + instruments + (vocals если нужно) + structure
- NEGATIVE_PROMPT содержит: bans (content + sonic + legal if any)
- LYRICS присутствует если required
- NOTES фиксирует constraint_lock
- символ `!` отсутствует во всём PROMPT_PACK

FAIL если:
- любое из FAIL CONDITIONS

---

## [M] EXAMPLE (mini, format only)
PROMPT_PACK:
- MAIN_PROMPT:
  "Genre: [..]. Substyle: [..]. BPM: [..]. Instruments: [..]. Groove: [..]. Vocals: [..]. Structure: [..]. Mix: [..]. Vibe: [..]."
- NEGATIVE_PROMPT:
  "- Avoid: [..]\n- Banned content: [..]\n- Legal bans: [..]"
- LYRICS:
  "[final lyrics here]"
- VARIANTS:
  - V1: "Same lock, softer energy, cleaner mix."
  - V2: "Same lock, more punch, modern drums."
- NOTES:
  "- LOCK: genre/bpm/instruments/vocal/lang/structure\n- Iteration: change only hook wording or drum tightness\n- Punctuation: no exclamation\n- Source policy: public-domain only"

(Содержимое зависит от входов. Этот блок только демонстрация формата.)

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff:
  - PROMPT_PACK → MUS.TRACK_BUILD_STEP
  - PROMPT_PACK → MUS.QA_CHECKS

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 expanded schema, step-run locks, adapters, hard punctuation gate
