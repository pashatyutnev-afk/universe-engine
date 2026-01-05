# XREF INDEX TEMPLATE — UNIVERSAL CROSSREF REGISTRY
FILE: 00__TEMPLATE__XREF_INDEX.md

SCOPE: Universe Engine Repository
LAYER: XREF
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: XREF.TEMPLATE.INDEX
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for an XREF index file that stores, groups, and validates cross-reference records. Enables navigation, auditing, and enforcement of "no hidden dependencies".

---

## 0) PURPOSE (LAW)

XREF Index — это реестр связей (не “просто список”).
Он нужен чтобы:
- видеть зависимости (DEPENDS_ON)
- видеть происхождение (DERIVED_FROM / PRODUCED_BY)
- видеть канон-ссылки (CANON_REF)
- видеть production связи (PRODUCTION_REF)
- видеть граф сущностей (ENTITY_LINK и др.)
- фиксировать замены/перемещения (REPLACED_BY / MOVED_TO / RENAMED_TO)
- ловить конфликты/дубли (CONFLICTS_WITH / DUPLICATES)

### NO HIDDEN LINKS RULE
> Любая связь, влияющая на канон/выход/зависимости, должна быть записана в XREF index.  
> Иначе это hidden link и она invalid.

---

## 1) INDEX IDENTITY (MANDATORY)

INDEX_NAME: <human readable>
INDEX_ID: <XREF.<DOMAIN>.<NAME>>
INDEX_SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
INDEX_OWNER: <team/person/system>
INDEX_STATUS: <ACTIVE|DEPRECATED>
UPDATED_AT: <YYYY-MM-DD>

APPLIES_TO:
- ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>
- LAYERS: [ENG, ORC, CTL, VAL, QA, PRJ, REG, XREF]
- LEVELS: [L0_INTAKE, L1_DRAFT, L2_CANON, L3_OUTPUT, N/A]

---

## 2) REQUIRED FORMAT (STRICT)

Each record MUST be a single normalized line (from XREF record template):

`<A_ID> -> <B_ID> | TYPE:<LINK_TYPE> | SCOPE:<...> | WHY:<...> | BY:<...> | AT:<YYYY-MM-DD>`

Rules:
- One relationship = one line
- No multi-line prose inside record blocks
- Use WHY as 1 short sentence
- AT must be date only (YYYY-MM-DD)

---

## 3) QUICK TABLE VIEW (OPTIONAL BUT RECOMMENDED)

| A_ID | B_ID | TYPE | SCOPE | BY | AT | WHY |
|---|---|---|---|---|---|---|
| <...> | <...> | <...> | <...> | <...> | <...> | <...> |

(If table is used, it must mirror the normalized lines.)

---

## 4) SECTIONS (STANDARD GROUPING)

### 4.1 Dependency Graph
(DEPENDS_ON / REQUIRED_FOR / BLOCKS / UNBLOCKS)

### 4.2 Provenance / Derivation
(DERIVED_FROM / PRODUCED_BY / INPUT_FOR / OUTPUT_OF)

### 4.3 Canon References
(CANON_REF / CANON_SOURCE_OF)

### 4.4 Production References
(PRODUCTION_REF)

### 4.5 Entity Graph
(ENTITY_LINK / MEMBER_OF / LOCATED_IN / OWNS / OWNED_BY)

### 4.6 Change / Replacement / Movement
(REPLACED_BY / MOVED_TO / RENAMED_TO / SPLIT_INTO / MERGED_INTO)

### 4.7 Conflicts / Duplicates
(CONFLICTS_WITH / DUPLICATES / MUTUALLY_EXCLUSIVE)

---

## 5) REQUIRED CONSISTENCY RULES (MANDATORY)

### 5.1 Registry existence
- If A_ID or B_ID is an ENTITY or ARTIFACT:
  it MUST exist in the relevant registry (REG).
- If not, record may exist only with SCOPE:DRAFT and WHY explains missing registry.

### 5.2 Canon protection
- Any link that involves L2_CANON or L3_OUTPUT MUST exist here:
  - L3_OUTPUT must have CANON_REF to L2_CANON
  - L2_CANON changes must have provenance (DERIVED_FROM or PRODUCED_BY)

### 5.3 No orphan outputs
- Any L3_OUTPUT artifact without at least one CANON_REF is invalid.

### 5.4 No hidden dependencies
- If engine declares DEPENDS_ON in its mini-contract, XREF must contain matching DEPENDS_ON records.

---

## 6) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [xref record lines, changes from engines/orchestrators]
  - sources: [ENG mini-contracts, ORC pipelines, manual decisions]
- OUTPUTS:
  - artifacts: [xref index file]
  - target_path: 90_XREF__CROSSREF/<domain>/<index>.md
- REGISTRY_UPDATES:
  - required: YES
  - registries: [REG.XREF.INDEXES]  # placeholder
  - entries_to_add: [this index registered]
- XREF_UPDATES:
  - required: N/A (this is xref index)
  - record_types: []
  - xref_targets: []
- GATES:
  - validators: [VAL.XREF.02.INDEX_CONSISTENCY] # placeholder
  - qa_checks: [QA.XREF.02.NO_ORPHANS]         # placeholder
- ORCHESTRATION:
  - orc_owner: []
  - ctl_enforcers: [CTL.XREF.02.ENFORCE_INDEX_RULES] # placeholder

---

## 7) TEMPLATE BODY (COPY-PASTE)

# <INDEX_NAME>
FILE: <...>

SCOPE: <...>
LAYER: XREF
DOC_TYPE: XREF_INDEX
ENTITY_KIND: <...>
PROJECT_SCOPE: <GLOBAL|PROJECT_ONLY>
OUTPUT_LEVEL: N/A
ID: <XREF...>
STATUS: ACTIVE
VERSION: <x.y>
ROLE: Crossref index for <domain>

UPDATED_AT: <YYYY-MM-DD>
OWNER: <...>

---

## 4.1 Dependency Graph
<records>

## 4.2 Provenance / Derivation
<records>

## 4.3 Canon References
<records>

## 4.4 Production References
<records>

## 4.5 Entity Graph
<records>

## 4.6 Change / Replacement / Movement
<records>

## 4.7 Conflicts / Duplicates
<records>

---

## FINAL RULE (LOCK)
> This XREF index is a canonical registry of relationships for its domain/scope.

OWNER: <...>
LOCK: <OPEN|FIXED>

---

## 8) EXAMPLE RECORDS (REFERENCE)

## Dependency Graph
ENG.NARR.04.SCENE_CONSTRUCTION -> ENG.NARR.02.STORY_STRUCTURE | TYPE:DEPENDS_ON | SCOPE:GLOBAL | WHY:Scene construction requires story structure constraints | BY:MANUAL | AT:2026-01-05

## Canon References
PRJ.ALPHA.FILM.EP01.SHOTLIST -> PRJ.ALPHA.NARR.CANON | TYPE:CANON_REF | SCOPE:PRJ:ALPHA | WHY:Shotlist must reference approved canon | BY:ORC.PROD.01.SHOT_PIPELINE | AT:2026-01-05

## Change / Replacement
ENG.NARR.02.STORY_STRUCTURE -> ENG.NARR.02.STORY_STRUCTURE.V2 | TYPE:REPLACED_BY | SCOPE:GLOBAL | WHY:Updated template structure and interfaces | BY:ENG.GOV.04.CHANGE_CONTROL | AT:2026-01-05
