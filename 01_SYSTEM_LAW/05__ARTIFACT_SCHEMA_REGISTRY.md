# SYSTEM LAW — ARTIFACT SCHEMA REGISTRY (CANON)

FILE: 01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md
SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: ARTIFACT_SCHEMA_REGISTRY
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.1
UID: UE.LAW.ARTIFACTS.001
OWNER: SYSTEM
ROLE: Single authoritative registry of artifact document types, their mandatory schemas, section markers, UID rules, and template bindings

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Introduced canonical artifact registry: artifact types, record schema, and template binding rule."
- REASON: "Force 'no naked output' discipline and unify deliverables."
- IMPACT: "Every result becomes auditable document artifact."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.ARTIFACTS.001

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: PATCH
- SUMMARY: "Aligned with START runtime: snapshot rule, boot-first, dispatcher entry, finish chain, stop-conditions-only, and KB scope block requirement where relevant."
- REASON: "Remove ambiguity about what counts as a valid deliverable."
- IMPACT: "Artifacts become deterministic units for ORC/ENG/CTL/VAL/QA pipelines."
- CHANGE_ID: UE.CHG.2026-01-19.LAW.ARTIFACTS.002

---

## 0) PURPOSE (LAW)
This registry defines what an “artifact” is in Universe Engine, and enforces:
- no naked output: every result is a document artifact
- deterministic schema: mandatory headers + mandatory section markers
- template binding: every artifact type must map to a template or a canonical schema standard
- routing and gates: artifacts must pass control/validation/QA before signoff

If an artifact type is not registered here, it is not a canonical deliverable.

---

## 1) ABSOLUTE ARTIFACT LAWS

### 1.1 No naked output (ABSOLUTE)
Any output (content/plan/decision/track/scene/entity passport) must be provided as an artifact document compliant with:
- DOC CONTROL rules
- UID rules
- versioning / change policy
- the artifact’s registered schema markers

### 1.2 Snapshot compliance (ABSOLUTE)
During runtime, artifact generation must rely only on RAW links provided by:
- ROOT LINK BASE snapshot, and/or
- explicit user message links
No guessing of paths or URLs outside the snapshot.

### 1.3 Boot-first (ABSOLUTE)
No artifact execution or packaging before BOOT completion markers are explicitly confirmed.

### 1.4 Mandatory governance chain (ABSOLUTE)
No artifact is “done” until it passes:
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.5 Stop conditions (only these)
- RAW missing
- marker not confirmed
- input absent

---

## 2) ARTIFACT TYPE ID FORMAT (ABSOLUTE)
FORMAT: `UE.ART.<DOMAIN>.<TYPE>.<NNN>`

- DOMAIN examples: SYS | DOC | KB | ENT | PPL | MUSIC | NARRATIVE | WORLD | VISUAL | PRODUCTION | MARKETING
- TYPE examples: INDEX | PASSPORT | CONTRACT | CARD | PROMPT | RELEASE | PACK | VIOLATION | QA_CHECK | REPORT
- NNN: 001..999 sequence within DOMAIN

---

## 3) ARTIFACT RECORD SCHEMA (REQUIRED)
Each artifact type entry in this registry must include:

- ARTIFACT_TYPE_ID:
- NAME:
- DOMAIN:
- PURPOSE:
- REQUIRED_HEADER_FIELDS:
- REQUIRED_SECTION_MARKERS:
- OPTIONAL_SECTION_MARKERS:
- TEMPLATE_BINDING (RAW) OR CANON_SCHEMA_STANDARD (RAW):
- UID_RULE_REFERENCE (RAW):
- VERSIONING_POLICY_REFERENCE (RAW):
- VALIDATION (VAL) HOOKS (optional):
- QA GATES (optional):
- OUTPUT_PLACEMENT (layer/folder guidance):
- NOTES:

---

## 4) GLOBAL ARTIFACT DOCUMENT HEADER (MINIMUM)
Every artifact document must start with a Doc Control header block containing, at minimum:

- FILE:
- SCOPE:
- LAYER:
- DOC_TYPE:
- STATUS:
- LOCK:
- VERSION:
- UID:
- OWNER:
- ROLE:
- CHANGE_NOTE (when updated)

If a specific artifact type requires extra header fields, it must be listed in REQUIRED_HEADER_FIELDS for that type.

