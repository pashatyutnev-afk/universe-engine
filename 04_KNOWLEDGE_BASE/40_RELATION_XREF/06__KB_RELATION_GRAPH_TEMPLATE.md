# KB — RELATION GRAPH TEMPLATE (REL + XREF) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/06__KB_RELATION_GRAPH_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.REL_GRAPH.006
OWNER: SYSTEM
ROLE: Canonical template to express module relationships as a graph: REL (semantic edges) + XREF (UID-only pointers). Ensures consistent dependency mapping, optional complements, governance edges, and deprecation links.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced canonical REL+XREF graph template for KB modules and maps."
- REASON: "Without a template, relations drift and cannot be audited/visualized consistently."
- IMPACT: "All KB modules can publish a consistent relationship block; enables future graph checks and tooling."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.006

---

## 0) PURPOSE (KB)
Provide a copy-paste template for relationship graph blocks:
- REL: semantic edges (depends_on, complements, governed_by, validated_by, supersedes, etc.)
- XREF: UID-only pointers (identity references)

This template does not include navigation links.
RAW navigation remains in KB master index.

---

## 1) ABSOLUTE RULES
- REL types must use the canonical REL dictionary.
- XREF targets must be UID-only (no URL/PATH).
- WHY is mandatory for every edge.
- Keep graph minimal: 3–10 edges is typical.

---

## 2) WHEN TO USE
Use this template in:
- TOPIC modules (methods)
- MAP modules (selection logic)
- POLICY modules (governance constraints)
- Any module that should be linked into the KB graph

---

## 3) REL GRAPH TEMPLATE (COPY)
REL:
- REL: depends_on -> <TARGET_UID_OR_LABEL> | WHY: <short reason>
- REL: complements -> <TARGET_UID_OR_LABEL> | WHY: <short reason>
- REL: governed_by -> <TARGET_UID_OR_LABEL> | WHY: <short reason>
- REL: constrained_by -> <TARGET_UID_OR_LABEL> | WHY: <short reason>
- REL: validated_by -> <TARGET_UID_OR_LABEL> | WHY: <short reason>
- REL: produces -> <TARGET_UID_OR_LABEL> | WHY: <short reason>
- REL: part_of -> <TARGET_UID_OR_LABEL> | WHY: <short reason>

Deprecation (only when replacing):
- REL: supersedes -> <OLD_UID> | WHY: <replacement reason>
- REL: deprecated_by -> <NEW_UID> | WHY: <pointer to new canon>

Rules:
- Use only relations that apply.
- Do not include empty placeholders in final docs.

---

## 4) XREF BLOCK TEMPLATE (UID-ONLY)
XREF:
- XREF: <TARGET_UID> | WHY: <short reason>
- XREF: <TARGET_UID> | WHY: <short reason>

Rules:
- UID-only; no labels or paths.
- One target per line.

---

## 5) MINIMAL GRAPH PATTERNS (RECOMMENDED)
### Pattern A — Typical TOPIC module
REL:
- REL: governed_by -> UE.KB.DICT.XREF_RULES.005 | WHY: must follow UID-only reference rules
- REL: depends_on -> <PREREQ_UID> | WHY: prerequisite method
- REL: complements -> <OPTIONAL_UID> | WHY: deepening pack
XREF:
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relation vocabulary
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: UID-only reference policy

### Pattern B — MAP module
REL:
- REL: governed_by -> UE.KB.DICT.XREF_RULES.005 | WHY: maps must keep UID-only references
- REL: maps_to -> <LABEL_OR_UID> | WHY: label translation / scope mapping
XREF:
- XREF: <RELATED_MAP_UID> | WHY: companion selection map

### Pattern C — POLICY module
REL:
- REL: governed_by -> <GOV_UID> | WHY: policy hierarchy
- REL: constrained_by -> <CONSTRAINT_UID> | WHY: enforce limits
XREF:
- XREF: <APPLIES_TO_UID> | WHY: typical module that uses the policy

---

## 6) QA CHECKLIST (PASS/FAIL)
PASS IF:
- REL types are from canonical enum
- all edges have WHY
- XREF is UID-only
- no URLs/PATH used as references
- graph is minimal and relevant

FAIL IF:
- custom relation types appear
- missing WHY
- any URL/PATH in XREF
- deprecation edges used without proper replacement logic

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relation types vocabulary
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: UID-only XREF rules

--- END.
