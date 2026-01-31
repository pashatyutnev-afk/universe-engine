# MUSIC VALIDATORS (VAL) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/00__README__MUSIC_VALIDATORS.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 50_VAL__VALIDATORS
FAMILY: 10_MUSIC_VALIDATORS
DOC_TYPE: README (FAMILY)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUSIC.REALM.README.001
OWNER: SYSTEM
ROLE: Canonical usage contract for music validators. Defines how VAL is selected via Validation Matrix, how it is applied inside ORC, and the standard violation record format.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt MUSIC_VALIDATORS README as matrix-driven validation contract aligned with ORC flows. Added standard violation output format."
- REASON: "Remove ambiguity: validators must be applied deterministically and produce auditable violations."
- IMPACT: "Pipelines can enforce compliance consistently; failures route back to producing ORC without guessing."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.MUSIC.README.001

---

## 0) WHAT IS VAL (IN MUSIC)
VAL (Validators) — проверки соответствия (compliance), которые:
- оценивают документ/артефакт по правилам,
- фиксируют нарушения в стандартном формате,
- дают требования к исправлению.

VAL НЕ ДЕЛАЕТ:
- не выполняет упаковку релиза,
- не заменяет QA (приёмка/скоринг),
- не назначает владельцев (это ORC→SPC),
- не выбирает ORC/ENG (это PIPELINES map и ENG→ORC).

---

## 1) ABSOLUTE RULES
### 1.1 Matrix-driven selection
Какие валидаторы обязательны — определяется `VALIDATION_MATRIX` по ARTIFACT_TYPE.
Нельзя “по желанию” делать валидатор обязательным без PATCH матрицы.

### 1.2 Placement order
VAL применяется после CTL (политики), но до QA.
Канон по умолчанию:
READINESS_CHECK_CTL → required CTL → required VAL → required QA → DOC_CONTROL

### 1.3 RAW-only navigation
Только RAW ссылки.

### 1.4 Output format is mandatory
Каждый VAL обязан выдавать VIOLATION RECORD(ы) в стандартном формате.

---

## 2) REQUIRED REFERENCES (RAW)
VALIDATION MATRIX (required gates per artifact type)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

PIPELINES (intent → pipeline selection)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

---

## 3) HOW ORC USES VAL (CANON FLOW)
1) ORC определяет ARTIFACT_TYPE (card/prompt/release/pack/spec)
2) ORC читает `VALIDATION_MATRIX` и получает REQUIRED_VAL
3) ORC вызывает REQUIRED_VAL на соответствующем шаге
4) VAL возвращает:
   - VERDICT (PASS/FAIL)
   - VIOLATION_RECORDS (0..n)
   - FIX_GUIDE (что исправлять)
5) Если FAIL:
   - ORC возвращает на producing step (обычно ALBUM→TRACK или RELEASE_PACK)
   - повторяет VAL после исправления

---

## 4) VIOLATION RECORD FORMAT (REQUIRED)
Каждая запись нарушения должна содержать минимум:

- VIOLATION_ID: (локальный id)
- VALIDATOR_ID: (file/uid of validator)
- ARTIFACT_TYPE: (CARD | PROMPT | RELEASE | PACK | SPEC)
- TARGET_RAW: (raw link to the checked artifact)
- SEVERITY: (S0 BLOCKER | S1 MAJOR | S2 MINOR | S3 NOTE)
- RULE: (short rule statement)
- EVIDENCE: (what exactly failed, concise)
- FIX_REQUIRED: (what must change)
- RETURN_TO: (which ORC pipeline should repair; raw link)

---

## 5) MUSIC VALIDATORS INVENTORY (CANON LIST, RAW)
00 — MUSIC VALIDATORS README (this doc)

01 — HOOK TIMING VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md

02 — UGC READY VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md

03 — REPEAT GUARD VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md

04 — PD ONLY VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

05 — COLLISION BLOCKER VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md

06 — RELEASE PACK READY VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md

07 — NAMING COLLISION VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md

08 — PROMPT FIDELITY VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md

09 — CREDITS RIGHTS VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

10 — VOICE DIVERSITY VAL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md

---

## 6) COMMON RETURN ROUTES (CANON)
- Fix track docs (CARD/PROMPT/RELEASE):
  - return_to: ALBUM_TO_TRACK ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

- Fix release packaging:
  - return_to: RELEASE_PACK ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

- Fix doc readiness checks:
  - return_to: TRACK_TEST_DOC_GATE ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

## 7) CHANGE POLICY (LOCK)
- Любые изменения валидаторов: PATCH + CHANGE_NOTE.
- Чтобы сделать валидатор обязательным для типа артефакта — сначала PATCH `VALIDATION_MATRIX`.

---

END.