---

## 5) UNIVERSAL SECTION MARKERS (BASELINE)
Unless a registered artifact type overrides this, the document must include these section markers:

- PURPOSE
- INPUTS (MINIMUM)
- OUTPUTS / DELIVERABLE
- RULES / CONSTRAINTS (if applicable)
- WORKFLOW / STEPS (if applicable)
- GATES (VAL/QA acceptance)
- INTERFACES (RAW links only)

### 5.1 KB SCOPE (MANDATORY WHEN KB IS USED)
If an artifact consumes or references Knowledge Base materials, it must include:

## KNOWLEDGE BASE (KB) SCOPE
- INPUTS (what KB modules/topics are allowed)
- OUTPUTS (what the artifact produces into KB, if any)
- BOUNDARIES (what is explicitly out of scope)
- RAW REFERENCES (KB entrypoints or modules used)

If KB scope cannot be confirmed via RAW links, STOP: marker not confirmed.

---

## 6) CANONICAL ARTIFACT TYPES (REGISTRY)

### 6.1 System / Governance artifacts

#### UE.ART.SYS.LAW.001
- NAME: System Law Document
- DOMAIN: SYS
- PURPOSE: Enforce canonical rules at L1.
- REQUIRED_HEADER_FIELDS: LAW_TYPE, LEVEL
- REQUIRED_SECTION_MARKERS:
  - PURPOSE
  - ABSOLUTE LAWS
  - ENFORCEMENT
  - INTERFACES (RAW)
- TEMPLATE_BINDING (RAW): (by system standards; if template exists it must be referenced)
- UID_RULE_REFERENCE (RAW): UID rules
- VERSIONING_POLICY_REFERENCE (RAW): versioning policy
- OUTPUT_PLACEMENT: 01_SYSTEM_LAW/
- NOTES: Laws are LOCK: FIXED once ACTIVE.

#### UE.ART.SYS.REGISTRY.001
- NAME: Registry Document (DB/Index/Registry)
- DOMAIN: SYS
- PURPOSE: Canonical list of entities/types/records.
- REQUIRED_SECTION_MARKERS:
  - PURPOSE
  - RECORD_SCHEMA
  - ENTRIES
  - CHANGELOG / NOTES
  - INTERFACES (RAW)
- TEMPLATE_BINDING (RAW): registry template (if present)
- OUTPUT_PLACEMENT: 08_DATABASES/ or registry realms
- NOTES: Registries are single sources of truth within their declared scope.

#### UE.ART.PPL.CONTRACT.001
- NAME: Pipeline Contract / ORC Step Contract
- DOMAIN: PPL
- PURPOSE: Deterministic orchestration: ordered steps + handoffs + gates placement.
- REQUIRED_SECTION_MARKERS:
  - PURPOSE
  - INPUTS (MIN)
  - OUTPUT_ARTIFACT_TYPES
  - STEPS (ORDERED)
  - HANDOFFS
  - FAILOVER
  - SIGNOFF_CHAIN
  - INTERFACES (RAW)
- TEMPLATE_BINDING (RAW): ORC pipeline contract template (if present)
- OUTPUT_PLACEMENT: ORC realm or pipeline docs
- NOTES: Must reference PIPELINE_ID from pipeline registry.

---

### 6.2 Entity artifacts (passports / role docs)

#### UE.ART.ENT.PASSPORT.001
- NAME: Entity Passport (SPC/ORC/ENG/CTL/VAL/QA)
- DOMAIN: ENT
- PURPOSE: Define identity, scope, rules, and interfaces of an entity role.
- REQUIRED_SECTION_MARKERS:
  - PURPOSE
  - SCOPE
  - RULES (CAN / CANNOT)
  - INPUTS / OUTPUTS
  - GATES (where applicable)
  - KNOWLEDGE BASE (KB) SCOPE (if entity consumes KB)
  - INTERFACES (RAW)
- TEMPLATE_BINDING (RAW): entity passport template (if present)
- OUTPUT_PLACEMENT: 03_SYSTEM_ENTITIES/<realm>/
- NOTES: If entity is missing, runtime must propose creation using templates.

---

### 6.3 Validation / QA artifacts

