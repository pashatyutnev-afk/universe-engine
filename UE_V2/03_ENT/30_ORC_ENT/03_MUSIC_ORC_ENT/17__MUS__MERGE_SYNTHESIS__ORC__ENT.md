FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/17__MUS__MERGE_SYNTHESIS__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.MERGE_SYNTHESIS.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_MERGE_SYNTHESIS
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.MERGE_SYNTHESIS.001

---

## [M] PURPOSE
Собирает финальную версию из нескольких вариантов: трек-версий, хуков, лирики, метаданных.
Задача — выбрать лучшие элементы и склеить в один канонический OUTPUT_PACK без потери ограничений (genre/style, identity locks, banned items, platform safe).
Работает как "финальный монтаж": решает конфликты, стабилизирует структуру и делает один целевой артефакт.

---

## [M] HARD_RULES
- NO EXCLAMATION: символ `!` запрещён в текстах и метаданных.
- NO INVENTED CLAIMS: не придумывать факты (фиты, лейблы, даты, награды).
- LOCKS WIN: любые IDENTITY_LOCKS/STYLE_LOCKS/QA_LOCKS имеют приоритет.
- TRACEABLE: каждое решение фиксируется как MERGE_DECISION (коротко).
- MINIMAL SURGERY: не переписывать всё заново, а выбирать и склеивать.
- SINGLE SOURCE OF TRUTH: на выходе один FINAL_PACK.
- FAIL FAST: если нет входных вариантов — FAIL.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- VARIANT_SET (минимум 2 варианта любого типа):
  - AUDIO_VARIANTS (optional)
  - LYRIC_VARIANTS (optional)
  - HOOK_VARIANTS (optional)
  - META_VARIANTS (optional)
- LOCKS:
  - IDENTITY_LOCKS
  - STYLE_LOCKS (если есть)
  - QA_LOCKS (если есть)
- TARGET_SPEC:
  - artifact_target: "track|lyrics|meta|full_pack"
  - platform_safe: true|false

### Inputs (optional)
- TEST_EVIDENCE (если уже прогнали тест-док)
- PREFERRED_VARIANT_HINT (например "вариант B по вайбу")

### Outputs
- FINAL_PACK
- MERGE_DECISION_LOG (short)
- MERGE_STATUS: PASS | FAIL
- MERGE_WARNINGS (list)
- NEXT_ACTION (обычно -> MUS.RELEASE_ASSEMBLER или MUS.RELEASE_PACK)

---

## [M] FINAL_PACK SCHEMA (canonical)

FINAL_PACK:
- identity:
  - IDENTITY_TOKENS
  - IDENTITY_LOCKS
- style:
  - STYLE_PROFILE
  - STYLE_LOCKS
- audio:
  - chosen_audio_variant_id: "<id or empty>"
  - audio_notes: ["..."]
- lyrics:
  - chosen_lyric_variant_id: "<id or empty>"
  - lyrics_final: "<text>"
  - structure: {verses: n, chorus: n, bridge: yes|no}
- hook:
  - chosen_hook_variant_id: "<id or empty>"
  - hook_lines: ["..."]
- metadata:
  - chosen_meta_variant_id: "<id or empty>"
  - title: "<string>"
  - artist: "<string>"
  - album: "<string>"
  - credits: {...}
  - tags: ["..."]
- packaging:
  - output_targets: ["wav|mp3|stems|lyrics_txt|metadata_json|cover"]
  - release_notes: "<string>"
- evidence:
  - tests_attached: true|false
  - qa_passed: true|false

---

## [M] VARIANT SET NORMALIZATION
Каждый вариант приводится к единому виду:

VARIANT:
- id: "A|B|C|..."
- type: "audio|lyrics|hook|meta|pack"
- strengths: ["..."]         # коротко
- weaknesses: ["..."]        # коротко
- constraints_observed: true|false
- payload: <content>

---

## [M] MERGE STRATEGY (deterministic)
S1) Validate inputs
- есть минимум 2 варианта
- есть LOCKS и TARGET_SPEC
- если platform_safe=true -> включить ограничения по длинам/символам

