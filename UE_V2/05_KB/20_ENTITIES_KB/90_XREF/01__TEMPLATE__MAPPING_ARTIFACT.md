# TEMPLATE — XREF MAPPING ARTIFACT (COPY) (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/01__TEMPLATE__MAPPING_ARTIFACT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 90_XREF
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.XREF.TPL.MAP.001
OWNER: SYSTEM
ROLE: Copy-paste template for creating deterministic XREF mapping artifacts (maps/matrices): explicit inputs/outputs, mapping rules, UID-only references, QA checklist, versioning, and deprecation pointers. Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created XREF mapping artifact template: deterministic mapping structure + QA checklist + version/deprecation discipline."
- REASON: "Maps must be explicit and auditable; template prevents ambiguous ‘sometimes’ mappings and link dumps."
- IMPACT: "More reliable cross-entity and cross-KB navigation-of-meaning."
- CHANGE_ID: UE.CHG.2026-01-14.KB.XREF.TPL.001

---

## 0) HOW TO USE
- Copy this template for any XREF map/matrix.
- Replace placeholders.
- Keep all references UID-only.
- This file must not become a RAW registry.

---

## 1) MAPPING HEADER (COPY)
XREF_MAPPING_ARTIFACT:
- MAP_UID:
- MAP_NAME:
- OWNER_XREF_UID:
- TYPE: ENTITY_SCOPE_MAP | ENG_ORC_SPC_MAP | VALIDATION_MATRIX | PIPELINE_MAP | DEPENDENCY_IMPACT_MAP | OTHER
- STATUS:
- LOCK:
- VERSION:
- PURPOSE:
- SCOPE:
  - COVERS:
  - EXCLUDES:
- CHANGE_NOTE:
  - DATE:
  - TYPE:
  - SUMMARY:
  - CHANGE_ID:

---

## 2) INPUTS / OUTPUTS (MUST BE EXPLICIT)
INPUTS:
- REQUIRED:
  - <input>
- OPTIONAL:
  - <input>

OUTPUTS:
- REQUIRED:
  - <output>
- OUTPUT_SCHEMA:
  - <fields/format>

---

## 3) MAPPING RULES (DETERMINISTIC)
MAPPING_RULES:
- Rule 1:
  - IF:
  - THEN:
  - ELSE:
- Rule 2:
  - IF:
  - THEN:

Notes:
- Avoid “usually/most likely”.
- If uncertainty exists, define a STOP condition or a fallback hierarchy rule.

---

## 4) MAPPING TABLE / MATRIX (UID-ONLY)
Use a table-like structure in markdown or bullet lists.

MAPPING_TABLE:
- ROW:
  - KEY (input token):
  - MAPS_TO (output UID(s)):
    - <uid> | WHY
  - CONDITIONS (optional):
  - PRIORITY:
  - NOTES:

Example patterns:
- entity_class -> required scope set
- output_type -> gates/rubrics/validators
- engine_uid -> orchestrator_uid + support_spc_uids

---

## 5) CONFLICT RESOLUTION (IF APPLICABLE)
CONFLICT_RULES:
- If multiple outputs match:
  - priority order:
  - tie-break:
  - stop condition:

---

## 6) QA CHECKLIST (FAST)
MAP_QA_FAST:
- [ ] inputs/outputs defined
- [ ] mapping rules deterministic
- [ ] all references UID-only
- [ ] no duplicate meaning (map overlap) without deprecation note
- [ ] change note updated for modifications
- [ ] hard fail conditions listed

RESULT: PASS/REWORK/FAIL

---

## 7) HARD FAIL CONDITIONS
HARD_FAIL_CONDITIONS:
- UID-only discipline broken
- mapping rules ambiguous (“sometimes”)
- this file becomes a RAW registry / second navigation index
- references point to non-existent UIDs (unverified)
- duplicate map meaning exists without deprecation/pointer plan

---

## 8) DEPRECATION / SUPERSEDE (OPTIONAL)
If this map replaces an older one:
DEPRECATION:
- SUPERSEDES_UID: <uid>
- MIGRATION NOTES:
- EFFECTIVE_DATE:

If this map is replaced later, convert to POINTER-ONLY.

---

## 9) RELATED (UID-ONLY)
RELATED_UIDS:
- <uid> | WHY

--- END.
