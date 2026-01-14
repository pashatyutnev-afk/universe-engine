# ENG — KB CONNECTOR STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/00__README__ENG_KB_CONNECTOR_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 20_ENG
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.ENG.STD.CONNECTOR.001
OWNER: SYSTEM
ROLE: Canonical connector standard for Engine entities: how engines load and apply KB deterministically, how engine knowledge modules are structured (method/parameters/edge cases/examples/gates), and how engines interface with ORC/SPC via UID-only XREF without inventing directives.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created ENG connector standard: deterministic KB loading, engine module structure, parameter discipline, edge-case handling, and gate-backed outputs."
- REASON: "Engines must be reproducible 'logic units'; without standards they drift, repeat patterns, and invent behavior."
- IMPACT: "More stable engine behavior and easier orchestration/validation."
- CHANGE_ID: UE.CHG.2026-01-14.KB.ENG.STD.001

---

## 0) PURPOSE (KB)
An Engine (ENG) is a reusable logic unit that:
- takes inputs (constraints, objectives, context)
- applies a defined method
- produces outputs (plans, specs, transformations)
- is testable by gates and examples

ENG is not a “persona”. ENG is a deterministic method container.

---

## 1) SCOPE (BOUNDARY)
COVERS:
- how ENG uses KB
- how ENG packs and modules are structured
- parameter discipline and edge-case handling
- output gates and example calibration

EXCLUDES:
- domain topics themselves (live in `10_TOPICS`)
- governance law authoring (lives in `00_KB_GOVERNANCE`)
- orchestration sequencing (primarily ORC)

---

## 2) ABSOLUTE RULES (ENG LAW)
R1 — Method must be explicit
- An engine must have a documented method, inputs, outputs, and constraints.
- No “implicit behavior”.

R2 — Parameter discipline
- If an engine has tunable parameters, they must be enumerated with defaults and allowed ranges.
- No hidden parameters.

R3 — UID-only authority
- Operational crossrefs are UID-only.
- Navigation via KB master index only.

R4 — No-fantasy engine execution
- Engines must not invent directives or facts not backed by loaded KB modules or pack content.
- If required knowledge missing → STOP or GAP.

R5 — Testability
- Every engine output type must have:
  - at least one gate or checklist (pass/rework/fail)
  - and example outputs for calibration

---

## 3) REQUIRED LOAD SET (MINIMAL)
ENG run requires:
- governance minimum set
- the engine’s own pack modules (method/params/gates/examples)
- minimal domain topics required for the engine’s domain (if any)
- reference glossaries when term ambiguity exists

Avoid over-loading.

---

## 4) ENG EXECUTION FLOW (DETERMINISTIC)
Step 1: Input normalization
- define inputs explicitly (what is known / unknown)
- set parameter defaults

Step 2: Apply method
- follow documented steps
- use only loaded knowledge

Step 3: Output structuring
- produce outputs in defined schema/template

Step 4: Self-check
- apply the engine’s gate/checklist to its output

Step 5: Trace
- list criteria UIDs and knowledge sources used

---

## 5) ENGINE MODULE STANDARD (CANON)
Any engine module should include:

ENGINE_MODULE_MINIMUM:
- PURPOSE
- INPUTS
- OUTPUTS
- METHOD STEPS (deterministic)
- PARAMETERS (if any)
- EDGE CASES (and handling)
- COMMON FAILS (and fixes)
- GATES (UID-only criteria)
- EXAMPLES (good/bad/borderline)
- RELATED (UID-only)

Notes:
- Keep modules atomic: one engine function per file.

---

## 6) ENGINE PACK STRUCTURE (CANON)
An ENG pack is a folder with at least:

ENG_PACK_ROOT:
- 00__PACK_PASSPORT.md
- 01__ENGINE_SCOPE_AND_IO.md
- 02__METHOD_AND_PARAMETERS.md
- 03__EDGE_CASES_LIBRARY.md
- 04__OUTPUT_TEMPLATES.md
- 05__KB_GATES/
- 06__EXAMPLES/
- 07__REGRESSION_GUARD.md
- 08__KB_SOURCES.md
- 09__TOPIC_BINDINGS.md (UID-only)
- 10__XREF_BINDINGS.md (UID-only: ORC/SPC connections)

---

## 7) INTERFACES (ENG ↔ ORC ↔ SPC)
Engines should be “callable” by ORC and supported by SPC when needed.

XREF usage:
- ORC calls ENG by UID (engine module UID).
- ENG declares:
  - “Expected caller contexts” (which ORC/pipelines)
  - “Required support specialists” (SPC UIDs) if needed
- This mapping lives in XREF artifacts (do not hardcode navigation).

---

## 8) COMMON FAIL MODES (ENG) (AND FIXES)
F1 — “Magic behavior”
- Fix: document method steps and parameters explicitly

F2 — Output not testable
- Fix: define gates + examples; add a checklist-as-gate minimum

F3 — Overloading topics
- Fix: minimal bindings; load only what supports the method

F4 — Parameter drift
- Fix: parameter enum with defaults; record changes with versioning

---

## 9) HARD FAIL CONDITIONS
FAIL IF:
- engine is used without explicit method and IO
- parameter changes occur without version/change note
- engine outputs claim compliance without self-check gate
- URL/PATH used as authority inside pack modules
- engine invents knowledge when KB is missing

---

## 10) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: global KB governance rules
- UE.KB.RULE.ENTITIES.001 | WHY: entity pack boundaries and minimums
- UE.KB.XREF.STD.CONNECTOR.001 | WHY: mapping artifacts and UID-only linking discipline
- UE.KB.MAP.ENTITY_TO_SCOPE.002 | WHY: minimal loading map
- UE.KB.STD.GATE_DEF.088 | WHY: gate definition standard for testability

--- END.
