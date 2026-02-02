# ORC — TRACK TEST DOC GATE (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
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
UID: UE.ORC.MUSIC.TRACK_TEST_DOC_GATE.001
OWNER: SYSTEM
ROLE: Gate-only orchestrator: runs deterministic doc readiness checks for a track document set using Validation Matrix (CTL→VAL→QA). No ENG usage. Produces auditable verdict trace for packaging eligibility.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt TRACK_TEST_DOC_GATE as pure gate orchestrator: matrix-driven checks only, strict outputs, no hidden logic."
- REASON: "Doc readiness must be auditable and reproducible; avoid any engine-driven implicit behavior."
- IMPACT: "Track doc sets can be accepted/rejected deterministically before packaging."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.DOCGATE.001

---

## 0) PURPOSE (LAW)
Этот ORC принимает набор документов трека и возвращает:
- PASS: “готово к упаковке”
- FAIL: “нельзя упаковывать” + причины + куда вернуть на исправление

Важно: этот ORC не производит контент и не использует ENG.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW.

### 1.2 Matrix-driven only
Все обязательные CTL/VAL/QA берутся из `VALIDATION_MATRIX` по ARTIFACT_TYPE каждого входного документа.

### 1.3 No ENG usage
Запрещено использовать любые ENG методы.
Это gate-only.

### 1.4 Canonical order
READINESS_CHECK_CTL → REQUIRED_CTL → REQUIRED_VAL → REQUIRED_QA → DOC_CONTROLLER_SPC verdict → (optional) MACHINE_ARCHITECT_SPC signoff

### 1.5 Stop conditions
Только:
- RAW missing
- marker not confirmed
- input absent

---

## 2) REQUIRED REFERENCES (RAW)
VALIDATION MATRIX
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

ORC → SPC ownership
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

READINESS CHECK CTL
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 3) INPUTS (MINIMUM)
### 3.1 Required — per track set
- MUSIC_TRACK_CARD RAW
- MUSIC_TRACK_PROMPT RAW
- MUSIC_TRACK_RELEASE RAW

### 3.2 Stop rule
Если отсутствует любой из трёх документов → STOP: input absent

---

## 4) OUTPUTS (STRICT)
- DOC_GATE_VERDICT: PASS | FAIL
- TRACE:
  - applied gates list (ctl/val/qa) per artifact type
  - verdicts per gate
  - violations / fix requirements summary
- RETURN_TO:
  - default ORC to repair (usually ALBUM_TO_TRACK_ORC raw)

---

## 5) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: DOC_CONTROLLER_SPC (primary per ORC→SPC map)  
Gate: READINESS_CHECK_CTL  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — POINTER CHECK (RAW OPEN)
Owner: DOC_CONTROLLER_SPC  
Action:
- verify each RAW pointer opens
Output:
- POINTER_CHECK: PASS/FAIL

If fail → STOP: RAW missing

---

### STEP 2 — RESOLVE REQUIRED GATES (FROM MATRIX)
Owner: DOC_CONTROLLER_SPC  
Action:
- For each doc:
  - determine ARTIFACT_TYPE:
    - MUSIC_TRACK_CARD
    - MUSIC_TRACK_PROMPT
    - MUSIC_TRACK_RELEASE
  - fetch REQUIRED_CTL/VAL/QA from matrix for that type
Output:
- REQUIRED_GATES_PLAN

If any type missing in matrix → STOP: marker not confirmed

---

### STEP 3 — APPLY REQUIRED CTL (PER DOC)
Owner: DOC_CONTROLLER_SPC  
Action:
- apply all REQUIRED_CTL listed by matrix per doc
Output:
- CTL_TRACE + CTL_VERDICTS

If any FAIL → go STEP 6 (FINAL FAIL)

---

### STEP 4 — APPLY REQUIRED VAL (PER DOC)
Owner: REQUIRED VAL entities  
Action:
- apply validators per matrix
Output:
- VIOLATION_RECORDS + VAL_VERDICTS

If any FAIL → go STEP 6 (FINAL FAIL)

---

### STEP 5 — APPLY REQUIRED QA (PER DOC)
Owner: REQUIRED QA entities  
Action:
- apply QA gates per matrix
Output:
- QA_VERDICTS + QA_TRACE

If any FAIL → go STEP 6 (FINAL FAIL)

---

### STEP 6 — FINAL VERDICT (DOC CONTROL)
Owner: DOC_CONTROLLER_SPC  
If all PASS:
- DOC_GATE_VERDICT: PASS
- RETURN_TO: (none)
Else:
- DOC_GATE_VERDICT: FAIL
- RETURN_TO default:
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
- FIX_SUMMARY: concise list

---

## 6) TRACE FORMAT (REQUIRED)
TRACE должен содержать минимум:
- TARGET_SET: {card_raw, prompt_raw, release_raw}
- GATES_APPLIED:
  - for each artifact type: list of ctls, vals, qas (raw links)
- RESULTS:
  - per gate: PASS/FAIL (+short reason)
- VIOLATIONS:
  - list of violation records (or pointers to them)
- DECISION:
  - PASS/FAIL
  - return_to (if fail)

---

## 7) EXTENSION POLICY (STRICT)
- Добавить новый doc в набор = PATCH этого ORC + PATCH матрицы
- Добавить обязательный gate = PATCH Validation Matrix
- Любая “логика” через ENG запрещена (если нужно — делайте отдельный ORC producer, не gate)

---

END.
