# SYSTEM LAW — PIPELINE REGISTRY (CANON)

FILE: 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md
SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: PIPELINE_REGISTRY
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.1
UID: UE.LAW.PIPELINES.001
OWNER: SYSTEM
ROLE: Single authoritative registry of pipelines (ORC step-orders) + runtime lifecycle pipelines, with IDs, contracts, gates, and failover rules

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Introduced canonical pipeline registry: IDs, record schema, lifecycle pipeline, and domain pipeline slots."
- REASON: "Make orchestration deterministic and auditable."
- IMPACT: "ORC/ENG/CTL/VAL/QA can reference pipelines by ID."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.PIPELINES.001

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: PATCH
- SUMMARY: "Aligned with START runtime: boot-first, dispatcher entry, finish chain, artifact-only outputs, and stop-conditions-only. Added mandatory pipeline contract fields."
- REASON: "Remove ambiguity and enforce stable routing."
- IMPACT: "Any run can be traced to PIPELINE_ID with explicit gates."
- CHANGE_ID: UE.CHG.2026-01-19.LAW.PIPELINES.002

---

## 0) PURPOSE (LAW)
This registry defines:
- what pipelines exist (runtime + domain orchestration)
- how they are identified (PIPELINE_ID)
- which entity owns each pipeline (ORC owner + governance signoff)
- mandatory step order, handoffs, gates placement
- failover behavior (missing entity/template/doc)
- how pipelines are added/changed (canon protocol)

If a pipeline is not in this registry, it is not runnable as a canonical route.

---

## 1) PIPELINE ID FORMAT (ABSOLUTE)
FORMAT: `UE.PPL.<DOMAIN>.<NAME>.<NNN>`

- DOMAIN: RUNTIME | BOOT | GOV | DOC | KB | MUSIC | NARRATIVE | WORLD | VISUAL | PRODUCTION | MARKETING
- NAME: short stable token
- NNN: 001..999 sequence within DOMAIN

Examples:
- UE.PPL.BOOT.SEQ.001
- UE.PPL.RUNTIME.TASK_LIFECYCLE.001
- UE.PPL.MUSIC.ALBUM_TO_TRACK.001

---

## 2) PIPELINE RECORD SCHEMA (REQUIRED)
Each pipeline record must include:

- PIPELINE_ID:
- NAME:
- DOMAIN:
- STATUS:
- OWNER_ENTITY:
- ENTRYPOINT (SPC):
- ORC_OWNER:
- INPUTS (MIN):
- OUTPUT_ARTIFACT_TYPES:
- STEPS (ORDERED):
  - STEP_ID
  - ROLE (SPC/ORC/ENG/CTL/VAL/QA)
  - ENTITY (UID/Name)
  - INPUTS
  - OUTPUTS
  - GATES (placed here)
  - STOP_CONDITIONS (only allowed)
- HANDOFFS:
- FAILOVER (MISSING ENTITY/TEMPLATE/DOC):
- SIGNOFF_CHAIN (MANDATORY):
- NOTES:

---

## 3) ENFORCEMENT PRINCIPLE (ABSOLUTE)
- Pipelines are executed only after BOOT completion.
- Every task pipeline must:
  - start at dispatcher SPC (`MACHINE_ARCHITECT_SPC`)
  - end via acceptance chain (`READINESS_CHECK_CTL` → relevant VAL → relevant QA → `DOC_CONTROLLER_SPC` → dispatcher signoff)
- Any output must be an artifact doc (no naked output).
- Stop conditions allowed are exclusive:
  - RAW missing
  - marker not confirmed
  - input absent

---

## 4) CANONICAL PIPELINES

### 4.1 BOOT PIPELINE

#### UE.PPL.BOOT.SEQ.001
- NAME: Boot Sequence (core laws + standards + entities + KB)
- DOMAIN: BOOT
- STATUS: ACTIVE
- OWNER_ENTITY: SYSTEM
- ENTRYPOINT (SPC): MACHINE_ARCHITECT_SPC
- ORC_OWNER: PIPELINE_ORCHESTRATOR (implicit; governed by START)
- INPUTS (MIN):
  - ROOT LINK BASE snapshot (RAW)
  - START command context
- OUTPUT_ARTIFACT_TYPES:
  - BOOT TRACE (chat trace / audit note)
