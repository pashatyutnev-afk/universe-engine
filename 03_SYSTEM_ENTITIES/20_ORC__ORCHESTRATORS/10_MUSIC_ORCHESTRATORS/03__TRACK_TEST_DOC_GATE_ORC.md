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
ROLE: Deterministic doc-gate pipeline: validates track document set (card/prompt/release/pack) against CTL policies + Validation Matrix; produces auditable verdicts and required fixes.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt TRACK_TEST_DOC_GATE as strict doc-gate contract: inputs/outputs, gate order, matrix-driven checks, and deterministic failover."
- REASON: "Prevent publishing or packaging with incomplete/invalid docs. Remove implicit, ad-hoc validation."
- IMPACT: "Doc readiness becomes measurable and repeatable; violations are recorded and routed for repair."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.TDG.001

---

## 0) PURPOSE (LAW)
Этот ORC — не про создание трека, а про проверку документации трека.
Он определяет:
- какие документы входят в “track doc set”,
- какие гейты обязательны (по матрице),
- как фиксировать нарушения,
- когда можно продолжать в RELEASE_PACK.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW ссылки.

### 1.2 Matrix-driven validation only
Обязательные проверки/гейты берутся из `VALIDATION_MATRIX`.
Нельзя добавлять “по ощущениям” обязательные проверки без PATCH матрицы.

### 1.3 Ownership is mandatory
Владельцы берутся только из `ORC → SPC`.

### 1.4 Mandatory gate order
READINESS_CHECK_CTL → required CTL (if any) → required VAL → required QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.5 Stop conditions
Только:
- RAW missing
- marker not confirmed
- input absent

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

QUALITY GATES (music, if applicable)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) INPUTS (MINIMUM)
### 4.1 Required track doc set (at least one track)
Для каждого трека:
- MUSIC_TRACK_CARD (RAW)
- MUSIC_TRACK_PROMPT (RAW)
- MUSIC_TRACK_RELEASE (RAW) — если релизный файл ожидается стадией

### 4.2 Optional
- Release pack draft (если проверяем готовность к упаковке)
- Notes about known issues

### 4.3 Stop rule
Если нет ни одного файла трека для проверки → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
- DOC_GATE_VERDICT (structured verdict, внутри ORC-run output)
- FIX_LIST (deterministic list of required fixes per file)
- READY_FOR_RELEASE_PACK: YES/NO

Примечание:
- Этот ORC не создаёт новые сущности. Если не хватает валидатора/QA — фиксируем GAP.

---

## 6) DOC-GATE CHECKLIST (DETERMINISTIC)
Для каждого входного файла:
1) RAW link opens (existence)
2) Doc control minimum (has header fields, status/lock/version/uid where expected)
3) Apply required gates by `VALIDATION_MATRIX` for the artifact type:
   - REQUIRED_CTL
   - REQUIRED_VAL
   - REQUIRED_QA
4) Record:
   - PASS / WARN / FAIL
   - violations list
   - required rework step (return to which ORC)

---

## 7) PIPELINE STEPS

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (from ORC→SPC)  
Gate: READINESS_CHECK_CTL  
Input: track doc set  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — INVENTORY & EXISTENCE CHECK
Owner: PRIMARY_SPC  
Action:
- собрать список файлов по трекам
- проверить открываемость RAW
Output:
- INVENTORY_TABLE
- MISSING_RAW list

If missing → STOP: RAW missing

---

### STEP 2 — MATRIX RESOLUTION
Owner: ORC (this doc)  
Action:
- определить ARTIFACT_TYPE для каждого файла (CARD/PROMPT/RELEASE/PACK)
- для каждого типа получить REQUIRED_CTL/VAL/QA из `VALIDATION_MATRIX`
Output:
- REQUIRED_GATES_PER_FILE

If matrix row missing → STOP: marker not confirmed (matrix gap)

---

### STEP 3 — APPLY CTL (POLICY)
Owner: PRIMARY_SPC + CTL  
Action:
- применить политики CTL из списка REQUIRED_CTL (и/или quality gates, если указан)
Output:
- CTL_VERDICT per file (PASS/FAIL + notes)

FAIL → return to producing ORC (обычно ALBUM→TRACK) for repair

---

### STEP 4 — APPLY VAL (COMPLIANCE)
Owner: required VAL (by matrix)  
Action:
- запустить проверки соответствия
Output:
- VIOLATIONS per file (0..n)
- VAL_VERDICT (PASS/FAIL)

FAIL → return to producing ORC for repair

---

### STEP 5 — APPLY QA (ACCEPTANCE)
Owner: required QA (by matrix)  
Action:
- применить гейты/скоринг
Output:
- QA_VERDICT (PASS/WARN/FAIL)
- QA_NOTES

FAIL → return to producing ORC for repair

---

### STEP 6 — DOC CONTROL + SIGNOFF
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Action:
- финальная проверка doc control целостности пакета документов
- подпись цепочки
Output:
- READY_FOR_RELEASE_PACK: YES/NO
- DOC_GATE_VERDICT (final)

---

## 8) FAILOVER (STRICT)
Если FAIL:
- нельзя “обойти” гейт
- возвращаемся к производящему ORC:
  - чаще всего `ALBUM_TO_TRACK_ORC` для правки CARD/PROMPT/RELEASE
  - `RELEASE_PACK_ORC` если проблема в упаковке
- после правки повторяем DOC-GATE заново

---

## 9) EXTENSION POLICY
Если нужно добавить новый тип документа в проверку:
1) добавить строку в `VALIDATION_MATRIX` (PATCH)
2) обновить этот ORC (PATCH)
3) обновить PIPELINES map (если нужно)

---

END.