#### UE.ART.VAL.VIOLATION.001
- NAME: Validation Violation Record
- DOMAIN: SYS
- PURPOSE: Record a compliance failure with fix guidance.
- REQUIRED_SECTION_MARKERS:
  - VIOLATION_SUMMARY
  - RULE_REFERENCES (RAW)
  - EVIDENCE (what failed)
  - FIX_GUIDE
  - RECHECK_INSTRUCTIONS
  - INTERFACES (RAW)
- TEMPLATE_BINDING (RAW): VAL violation template (if present)
- OUTPUT_PLACEMENT: validation realm or logs
- NOTES: Must be referenced by pipeline trace if a gate fails.

#### UE.ART.QA.CHECK.001
- NAME: QA Gate Check Record
- DOMAIN: SYS
- PURPOSE: Acceptance scoring against rubric/exemplars.
- REQUIRED_SECTION_MARKERS:
  - CHECK_SCOPE
  - RUBRIC (or RUBRIC_REF RAW)
  - RESULTS
  - PASS_FAIL
  - REGRESSION_NOTES (if any)
  - INTERFACES (RAW)
- TEMPLATE_BINDING (RAW): QA check template (if present)
- OUTPUT_PLACEMENT: QA realm or logs

---

### 6.4 Music system artifacts (minimum set)

#### UE.ART.MUSIC.TRACK_CARD.001
- NAME: Track Card
- DOMAIN: MUSIC
- PURPOSE: Track identity + intent + positioning + slot metadata.
- REQUIRED_SECTION_MARKERS:
  - PURPOSE
  - TRACK_IDENTITY
  - STYLE_FINGERPRINT (high level)
  - DURATION_TARGET
  - VOCAL_INTENT
  - QA_TARGETS
  - INTERFACES (RAW)
- CANON_SCHEMA_STANDARD (RAW): Music doc schema standard (if present)
- OUTPUT_PLACEMENT: 08_DATABASES/10_MUSIC_CATALOG/.../TRACKS/.../00__TRACK__CARD.md

#### UE.ART.MUSIC.TRACK_PROMPT.001
- NAME: Track Prompt Document
- DOMAIN: MUSIC
- PURPOSE: Prompt contract payload for a generation tool.
- REQUIRED_SECTION_MARKERS:
  - PROMPT_CONTRACT
  - LYRICS / STRUCTURE
  - NEGATIVE_SPECS (if used)
  - ONE_AXIS_CHANGE_NOTE (if revision)
  - INTERFACES (RAW)
- CANON_SCHEMA_STANDARD (RAW): Music prompt contract standard (if present)
- OUTPUT_PLACEMENT: .../01__TRACK__PROMPT.md

#### UE.ART.MUSIC.TRACK_RELEASE.001
- NAME: Track Release Document
- DOMAIN: MUSIC
- PURPOSE: Final metadata + packaging + variants list.
- REQUIRED_SECTION_MARKERS:
  - METADATA
  - CREDITS_RIGHTS
  - VARIANTS
  - QA_SIGNOFFS
  - INTERFACES (RAW)
- OUTPUT_PLACEMENT: .../02__TRACK__RELEASE.md

#### UE.ART.MUSIC.OUTPUT_PACK.001
- NAME: Track Output Pack (bundle)
- DOMAIN: MUSIC
- PURPOSE: A single exportable pack for publishing/hand-off.
- REQUIRED_SECTION_MARKERS:
  - CONTENT (what is included)
  - FILE_LIST
  - PLATFORM_NOTES
  - QA_PASS
  - INTERFACES (RAW)
- OUTPUT_PLACEMENT: 05_PROJECTS/07_MUSIC_LABEL/.../10_RELEASES/...__OUTPUT_PACK.md

---

## 7) GAP RULE: ARTIFACT TYPE NOT FOUND (MANDATORY)
If task requires an artifact type not registered here:
1) Declare GAP: missing artifact type
2) Propose a new ARTIFACT_TYPE record (full schema)
3) Bind it to a template or a canon schema standard (RAW link required)
4) Only then produce artifacts under that type

---

## 8) INTERFACES (RAW)
System law + standards used by this registry:

- UID rules
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- Versioning & change policy
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Canon protocol
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- Doc control standard
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- Index structure spec
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md
- Storage map standard
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

Templates index (if templates are referenced during GAP creation):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES.md

--- END.
