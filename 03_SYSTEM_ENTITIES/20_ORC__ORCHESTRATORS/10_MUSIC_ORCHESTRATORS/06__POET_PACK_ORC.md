# ORC — POET PACK (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 20_ORC__ORCHESTRATORS
FAMILY: 10_MUSIC_ORCHESTRATORS
LEVEL: L2
DOC_TYPE: ORC (ORCHESTRATOR)
ENTITY_TYPE: ORCHESTRATOR
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUSIC.POET_PACK.001
OWNER: SYSTEM
ROLE: Deterministic pipeline: select/curate poet materials under policy constraints (PD/allowed corpus), package them as inputs for track production. Outputs are SPEC/PACKAGE only.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt POET_PACK as strict contract: inputs/outputs, PD-only boundary, XREF dependencies, allowlisted engines, and signoff chain."
- REASON: "Prevent unclear rights sourcing and non-reproducible poem selection."
- IMPACT: "Poet sources become auditable inputs for music pipelines; selection is deterministic and policy-bound."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.POETPACK.001

---

## 0) PURPOSE (LAW)
Этот ORC собирает “поэт-пак” — набор разрешённых поэтических источников/фрагментов/правил отбора,
который затем используется в ALBUM→TRACK (как вход для lyrics/mosaic).

Этот ORC не создаёт треки. Только входные пакеты (SPEC/PACKAGE).

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW.

### 1.2 Ownership is mandatory
Владельцы берутся только из `ORC → SPC`.

### 1.3 Allowlist engines only
ENG допускаются только по `ENG → ORC` allowlist.

### 1.4 Rights boundary (PD-only)
Если политика требует PD-only, то любые не-PD источники запрещены.
Если нет явного подтверждения правового режима источника → STOP: marker not confirmed (source policy gap).

### 1.5 Mandatory gate order
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.6 Planning-only scope
Запрещены аудио-выходы.
Выходы только: SPEC / PACKAGE.

---

## 2) REQUIRED XREF (RAW)
PIPELINES (intent → pipeline)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

ENG → ORC allowlist
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

ORC → SPC ownership
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

VALIDATION MATRIX
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

---

## 3) REQUIRED CONTROL (RAW)
READINESS CHECK (mandatory)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 4) INPUTS (MINIMUM)
### 4.1 Required
- Selection goal (для чего пак):
  - mood/genre alignment (кратко)
  - language constraint (если есть)
- Rights policy:
  - PD_ONLY = YES/NO (должно быть явно)
- Quantity targets:
  - number of poets (пример: 5–20)
  - excerpt count per poet (пример: 3–10)
- Collision constraints (optional, but recommended):
  - avoid repeating same famous excerpts across catalog (intent-level)

### 4.2 Optional
- Candidate poet list (если уже есть)
- Exclusion list (что нельзя использовать)

### 4.3 Stop rule
Если не задан rights policy (PD_ONLY YES/NO) → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
- POET_PACK_SPEC (SPEC doc)
- POET_PACK_PACKAGE (PACKAGE doc, если нужно упаковать с приложениями)

Gates берём из `VALIDATION_MATRIX` для типов SPEC/PACKAGE.

---

## 6) POET PACK CONTENT REQUIREMENTS (STRICT)
SPEC обязан содержать минимум:
- policy block:
  - PD_ONLY flag
  - selection boundaries
- selection method summary:
  - критерии отбора (коротко)
  - что считается допустимым источником
- poet roster:
  - Poet_ID/Name
  - short rationale (почему подходит)
  - planned excerpt types (theme/tone)
- usage contract:
  - как этот пак используется в ALBUM→TRACK
  - какие поля должны попасть в prompt/lyrics pipeline (без генерации текста)

---

## 7) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (from ORC→SPC map)  
Gate: READINESS_CHECK_CTL  
Input: rights policy + selection goal + targets  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — CANDIDATE SET BUILD (SPC)
Owner: PRIMARY_SPC  
Input: candidate list or open selection within constraints  
Output:
- CANDIDATE_POETS (list)
- EXCLUSION_RULES

Notes:
- Если источники не определены и нет механизма выбора → фиксируем GAP (нельзя угадывать).

---

### STEP 2 — ENGINE METHOD APPLICATION (ENG via allowlist)
Owner: PRIMARY_SPC + ENG methods  
Constraint:
- использовать только allowlisted ENG реалмы для этого ORC (по `ENG→ORC`).
Output:
- SELECTION_METHOD_TRACE (коротко: какие методы применили)
- FILTERED_POETS list

Fail:
- если для отбора нужен ENG, которого нет в allowlist → STOP: marker not confirmed (GAP)

---

### STEP 3 — RIGHTS CHECK (POLICY BOUNDARY)
Owner: PRIMARY_SPC (policy enforcement)
Action:
- если PD_ONLY=YES, то каждый кандидат должен иметь подтверждение PD статуса внутри системы/источника
Output:
- RIGHTS_VERDICT per poet: PASS/FAIL/UNKNOWN

If UNKNOWN and PD_ONLY=YES → STOP: marker not confirmed

---

### STEP 4 — SPEC ASSEMBLY (SPC)
Owner: PRIMARY_SPC  
Output:
- POET_PACK_SPEC draft

---

### STEP 5 — VALIDATION + QA (by matrix)
Owner: relevant VAL + relevant QA  
Apply:
- gates for SPEC (and PACKAGE if produced)
Output:
- VIOLATIONS / QA_VERDICT

FAIL → return to STEP 4

---

### STEP 6 — PACKAGING (optional)
Owner: PRIMARY_SPC  
Output:
- POET_PACK_PACKAGE (manifest + pointers to spec and any attachments)

---

### STEP 7 — DOC CONTROL + SIGNOFF
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Output:
- FINAL SPEC/PACK

---

## 8) EXTENSION POLICY (STRICT)
Если добавляем новый тип источников или новые обязательные проверки:
1) обновить `VALIDATION_MATRIX` (PATCH)
2) обновить `ENG→ORC` allowlist (если нужен новый ENG)
3) затем обновить этот ORC (PATCH)

---

END.
