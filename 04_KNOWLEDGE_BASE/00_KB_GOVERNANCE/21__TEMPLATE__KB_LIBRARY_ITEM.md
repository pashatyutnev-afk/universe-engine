# TEMPLATE — KB LIBRARY ITEM (SHARED ASSET)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/21__TEMPLATE__KB_LIBRARY_ITEM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
INDEX_TYPE: KB_LIBRARY_ITEM_TEMPLATE
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.LIBRARY_ITEM.001
OWNER: SYSTEM
ROLE: Copy template for shared library assets (CHECKLIST/RUBRIC/TEMPLATE/PATTERN/ANTI/EXAMPLE/PROMPT) with mandatory usage rules, gates, and evidence blocks

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB library item template: standardized structure for reusable quality assets across domains."
- REASON: "Shared libraries are the fastest quality amplifier; they must be consistent and auditable."
- IMPACT: "All library assets become connector-ready and enforceable via KB usage gate."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.LIB.001

---

## 0) HEADER FIELDS (FILL THESE)
LIB_TYPE: <checklist | rubric | template | pattern | anti_pattern | example | prompt_lib>
PREFIX: <CL__ | RUBRIC__ | TPL__ | PATTERN__ | ANTI__ | EXAMPLE__ | PROMPT__>
STATE: <UNREAD | READ_ONCE | VERIFIED | DEPRECATED>
TAGS:
- <domain_*>
- <type_*>
- <optional skill_*/gate_*/maturity_*>

---

## 1) PURPOSE
(1–3 строки: что это за актив и какую проблему качества решает.)

---

## 2) USAGE (MANDATORY)
### 2.1 When to use
- ...

### 2.2 When not to use
- ...

### 2.3 How to apply (short)
1)
2)

---

## 3) ASSET BODY (CHOOSE ONE; FILL FULLY)
Выбери соответствующий блок по LIB_TYPE и заполни.

### A) CHECKLIST (CL__)
- [ ] ...
- [ ] ...
PASS IF:
- ...
FAIL IF:
- ...

### B) RUBRIC (RUBRIC__)
CRITERIA:
- PASS: ...
- REWORK: ...
- FAIL: ...
SCORING (optional):
- ...

### C) TEMPLATE (TPL__)
REQUIRED SECTIONS:
- ...
FIELD RULES:
- ...
MINI EXAMPLE OUTPUT:
- ...

### D) PATTERN (PATTERN__)
STRUCTURE:
- ...
WHY IT WORKS:
- ...
WHEN IT FAILS:
- ...

### E) ANTI-PATTERN (ANTI__)
SYMPTOMS:
- ...
WHY IT'S BAD:
- ...
FIX:
- ...
PREVENTION:
- ...

### F) EXAMPLE (EXAMPLE__)
INPUT CONTEXT:
- ...
OUTPUT:
- ...
WHY PASS / WHY FAIL:
- ...
LINKED RULES:
- PATH: ...
- PATH: ...

### G) PROMPT LIB (PROMPT__)
CONTEXT:
- ...
POSITIVE INSTRUCTIONS:
- ...
NEGATIVE INSTRUCTIONS (if applicable):
- ...
PARAMETERS (if applicable):
- ...
EXAMPLE PROMPT:
- ...
EXAMPLE OUTPUT NOTES:
- ...

---

## 4) EVIDENCE (RECOMMENDED)
Если актив опирается на нормы/правила:
- SOURCE MODULES (PATH):
  - PATH: ...
- GATES USING THIS (PATH):
  - PATH: ...

---

## 5) EXAMPLES (MANDATORY FOR RUBRIC/CHECKLIST/TEMPLATE; RECOMMENDED FOR ALL)
### PASS
- ...
### FAIL
- ...
### EDGE (if applicable)
- ...

---

## 6) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: ...
- REL: reinforces -> PATH: ...
- REL: complements -> PATH: ...
- REL: conflicts_with -> PATH: ...   # link to resolution policy
- REL: supersedes -> PATH: ...

XREF:
- XREF: task_to_scope -> PATH: ...
- XREF: validation_matrix -> PATH: ...
- XREF: pipeline_to_scope -> PATH: ...

---

## 7) COMPLIANCE (MANDATORY)
- SOURCE_LOCK: required (no invention)
- KB_USAGE_GATE: this asset must be referenceable via PATH in KB_SOURCES/KB_GATES
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged

--- END.
