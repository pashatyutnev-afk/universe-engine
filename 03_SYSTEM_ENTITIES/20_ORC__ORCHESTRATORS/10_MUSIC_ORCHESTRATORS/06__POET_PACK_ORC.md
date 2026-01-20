# ORC — POET PACK (PD-ONLY) (CANON)

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
ROLE: Deterministic PD-only corpus pipeline: selects poems/excerpts from KB-approved sources, produces a reusable POET_PACK_SPEC (PD-only) for downstream music prompts. Enforces KB source lock and PD policy via CTL/VAL + matrix.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt POET_PACK_ORC as strict KB-bound PD-only pipeline: KB entrypoints, source lock, CTL/VAL enforcement, and reusable output spec."
- REASON: "Prevent copyright-risk ingestion and 'fantasy sources'. Ensure poet packs are auditable and reusable."
- IMPACT: "Poetry selection becomes compliant: PD-only guaranteed; downstream prompts can safely reference approved text."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.POETPACK.001

---

## 0) PURPOSE (LAW)
Этот ORC создаёт POET_PACK_SPEC — документ-спеку набора поэзии/выдержек, которые:
- происходят только из PD (public domain) или явно разрешённых источников по политике,
- имеют доказуемое происхождение (KB provenance),
- пригодны для многократного использования в треках/альбомах.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW.

### 1.2 KB source lock (no fantasy)
Нельзя использовать источники, которых нет в KB/политике.
Нельзя “угадывать” происхождение текста.

### 1.3 PD-only enforcement
Если политика требует PD-only → обязательное выполнение PD policy CTL + PD-only VAL.

### 1.4 Matrix-driven gates
Обязательные CTL/VAL/QA берутся из `VALIDATION_MATRIX` по ARTIFACT_TYPE: POET_PACK_SPEC.

### 1.5 Allowlist engines only
ENG разрешены только по `ENG → ORC` allowlist.

### 1.6 Stop conditions
Только:
- RAW missing
- marker not confirmed
- input absent

---

## 2) REQUIRED REFERENCES (RAW)

### 2.1 Knowledge Base entrypoints
KB MASTER INDEX
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

KB RULES
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

KB SOURCE LOCK (NO FANTASY)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

### 2.2 XREF maps
VALIDATION MATRIX
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

ENG → ORC allowlist
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

ORC → SPC ownership
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

---

## 3) REQUIRED POLICY & VALIDATION (RAW)
POET PD POLICY (CTL)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

PD ONLY (VAL)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

---

## 4) INPUTS (MINIMUM)
### 4.1 Required
- Poet selection intent:
  - poet name(s) or era (if known)
  - theme/mood keywords (short)
  - language constraint
- Usage intent:
  - for which group/album/track (optional pointer)
  - target style (short)
- KB source scope:
  - which KB module(s) contain approved sources (RAW links if user provides)

### 4.2 Stop rule
Если нет poet selection intent или нет KB source scope → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT)
- POET_PACK_SPEC (ARTIFACT_TYPE: POET_PACK_SPEC)

---

## 6) POET_PACK_SPEC — MINIMUM CONTENT (CANON)
POET_PACK_SPEC обязан содержать:
- UID / VERSION / STATUS / LOCK
- Poet identity (as declared)
- Scope & intent (theme/mood/use)
- SOURCE_PROVENANCE (REQUIRED):
  - KB module/item RAW pointer(s)
  - source record reference (if present)
  - note of PD status basis (per policy)
- CORPUS ITEMS (list):
  - item_id
  - excerpt (short, within allowed policy)
  - tags (mood/imagery)
  - collision note (avoid repeating same famous lines)
- USAGE GUIDANCE:
  - how to blend excerpts (mosaic allowed or not)
  - constraints for prompts (no full poem dump unless policy allows)

---

## 7) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (OWNERSHIP + READINESS)
Owner: PRIMARY_SPC (from ORC→SPC map)  
Action:
- confirm KB scope links present
- confirm PD policy applies
Output:
- PRECHECK: PASS/FAIL

Fail → STOP

---

### STEP 1 — LOAD KB SOURCES (LOCKED)
Owner: PRIMARY_SPC  
Action:
- open KB scope modules/items by RAW
- build source candidate list
Output:
- KB_SOURCE_CANDIDATES

If any required KB pointer missing → STOP: RAW missing

---

### STEP 2 — APPLY PD POLICY CTL (REQUIRED)
Owner: POET_PD_POLICY_CTL  
Action:
- enforce what is considered “PD acceptable” per policy
Output:
- CTL_VERDICT + REQUIREMENTS

FAIL → STOP: marker not confirmed

---

### STEP 3 — SELECT CORPUS ITEMS (ALLOWLISTED ENG)
Owner: PRIMARY_SPC + allowed poet corpus engines  
Constraint:
- ENG only from allowlist (Poet corpus engines)
Action:
- pick excerpts/items from KB sources
- avoid duplicates / famous-line collisions when possible
Output:
- CORPUS_DRAFT

---

### STEP 4 — APPLY PD ONLY VAL (REQUIRED)
Owner: PD_ONLY_VAL  
Action:
- validate provenance and PD compliance
Output:
- VAL_VERDICT + VIOLATION_RECORDS (if any)

FAIL → return to STEP 3 (or STEP 1 if sources invalid)

---

### STEP 5 — MATRIX GATES FOR POET_PACK_SPEC
Owner: PRIMARY_SPC  
Action:
- resolve row ARTIFACT_TYPE: POET_PACK_SPEC in Validation Matrix
- apply required CTL/VAL/QA listed there
Output:
- GATE_TRACE + FINAL_VERDICT

If matrix row missing → STOP: marker not confirmed

---

### STEP 6 — PACKAGE OUTPUT SPEC
Owner: PRIMARY_SPC  
Output:
- POET_PACK_SPEC (final)

---

## 8) FAILOVER (STRICT)
- Invalid/unknown source provenance → STOP or return to STEP 1
- PD policy mismatch → STOP: marker not confirmed
- Need new KB source module not present → STOP: input absent (user must provide KB scope link) or propose creating KB module via KB templates.

---

## 9) EXTENSION POLICY (STRICT)
- Change PD rules = update POET_PD_POLICY_CTL (PATCH)
- Change required gates = update Validation Matrix (PATCH)
- Add new poet corpus engines = update ENG→ORC allowlist (PATCH)

---

END.
