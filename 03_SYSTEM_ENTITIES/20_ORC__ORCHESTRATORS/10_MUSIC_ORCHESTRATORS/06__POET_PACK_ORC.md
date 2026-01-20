# ORC — POET PACK (KB-SOURCED CORPUS ROUTE) (CANON)

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
ROLE: Deterministic pipeline that produces a POET_PACK (lyrics corpus package) strictly from KB-tracked sources. Enforces provenance markers, PD/licensing status, and provides handoff artifacts for track generation. No external text allowed without KB source lock markers.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt POET_PACK_ORC: KB-only corpus routing, mandatory provenance markers, PD policy enforcement, and deterministic outputs for downstream track prompts."
- REASON: "Poetry/corpus ingestion was the main ambiguity point (rights + unverifiable sources)."
- IMPACT: "All corpus used by music pipelines becomes auditable, rights-safe, and compatible with CTL/VAL."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.POETPACK.001

---

## 0) PURPOSE (LAW)
Этот ORC делает одну вещь:
создаёт **POET_PACK** (пак поэзии/корпуса) для дальнейшего использования в треках.

Жёсткое правило: **корпус берётся только из KB-tracked sources** и только при наличии provenance markers.

---

## 1) INPUTS (MINIMUM)
### 1.1 Required
- TASK: запрос пользователя (какой поэт/стих/тематика/мод)
- KB_SCOPE_RAW: RAW ссылка(и) на KB источник(и) / KB item(s), откуда берётся корпус

### 1.2 Optional
- LIMITS: лимиты на объём выдержек / количество фрагментов
- STYLE_HINTS: стилистика группы/альбома (без текста источника)

---

## 2) ABSOLUTE LAWS (ENFORCED)
### 2.1 RAW-only
Только RAW ссылки.

### 2.2 KB Source Lock
Нельзя использовать внешний текст без KB provenance.

KB SOURCE LOCK / NO FANTASY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

### 2.3 PD / License status is mandatory
Для корпуса обязателен статус:
- PD_CONFIRMED или LICENSE_CONFIRMED

### 2.4 Stop conditions
Если нет KB_SCOPE_RAW или provenance markers не подтверждены:
- STOP: input absent (KB scope missing)
или
- STOP: marker not confirmed (provenance missing)

---

## 3) REQUIRED REFERENCES (RAW)
KB RULES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

POET PD POLICY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

PD ONLY (VAL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

PROMPT CONTRACT (context consumer)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

---

## 4) OUTPUTS (ARTIFACTS)
ORC обязан выдать POET_PACK как артефакт-документ (минимум):

### 4.1 POET_PACK PASSPORT
- PACK_UID (or placeholder)
- SOURCE_NAME (poet/work)
- KB_SOURCE_RAW (raw link)
- SOURCE_STATUS (PD_CONFIRMED | LICENSE_CONFIRMED)
- SOURCE_NOTE
- FULL_TEXT_ALLOWED (only if applicable)
- EXCERPT_POLICY (how many / how long)
- GENERATED_DATE
- VERSION / STATUS / LOCK

### 4.2 POET_PACK CONTENT (excerpts only by default)
- EXCERPTS: numbered list of short excerpts
- Each excerpt must be short (avoid full text unless FULL_TEXT_ALLOWED exists)

### 4.3 DOWNSTREAM HANDOFF BLOCK (for track prompts)
- LYRICS_MODE: CORPUS
- PROVENANCE BLOCK: (repeat required fields)
- EXCERPT_REFERENCES: list of excerpt IDs
- USAGE_NOTE: how to use (mosaic/quotes/seed)

---

## 5) PIPELINE STEPS (DETERMINISTIC)
### STEP 1 — Intake normalize (ORC)
- verify TASK exists
- verify KB_SCOPE_RAW exists
If missing → STOP.

### STEP 2 — Load KB source (ORC)
- open KB_SCOPE_RAW source item/module
- extract provenance markers:
  - KB_SOURCE_RAW
  - SOURCE_STATUS
  - SOURCE_NOTE
  - FULL_TEXT_ALLOWED (optional)

If missing → STOP: marker not confirmed.

### STEP 3 — Apply POET PD POLICY (CTL)
- run POET_PD_POLICY_CTL against the intended usage
- record CTL trace in POET_PACK (PASS/FAIL)

If FAIL → STOP (policy violation / marker not confirmed depending on CTL output).

### STEP 4 — Validate PD-only (VAL)
- run PD_ONLY_VAL (or equivalent) and record verdict
If FAIL → STOP (policy violation).

### STEP 5 — Build excerpts (ORC)
Default mode: EXCERPTS ONLY
- select excerpts according to LIMITS
- ensure no full text unless FULL_TEXT_ALLOWED present
- ensure no “external text” outside KB source

### STEP 6 — Package POET_PACK (ORC)
- produce POET_PACK PASSPORT + EXCERPTS + HANDOFF BLOCK
- ensure provenance block included verbatim

### STEP 7 — Handoff (ORC)
Return pointers for downstream:
- POET_PACK_RAW: (raw link to the pack)
- ready-to-use PROVENANCE block for MUSIC_TRACK_PROMPT

---

## 6) REQUIRED TRACE (MUST RECORD)
POET_PACK must contain:
- KB_SCOPE_RAW (input)
- KB_SOURCE_RAW (resolved)
- SOURCE_STATUS
- CTL_VERDICT (POET_PD_POLICY_CTL)
- VAL_VERDICT (PD_ONLY_VAL)
- EXCERPT_POLICY

If any trace component missing → FAIL the pack.

---

## 7) FAILOVER (ROUTES)
### 7.1 If KB source missing
- propose creating KB source item via KB templates (not executed here)
- STOP: input absent

### 7.2 If provenance incomplete
- STOP: marker not confirmed

### 7.3 If PD policy fails
- STOP: policy violation
- suggest alternative KB source / alternative excerpt mode

---

## 8) DEFAULT CONSUMER ROUTE (RAW)
ALBUM_TO_TRACK_ORC (uses POET_PACK to fill prompt provenance)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 9) ORC OUTPUT FORMAT (CHAT CONTRACT)
When this ORC runs, it must output:
- MODE
- RESOURCES USED (USING RAW + MARKER FOUND)
- DELIVERABLES (POET_PACK document + pointers)
- GATES (PASS/FAIL reasons)

---

END.
