# SYSTEM LAW — PIPELINE REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: PIPELINE
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.PIPELINE.001
OWNER: SYSTEM
ROLE: Registry of canonical pipeline types and mandatory structure; step-by-step maps are SoT in XREF and are referenced here; ORC executes pipelines deterministically

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable pipeline registry: PIPELINE_ID format, minimum pipeline structure, SoT rules (XREF for steps), change/migration rules, and baseline MVP pipeline types."
- REASON: "System requires deterministic execution paths to connect ENG/SPC/VAL/QA/CTL into repeatable production flows."
- IMPACT: "Tasks can be routed to canonical ORC pipelines; step maps become checkable; drift between ORC and XREF becomes detectable."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.PIPELINE.001

---

## 0) PURPOSE (LAW)
This law defines:
- how pipelines are identified and registered
- the minimum required structure of any pipeline
- where the source of truth for pipeline steps lives (XREF)
- how pipelines are changed safely (versioning + migration)

---

## 1) DEFINITIONS (STRICT)
- PIPELINE: A deterministic execution flow that produces artifacts from inputs using engines and specialists under required gates.
- PIPELINE TYPE: A registered pipeline category (e.g., Scene, Character) with defined structure and targets.
- STEP: An ordered unit of work within a pipeline (executed by ORC; defined by XREF step map).
- GATE: A required validation/quality/control check (VAL/QA/CTL).
- ORCHESTRATOR (ORC): The executor that runs pipeline steps and enforces gates.
- XREF STEP MAP: Cross-layer map defining the step-by-step truth (SoT) for a pipeline.
- OUTPUT TARGET: Where pipeline outputs are stored (as defined by artifact schemas/standards).
- PIPELINE_ID: Stable identifier of a pipeline type (never reused).

---

## 2) PIPELINE_ID FORMAT (ABSOLUTE)
- FORMAT: `UE.PIP.<DOMAIN>.<NAME>.<NNN>`
Where:
- `<DOMAIN>`: NARRATIVE|CHARACTER|WORLD|VISUAL|SOUND|PRODUCTION|MARKETING|RESEARCH|SYSTEM|META|GENERIC
- `<NAME>`: stable semantic token (UPPER_SNAKE or short tokens, but must be consistent)
- `<NNN>`: 001..999 unique sequence within the pipeline family

Rules:
- PIPELINE_ID is stable and must never change.
- PIPELINE_ID collisions are forbidden.
- PIPELINE_ID must never be reused even if a pipeline is deprecated.

Examples:
- `UE.PIP.NARRATIVE.SCENE.001`
- `UE.PIP.CHARACTER.PROFILE.001`
- `UE.PIP.WORLD.LOCATION.001`

---

## 3) SoT RULE FOR PIPELINE STEPS (ABSOLUTE)
- This registry defines pipeline TYPES and mandatory structure only.
- Step-by-step execution maps are SoT in:
  `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/*`
- ORC executes pipelines and must reference the XREF step map.
- ORC must not redefine step truth without updating XREF (and logging via canon protocol).

If ORC content conflicts with XREF step map → XREF wins (SoT).

---

## 4) PIPELINE MINIMUM STRUCTURE (MANDATORY)
Any pipeline type must have, at minimum:

1) PIPELINE_ID
2) PURPOSE
3) INPUTS (artifact types or explicit inputs)
4) OUTPUTS (artifact types)
5) ORC (RAW link to executor)
6) XREF_STEP_MAP (RAW link; SoT for steps)
7) REQUIRED_GATES (VAL/QA/CTL)
8) OUTPUT_TARGET (where outputs go)
9) STORAGE / TRACEABILITY (how results are logged or referenced)

Pipelines missing any required field are INCOMPLETE.

---

## 5) PIPELINE CHANGE RULES (MANDATORY)
### 5.1 Breaking pipeline change
Breaking change includes:
- changing required gates
- changing required outputs or their schemas
- changing step order/meaning in a way that breaks downstream expectations
- changing output targets that break storage rules

Breaking changes require:
- MAJOR version bump on affected canon artifacts
- migration notes (what changed and how to adapt)
- updated XREF step map and ORC references

### 5.2 Non-breaking pipeline change
Non-breaking changes include:
- clarifying notes
- adding optional steps explicitly marked optional (only if standards allow)
- improving documentation without changing obligations

---

# REGISTRY — PIPELINE TYPES (CANON)

---

## UE.PIP.NARRATIVE.SCENE.001
- PIPELINE_ID: UE.PIP.NARRATIVE.SCENE.001
- PURPOSE: Produce a canonical Scene Pack for a project, with continuity and required quality/consistency gates.
- INPUTS:
  - PRJ context (project scope + canon targets)
  - Narrative requirements / outline (if available)
- OUTPUTS:
  - UE.ART.PRJ.NARRATIVE.SCENE_PACK.001
- ORC (RAW): <RAW: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/...>
- XREF_STEP_MAP (RAW): <RAW: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/...>
- REQUIRED_GATES: [VAL:CONSISTENCY, QA:NATURALNESS, CTL:READINESS]
- OUTPUT_TARGET: `05_PROJECTS/*` (project narrative outputs)
- STORAGE / TRACEABILITY:
  - Scene output must reference pipeline id + step map version context.
- NOTES:
  - Visual/sound notes must respect constraints and production boundaries.

---

