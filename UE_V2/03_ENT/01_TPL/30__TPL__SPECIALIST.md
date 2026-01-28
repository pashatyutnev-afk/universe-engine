# TPL SPECIALIST — ENTITY TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/30__TPL__SPECIALIST.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_SPECIALIST
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.SPC.001
OWNER: SYSTEM
ROLE: Canonical template to create any SPC Specialist file (role contract + outputs + integration checklist)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created SPC specialist template: canonical header, role boundaries, output pack, and registration checklist."
- REASON: "Specialists must be uniform and easy to invoke by orchestrators."
- IMPACT: "SPC files become deterministic and indexable."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.SPC.001

---

## 0) PURPOSE
This template creates an SPC Specialist entity file:
`03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/<FAMILY>/NN__<SPECIALIST_NAME>_SPC`

It enforces:
- clear role definition (what the specialist does / does not do)
- input/output contract (what it consumes and produces)
- invocation protocol (how to ask it to work)
- output pack format (what artifacts it returns)

---

## 1) TARGET
TARGET_CLASS: SPC  
TARGET_FOLDER: `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/`  
REQUIRED_INDEX_OWNER (GLOBAL): `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS`  
REQUIRED_FAMILY_README: `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/<FAMILY>/00__README__...`

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW SPC FILE)
> IMPORTANT: keep the section order exactly.
> Specialist must be usable without opening other docs.

--- CUT HERE ---

# <SPECIALIST TITLE> — SPECIALIST (SPC)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/<FAMILY_PATH>/NN__<SPECIALIST_NAME>_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: SPECIALIST
SPECIALIST_TYPE: <CREATIVE|NARRATIVE|CHARACTER|WORLD|VISUAL|SOUND_MUSIC|PRODUCTION|PSYCHOLOGY|RESEARCH|MARKETING|META|TOP_GOVERNANCE>
LEVEL: <L1|L2|L3>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.SPC.<FAMILY>.<NAME>.<NNN>>
OWNER: SYSTEM
ROLE: <One-line: what this specialist guarantees>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) ROLE (LAW)
- PRIMARY MISSION: <what the specialist is responsible for>
- GUARANTEE: <what output quality it guarantees>
- FAILURE MODES: <what can go wrong if misused>

---

## 1) SCOPE & BOUNDARIES (CRITICAL)
### 1.1 In scope
- <bullet list>

### 1.2 Out of scope
- <bullet list>

### 1.3 Interfaces with neighbors
- Works with: <ENG/ORC/CTL/VAL/QA references or names>
- Must not duplicate: <neighbor specialist/engine responsibility>

---

## 2) INPUTS / OUTPUTS (SPECIALIST CONTRACT — MANDATORY)
CONSUMES:
- <1..5 input artifact types or prompts>

PRODUCES:
- <1..5 outputs: texts/specs/checklists/briefs etc.>

DEPENDS_ON:
- [] OR
- - <RAW links to prerequisite entities (optional)>

OUTPUT_TARGET:
- <where the produced artifacts must be placed (project path / pack / index)>

---

## 3) INVOCATION PROTOCOL (HOW TO ASK THIS SPC)
### 3.1 Required prompt fields (minimal)
- CONTEXT: <short>
- GOAL: <what to achieve>
- CONSTRAINTS: <must-follow rules>
- OUTPUT FORMAT: <what to return>

### 3.2 Default assumptions (if not provided)
- <assumption 1>
- <assumption 2>

### 3.3 Negative spec (what to avoid)
- <avoid 1>
- <avoid 2>

---

## 4) OUTPUT PACK (STANDARD)
Return outputs as a pack with:
1) SUMMARY (1–5 lines)
2) MAIN OUTPUT (full)
3) OPTIONS (2–5 alternatives if applicable)
4) QA NOTES (risks, weak spots, what to improve)
5) NEXT ACTIONS (what to do next in pipeline)

---

## 5) QUALITY BAR (ACCEPTANCE)
- <acceptance criteria bullets>
- <what “good” must include>
- <what “bad” looks like>

---

## 6) INTEGRATION (WHEN USED IN PIPELINES)
- Typical ORC stages where this SPC is invoked: <stage labels>
- Typical CTL policies affecting it: <policy names / RAW>
- Typical VAL/QA gates after it: <names / RAW>

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX + REGISTRATION CHECKLIST (MANDATORY)
When a new SPC file is created:
1) Add RAW link to `30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS`
2) Ensure correct FAMILY folder + correct numbering `NN__`
3) Ensure FAMILY README exists and includes the specialist in order
4) If specialist is used by ORC pipelines → ensure ORC references are updated (if needed)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
