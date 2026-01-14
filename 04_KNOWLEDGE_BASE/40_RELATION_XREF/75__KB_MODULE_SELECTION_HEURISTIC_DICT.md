# KB — MODULE SELECTION HEURISTICS (DICTIONARY) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/75__KB_MODULE_SELECTION_HEURISTIC_DICT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: DICTIONARY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.DICT.MODULE_SELECT_HEUR.075
OWNER: SYSTEM
ROLE: Provides labeled HEURISTICS for choosing which KB module types to load (policy/map/checklist/topic/template/example) based on task needs. Not a hard law; used to improve selection quality while remaining transparent and deterministic.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created a dictionary of labeled heuristics for module type selection during KB runs."
- REASON: "Entities need guidance on selecting modules efficiently; heuristics reduce overload and improve consistency."
- IMPACT: "Better module selection and clearer trace, without pretending heuristics are facts."
- CHANGE_ID: UE.CHG.2026-01-14.KB.DICT.075

---

## 0) PURPOSE (KB)
Provide HEURISTIC guidance for module selection:
- decide which type of module is most useful now
- prevent loading everything
- keep selection explainable

All items here are HEURISTIC, not FACT.

---

## 1) HOW TO USE THIS DICT
- Use after scopes are selected.
- Use alongside loading rules (priority order + limits).
- If a heuristic conflicts with a hard rule/policy, the hard rule wins.

---

## 2) HEURISTICS (LABELED)
### H1 — When to load POLICY/RULE/STANDARD
Use if:
- you must not violate constraints
- task impacts canon/governance/validation
- you need definitions and boundaries first

### H2 — When to load MAP
Use if:
- you need a deterministic selection among options
- scope selection or slot/tag mapping is required
- you need a compact decision table

### H3 — When to load CHECKLIST/GATE
Use if:
- you must validate quality
- pass/rework/fail must be explicit
- you suspect regressions or want consistent standards

### H4 — When to load PLAYBOOK/PROTOCOL
Use if:
- task requires step-by-step execution
- there are branches and recovery paths
- you need a reproducible pipeline

### H5 — When to load TOPIC
Use if:
- you need domain craft knowledge and reasoning context
- you need a concept explanation to choose methods
- you are designing or exploring, but still within scope

### H6 — When to load TEMPLATE
Use if:
- you must produce artifacts quickly and consistently
- you need copyable cards/forms/checklists

### H7 — When to load EXAMPLE
Use if:
- quality is hard to judge without exemplars
- you need good/bad comparisons
- you need calibration of “what passes”

---

## 3) QUICK DECISION TABLE (HEURISTIC)
- High-risk / governance / certification → POLICY + CHECKLIST first
- Selection task (choose scope/pack/variant) → MAP first
- Execution task (do steps) → PROTOCOL/PLAYBOOK first
- Output artifact needed → TEMPLATE early
- Taste/quality calibration needed → EXAMPLE + CHECKLIST

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- heuristics are treated as hard law overriding policies/rules
- heuristics are used to justify skipping governance or trace
- heuristics are used to invent missing modules instead of gap handling

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULE.SCOPE_MODULE_LOAD.074 | WHY: loading rules are the hard constraints
- XREF: UE.KB.README.SCOPE_MAPS.073 | WHY: scope selection happens before module selection
- XREF: UE.KB.PROC.GAP_HANDLING.066 | WHY: missing modules trigger gap handling, not invention

--- END.