S2) Score candidates (simple rubric)
- Constraint fit (0–3)
- Clarity / catchiness (0–3)
- Originality without chaos (0–2)
- Consistency with identity/style (0–3)
Итого 0–11. Победитель по типу (audio/lyrics/hook/meta).

S3) Compose
- взять победителя как BASE
- добавить лучшие фрагменты из runner-up только если:
  - не нарушают LOCKS
  - улучшают один конкретный критерий
  - не ломают структуру

S4) Stabilize
- унифицировать термины/имена по IDENTITY_TOKENS
- устранить конфликтующие строки/теги
- убрать `!`, двойные пробелы, мусорные символы

S5) Output
- собрать FINAL_PACK
- сделать MERGE_DECISION_LOG

---

## [M] CONFLICT RULES
- Conflict: identity fields (artist, label, series)
  -> всегда брать из IDENTITY_TOKENS, варианты игнорировать
- Conflict: style constraints (genre, bpm, mood)
  -> STYLE_LOCKS > STYLE_PROFILE > variant hints
- Conflict: lyrics content vs banned_items
  -> banned_items wins, заменить/удалить строки
- Conflict: title different across variants
  -> правило: краткость + ясность + бренд; если нет выбора, брать из META_VARIANT с лучшим score

---

## [M] TEXT HYGIENE RULES
- Запрещено: `!`
- Запрещено: "feat." если не дано пользователем/в LOCKS
- Запрещено: явные утверждения о чартах/наградах
- Разрешено: нейтральные эмоциональные формулировки в notes

---

## [M] VALIDATION CHECKS (gate)

### V1) completeness
- FINAL_PACK содержит обязательные секции по artifact_target
  - track -> audio + identity + style + metadata (минимум title/artist)
  - lyrics -> lyrics + identity + style
  - full_pack -> всё

### V2) locks respected
- IDENTITY_LOCKS не нарушены
- STYLE_LOCKS не нарушены

### V3) hygiene
- нет `!`
- нет banned_items (если заданы)

### V4) platform_safe (если true)
- title <= 60 chars
- artist <= 60 chars
- album <= 60 chars
- tags count <= 20
- lyrics lines <= 200 (мягкий лимит; warning если выше)

PASS если V1–V4 ok.
FAIL если V1 или V2 fail.

---

## [M] FAIL CODES
- FAIL_CODE: MUS.FAIL.MERGE.NO_VARIANTS
- FAIL_CODE: MUS.FAIL.MERGE.MISSING_LOCKS
- FAIL_CODE: MUS.FAIL.MERGE.LOCK_VIOLATION
- FAIL_CODE: MUS.FAIL.MERGE.INCOMPLETE_OUTPUT
- FAIL_CODE: MUS.FAIL.MERGE.HYGIENE

---

## [M] MERGE_DECISION_LOG (format)
MERGE_DECISION_LOG:
- picked:
  - audio: "A"
  - lyrics: "B"
  - hook: "B"
  - meta: "A"
- merges:
  - "Added hook line 2 from C because stronger cadence"
  - "Replaced verse 1 line 3 from A with B to remove banned item"
- locks_applied:
  - "artist_name locked to <...>"
  - "removed exclamation symbols"
- warnings:
  - "lyrics length high"
  - "platform_safe tag count trimmed"

---

## [M] ROUTE BACK (on fail)
- no_variants -> MUS.TRACK_BUILD_STEP (generate variants)
- lock_violation -> MUS.LYRIC_EDITOR or MUS.GENRE_STYLE_ROUTER (repair) then retry
- incomplete_output -> MUS.METADATA_FACTORY / MUS.LYRIC_DRAFTER (fill missing) then retry
- hygiene -> rerun MERGE with sanitation only

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.HOOK_FOCUS_LOOP
  - MUS.LYRICS_FOCUS_LOOP
  - MUS.MIX_FOCUS_LOOP
  - MUS.METADATA_FACTORY
- Returns to:
  - MUS.RELEASE_ASSEMBLER
  - MUS.RELEASE_PACK

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 deterministic merge rubric, conflict rules, validation gates, decision log format
