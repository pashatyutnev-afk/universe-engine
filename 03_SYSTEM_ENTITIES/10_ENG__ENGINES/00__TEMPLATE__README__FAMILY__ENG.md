# ENG FAMILY README TEMPLATE (BASE v2)
FILE: 00__TEMPLATE__README__FAMILY__ENG.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_BASE
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Canonical base template for any ENG family README (Realm). Enforces ownership boundaries, canon order, required templates block, and integration with REG/XREF.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

This README defines:
- what the family owns (and does not own)
- how the family is used as a navigation/roadmap
- mandatory template links (base + family overlays)
- required registries and xref indexes
- the canon order of engines inside the family

Existence rule:
> If an engine is not listed in the family README canon order — it does not exist for this family.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: <UPPER_SNAKE_CASE>
FAMILY_CODE: <GOV|CORE|NAR|CHR|WLD|EXP|STY|FMT|PRD|MUS|MET>
FAMILY_CLASS: <GOVERNANCE|CORE|DOMAIN|EXPRESSION|STYLE|PRODUCTION|SOUND|META>
FAMILY_LEVEL: <L1|L2|L3|L4>

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/<NN_<FAMILY_NAME>_ENGINES>/`

README_FILE:
`00__README__<FAMILY_NAME>_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- <what this family owns>

### 2.2 DOES NOT OWN (hard boundaries)
- <what this family does NOT own>

Rule:
> Families must explicitly carve boundaries to prevent duplication with other families.

---

## 3) ROLE MAP (MANDATORY)

Explain roles in the family:
- FOUNDATION
- BUILDER
- VALIDATOR
- BRIDGE
- OUTPUT

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | ... | ... | ... |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Routing law reference:
- Outputs must follow ENG Engine Base routing (ENTITY/PROJECT scope).

Recommended:
- L0: intake
- L1: drafts
- L2: canon
- L3: output packs

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped (typical):
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md` (if entity outputs exist)
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ASSETS.md` (if media/assets exist)

System-scoped (only with governance):
- `00_REG__REGISTRIES/REG.SYS.<NAME>.md`

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped (typical):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`

Optional by family nature:
- `XREF__CAUSE_EFFECT_GRAPH.md` (Expression/Narrative)
- `XREF__ASSET_GRAPH.md` (Production/Music)
- `XREF__EDIT_DECISIONS.md` (Production)
- `XREF__CHANGES.md` (Meta/Governance)

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates (required for every family):
- ENGINE TEMPLATE (base) — 🔗 <raw link to 00__TEMPLATE__ENGINE__ENG.md>
- FAMILY README TEMPLATE (base) — 🔗 <raw link to 00__TEMPLATE__README__FAMILY__ENG.md>

Family overlays (required for this family):
- ENGINE TEMPLATE (family) — 🔗 <raw link to 00__TEMPLATE__ENGINE__<FAMILY>_ENGINES.md>
- README TEMPLATE (family) — 🔗 <raw link to 00__TEMPLATE__README__<FAMILY>_ENGINES.md>

Rule:
> Every family README must contain both base template links + its overlay template links.

---

## 8) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — <Engine 01>  
02 — <Engine 02>  
...

Rule:
> Engine NN in this list must match the NN in engine file name.

---

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Any change in:
- ownership boundaries
- canon order
- template requirements
- registries/xref requirements

Must go through governance pipeline:
- Change Control
- Canon Authority
- Versioning & Memory
- Audit Log

---

## 10) RAW LINK (MANDATORY)

RAW: <raw github link to this file>

---

## FINAL RULE (LOCK)

> This family README is the realm law of the family and the navigation contract.

LOCK: FIXED
