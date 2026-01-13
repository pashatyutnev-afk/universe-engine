# LAW — SPC GOVERNANCE & SIGNOFF (UNIVERSAL)

MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
OWNER: SYSTEM
SCOPE: Universal (all domains)

## PURPOSE (LAW)
Восстановить архитектуру:
- SPC = судьи/руководители/арбитры (решают что делать и по каким правилам)
- ENG = исполнители (делают по решению SPC)
- VAL/QA = гейты (PASS/FAIL)
Без SPC_SIGNOFF результат не считается готовым.

---

## ROLES (HIERARCHY)
### TIER 0 — TOP GOVERNANCE SPC (always-on judges)
- MACHINE_ARCHITECT_SPC (final arbiter)
- GOVERNANCE_OWNER_SPC (laws/locks/what is canon)
- DOC_CONTROLLER_SPC (deliverable format + naming/versioning)
- PIPELINE_ARCHITECT_SPC (pipeline/order/gates)
- INTEGRATION_PACKER_SPC (packaging/export/release-pack)

### TIER 1 — DOMAIN SPC (selected per task)
Examples: Prompt Architect, Album Showrunner, Audio QA, Poet Juice Editor, Mosaic Editor, etc.

### TIER 2 — EXECUTION
- ORC orchestrates steps
- ENG executes creation

---

## MANDATORY PIPELINE (NO BYPASS)
Every task that creates/adapts/validates a deliverable MUST follow:
1) SPC_JURY
2) ENG_BUILD
3) VAL/QA_GATES
4) SPC_FINAL (SPC_SIGNOFF)

### SPC_JURY (required output)
- decision: theme/scope/lexicon/ban-list/constraints
- acceptance criteria (PASS definition)

### ENG_BUILD (required output)
- build deliverable strictly from SPC_JURY decisions

### VAL/QA_GATES (required output)
- PASS/FAIL per gate
- list of violations (if FAIL)

### SPC_FINAL (required output)
- FINAL: PASS/FAIL
- allowed fixes (max 1–3)
- if FAIL → return to ENG_BUILD

---

## STOP RULE (CANON)
If SPC_FINAL != PASS:
- deliverable cannot be marked CANON
- publish/release is blocked

---

## UNIVERSAL RESPONSE FORMAT (CHAT ENFORCEMENT)
Assistant must always output:
1) MODE
2) RESOURCES USED (USING RAW + MARKER FOUND)
3) DELIVERABLES (SPC_JURY → ENG_BUILD → VAL/QA → SPC_FINAL)
4) GATES (PASS/FAIL)

---

## TRIGGERS (AUTO-ON)
SPC_JURY must be invoked automatically when task includes:
- “сделай/собери/адаптируй/проверь/валидация/качество/пайплайн”
- any release or publication workflow
- any repeated-failure or “AI feels fake” issue
