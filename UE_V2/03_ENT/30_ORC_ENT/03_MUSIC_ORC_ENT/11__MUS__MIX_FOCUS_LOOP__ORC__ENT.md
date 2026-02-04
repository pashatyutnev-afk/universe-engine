FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/11__MUS__MIX_FOCUS_LOOP__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.MIX_FOCUS_LOOP.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_MIX_FOCUS_LOOP
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.MIX_FOCUS_LOOP.001

---

## [M] PURPOSE
Итеративно стабилизирует микс-цели: баланс, энергия, читаемость, плотность, punch и переводимость.
Работает как локальный loop внутри track-build: задаёт mix targets, генерирует варианты (или инструкции на правки), оценивает, выбирает победителя, фиксирует evidence.
Не меняет сам трек по смыслу. Не ломает жанр и стиль. Меняет только микс-слой и его параметры.

---

## [M] HARD_RULES
- CONSTRAINT LOCK: genre/substyle, bpm, arrangement, hook/structure нельзя менять в лупе.
- MIX SCOPE ONLY: правим баланс, динамику, EQ, saturation, spatial, transient, loudness target.
- ONE-AXIS-AT-A-TIME: в одной итерации меняем 1 ось, максимум 2 если они связаны (EQ + masking).
- VARIANT BUDGET: не более 5 вариантов на итерацию.
- AVOID OVERPROCESS: запрещены резкие “всё в лимитер” решения без причины.
- EVIDENCE REQUIRED: каждая итерация оставляет краткий лог, scorecard, и выбранный winner.
- TEXT HYGIENE: запрещён символ `!` в любых текстовых полях (notes, prompts, labels).

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- LOCKS (immutable constraints set)
  - genre/substyle
  - bpm
  - arrangement core (main instruments, hook placement)
- CURRENT_MIX_STATE
  - description (or tool settings summary)
  - reference notes (what is wrong)
- MIX_TARGETS (initial)
- PROMPT_PACK (if using generative tooling)

### Inputs (optional)
- USER_FEEDBACK (например: “грязно”, “вокал тонет”, “слишком ярко”, “нет панча”)
- REFERENCES (safe references list: 1–3 pointers, not mandatory)
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE
- DELIVERY_CONTEXT
  - platform: streaming | youtube | club | tiktok
  - loudness_policy: conservative | normal | loud

### Outputs
- MIX_WINNER
  - mix_id
  - change_axis
  - applied_moves (bullet list)
  - target_summary (loudness, tonal balance, space)
  - prompt_delta (if applicable)
- MIX_EVIDENCE_PACK
  - variants_list (ids)
  - scorecards
  - decision_rationale (1–2 строки)
- NEXT_ACTION
  - return_to: MUS.TRACK_BUILD_STEP
  - or handoff: MUS.MERGE_SYNTHESIS (если нужно склеить best-of moves)

---

## [M] MIX_TARGETS MODEL (canonical)
MIX_TARGETS:
- loudness_target: (LUFS policy, relative, no hard numbers required)
- peak_policy: safe headroom policy
- tonal_balance:
  - low: controlled | heavy | lean
  - mid: clear | warm | dense
  - high: smooth | bright | airy
- vocal_presence: forward | balanced | tucked (if vocal)
- punch: soft | medium | hard
- width: narrow | natural | wide
- depth: flat | moderate | deep
- clarity_goal: “what must be clearly heard first”
- avoid_list:
  - harsh highs
  - muddy low-mids
  - pumping artifacts
  - brittle saturation

---

## [M] LOOP CANON (step-run)

### L0) PRECHECK
- verify LOCKS present
- verify CURRENT_MIX_STATE present
- normalize text fields to remove `!`
- derive MIX_TARGETS if missing (default: balanced + clear + natural)

If missing:
- FAIL or GAP (см Fail Conditions)

### L1) DIAGNOSE
Create DIAG_MAP (short):
- masking suspects
- harshness zones
- low-end issues
- dynamic issues
- stereo/phase risks
- vocal/instrument priority (if applicable)

### L2) VARIANT PLAN (up to VARIANT_BUDGET)
Generate V1..Vn.
Each variant must declare:
- change_axis: EQ | DYNAMICS | SPACE | SATURATION | TRANSIENTS | STEREO | MASTER_BUS
- micro-moves (3–6 bullets)
- expected effect (1 line)
- risk note (1 line)

Variant pattern set:
- Pattern A: clarity-first (de-mud + presence)
- Pattern B: punch-first (transients + controlled comp)
- Pattern C: glue-first (bus cohesion, subtle saturation)
- Pattern D: space-first (depth, reverb discipline)
- Pattern E: loudness-safe (translation + headroom)

### L3) SCORE
Score each variant 0–5:
- clarity
- punch
- tonal_balance
- translation (phone, small speakers)
- fatigue (listening comfort)
- genre_fit

### L4) SELECT + STABILIZE
- pick top 1 by score
- optionally borrow 1 move from runner-up if it does not break lock rules
- generate MIX_WINNER
- write rationale (1–2 lines)

### L5) EXIT CHECK
Exit when:
- clarity >= 4 and translation >= 4
- and fatigue >= 3
- and genre_fit >= 4
- or iteration_budget exhausted

Return:
- MIX_WINNER + evidence pack + next action

---

## [M] MODE_HINT BEHAVIOR

### FAST
- 1 iteration
- up to 2 variants
- minimal move list, quick winner

### RELEASE_READY
- up to 2 iterations
- up to 4 variants
- enforce translation and fatigue scoring

### MASTERPIECE
- up to 3 iterations
- up to 5 variants
- must include at least 3 different pattern families across loop (A–E)
- extra stabilization pass: tiny EQ and gain staging polish

---

## [M] OUTPUT FORMATS

### MIX_WINNER (canonical)
MIX_WINNER:
- mix_id: <M001>
- change_axis: <EQ|DYNAMICS|...>
- applied_moves:
  - "<move1>"
  - "<move2>"
  - "<move3>"
- target_summary:
  - loudness: "<policy>"
  - tonal: "<short>"
  - space: "<short>"
- prompt_delta:
  - add: "<one line>"
  - avoid: "<one line>"

### MIX_EVIDENCE_PACK (canonical)
MIX_EVIDENCE_PACK:
- iteration: <1..n>
- variants:
  - id: <V1> score: {clarity: x, punch: y, tonal_balance: z, translation: a, fatigue: b, genre_fit: c}
  - id: <V2> ...
- winner: <V?>
- rationale: "<1–2 lines>"

---

## [M] FAIL CONDITIONS
- FAIL_CODE: MUS.FAIL.MIX_LOOP.MISSING_LOCKS
  - отсутствуют LOCKS или они неполные
- FAIL_CODE: MUS.FAIL.MIX_LOOP.MISSING_STATE
  - нет CURRENT_MIX_STATE
- FAIL_CODE: MUS.FAIL.MIX_LOOP.MISSING_TARGETS
  - MIX_TARGETS не заданы и не выводятся из контекста
- FAIL_CODE: MUS.FAIL.MIX_LOOP.INVALID_PUNCT
  - найден символ `!` после нормализации
- FAIL_CODE: MUS.FAIL.MIX_LOOP_NON_LOCKED_CHANGE
  - попытка поменять arrangement/genre/bpm/structure

---

## [M] GATES
PASS если:
- LOCKS подтверждены
- есть минимум 2 варианта (FAST допускает 1)
- есть scorecard на каждый вариант
- выбран MIX_WINNER
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
  - MUS.MERGE_SYNTHESIS

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 loop canon, scoring model, mode behavior, strict locks
