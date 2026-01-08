# ENGINE TEMPLATE — GOVERNANCE ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.GOV.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for governance-class ENG engines (audit/control/enforcement)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>               # e.g., AUDIT_LOG, CANON_AUTHORITY
ENGINE_NUMBER: <NN>                     # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.GOV.<CODE>.NNN>

STATUS_INTENT:
- What it governs (1 line)
- What it enforces (1 line)

---

## 1) PURPOSE (LAW)
Зачем существует этот governance-движок:
- какой риск/хаос он предотвращает
- какой порядок/правило он закрепляет
- какой артефакт/решение он делает обязательным

---

## 2) SCOPE & AUTHORITY
SCOPE:
- Applies to: <layers / entity classes / pipelines>
- Excludes: <what is explicitly out of scope>

AUTHORITY:
- Hard authority: <what it can block/forbid>
- Soft authority: <what it recommends>

BOUNDARIES (ANTI-DUP):
- This engine owns: <areas>
- NOT owned here: <areas + where it lives>

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

DECISION_OUTPUT (REQUIRED):
- DECISION: <APPROVE | REJECT | REQUEST_CHANGES | ESCALATE | RECORD_ONLY>
- DECISION_CRITERIA: <bullets, measurable>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where the produced artifact/record must live> (descriptive, no path-nav)

---

## 4) ENFORCEMENT RULES (HARD)
ENFORCEMENT_MODE:
- HARD_BLOCK | SOFT_WARN | RECORD_ONLY

BLOCKER CONDITIONS (if HARD_BLOCK):
- Condition:
  WHY:
  HOW TO FIX:

WARN CONDITIONS (if SOFT_WARN):
- Condition:
  WHY:
  SUGGESTED FIX:

---

## 5) REQUIRED RECORDS (AUDIT / LOG)
This engine must produce records when it runs:

RECORD_FORMAT:
- RECORD_UID: <uid or generated>
- TIMESTAMP: <iso>
- SUBJECT_UID: <uid of thing being audited>
- ACTION: <created/changed/deprecated/etc>
- RESULT: <pass/fail/approve/reject>
- WHY: <short>

MINIMUM FIELDS (ABSOLUTE):
- SUBJECT_UID
- ACTION
- RESULT
- WHY

---

## 6) CHECKLIST (OPERATOR VIEW)
Before run:
- ...

During run:
- ...

After run:
- ...

FAIL-SAFE:
- What happens if inputs missing?
- What happens if conflict detected?

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

RULE:
- No PATH navigation inside content.
- If a clickable reference is needed, use RAW in indexes/registries, not here.

---

## 8) CHANGE NOTES (OPTIONAL)
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:

--- END.
