# KB — SCOPE SELECTION MAPS README (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/73__KB_SCOPE_SELECTION_MAP_README.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.SCOPE_MAPS.073
OWNER: SYSTEM
ROLE: Explains how to use KB scope selection maps deterministically (entity→scope, task→scope), how to interpret outputs, and how to update maps without breaking determinism.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created README for deterministic scope selection maps usage and maintenance."
- REASON: "Maps are only useful if entities apply them consistently; README ensures shared understanding and correct order."
- IMPACT: "Fewer scope selection errors, less missing knowledge, and faster correct module loading."
- CHANGE_ID: UE.CHG.2026-01-14.KB.README.073

---

## 0) PURPOSE (KB)
Scope selection maps answer:
- which KB scopes should be loaded for a given entity or task
so entities do not rely on intuition.

This README defines:
- map order
- expected outputs
- safe update rules

---

## 1) MAP TYPES (WHAT EXISTS)
Two core map types:
- ENTITY→SCOPE map: chooses scopes based on entity class and domain
- TASK→SCOPE map: chooses scopes based on task intent/classification

Rule:
- Use ENTITY→SCOPE first, then refine with TASK→SCOPE when needed.

---

## 2) DEFAULT ORDER (DETERMINISTIC)
Step 1: Load governance baseline scope.
Step 2: Apply ENTITY→SCOPE map:
- returns REQUIRED_SCOPES + OPTIONAL_SCOPES
Step 3: If task is non-trivial, apply TASK→SCOPE map:
- adds/refines scopes (e.g., QA, production, marketing)
Step 4: Open modules for selected scopes via master index.
Step 5: Emit trace.

---

## 3) EXPECTED MAP OUTPUTS
Each map should output:
- REQUIRED_SCOPES (must load)
- OPTIONAL_SCOPES (load if needed)
- EXCLUSIONS (scopes to avoid)
- NOTES (why)

Maps must not output RAW links (navigation belongs to master index).

---

## 4) COMMON FAILS
Fail: skipping maps
- Fix: enforce navigation quickstart and run trace review

Fail: using too many scopes
- Fix: keep scopes minimal; use optional scopes only when needed

Fail: missing a critical scope (e.g., QA)
- Fix: update task→scope map rules; add missing mapping

---

## 5) SAFE UPDATE RULES
When updating maps:
- keep determinism (no vague “sometimes”)
- add explicit conditions
- update audit trail for major changes
- ensure no scope boundary violations (don’t load unrelated domains)

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- entity runs without governance scope
- maps output URLs/RAW links
- maps become narrative text without deterministic rules
- map updates are made without audit when impacting many entities

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.PLAYBOOK.NAV_QUICKSTART.062 | WHY: quickstart defines run sequence using maps
- XREF: UE.KB.MAP.ENTITY_SCOPE.002 | WHY: entity→scope map
- XREF: UE.KB.MAP.TASK_SCOPE.001 | WHY: task→scope map
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: trace shows which scopes/modules were used

--- END.
