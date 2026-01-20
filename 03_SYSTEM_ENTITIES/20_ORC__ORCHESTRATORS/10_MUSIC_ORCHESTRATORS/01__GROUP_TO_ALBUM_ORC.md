# ORC — GROUP → ALBUM (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
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
UID: UE.ORC.MUSIC.GROUP_TO_ALBUM.001
OWNER: SYSTEM
ROLE: Deterministic planning pipeline: converts group identity/style into an album blueprint (track slots + intent). Produces SPEC-level planning artifacts used by ALBUM→TRACK. No audio outputs.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt GROUP_TO_ALBUM as strict planner: inputs/outputs, allowlisted engines, readiness gate, and deterministic album blueprint contract."
- REASON: "ALBUM→TRACK requires a stable blueprint; avoid vague planning that breaks production."
- IMPACT: "Album planning becomes reproducible and auditable; downstream pipelines receive complete slot spec."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.G2A.001

---

## 0) PURPOSE (LAW)
Этот ORC делает ALBUM BLUEPRINT (SPEC) из данных группы:
- стиль/ДНК/ограничения
- цель альбома и концепт
- N слотов треков с intent и differentiation

Выход — план (SPEC), который потом читает `ALBUM_TO_TRACK_ORC`.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW.

### 1.2 Ownership is mandatory
PRIMARY_SPC берётся только из `ORC → SPC`.

### 1.3 Allowlist engines only
ENG разрешены только по `ENG → ORC`.

### 1.4 No audio outputs
Запрещено выдавать аудио/трек.
Только план (SPEC) и связанные плановые документы.

### 1.5 Stop conditions
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

VALIDATION MATRIX (for SPEC row, if applied)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

---

## 3) REQUIRED CONTROL (RAW)
READINESS CHECK (mandatory)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 4) INPUTS (MINIMUM)
### 4.1 Required
- Group identity/style (RAW link if exists, else user text)
- Album goal (what this album is for) — short
- Album constraints:
  - language constraint (if any)
  - mood/genre intent (short)
  - taboo/exclusions (optional but recommended)
- Track count target: N

### 4.2 Optional
- Audience segment intent (if used later by CTL)
- Poet pack usage intent (if poetry-based)

### 4.3 Stop rule
Если нет group style или album goal или N → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
- ALBUM_BLUEPRINT_SPEC (SPEC doc)
Optional:
- ALBUM_SLOT_TABLE (может быть внутри SPEC)
- PLANNING_NOTES (внутри SPEC)

---

## 6) ALBUM BLUEPRINT SPEC — MINIMUM CONTENT (CANON)
SPEC обязан содержать минимум:
- Album UID/Title placeholder
- Album concept (1–3 строки)
- Global constraints:
  - language
  - mood/genre intent
  - exclusions
- Track slot table (T01..TN):
  - slot intent (mood/energy/story role)
  - hook intent (if known)
  - differentiation note (чем отличается от соседних)
  - lyric approach (original / poetry mosaic / instrumental etc)
- Handoff contract:
  - “This blueprint feeds ALBUM_TO_TRACK_ORC”
  - expected outputs per track (card/prompt/release)

---

## 7) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC  
Gate: READINESS_CHECK_CTL  
Input: group style + album goal + N  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — LOAD GROUP CONSTRAINTS
Owner: PRIMARY_SPC  
Action:
- зафиксировать стиль/ДНК/ограничения в плановом виде
Output:
- GROUP_CONSTRAINTS_BLOCK

---

### STEP 2 — BUILD ALBUM CONCEPT
Owner: PRIMARY_SPC + allowlisted ENG methods  
Constraint:
- использовать только allowlisted ENG (см. ENG→ORC запись для GROUP→ALBUM)
Output:
- ALBUM_CONCEPT_BLOCK (concise)

---

### STEP 3 — BUILD TRACK SLOT TABLE
Owner: PRIMARY_SPC + allowlisted ENG methods  
Action:
- создать T01..TN
- для каждого: intent + differentiation
Output:
- TRACK_SLOT_TABLE

---

### STEP 4 — ASSEMBLE SPEC DRAFT
Owner: PRIMARY_SPC  
Output:
- ALBUM_BLUEPRINT_SPEC_DRAFT

---

### STEP 5 — (OPTIONAL) APPLY SPEC GATES VIA MATRIX
Owner: PRIMARY_SPC  
Action:
- если ты используешь строку ARTIFACT_TYPE: SPEC из матрицы — прогнать REQUIRED_CTL/VAL/QA
Output:
- SPEC_GATES_VERDICT

Fail → return to STEP 4

---

### STEP 6 — HANDOFF TO ALBUM→TRACK
Owner: PRIMARY_SPC  
Output:
- HANDOFF_RAW (pointer to spec)
Handoff target:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 8) FAILOVER (STRICT)
- Если не хватает group style или album goal → STOP: input absent
- Если нужен ENG, которого нет в allowlist → STOP: marker not confirmed (GAP)

---

## 9) EXTENSION POLICY (STRICT)
- Новые поля blueprint = PATCH этого ORC
- Новый ENG нужен = PATCH ENG→ORC allowlist
- Сделать SPEC gates обязательными = PATCH Validation Matrix

---

END.
