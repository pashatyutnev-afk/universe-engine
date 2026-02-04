FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/10__MUS__HOOK_FOCUS_LOOP__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.HOOK_FOCUS_LOOP.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_HOOK_FOCUS_LOOP
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.HOOK_FOCUS_LOOP.001

---

## [M] PURPOSE
Итеративно усиливает хук, чтобы он был цепким и узнаваемым без смены жанра и базовой опоры.
Работает как локальный loop внутри track-build: генерирует варианты хука, оценивает, выбирает лучшие элементы и синтезирует финальный hook-кандидат.
Держит constraints стабильными, меняет только узкий набор параметров, фиксирует evidence на каждом шаге.

---

## [M] HARD_RULES
- CONSTRAINT LOCK: genre/substyle, bpm, core instruments, vocal preference, language, structure нельзя менять в лупе.
- HOOK SCOPE ONLY: правим только hook-модуль (melody contour, phrasing, lyric hook line, rhythmic placement).
- ONE-AXIS-AT-A-TIME: в одной итерации меняем 1 ось, максимум 2 если они связаны (например phrasing + placement).
- VARIANT BUDGET: не более 6 вариантов на итерацию.
- NO EXCLAMATION: запрещён символ `!` в любом тексте (prompts, lyrics, notes).
- EVIDENCE REQUIRED: каждая итерация оставляет краткий лог, scorecard, и выбранный winner.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- HOOK_TARGET (что усиливаем)
- LOCKS (immutable constraints set)
  - genre/substyle
  - bpm
  - instruments
  - vocals/lang
  - structure (if defined)
- CURRENT_CANDIDATE (audio/description/lyrics hook snippet)
- PROMPT_PACK (base prompts)

### Inputs (optional)
- USER_FEEDBACK (фразы типа: "слишком прост", "не липнет", "хочу больше дерзости")
- PRIOR_HOOKS (история вариантов)
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE

### Outputs
- HOOK_WINNER
  - hook_id
  - hook_text (if vocal)
  - hook_instruction (placement, rhythm, contour notes)
  - prompt_delta (what changed vs base)
- HOOK_EVIDENCE_PACK
  - variants_list (ids)
  - scorecards
  - decision_rationale (1–2 строки)
- NEXT_ACTION
  - return_to: MUS.TRACK_BUILD_STEP
  - or handoff: MUS.MERGE_SYNTHESIS (если нужно склеить best-of)

---

## [M] HOOK_TARGET MODEL (canonical)
HOOK_TARGET:
- axis_primary: MELODY | RHYTHM | WORDING | DELIVERY | HARMONY_HINT | CALL_RESPONSE
- axis_secondary: optional
- desired_effect: CATCHY | ANTHEMIC | DARK | PLAYFUL | EMOTIONAL | AGGRESSIVE | AIRY
- avoid_list:
  - clichés
  - слишком длинные фразы
  - сложные слова (если нужен прост)
  - перегруз слогов
- success_definition:
  - 1–2 measurable heuristics (например: "можно напеть после 1 прослушивания", "есть 4–8 слов якоря")

---

## [M] LOOP CANON (step-run)

### L0) PRECHECK
- verify LOCKS present
- verify CURRENT_CANDIDATE present
- normalize text fields to remove `!`

If missing:
- FAIL or GAP (см Fail Conditions)

### L1) VARIANT GENERATION
Generate up to VARIANT_BUDGET variants:
- V1..Vn
Each variant must declare:
- changed_axis
- micro-change description
- hook_text snippet (if vocal)
- placement hint (bar/beat or "before drop" etc)

Variant pattern set:
- Pattern A: simplify and sharpen
- Pattern B: contrast and twist (one unexpected word or interval)
- Pattern C: repetition with a turn (A A B A)
- Pattern D: call-response
- Pattern E: rhythmic syncopation
- Pattern F: vowel/phonetic glue (если вокал)

### L2) SCORE
Score each variant 0–5:
- singability
- memorability
- groove_lock (как садится на бит)
- uniqueness
- emotional_hit
- brevity_fit

### L3) SELECT + SYNTHESIS
- pick top 1–2 by score
- synthesize HOOK_WINNER:
  - optionally merge best phrase from runner-up if it does not break lock rules
- write rationale (1–2 lines)

### L4) EXIT CHECK
Exit when:
- memorability >= 4 and singability >= 4
- and brevity_fit >= 3
- or iteration_budget exhausted

Return:
- HOOK_WINNER + evidence pack + next action

---

## [M] MODE_HINT BEHAVIOR

### FAST
- 1 iteration
- up to 3 variants
- pick winner fast, minimal synthesis

### RELEASE_READY
- up to 2 iterations
- up to 5 variants
- synthesis allowed, evidence required

### MASTERPIECE
- up to 3 iterations
- up to 6 variants
- enforce diversity patterns A-F at least once across the loop
- synthesis plus micro-polish of phonetics if vocal

---

## [M] OUTPUT FORMATS

### HOOK_WINNER (canonical)
HOOK_WINNER:
- hook_id: <H001>
- changed_axis: <MELODY|WORDING|...>
- hook_text: "<line1> / <line2 optional>"
- placement_hint: "<where the hook sits>"
- contour_hint: "<up/down/steps or mood note>"
- prompt_delta:
  - add: "<one line>"
  - avoid: "<one line>"

### HOOK_EVIDENCE_PACK (canonical)
HOOK_EVIDENCE_PACK:
- iteration: <1..n>
- variants:
  - id: <V1> score: {singability: x, memorability: y, groove_lock: z, uniqueness: a, emotional_hit: b, brevity_fit: c}
  - id: <V2> ...
- winner: <V?>
- rationale: "<1–2 lines>"

---

## [M] FAIL CONDITIONS
- FAIL_CODE: MUS.FAIL.HOOK_LOOP.MISSING_LOCKS
  - отсутствуют LOCKS или они неполные
- FAIL_CODE: MUS.FAIL.HOOK_LOOP.MISSING_CANDIDATE
  - нет CURRENT_CANDIDATE
- FAIL_CODE: MUS.FAIL.HOOK_LOOP.MISSING_PROMPT_PACK
  - нет PROMPT_PACK
- FAIL_CODE: MUS.FAIL.HOOK_LOOP.INVALID_PUNCT
  - найден символ `!` после нормализации
- FAIL_CODE: MUS.FAIL.HOOK_LOOP.NON_LOCKED_CHANGE
  - попытка сменить genre/bpm/style в ходе лупа

---

## [M] GATES
PASS если:
- LOCKS подтверждены
- есть минимум 2 варианта (FAST допускает 1)
- есть scorecard на каждый вариант
- выбран HOOK_WINNER
- нет символа `!`

FAIL если:
- любое FAIL condition

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.TRACK_BUILD_STEP
- Returns to:
  - MUS.TRACK_BUILD_STEP
- Optional handoff:
  - MUS.MERGE_SYNTHESIS (best-of merge)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 loop canon, scorecard, mode behavior, strict locks
