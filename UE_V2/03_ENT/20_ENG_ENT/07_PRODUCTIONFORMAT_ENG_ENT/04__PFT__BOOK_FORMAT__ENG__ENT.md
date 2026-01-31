# BOOK FORMAT ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/04__BOOK_FORMAT_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.PROD.FORMAT.BOOK.001
OWNER: SYSTEM
ROLE: Defines deterministic book-format constraints and planning artifacts: chapter unit model, structural expectations, pacing envelopes (as constraints), deliverable spec, and compliance gates (without writing prose).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Book Format Engine created: book plan schema, chapter model, structural expectations, and compliance gates."
- REASON: "Book medium requires specific unit planning and deliverable requirements distinct from series/video/game."
- IMPACT: "Projects can generate consistent book plans and validate against format constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.BOOK.001

---

## 0) PURPOSE (LAW)
This engine owns **BOOK format constraints and planning**:
- defines chapter as the primary unit
- defines book-level structural expectations (front matter, arcs, act-like partitions as optional constraints)
- defines pacing envelopes as constraints (not editing rhythm)
- emits a BOOK_PLAN and BOOK_DELIVERABLE_SPEC with validation gates

Hard rule:
- This engine plans structure and constraints; it does NOT write the book.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write chapters/prose (narrative engines)
- define story structure as canon (story structure engine owns narrative structure)
- define style palettes (style family)
- define production implementation (camera/editing/audio)
- define marketing/distribution packaging

Also forbidden:
- turning “pacing envelope” into editing/montage timing.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- FORMAT_CONSTRAINT_PACKAGE (required)
- UNIT_SIZING_RULES (required; format=BOOK)
- GENRE_PROFILE (optional)
- GENRE_BLEND_PROFILE (optional)
- TONE_PROFILE (optional)
- STORY_STRUCTURE (optional)
- EVENT_SCHEDULE (optional)

PRODUCES:
- BOOK_PLAN
- CHAPTER_UNIT_MODEL
- BOOK_DELIVERABLE_SPEC
- BOOK_FORMAT_GATES_REPORT

DEPENDS_ON:
- [07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/BOOK/
OPTIONAL:
- KB/FORMAT/BOOK (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Chapter Unit: planned unit with purpose, constraint tags, target size proxy.
- Book Plan: ordered set of chapter units plus structural expectations.
- Deliverable Spec: definition of what “done” means for the book artifact.
- Pacing Envelope: constraints on progression density (not wordsmithing).
- Front Matter / Back Matter: optional structural elements.

Enums (baseline):
- unit_size_proxy: WORDS|SCENES|BEATS
- scope: BOOK|PART|CHAPTER
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- chapter unit model and sizing constraints
- book plan structure (parts, chapter order, optional milestones)
- deliverable spec and compliance gates

OUT OF SCOPE (HARD):
- writing and stylistic prose execution
- narrative canon decisions (what happens) — narrative engines own content
- editing/montage logic

COLLISION RULE:
- If request is “plan episodes/seasons” → `05__SERIES_EPISODE_ENG`
- If request is “short content constraints” → `06__SHORT_CONTENT_ENG`
- If request is “write chapter text” → narrative scene/writing engines
- If request is “tone/mood palette” → style engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: CHAPTER_UNIT_MODEL defines chapter fields and sizing proxies.
R2 (HARD) MUST: BOOK_PLAN defines ordered chapters with targets and constraints.
R3 (HARD) MUST: BOOK_DELIVERABLE_SPEC defines required components and validation checks.
R4 (HARD) MUST: gates report detects missing sizing rules and format conflicts.
R5 (HARD) FORBIDDEN: “book plan” that is only a chapter list without unit model and constraints.
R6 (SOFT) SHOULD: include optional “part” segmentation rules if story structure requires.
R7 (HARD) MUST: plan must remain compatible with FORMAT_CONSTRAINT_PACKAGE.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: CHAPTER_UNIT_MODEL
- MUST:
  - chapter_model_id
  - version
  - unit_size_proxy (WORDS|SCENES|BEATS)
  - required_fields[] (non-empty)
  - allowed_tags[] (optional)
  - checks[] (non-empty)
- REQUIRED FIELD (baseline):
  - chapter_id
  - title_stub (optional)
  - purpose (testable)
  - constraint_tags[] (optional)
  - target_size (proxy number)
  - size_bounds (min,max optional)
  - key_obligations[] (optional: turning point/climax obligations refs)
  - proof_events[] (optional)
- VALIDATION:
  - required_fields non-empty
  - unit_size_proxy matches UNIT_SIZING_RULES
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/BOOK/CHAPTER_UNIT_MODEL.md

ARTIFACT: BOOK_PLAN
- MUST:
  - book_plan_id
  - version
  - sizing_rules_ref
  - format_constraints_ref
  - chapters[] (non-empty; ordered)
  - optional_structure (parts/front/back matter optional)
  - checks[] (non-empty)
- CHAPTER (minimum):
  - chapter_id
  - order_index
  - purpose
  - target_size
  - size_bounds (optional)
  - constraint_refs[] (optional: genre/format/style constraints)
  - obligations_refs[] (optional)
  - notes
- VALIDATION:
  - chapters ordered with unique order_index
  - target_size respects sizing bounds
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/BOOK/BOOK_PLAN.md

ARTIFACT: BOOK_DELIVERABLE_SPEC
- MUST:
  - deliverable_id
  - version
  - required_components[] (non-empty)
  - quality_checks[] (non-empty)
  - export_targets[] (optional)
- REQUIRED COMPONENT (baseline examples):
  - manuscript_body
  - chapter_structure
  - metadata_block (title, author, version)
  - revision_log (optional)
- QUALITY CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - required_components non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/BOOK/BOOK_DELIVERABLE_SPEC.md

ARTIFACT: BOOK_FORMAT_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
  - recommended_repairs[] (required if S0)
- Minimum required gates:
  - G1_SIZING_RULES_MISSING (S0)
  - G2_CHAPTERS_EMPTY (S0)
  - G3_SIZE_OUT_OF_BOUNDS (S1)
  - G4_CONSTRAINT_CONFLICT (S1)
  - G5_DELIVERABLE_INCOMPLETE (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/BOOK/BOOK_FORMAT_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load format constraint package + sizing rules (BOOK).
2) Instantiate chapter unit model (fields + proxy).
3) Build book plan:
   - number of chapters within sizing constraints
   - order and optional part segmentation
4) Bind constraints:
   - map genre/blend/style constraints onto chapters (refs only)
5) Define deliverable spec and checks.
6) Run gates and emit outputs.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing sizing rules or mismatched unit_size_proxy.
- S0-2: chapters[] empty.
- S0-3: deliverable spec missing required components.
- S0-4: produced artifacts missing schema fields.
- S0-5: hidden dependency on format adaptation package.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- format adaptation provides translated constraints and sizing rules

Downstream:
- narrative engines can write chapters following plan constraints
- QA/consistency engines validate manuscript against deliverable spec and chapter plan
- marketing/distribution layer consumes final deliverable (outside scope)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