- STEPS (ORDERED):
  1) Load System Law index + laws (naming/UID/versioning/canon)
  2) Load Standards (doc control, index structure, storage map, chat/change protocols)
  3) Load Entities model + registries/templates indexes
  4) Load KB entrypoint + KB governance rules
  5) Confirm BOOT COMPLETE markers explicitly:
     - naming + UID loaded
     - doc control + index structure loaded
     - entity model loaded
     - KB entrypoint loaded
  STOP_CONDITIONS:
  - RAW missing
  - marker not confirmed
  - input absent
- HANDOFFS:
  - If boot complete → task routing may begin
- FAILOVER:
  - If any required link missing → STOP: RAW missing (request updated snapshot/link)
- SIGNOFF_CHAIN (MANDATORY):
  - MACHINE_ARCHITECT_SPC confirms boot markers in trace
- NOTES:
  - Boot is not optional. No execution before completion.

---

### 4.2 GLOBAL TASK LIFECYCLE PIPELINE (DEFAULT)

#### UE.PPL.RUNTIME.TASK_LIFECYCLE.001
- NAME: Default Task Lifecycle (end-to-end)
- DOMAIN: RUNTIME
- STATUS: ACTIVE
- OWNER_ENTITY: SYSTEM
- ENTRYPOINT (SPC): MACHINE_ARCHITECT_SPC
- ORC_OWNER: PIPELINE_ORCHESTRATOR (implicit)
- INPUTS (MIN):
  - TASK text
  - ROOT snapshot links
- OUTPUT_ARTIFACT_TYPES:
  - One or more artifact docs (domain-specific)
- STEPS (ORDERED):
  1) INTAKE — MACHINE_ARCHITECT_SPC
     - produce deterministic task spec: goal/scope/inputs/output type
  2) ROUTING — Top Governance SPC cluster
     - assign responsible SPC(s)
     - select domain ORC pipeline (or default)
  3) EXECUTION — ORC + ENG
     - produce draft artifacts
  4) CONTROL — CTL
     - enforce constraints/policies, block if needed
  5) VALIDATION — VAL
     - record violations (if any)
  6) QA — QA realm
     - acceptance gates
  7) PACKAGING — INTEGRATION_PACKER_SPC
     - output pack formatting, filenames, structure
  8) SIGNOFF — DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC
     - final approval
  STOP_CONDITIONS:
  - RAW missing
  - marker not confirmed
  - input absent
- HANDOFFS:
  - Routing selects a domain pipeline ID
- FAILOVER:
  - Missing entity/template/doc → GAP protocol (see section 4.3)
- SIGNOFF_CHAIN (MANDATORY):
  - READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC
- NOTES:
  - Any deviation must be recorded as a pipeline variant and registered here.

---

### 4.3 FAILOVER PIPELINE: CREATE MISSING ENTITY / TEMPLATE

#### UE.PPL.GOV.GAP_CREATE.001
- NAME: GAP → Create Missing Entity/Template → Resume
- DOMAIN: GOV
- STATUS: ACTIVE
- OWNER_ENTITY: SYSTEM
- ENTRYPOINT (SPC): MACHINE_ARCHITECT_SPC
- ORC_OWNER: ORC_CREATE_FLOW (if present)
- INPUTS (MIN):
  - GAP description (what is missing, why required)
  - template links (RAW)
- OUTPUT_ARTIFACT_TYPES:
  - New entity doc (full file) and/or template doc
  - Registry/log update proposal (artifact)
- STEPS (ORDERED):
  1) Declare GAP with reason + required class (SPC/ORC/ENG/CTL/VAL/QA/TPL)
  2) Select template (RAW link must exist)
  3) Generate minimal entity pack (full file content)
  4) Propose registry/DB/log registration (as artifact doc)
  5) Resume original pipeline at the blocked step
  STOP_CONDITIONS:
  - RAW missing
  - marker not confirmed
  - input absent
- HANDOFFS:
  - Back to the original pipeline
- FAILOVER:
  - If template link missing → STOP: RAW missing
- SIGNOFF_CHAIN (MANDATORY):
  - DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC
- NOTES:
  - This is mandatory when required entities/templates are missing.

---

### 4.4 MUSIC DOMAIN PIPELINES (CANONICAL ROUTES)

#### UE.PPL.MUSIC.GROUP_TO_ALBUM.001
- NAME: Group → Album planning route
- DOMAIN: MUSIC
- STATUS: ACTIVE
- OWNER_ENTITY: MUSIC_ORCHESTRATORS_REALM
- ENTRYPOINT (SPC): MACHINE_ARCHITECT_SPC
- ORC_OWNER: GROUP_TO_ALBUM_ORC
- INPUTS (MIN):
  - Group identity + intent
