# ENGINE TEMPLATE — ENG UNIVERSAL (BASE)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG_UNIVERSAL.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
LEVEL: <L1|L2|L3|L4>
STATUS: ACTIVE
VERSION: 1.0.0
ROLE: Universal base template for any ENG engine file (all families)

LOCK: FIXED
UID: <UE.TPL.ENG.UNIVERSAL.ENGINE.###>     # MUST follow 01_SYSTEM_LAW/02__UID_RULES.md

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                  # short stable code (e.g., AUDIT_LOG, STORY_STRUCTURE, LIGHTING)
ENGINE_NUMBER: <NN>                        # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.<FAMILY>.<CODE>.###>   # MUST follow UID_RULES

FAMILY: <NN_FAMILY_ENGINES>
CLASS: <GOVERNANCE|CORE|DOMAIN|EXPRESSION|STYLE|PRODUCTION|SOUND|META>
LEVEL_TAG: <L1|L2|L3|L4>

---

## 1) PURPOSE (LAW)
- What this engine is responsible for (1–5 bullets)
- What it prevents / why it exists
- What it explicitly does NOT do (boundary)

---

## 2) CRITICAL BOUNDARY (ANTI-DUP) — ABSOLUTE
OWNED HERE:
- <owned items...>

NOT OWNED HERE:
- <not owned items...>

BOUNDARY NOTES:
- If output resembles “final domain content”, mark it as INPUT for domain engines unless family explicitly allows final outputs.

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES:
- <1–5 input artifact types>
- ...

PRODUCES:
- <1–5 output artifact types>
- ...

DEPENDS_ON:
- []
# OR:
# - <ENGINE_UID>

OUTPUT_TARGET:
- <where results live in projects/artifacts>

OUTPUT_ARTIFACT_RULE:
- Every PRODUCES type must be compatible with artifact registries / schemas.

---

## 4) METHOD (REQUIRED)
INPUT ASSUMPTIONS:
- <what must already exist / be true>

PROCESS:
- Step 1:
- Step 2:
- Step 3:

QUALITY CRITERIA:
- <how we know output is good>

FAIL MODES:
- <common failures and fixes>

SAFE MODE DEFAULT:
- If uncertainty is high → propose options, do not enforce canon changes.

---

## 5) GATES (HARD) — REQUIRED
- GATE: completeness
  CHECK: identity + mini-contract present
  FAIL: missing contract fields
  FIX: fill contract

- GATE: boundary compliance
  CHECK: stays inside OWNED HERE
  FAIL: output duplicates another family
  FIX: move or mark as INPUT

- GATE: dependency transparency
  CHECK: DEPENDS_ON lists all prerequisites
  FAIL: hidden dependency
  FIX: add DEPENDS_ON + register in dependency system

- GATE: artifact compatibility
  CHECK: PRODUCES types valid
  FAIL: unknown artifact type
  FIX: align to artifact registry

- GATE: reversibility (when changes affect canon/pipeline)
  CHECK: has rollback/backout
  FAIL: no backout
  FIX: add rollback

---

## 6) EXAMPLES (REQUIRED)
GOOD:
- <example output and why it passes gates>

BAD:
- <example violation and why>

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET_UID: <UID> | WHY: <reason>

XREF:
- XREF_UID: <UID> | WHY: <reason>

RULE:
- Canonical RAW links live in INDEX/REGISTRY.
- Engine files are UID-first to avoid “second index”.

--- END.
