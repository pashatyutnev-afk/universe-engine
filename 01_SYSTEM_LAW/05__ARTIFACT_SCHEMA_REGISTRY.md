# SYSTEM LAW — ARTIFACT SCHEMA REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: ARTIFACT_SCHEMA
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.ARTIFACT_SCHEMA.001
OWNER: SYSTEM
ROLE: Registry of artifact types and their required schemas, owners, output targets, and required gates to keep outputs consistent across engines, specialists, pipelines, KB, and projects

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable artifact schema registry: strict TYPE_ID format, record schema, baseline artifact types for cube operation (SPC/ENG/ORC/XREF/KB/PRJ), and schema change rules with enforcement."
- REASON: "System needs a single authoritative definition of output artifact shapes; otherwise pipelines produce incompatible outputs."
- IMPACT: "All outputs become deterministic and checkable; breaking schema changes require migration and proper versioning."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.ARTIFACT_SCHEMA.001

---

## 0) PURPOSE (LAW)
This registry defines canonical artifact types and their required fields.
It ensures:
- engines/specialists/orchestrators produce compatible outputs
- validators and QA can check artifacts deterministically
- breaking schema changes are detected and require migration

---

## 1) DEFINITIONS (STRICT)
- ARTIFACT: Any produced output intended to be stored, referenced, validated, or used by pipelines.
- TYPE_ID: Stable identifier of an artifact type (never reused).
- SCHEMA: Required and optional fields for an artifact type.
- OWNER_LAYER: The layer/group responsible for maintaining the schema (LAW/STD/ENT/KB/PRJ/etc).
- OUTPUT_TARGET: Where artifacts of this type are stored (by rule, not necessarily one folder).
- REQUIRED_GATES: Which gates are required when producing/accepting the artifact (VAL/QA/CTL).
- BREAKING SCHEMA CHANGE: Any change that makes previously valid artifacts invalid or changes required interpretation.

---

## 2) ARTIFACT TYPE ID FORMAT (ABSOLUTE)
- FORMAT: `UE.ART.<LAYER>.<DOMAIN>.<TYPE>.<NNN>`
- `<LAYER>`: LAW|STD|ENT|KB|PRJ|XREF|OUT|AST|LOG (use primary owner layer)
- `<DOMAIN>`: NARRATIVE|CHARACTER|WORLD|VISUAL|SOUND|PRODUCTION|MARKETING|RESEARCH|SYSTEM|META|GENERIC
- `<TYPE>`: UPPER_SNAKE_CASE token (stable semantic name)
- `<NNN>`: 001..999 unique sequence within that TYPE family

Rules:
- TYPE_ID is stable and must never change.
- TYPE_ID collisions are forbidden.
- TYPE_ID must never be reused even if artifact type is deprecated.

---

## 3) ARTIFACT TYPE RECORD FORMAT (ABSOLUTE)
Each registry record MUST include:

- TYPE_ID: `UE.ART....`
- NAME: human name
- REQUIRED_FIELDS: list of required top-level fields/sections
- OPTIONAL_FIELDS: list of optional top-level fields/sections
- OWNER_LAYER: LAW|STD|ENT|KB|PRJ|XREF|...
- OUTPUT_TARGET: storage rule (path or layer target)
- REQUIRED_GATES: [VAL:<...>, QA:<...>, CTL:<...>] (may be empty)
- NOTES: clarifications, allowed variants, forbidden patterns

---

## 4) SCHEMA CHANGE RULES (MANDATORY)
### 4.1 Breaking vs non-breaking
- BREAKING (requires MAJOR + migration):
  - adding/removing/renaming required fields
  - changing meaning of a required field
  - changing required ordering if ordering is declared mandatory
- NON-BREAKING (may be MINOR/PATCH):
  - adding optional fields
  - adding examples, clarifying notes
  - tightening language without changing requirements

### 4.2 Migration requirement
Any breaking schema change requires:
- migration note describing old→new mapping
- update to relevant templates (if any)
- update to validators/QA expectations (if any)

---

# REGISTRY — ARTIFACT SCHEMAS (CANON)

---

## UE.ART.ENT.GENERIC.SPC_OUTPUT_PACK.001
- TYPE_ID: UE.ART.ENT.GENERIC.SPC_OUTPUT_PACK.001
- NAME: SPC Output Pack (Standard)
- REQUIRED_FIELDS:
  - HEADER (canonical metadata)
  - INPUTS (what was consumed)
  - DECISIONS (what was decided, with rationale)
  - OUTPUTS (deliverables list)
  - RISKS / ASSUMPTIONS (if applicable)
  - NEXT ACTIONS (handoff steps)
- OPTIONAL_FIELDS:
  - CHECKLIST (self-check)
  - REFERENCES (extra sources)
