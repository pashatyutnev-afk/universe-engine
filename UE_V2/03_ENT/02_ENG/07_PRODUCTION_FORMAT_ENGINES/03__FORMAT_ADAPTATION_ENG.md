# FORMAT ADAPTATION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG.md
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
UID: UE.ENG.PROD.FORMAT.ADAPT.001
OWNER: SYSTEM
ROLE: Translates genre/style/narrative constraints into format-specific constraints (book/series/short/youtube/game): structure limits, unit sizing, deliverable rules, and validation gates ensuring format compliance without changing canon content.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Format Adaptation Engine created: format constraint translation schema, unit sizing rules, and compliance gates."
- REASON: "Same canon must be expressible across media formats; adaptation must be deterministic."
- IMPACT: "Projects can retarget outputs to new formats while preserving canon and constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.ADAPT.001

---

## 0) PURPOSE (LAW)
This engine owns **FORMAT ADAPTATION constraints**:
- converts upstream constraints (genre blend, tone/mood, narrative structure) into format rules
- defines unit sizing constraints (chapter/episode/segment lengths as ranges, not writing)
- defines deliverable requirements per format
- validates that a project plan fits the chosen format

Hard rule:
- Adaptation translates constraints; it does NOT rewrite plot or characters.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- generate scenes, scripts, chapters (narrative engines own)
- choose story structure (story structure engine owns)
- define editing/montage rules (production editing engine)
- define marketing/distribution packaging (separate layer)
- define style palettes (style family owns)

Also forbidden:
- “format adaptation” that changes canon facts (must route to governance if canon change).

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- GENRE_PROFILE (required)
- GENRE_BLEND_PROFILE (optional)
- HYBRID_CONVENTION_SET (optional)
- TONE_PROFILE (optional)
- MOOD_PROFILE (optional)
- STORY_STRUCTURE (optional)
- PROJECT_INTENT
- FORMAT_TARGET (required: BOOK|SERIES|SHORT|YOUTUBE_LONGFORM|GAME)

PRODUCES:
- FORMAT_CONSTRAINT_PACKAGE
- UNIT_SIZING_RULES
- FORMAT_COMPLIANCE_REPORT

DEPENDS_ON:
- [07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG]
(soft) [07_PRODUCTION_FORMAT_ENGINES/02__GENRE_BLENDING_ENG, 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG, 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/ADAPTATION/
OPTIONAL:
- KB/FORMAT/ADAPTATION (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Format Target: chosen medium (BOOK, SERIES, SHORT, YOUTUBE_LONGFORM, GAME).
- Constraint Translation: mapping rule from upstream constraint -> format rule.
- Unit: minimal delivery chunk (chapter, episode, short, video segment, quest).
- Unit Sizing: allowed ranges and limits for unit duration/length (as proxies).
- Compliance: the plan satisfies all format constraints.

Enums (baseline):
- format: BOOK|SERIES|SHORT|YOUTUBE_LONGFORM|GAME
- scope: GLOBAL|ARC|UNIT
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- translating constraints into format-specific packages
- unit sizing rules (ranges, caps, minima)
- compliance validation gates

OUT OF SCOPE (HARD):
- writing or scripting
- story logic decisions
- production execution details (camera/editing/audio)
- deep style palette construction (style engines)

COLLISION RULE:
- If request is “book-specific structure rules” → Book Format engine (04) owns final spec; this engine outputs package for it
- If request is “episode/season planning” → Series & Episode engine (05)
- If request is “shorts constraints” → Short Content engine (06)
- If request is “youtube longform constraints” → YouTube Longform engine (07)
- If request is “game narrative constraints” → Game Narrative engine (08)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: FORMAT_CONSTRAINT_PACKAGE declares target format and translated constraints.
R2 (HARD) MUST: UNIT_SIZING_RULES exist for the selected format.
R3 (HARD) MUST: translation rules are testable and do not modify canon facts.
R4 (HARD) MUST: compliance report checks conflicts between genre conventions and format limits.
R5 (HARD) FORBIDDEN: mixing production implementation directives into format constraints.
R6 (SOFT) SHOULD: produce “lossy adaptation warnings” when constraints cannot be fully preserved.
R7 (HARD) MUST: if adaptation implies canon change, raise S0 and route to governance.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: FORMAT_CONSTRAINT_PACKAGE
- MUST:
  - package_id
  - version
  - format_target (BOOK|SERIES|SHORT|YOUTUBE_LONGFORM|GAME)
  - upstream_refs[] (genre/style/narrative refs)
  - translated_constraints[] (non-empty)
  - forbidden_changes[] (non-empty recommended)
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- TRANSLATED CONSTRAINT (minimum):
  - tc_id
  - source_ref (upstream artifact id)
  - target_scope (GLOBAL|ARC|UNIT)
  - format_rule (testable)
  - severity_if_broken (S0|S1|S2|S3)
  - notes
- VALIDATION:
  - format_target present
  - translated_constraints non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/ADAPTATION/FORMAT_CONSTRAINT_PACKAGE.md

ARTIFACT: UNIT_SIZING_RULES
- MUST:
  - sizing_id
  - version
  - format_target
  - unit_type (CHAPTER|EPISODE|SHORT|SEGMENT|QUEST)
  - unit_size_proxy (WORDS|MINUTES|SCENES|BEATS)
  - bounds:
    - min
    - target
    - max
  - per_arc_limits (optional)
  - checks[] (non-empty)
- VALIDATION:
  - bounds valid and min<=target<=max
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/ADAPTATION/UNIT_SIZING_RULES.md

ARTIFACT: FORMAT_COMPLIANCE_REPORT
- MUST:
  - report_id
  - version
  - format_target
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
  - recommended_repairs[] (required if S0)
- Minimum required gates:
  - G1_FORMAT_MISSING (S0)
  - G2_UNIT_SIZING_MISSING (S0)
  - G3_GENRE_FORMAT_CONFLICT (S1)
  - G4_TRANSLATION_VAGUE (S1)
  - G5_CANON_CHANGE_IMPLIED (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/ADAPTATION/FORMAT_COMPLIANCE_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load target format and upstream constraints (genre/style/narrative).
2) Translate constraints:
   - map each upstream rule into format scope (GLOBAL/ARC/UNIT)
3) Build unit sizing rules:
   - choose proxies and bounds for the format
4) Detect conflicts:
   - genre conventions vs format limits; hybrid conventions vs unit sizing
5) Emit compliance report with repairs:
   - relax via warning, partition via scope, or route to governance if canon change implied
6) Output: package + sizing rules + report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: format_target missing.
- S0-2: unit sizing rules missing or invalid bounds.
- S0-3: translated constraints empty.
- S0-4: canon change implied (must route to governance).
- S0-5: produced artifacts missing schema fields.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- genre + blend provide conventions
- style provides feel constraints (optional)
- narrative structure provides shape constraints (optional)

Downstream:
- Book Format engine consumes format package and produces book-specific plan.
- Series/Episode, Short, YouTube, Game engines consume package and produce medium plans.
- QA/consistency engines can validate deliverables against compliance report.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
