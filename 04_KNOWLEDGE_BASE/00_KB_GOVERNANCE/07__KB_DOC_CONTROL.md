# KB DOC CONTROL (GOVERNANCE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_SYSTEM
SYSTEM_OBJ: DOC_CONTROL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.SYS.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: KB-layer doc control: required header fields, allowed values, naming ranges, alias policy, root exceptions

---

## REQUIRED HEADER (MANDATORY)
SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE

## ALLOWED VALUES (STRICT)
STATUS: DRAFT | ACTIVE | DEPRECATED | ARCHIVED
LOCK: OPEN | FIXED
VERSION: X.Y.Z

## NAMING RANGES (HARD)
- Root entrypoint (only one allowed):
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- Governance:
  - `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/NN__*.md`
  - system dictionaries: `90__*..99__*` inside governance
- Realms:
  - `04_KNOWLEDGE_BASE/01__*..08__*.md`
- Topics:
  - `04_KNOWLEDGE_BASE/10_TOPICS/NN__*.md`
  - existence SoT: `10_TOPICS/00__INDEX__TOPICS.md`
- Aliases (non-canon):
  - `04_KNOWLEDGE_BASE/98__*.md` and `04_KNOWLEDGE_BASE/99__*.md` only

## ALIAS POLICY (HARD)
Alias-файлы содержат только pointer на master-index. Никакого контента/правил.

--- END.