- OWNER_LAYER: ENT
- OUTPUT_TARGET: Stored inside SPC deliverables or PRJ output sections depending on pipeline.
- REQUIRED_GATES: [QA:READABILITY, CTL:READINESS]
- NOTES:
  - Output pack must not declare existence/canon by itself.
  - Output pack is attachable to ORC steps and PRJ artifacts.

---

## UE.ART.ENT.GENERIC.ENGINE_OUTPUT.001
- TYPE_ID: UE.ART.ENT.GENERIC.ENGINE_OUTPUT.001
- NAME: Engine Output (Standard)
- REQUIRED_FIELDS:
  - HEADER (canonical metadata)
  - CONSUMED (inputs)
  - PRODUCED (outputs)
  - DEPENDS_ON (explicit dependencies)
  - OUTPUT_TARGET (where result is stored)
- OPTIONAL_FIELDS:
  - METRICS (if measurable)
  - LIMITATIONS
- OWNER_LAYER: ENT
- OUTPUT_TARGET: Stored in PRJ outputs or system entity logs depending on engine.
- REQUIRED_GATES: [CTL:READINESS]
- NOTES:
  - Engine output must be contract-compatible with engine mini-contract.

---

## UE.ART.XREF.SYSTEM.PIPELINE_STEP_MAP.001
- TYPE_ID: UE.ART.XREF.SYSTEM.PIPELINE_STEP_MAP.001
- NAME: XREF Pipeline Step Map (SoT)
- REQUIRED_FIELDS:
  - HEADER
  - PIPELINE_ID
  - STEPS (ordered list)
  - FOR EACH STEP: ORC_REF, ENG_REF, SPC_OWNER_REF, INPUTS, OUTPUTS, GATES, OUTPUT_TARGET
- OPTIONAL_FIELDS:
  - NOTES
  - VARIANTS (if declared)
- OWNER_LAYER: XREF
- OUTPUT_TARGET: `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/*`
- REQUIRED_GATES: [CTL:LINK_VALIDATION]
- NOTES:
  - This artifact is SoT for step maps; ORC must reference it, not redefine it.

---

## UE.ART.ENT.GENERIC.ORC_PIPELINE_SPEC.001
- TYPE_ID: UE.ART.ENT.GENERIC.ORC_PIPELINE_SPEC.001
- NAME: ORC Pipeline Specification (Executable)
- REQUIRED_FIELDS:
  - HEADER
  - PIPELINE_ID
  - PURPOSE
  - ENTRY CONDITIONS
  - STEP EXECUTION RULE (must reference XREF map)
  - OUTPUT TARGETS
  - REQUIRED GATES
- OPTIONAL_FIELDS:
  - RETRY POLICY
  - ESCALATION RULES
