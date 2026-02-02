# MUSIC CONTROLLERS (CTL) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/00__README__MUSIC_CONTROLLERS.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
FAMILY: 10_MUSIC_CONTROLLERS
DOC_TYPE: README (FAMILY)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUSIC.REALM.README.001
OWNER: SYSTEM
ROLE: Canonical usage contract for music CTL policies. Defines how CTL is applied inside ORC, how it interacts with Validation Matrix, and what CTL can/cannot do.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt MUSIC_CONTROLLERS README as policy-only contract aligned with ORC usage + Validation Matrix. No guessing."
- REASON: "Remove ambiguity: CTL must enforce constraints, not generate content. ORC must be able to apply CTL deterministically."
- IMPACT: "Music pipelines can consistently apply policies and produce auditable gate traces."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.MUSIC.README.001

---

## 0) WHAT IS CTL (IN MUSIC)
CTL (Controllers) — это политики, ограничения, лимиты и обязательные гейты.
CTL:
- запрещает/требует/ограничивает,
- формализует “как должно быть”,
- возвращает VERDICT (PASS/FAIL) + причины + требования к исправлению.

CTL НЕ ДЕЛАЕТ:
- не создаёт музыку,
- не пишет финальные тексты трека,
- не выбирает владельцев (это XREF ORC→SPC),
- не выбирает движки (это XREF ENG→ORC),
- не подменяет VAL/QA.

---

## 1) ABSOLUTE RULES
### 1.1 Policy-only
CTL всегда возвращает:
- POLICY_APPLIED (что применили)
- VERDICT (PASS/FAIL)
- REASONS (почему)
- FIX_REQUIREMENTS (что надо исправить)

### 1.2 CTL placement is matrix-driven
Если для ARTIFACT_TYPE матрица требует CTL — ORC обязан применить CTL на соответствующем шаге.
Если матрица не требует CTL — CTL может применяться только как OPTIONAL (и не блокировать), либо через PATCH матрицы.

### 1.3 RAW-only navigation
Только RAW ссылки.

---

## 2) REQUIRED GLOBAL REFERENCES (RAW)
VALIDATION MATRIX (required gates per artifact type)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

PIPELINES (intent → pipeline)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

READINESS CHECK CTL (global mandatory precheck)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 3) HOW ORC USES CTL (CANON FLOW)
1) ORC определяет ARTIFACT_TYPE (card/prompt/release/pack/spec)
2) ORC читает `VALIDATION_MATRIX` и получает REQUIRED_CTL
3) ORC применяет REQUIRED_CTL на соответствующем шаге пайплайна
4) Если CTL=FAIL:
   - ORC обязан остановить выпуск артефакта
   - вернуть на шаг исправления (обычно к производящему ORC)
   - повторить CTL после исправления
5) Только после CTL PASS — ORC идёт в VAL, затем QA, затем Doc Control

---

## 4) MUSIC CTL INVENTORY (CANON LIST, RAW)
00 — MUSIC CONTROLLERS README (this doc)

01 — PROMPT CONTRACT CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

02 — UGC VIRAL RULESET CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

03 — DURATION POLICY CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

04 — RELEASE VARIANTS CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md

05 — POET PD POLICY CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

06 — FINGERPRINT COLLISION THRESHOLDS CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

07 — CATALOG MEMORY CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

08 — AUDIENCE SEGMENTS CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md

09 — QUALITY GATES CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

10 — SUNO PHRASEBOOK CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md

11 — UDIO PHRASEBOOK CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md

12 — NEGATIVE SPEC LIBRARY CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

13 — CREDITS METADATA POLICY CTL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

---

## 5) COMMON APPLICATION POINTS (BY PIPELINE)
- ALBUM→TRACK ORC:
  - PROMPT_CONTRACT_CTL
  - DURATION_POLICY_CTL
  - NEGATIVE_SPEC_LIBRARY_CTL
  - (optional) UGC_VIRAL_RULESET_CTL for shorts variants
- TRACK_TEST_DOC_GATE ORC:
  - QUALITY_GATES_CTL (as policy gate)
- RELEASE_PACK ORC:
  - CREDITS_METADATA_POLICY_CTL
  - FINGERPRINT_COLLISION_THRESHOLDS_CTL
  - RELEASE_VARIANTS_CTL (if variants exist)
- POET_PACK ORC:
  - POET_PD_POLICY_CTL

Примечание: фактическая обязательность берётся из `VALIDATION_MATRIX`.

---

## 6) OUTPUT FORMAT (CTL VERDICT) — REQUIRED
Любой CTL при применении должен давать минимум:
- VERDICT: PASS | FAIL
- POLICY_ID: (file/uid)
- REASONS: bullet list
- FIX_REQUIREMENTS: bullet list
- SCOPE: what artifact(s) it applied to

---

## 7) CHANGE POLICY (LOCK)
- Любые изменения CTL семейства: PATCH + CHANGE_NOTE.
- Если CTL нужно сделать обязательным для типа артефакта — сначала PATCH `VALIDATION_MATRIX`.

---

END.