- OUTPUT_ARTIFACT_TYPES:
  - Album blueprint / album pack docs (domain schema)
- STEPS (ORDERED):
  1) INTAKE (SPC dispatcher)
  2) ORC plan (album blueprint)
  3) ENG execution (style, tracklist logic)
  4) CTL policy checks (duration, prompt contract, etc)
  5) VAL compliance (PD-only, collision, naming)
  6) QA gates (hook/readability/UGC readiness)
  7) PACKAGING + SIGNOFF
  STOP_CONDITIONS:
  - RAW missing
  - marker not confirmed
  - input absent
- FAILOVER:
  - missing music entities → run UE.PPL.GOV.GAP_CREATE.001
- SIGNOFF_CHAIN:
  - READINESS_CHECK_CTL → music VAL → music QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

#### UE.PPL.MUSIC.ALBUM_TO_TRACK.001
- NAME: Album → Track production route
- DOMAIN: MUSIC
- STATUS: ACTIVE
- OWNER_ENTITY: MUSIC_ORCHESTRATORS_REALM
- ENTRYPOINT (SPC): MACHINE_ARCHITECT_SPC
- ORC_OWNER: ALBUM_TO_TRACK_ORC
- INPUTS (MIN):
  - Album blueprint
  - Track slot (T01..TN)
- OUTPUT_ARTIFACT_TYPES:
  - Track card / prompt / release docs (or output pack)
- STEPS (ORDERED):
  1) INTAKE + slot selection
  2) ENG: track concept + structure + lyrics framing
  3) CTL: prompt contract / duration / variants policies
  4) VAL: repetition/collision/rights/naming checks
  5) QA: hook/recognition/loop/regression checks
  6) PACK + SIGNOFF
  STOP_CONDITIONS:
  - RAW missing
  - marker not confirmed
  - input absent

#### UE.PPL.MUSIC.TRACK_TEST_DOC_GATE.001
- NAME: Track test doc → gate route
- DOMAIN: MUSIC
- STATUS: ACTIVE
- OWNER_ENTITY: MUSIC_ORCHESTRATORS_REALM
- ENTRYPOINT (SPC): MACHINE_ARCHITECT_SPC
- ORC_OWNER: TRACK_TEST_DOC_GATE_ORC
- INPUTS (MIN):
  - Track artifact docs
- OUTPUT_ARTIFACT_TYPES:
  - Gate results note (artifact)
- STEPS:
  - READINESS_CHECK_CTL → music VAL set → music QA set → DOC controller → dispatcher signoff

#### UE.PPL.MUSIC.RELEASE_PACK.001
- NAME: Release pack build route
- DOMAIN: MUSIC
- STATUS: ACTIVE
- OWNER_ENTITY: MUSIC_ORCHESTRATORS_REALM
- ENTRYPOINT (SPC): MACHINE_ARCHITECT_SPC
- ORC_OWNER: RELEASE_PACK_ORC
- INPUTS (MIN):
  - Approved track artifacts
- OUTPUT_ARTIFACT_TYPES:
  - Release pack (docs bundle)
- STEPS:
  - Validate metadata/credits → QA acceptance → packaging → signoff

---

## 5) DEPRECATION & VERSIONING (ABSOLUTE)
- Pipelines are versioned by this registry version + per-pipeline status.
- If a pipeline is replaced:
  - mark old pipeline as DEPRECATED
  - create a new PIPELINE_ID
  - add a pointer note (do not overwrite history)

---

## 6) GAP: PIPELINE MISSING (MANDATORY)
If a task requires a pipeline not listed here:
1) Declare GAP (pipeline missing)
2) Propose a new pipeline record (full schema)
3) Identify ORC owner (or propose creating ORC entity)
4) Register before using it as canonical

---

## 7) INTERFACES (RAW)
Top governance entry (dispatcher core):
- MACHINE_ARCHITECT_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
- DOC_CONTROLLER_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- INTEGRATION_PACKER_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md

Core controller:
- READINESS_CHECK_CTL
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

Music orchestrators realm:
- 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/00__README__MUSIC_ORCHESTRATORS.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/00__README__MUSIC_ORCHESTRATORS.md

--- END.