## UE.PIP.CHARACTER.PROFILE.001
- PIPELINE_ID: UE.PIP.CHARACTER.PROFILE.001
- PURPOSE: Produce a Character Profile aligned with narrative continuity and psychological consistency.
- INPUTS:
  - PRJ context
  - Existing canon character references (if any)
- OUTPUTS:
  - UE.ART.PRJ.CHARACTER.CHARACTER_PROFILE.001
- ORC (RAW): <RAW: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/...>
- XREF_STEP_MAP (RAW): <RAW: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/...>
- REQUIRED_GATES: [VAL:CONSISTENCY, QA:READABILITY, CTL:READINESS]
- OUTPUT_TARGET: `05_PROJECTS/*` (project character outputs)
- STORAGE / TRACEABILITY:
  - Character output must include UID and reference constraints as applicable.
- NOTES:
  - Must not silently violate WORLD constraints (if relevant through culture/economy content).

---

## UE.PIP.WORLD.LOCATION.001
- PIPELINE_ID: UE.PIP.WORLD.LOCATION.001
- PURPOSE: Produce a Location Dossier consistent with world laws, resources, culture, and constraints.
- INPUTS:
  - PRJ context
  - World framework (timeline/geo rules if available)
- OUTPUTS:
  - UE.ART.PRJ.WORLD.LOCATION_DOSSIER.001
- ORC (RAW): <RAW: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/...>
- XREF_STEP_MAP (RAW): <RAW: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/...>
- REQUIRED_GATES: [VAL:CONSISTENCY, QA:READABILITY, CTL:READINESS]
- OUTPUT_TARGET: `05_PROJECTS/*` (project world outputs)
- STORAGE / TRACEABILITY:
  - Must check WORLD constraints (e.g., no currency for great civilizations).
- NOTES:
  - Any economic framing must comply with constraints registry.

---

## UE.PIP.MARKETING.TEASER.001
- PIPELINE_ID: UE.PIP.MARKETING.TEASER.001
- PURPOSE: Produce a marketing teaser/trailer brief aligned with canon content and platform packaging.
- INPUTS:
  - PRJ canon elements (scenes/characters/world hooks)
  - Target platform notes (if any)
- OUTPUTS:
  - UE.ART.ENT.GENERIC.SPC_OUTPUT_PACK.001 (packaging brief) OR project marketing output (if defined later)
- ORC (RAW): <RAW: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/...>
- XREF_STEP_MAP (RAW): <RAW: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/...>
- REQUIRED_GATES: [QA:READABILITY, CTL:READINESS]
- OUTPUT_TARGET: `05_PROJECTS/*` (project marketing outputs)
- STORAGE / TRACEABILITY:
  - Must reference which canon elements were used; must not invent canon without pipeline.
- NOTES:
  - Distribution/SEO rules live in marketing specialists + standards.

---

## UE.PIP.SYSTEM.CANON_CHANGE.001
- PIPELINE_ID: UE.PIP.SYSTEM.CANON_CHANGE.001
- PURPOSE: Execute a canon change safely using canon protocol and audit discipline.
- INPUTS:
  - Change proposal (scope/type/reason/impact/migration)
- OUTPUTS:
  - Updated canon artifact(s) + required logs/records
- ORC (RAW): <RAW: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/...>
- XREF_STEP_MAP (RAW): <RAW: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/...>
- REQUIRED_GATES: [CTL:READINESS]
- OUTPUT_TARGET: `01_SYSTEM_LAW/*` and impacted scopes (as per change)
- STORAGE / TRACEABILITY:
  - Must include CHANGE_NOTE + CHANGE_ID + required governance record(s).
- NOTES:
  - This pipeline is the governance spine for canon edits.

---

## 6) BOUNDARIES (ANTI-OVERLAP)
- This registry defines pipeline type structure; it does not replace XREF step maps.
- Pipelines do not create existence; indexes do.
- Conflicts are resolved by ORDER OF AUTHORITY in `00__SYSTEM_LAW.md`.

---

## 7) ENFORCEMENT (MANDATORY)
### 7.1 MANDATORY CHECKS
- PIPELINE_ID follows strict format.
- Every pipeline record includes ORC + XREF step map references.
- Required gates are defined and compatible with artifact schema requirements.
- Output targets are consistent with artifact schema registry.
- Breaking pipeline changes are migrated and versioned properly.

### 7.2 FAIL CONDITIONS
- Pipeline type exists without a registered PIPELINE_ID.
- ORC defines steps that conflict with XREF step map.
- Missing gates or missing output target.
- Breaking changes applied as PATCH/MINOR without migration.

### 7.3 FIX PROCEDURE
- Register missing pipeline types or deprecate non-canon ones.
- Update XREF map to match ORC (or update ORC to match XREF; XREF wins).
- Add missing gates/targets and align with artifact schemas.
- Apply migration + correct versioning classification.

---

## 8) INTERFACES (RAW ONLY)
- System Law index (SoT):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Core constitution:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- XREF realm (SoT for step maps): <RAW: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md>
- ORC index (SoT for orchestrators): <RAW: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md>
- Standards master index:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

---

## FINAL RULE (LOCK)
Pipeline types are canonical only when registered here and executed via ORC referencing XREF step maps.  
Any drift between ORC and XREF is a violation until corrected.

OWNER: SYSTEM
LOCK: FIXED

--- END.
