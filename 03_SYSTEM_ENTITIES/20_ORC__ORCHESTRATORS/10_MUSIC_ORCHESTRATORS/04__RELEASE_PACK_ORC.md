# ORC — RELEASE PACK (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
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
UID: UE.ORC.MUSIC.RELEASE_PACK.001
OWNER: SYSTEM
ROLE: Deterministic packaging pipeline: assemble a self-contained MUSIC_RELEASE_PACK from validated track artifacts. Matrix-driven CTL/VAL/QA, allowlisted ENG only, explicit ownership and signoff.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt RELEASE_PACK_ORC as strict contract: inputs/outputs, matrix-driven gates, pointer completeness rules, allowlist engines, and deterministic failover."
- REASON: "Release packaging must be auditable and reproducible; prevent broken pointers/credits/rights/collision issues."
- IMPACT: "Release packs become self-contained, validated, and safe to publish; downstream distribution is stable."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.RPACK.001

---

## 0) PURPOSE (LAW)
Этот ORC собирает релизный пакет (PACKAGE) из уже подготовленных артефактов треков:
- Track Card
- Track Prompt
- Track Release
и оформляет один self-contained релизный пакет (MUSIC_RELEASE_PACK), проходящий CTL/VAL/QA по матрице.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW ссылки.

### 1.2 Ownership is mandatory
PRIMARY_SPC берётся только из `ORC → SPC`.

### 1.3 Allowlist engines only
ENG разрешены только по `ENG → ORC` allowlist.

### 1.4 Matrix-driven gates only
Обязательные CTL/VAL/QA берутся из `VALIDATION_MATRIX` по ARTIFACT_TYPE.

### 1.5 Package must be self-contained
Пакет обязан содержать рабочие RAW pointers на все компоненты.
Если любой pointer невалиден → FAIL.

### 1.6 Mandatory gate order
READINESS_CHECK_CTL → REQUIRED_CTL → REQUIRED_VAL → REQUIRED_QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.7 Stop conditions
Только:
- RAW missing
- marker not confirmed
- input absent

---

## 2) REQUIRED XREF (RAW)
PIPELINES
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
Для каждого включаемого трека — рабочие RAW ссылки:
- MUSIC_TRACK_CARD (RAW)
- MUSIC_TRACK_PROMPT (RAW)
- MUSIC_TRACK_RELEASE (RAW)

Также:
- Release intent (single / ep / album pack) — коротко
- Pack target (platform/purpose) — коротко

### 4.2 Optional
- Variants intent (shorts, instrumental, etc) — если реально будет упаковано
- Catalog memory snapshot (если есть)

### 4.3 Stop rule
Если нет ни одного полного набора (card+prompt+release) → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
- MUSIC_RELEASE_PACK (PACKAGE doc) — главный выход
- PACK_MANIFEST (внутри PACKAGE: список всех компонентов и их pointers)

Примечание:
- Обязательные гейты на PACKAGE берутся из `VALIDATION_MATRIX` (ARTIFACT_TYPE: PACKAGE и MUSIC_RELEASE_PACK если выделяешь отдельно).

---

## 6) PACKAGE CONTENT (CANON REQUIREMENTS)
Пакет обязан содержать минимум:
- PACK_ID / UID / VERSION / STATUS / LOCK
- INTENT (что это за релиз)
- COMPONENTS:
  - for each track:
    - CARD_RAW
    - PROMPT_RAW
    - RELEASE_RAW
- CREDITS & RIGHTS block (ссылка/summary на track release metadata)
- VARIANTS block (если есть)
- QA/VAL/CTL trace summary (коротко: что применили и какой verdict)

---

## 7) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (from ORC→SPC map)  
Gate: READINESS_CHECK_CTL  
Input: track sets + release intent  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — INVENTORY & POINTER CHECK
Owner: PRIMARY_SPC  
Action:
- составить inventory по трекам
- проверить что каждый RAW открывается
Output:
- INVENTORY_TABLE
- MISSING_RAW list

If missing → STOP: RAW missing

---

### STEP 2 — APPLY DOC-GATE (OPTIONAL BUT RECOMMENDED)
Owner: PRIMARY_SPC  
Action:
- если пайплайн требует: прогнать TRACK_TEST_DOC_GATE_ORC до упаковки
Output:
- DOC_GATE_VERDICT

Notes:
- Обязательность doc-gate определяется твоим процессом; обязательность CTL/VAL/QA для артефактов всё равно берётся из матрицы.

---

### STEP 3 — ASSEMBLE PACKAGE DRAFT
Owner: PRIMARY_SPC + allowlisted ENG methods  
Constraint:
- ENG использовать только allowlisted (см. ENG→ORC).
Output:
- MUSIC_RELEASE_PACK_DRAFT (with manifest + pointers)

---

### STEP 4 — MATRIX RESOLUTION FOR PACKAGE
Owner: ORC (this doc)  
Action:
- определить ARTIFACT_TYPE = PACKAGE (и/или MUSIC_RELEASE_PACK если ты выделяешь отдельным типом)
- получить REQUIRED_CTL/VAL/QA из `VALIDATION_MATRIX`
Output:
- REQUIRED_GATES_FOR_PACK

If matrix row missing → STOP: marker not confirmed

---

### STEP 5 — APPLY REQUIRED CTL
Owner: PRIMARY_SPC + CTL  
Action:
- применить все REQUIRED_CTL к пакету (и к компонентам, если CTL требует)
Output:
- CTL_VERDICT (PASS/FAIL) + FIX_REQUIREMENTS

FAIL → return to STEP 3 (или к producing ORC, если проблема в компонентах)

---

### STEP 6 — APPLY REQUIRED VAL
Owner: REQUIRED VAL (by matrix)  
Output:
- VIOLATION_RECORDS
- VAL_VERDICT

FAIL → return to producing ORC (обычно ALBUM→TRACK) или к STEP 3 если чисто packaging

---

### STEP 7 — APPLY REQUIRED QA
Owner: REQUIRED QA (by matrix)  
Output:
- QA_VERDICT (PASS/WARN/FAIL)
- FIX_REQUIRED

FAIL → return to producing ORC or STEP 3

---

### STEP 8 — DOC CONTROL + SIGNOFF
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Action:
- doc control целостность
- финальная подпись
Output:
- FINAL MUSIC_RELEASE_PACK (PACKAGE)

---

## 8) FAILOVER (STRICT)
- Если проблема в компонентах трека → вернуть в ALBUM_TO_TRACK ORC
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

- Если проблема только в упаковке → вернуться на STEP 3 и пересобрать пакет.

---

## 9) EXTENSION POLICY (STRICT)
Если добавляем новые типы пакетов/вариантов:
1) обновить `VALIDATION_MATRIX` (PATCH)
2) при необходимости обновить `ENG→ORC` allowlist (PATCH)
3) обновить этот ORC (PATCH)

---

END.
