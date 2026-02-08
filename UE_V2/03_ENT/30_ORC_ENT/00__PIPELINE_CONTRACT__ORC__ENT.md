FILE: UE_V2/03_ENT/30_ORC_ENT/00__PIPELINE_CONTRACT__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT (REALM)
DOMAIN: ORC_ENT
UID: UE.V2.ENT.PIPE.ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Resolve by KEY via INDEX_MANIFEST__ORC__ENT only. No PATH bypass.

---

## [M] PURPOSE
Единый контракт навигации и handoff для реалма ORC_ENT.
Принимает ROUTE_TOKEN и переводит задачу в нужный под-реалм ORC_ENT по KEY.
Принуждает: Intake → Router → Nav confirm → Step-run → Log hooks → Output pack.

---

## [M] INPUTS (from RUNTIME)
- TASK_TEXT (required)
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE
  - PIPE_SELECTED (optional)
  - DEFAULT_ORC
  - REQUIRED_IDX
  - REQUIRED_CHECKS
  - EXEC_MODE (STEP_RUN)
- OPTIONAL: constraints (platform, duration, style, references)

---

## [M] HARD_RULES
- Единственный справочник адресов: 00__INDEX_MANIFEST__ORC__ENT (KEY → RAW).
- Любой переход в файл/под-реалм — только по KEY из индекса.
- Не грузить деревья. Только: индекс → 1 под-реалм индекс → 1–3 target файла.
- Любая недостача обязательного KEY/RAW/маркерного блока = GAP (не STOP), если TASK_TEXT есть.

---

## [M] REQUIRED RESOURCES (KEYS)
- INDEX_MANIFEST  (self)
- PIPELINE_CONTRACT (this)
- SUB-REALMS (folders, entry by KEY):
  - REALM.GOVERNANCE_ORC_ENT
  - REALM.CORE_ORC_ENT
  - REALM.CREATIVE_ORC_ENT
  - REALM.MUSIC_ORC_ENT
  - REALM.VIDEO_ORC_ENT
  - REALM.DOCS_ORC_ENT
  - REALM.WEB_ORC_ENT
  - REALM.RESEARCH_ORC_ENT
  - REALM.META_ORC_ENT

---

## [M] ROUTING POLICY (deterministic)
### 1) Primary selector
IF ROUTE_TOKEN.PIPE_SELECTED is set:
- Route to the corresponding REALM.* by mapping table below (PIPE_SELECTED → KEY)

ELSE:
- Use ROUTE_TOKEN.DOMAIN and ROUTE_TOKEN.ARTIFACT_TYPE to select REALM.*

### 2) Mapping table (minimal v1)
- DOMAIN in [AUD, MUSIC] OR ARTIFACT_TYPE in [TRACK, LYRICS, IDENTITY] -> KEY: REALM.MUSIC_ORC_ENT
- DOMAIN in [VIS, VIDEO] OR ARTIFACT_TYPE in [VIDEO, SHOT_PLAN, PROMPT_PACK] -> KEY: REALM.VIDEO_ORC_ENT
- DOMAIN in [DOC, KB, SPEC, README] OR ARTIFACT_TYPE in [DOC, TEMPLATE, KB_ITEM] -> KEY: REALM.DOCS_ORC_ENT
- DOMAIN in [WEB, MPS] OR ARTIFACT_TYPE in [HTML_BLOCK, LANDING, SEO_PACK] -> KEY: REALM.WEB_ORC_ENT
- DOMAIN in [RESEARCH, SOURCES] -> KEY: REALM.RESEARCH_ORC_ENT
- DOMAIN in [META, UID, NORMALIZE, DEPRECATE] -> KEY: REALM.META_ORC_ENT
- DOMAIN in [GOV, COMPLIANCE, RISK, APPROVAL] -> KEY: REALM.GOVERNANCE_ORC_ENT
- Fallback (default): KEY: REALM.CORE_ORC_ENT

---

## [M] EXECUTION SEQUENCE (ORC_ENT)
E0) INTAKE CHECK
- Require: TASK_TEXT present
- Require: ROUTE_TOKEN present
- Require: REQUIRED_IDX present

E1) NAV CONFIRM
- Confirm access by KEY:
  - INDEX_MANIFEST
  - PIPELINE_CONTRACT
  - selected REALM.* index (00__INDEX_MANIFEST__... inside sub-realm)
- Confirm ROUTE_TOKEN.REQUIRED_IDX is reachable from NAV.

E2) HANDOFF (sub-realm)
- Open selected REALM.* index-manifest
- Resolve its PIPELINE_CONTRACT (or entrypoint) by KEY inside that sub-realm
- Transfer control to that contract in STEP_RUN mode

E3) STEP_RUN DISCIPLINE
- Follow global STEP_RUN / FOCUS_LOOP / COMMANDS protocols (called by runtime; ORC_ENT does not duplicate them)
- Output must be incremental and "go"-driven.

E4) LOG HOOKS (routing-level)
- Emit routing decision into DECISION_LOG token (who/why/what key)
- Emit GAP card if any required KEY/RAW missing (see GAP section)

---

## [M] GAP POLICY (who issues / who owns)
GAP is issued by: RUNTIME_ROUTER / PIPE routing layer (this contract at E1/E2 when missing KEY/RAW/marker).
GAP is owned by: ROUTE_TOKEN.DEFAULT_ORC (assigned executor).
GAP must contain:
- Missing: KEY / RAW / marker
- Where: E-step (E1/E2)
- Selected realm key (or fallback) and reason
- Minimal fix suggestion (add entry to index or add missing file)

---

## [M] STOP CONDITIONS (strict)
STOP only if:
- TASK_TEXT missing
- ROUTE_TOKEN missing

Everything else is GAP (not STOP).

---

## [M] OUTPUT CONTRACT (what to return)
- ROUTE_TOKEN (unchanged or refined: PIPE_SELECTED + REALM_KEY)
- HANDOFF_TARGET (REALM_KEY + sub-realm contract KEY)
- FIRST_STEP_PROMPT: "го"
- If GAP: GAP_CARD (one, concrete)

---

## [M] SELF-CHECK GATES
PASS if:
- Selected REALM_KEY resolved deterministically
- Sub-realm index reachable
- Handoff target resolved by KEY

GAP if:
- Any required KEY/RAW/marker missing for selected step

STOP if:
- No TASK_TEXT OR no ROUTE_TOKEN