- OWNER_LAYER: ENT
- OUTPUT_TARGET: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/*`
- REQUIRED_GATES: [CTL:READINESS]
- NOTES:
  - ORC must be a deterministic executor; step truth comes from XREF.

---

## UE.ART.KB.SYSTEM.KB_ENTITY_PASSPORT.001
- TYPE_ID: UE.ART.KB.SYSTEM.KB_ENTITY_PASSPORT.001
- NAME: KB Entity Passport (Knowledge Card)
- REQUIRED_FIELDS:
  - HEADER
  - KB_SCOPE (domain/topic)
  - DEFINITIONS (if needed)
  - CONTENT (knowledge)
  - TAGS
  - RELATIONS (if applicable)
- OPTIONAL_FIELDS:
  - SOURCES
  - EXAMPLES
- OWNER_LAYER: KB
- OUTPUT_TARGET: `04_KNOWLEDGE_BASE/*` or KB governance-defined storage map
- REQUIRED_GATES: [QA:READABILITY]
- NOTES:
  - KB passports do not create canon facts; they are methods/knowledge unless explicitly governed otherwise.

---

## UE.ART.PRJ.SYSTEM.PRJ_PASSPORT.001
- TYPE_ID: UE.ART.PRJ.SYSTEM.PRJ_PASSPORT.001
- NAME: Project Passport (PRJ Entity)
- REQUIRED_FIELDS:
  - HEADER
  - SCOPE (what project covers)
  - CANON TARGETS (what becomes canon)
  - ENTITY LIST (what entities are produced)
  - PIPELINES USED (references)
  - OUTPUT TARGETS
- OPTIONAL_FIELDS:
  - ROADMAP
  - RISKS
- OWNER_LAYER: PRJ
- OUTPUT_TARGET: `05_PROJECTS/00_PRJ_GOVERNANCE/*` and per-project location
- REQUIRED_GATES: [CTL:READINESS]
- NOTES:
  - PRJ passport is the bridge between system and produced canon content.

---

## UE.ART.PRJ.NARRATIVE.SCENE_PACK.001
- TYPE_ID: UE.ART.PRJ.NARRATIVE.SCENE_PACK.001
- NAME: Scene Pack (Project Narrative Output)
- REQUIRED_FIELDS:
  - HEADER
  - SCENE_ID / UID
  - SCENE STACK (if standardized)
  - SUMMARY
  - BEATS / EVENTS (structured)
  - DIALOGUE (if present)
  - CONTINUITY NOTES
- OPTIONAL_FIELDS:
  - VISUAL NOTES (constraints only)
  - SOUND NOTES (constraints only)
  - ALT VERSIONS
- OWNER_LAYER: PRJ
- OUTPUT_TARGET: `05_PROJECTS/*` (project-specific output folders)
- REQUIRED_GATES: [QA:NATURALNESS, VAL:CONSISTENCY]
- NOTES:
  - Visual/sound notes must respect boundaries (no montage decisions if forbidden by standards).

---

## UE.ART.PRJ.CHARACTER.CHARACTER_PROFILE.001
- TYPE_ID: UE.ART.PRJ.CHARACTER.CHARACTER_PROFILE.001
- NAME: Character Profile (Project Character Output)
- REQUIRED_FIELDS:
  - HEADER
  - CHARACTER_ID / UID
  - CORE (identity)
  - MOTIVATION
  - PSYCHOLOGY
  - RELATIONSHIPS
  - ARC (growth/trauma if applicable)
- OPTIONAL_FIELDS:
  - DIALOGUE STYLE NOTES
  - CONTRADICTIONS / RISKS
- OWNER_LAYER: PRJ
- OUTPUT_TARGET: `05_PROJECTS/*`
- REQUIRED_GATES: [VAL:CONSISTENCY, QA:READABILITY]
- NOTES:
  - Must align with character engines and narrative continuity constraints.

---

## UE.ART.PRJ.WORLD.LOCATION_DOSSIER.001
- TYPE_ID: UE.ART.PRJ.WORLD.LOCATION_DOSSIER.001
- NAME: Location Dossier (World/Geography Output)
- REQUIRED_FIELDS:
  - HEADER
  - LOCATION_ID / UID
  - GEOGRAPHY (facts)
  - CULTURE/SOCIETY (if applicable)
  - CONFLICT/POWER (if applicable)
  - RESOURCES (non-currency framing if great civ)
- OPTIONAL_FIELDS:
  - MAP NOTES
  - HISTORICAL NOTES
- OWNER_LAYER: PRJ
- OUTPUT_TARGET: `05_PROJECTS/*`
- REQUIRED_GATES: [VAL:CONSISTENCY, QA:READABILITY]
- NOTES:
  - Must comply with WORLD constraints (e.g., no currency for great civilizations).

---

## UE.ART.ENT.SYSTEM.CTL_READINESS_REPORT.001
- TYPE_ID: UE.ART.ENT.SYSTEM.CTL_READINESS_REPORT.001
- NAME: Controller Readiness Report
- REQUIRED_FIELDS:
  - HEADER
  - CHECKS_RUN
  - FAILURES (if any)
  - PASS/FAIL
  - FIX_ACTIONS
- OPTIONAL_FIELDS:
  - LINKS
- OWNER_LAYER: ENT
- OUTPUT_TARGET: `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/*` or logs per system design
- REQUIRED_GATES: []
- NOTES:
  - Used as enforcement evidence for protocol compliance.

---

## 5) BOUNDARIES (ANTI-OVERLAP)
- This registry defines artifact schema expectations; it does not define existence.
- Schemas here do not override higher laws (authority order applies).
- Pipelines may require additional checks but must not contradict required fields without updating this registry.

---

## 6) ENFORCEMENT (MANDATORY)
### 6.1 MANDATORY CHECKS
- Every TYPE_ID follows the strict format.
- No TYPE_ID is reused.
- Every record has REQUIRED_FIELDS + OWNER_LAYER + OUTPUT_TARGET.
- Breaking schema changes are versioned as MAJOR and include migration requirements.

### 6.2 FAIL CONDITIONS
- Artifacts produced without required fields (when claimed to conform).
- Two different types share same TYPE_ID.
- Breaking schema changes introduced without migration or proper versioning.

### 6.3 FIX PROCEDURE
- Update templates and production steps to include missing fields.
- Reissue TYPE_ID if collision occurs (never reuse old).
- Add migration notes and adjust version classification for breaking changes.

---

## 7) INTERFACES (RAW ONLY)
- System Law index (SoT):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Core constitution:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- Versioning & Change Policy:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Standards master index:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

---

## FINAL RULE (LOCK)
This registry is the only authoritative source for artifact type schemas.  
Any artifact claiming compliance must satisfy required fields, or be treated as invalid until fixed.

OWNER: SYSTEM
LOCK: FIXED

--- END.
