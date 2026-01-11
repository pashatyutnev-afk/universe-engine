# TPL README REALM — TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/91__TPL__README_REALM.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: README_REALM_TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.README.REALM.001
OWNER: SYSTEM
ROLE: Canonical template for folder/family README realm files (scope, boundaries, rules, and navigation)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created README realm template: scope/boundaries/rules + how-to + canonical links."
- REASON: "Every family folder needs a self-explaining realm entrypoint."
- IMPACT: "Folders become navigable and deterministic."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.README.REALM.001

---

## 0) PURPOSE
This template creates a realm README file for a folder/family/layer.

Realm README responsibilities:
- explain what exists in this folder
- define boundaries (what belongs / what does not)
- define rules used inside the folder (no new laws; only references)
- provide operational navigation (RAW links)

---

## 1) TARGET
TARGET_CLASS: README (REALM)  
TARGET_FOLDER: <folder/family being described>  
REQUIRED_PARENT_INDEX: <index that must list this README>  

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW README FILE)
> IMPORTANT: keep the section order exactly.
> README is not an index; it is a realm entrypoint.

--- CUT HERE ---

# <REALM TITLE> — README (REALM)
FILE: <PATH>

SCOPE: Universe Engine
LAYER: <LAYER>
ENTITY_GROUP: <GROUP>
DOC_TYPE: README
README_TYPE: REALM
LEVEL: <L1|L2|L3>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UID>
OWNER: SYSTEM
ROLE: <one-line: what this realm folder is>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) WHAT THIS REALM IS
- <what the folder represents>
- <who uses it>
- <what outputs are expected>

---

## 1) SCOPE & BOUNDARIES (CRITICAL)
### 1.1 In scope
- <what belongs here>

### 1.2 Out of scope
- <what must never be placed here>

---

## 2) RULES USED (REFERENCES ONLY)
IMPORTANT:
- This README does not create laws.
- It references existing law/standards.

Referenced authorities (RAW preferred):
- <RAW: law or standard>
- <RAW: ruleset>

---

## 3) HOW TO USE (OPERATIONAL)
1) <how to navigate>
2) <how to add new entities here>
3) <how to update indexes>

---

## 4) STRUCTURE (WHAT FILES EXIST HERE)
- Mandatory files:
  - <e.g. index, rules, create flow>
- Optional files:
  - <optional>

---

## 5) NAV (RAW LINKS)
Operational links (RAW):
- <RAW: index>
- <RAW: rules>
- <RAW: create flow>
- <RAW: templates (if any)>

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) README QA CHECKLIST (MANDATORY)
Before marking README ACTIVE:
- Boundaries are explicit (in/out scope)
- Rules section is references-only (no new laws)
- NAV links are present and valid
- Parent index includes this README if required

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
