# GENRE BLENDING ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/02__GENRE_BLENDING_ENG.md
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
UID: UE.ENG.PROD.FORMAT.GENRE.BLEND.001
OWNER: SYSTEM
ROLE: Defines deterministic multi-genre blending: conflict resolution between conventions, dominance schedules by scope, hybrid rulesets, and validation gates to prevent incoherent genre mixtures.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Genre Blending Engine created: blend profile schema, dominance schedule, convention conflict resolver, and drift gates."
- REASON: "Projects frequently mix genres; without rules the output becomes incoherent."
- IMPACT: "Hybrid genre products become stampable and auditable across formats."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.GENRE.BLEND.001

---

## 0) PURPOSE (LAW)
This engine owns **GENRE BLENDING constraints**:
- defines how multiple genres coexist (dominant vs subordinate)
- resolves convention conflicts (must/forbidden collisions)
- defines dominance schedule by scope (global/arc/episode)
- emits hybrid conventions and gates against “genre soup”

Hard rule:
- Blending is deterministic: each scope has a dominance rule and conflict policy.
- This engine does NOT replace style engines; it resolves *genre conventions*, not tone palettes.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write content (narrative/character)
- define tone/mood/atmosphere (style family)
- define world laws (world family)
- define editing/camera/sound recipes (production media engines)
- define format rules (format adaptation/book/series engines own)

Also forbidden:
- “blend = list two genres” without conflict rules and dominance schedule.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- GENRE_PROFILE (required)
- GENRE_CONVENTION_SET (required)
- PROJECT_INTENT (optional)
- FORMAT_TARGET (optional)

PRODUCES:
- GENRE_BLEND_PROFILE
- HYBRID_CONVENTION_SET
- BLEND_GATES_REPORT

DEPENDS_ON:
- [07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/GENRE_BLEND/
OPTIONAL:
- KB/FORMAT/GENRE_BLEND (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Dominant Genre: genre whose conventions win in conflicts for a given scope.
- Subordinate Genre: genre whose conventions apply only when non-conflicting or explicitly scheduled.
- Dominance Schedule: mapping of scope -> dominant genre(s).
- Convention Conflict: two conventions cannot both be satisfied.
- Hybrid Convention: resolved rule produced by this engine (merge/override/partition).

Enums (baseline):
- scope: GLOBAL|ARC|EPISODE|SCENE_WINDOW
- conflict_policy: OVERRIDE|PARTITION|MERGE|VETO
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- multi-genre dominance schedule
- conflict resolution between conventions
- hybrid convention packaging
- drift and incoherence gates

OUT OF SCOPE (HARD):
- style palette decisions (tone/mood/atmosphere)
- narrative structure decisions
- format-specific adaptation rules (handled by format adaptation)

COLLISION RULE:
- If request is “adapt these genres to series/book/game constraints” → `03__FORMAT_ADAPTATION_ENG`
- If request is “choose tone/mood for hybrid” → style engines (tone/mood)
- If request is “plot must include X because genre” → narrative engines decide content, this engine only constrains conventions

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: GENRE_BLEND_PROFILE lists all genres involved and assigns dominance schedule per scope.
R2 (HARD) MUST: HYBRID_CONVENTION_SET includes explicit conflict resolutions for collisions.
R3 (HARD) MUST: each conflict uses one policy: OVERRIDE, PARTITION, MERGE, or VETO.
R4 (HARD) MUST: partitions specify where each convention applies (scope/segment tags).
R5 (HARD) FORBIDDEN: unresolved convention conflicts (if detected).
R6 (SOFT) SHOULD: limit to 2–3 active genres per scope (else warn).
R7 (HARD) MUST: gates detect incoherence (genre soup), missing dominance, and unresolved conflicts.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: GENRE_BLEND_PROFILE
- MUST:
  - blend_profile_id
  - version
  - genres[] (non-empty; includes primary+secondary)
  - dominance_schedule[] (non-empty)
  - active_limit_policy (optional)
  - conflict_policy_defaults (optional)
  - validation_checks[] (non-empty)
- GENRE ENTRY (minimum):
  - genre_tag
  - role (PRIMARY|SECONDARY|ACCENT)
  - weight (0..100) (optional)
- DOMINANCE SCHEDULE ENTRY (minimum):
  - scope (GLOBAL|ARC|EPISODE|SCENE_WINDOW)
  - dominant_genre_tags[] (non-empty)
  - subordinate_genre_tags[] (optional)
  - rationale (short)
- VALIDATION:
  - at least one dominant genre for GLOBAL
  - all listed genres are in GENRE_PROFILE
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GENRE_BLEND/GENRE_BLEND_PROFILE.md

ARTIFACT: HYBRID_CONVENTION_SET
- MUST:
  - hybrid_convention_set_id
  - version
  - base_convention_set_ref
  - resolved_conventions[] (non-empty)
  - conflicts_resolved[] (non-empty if conflicts exist)
  - checks[] (non-empty)
- RESOLVED CONVENTION (minimum):
  - rc_id
  - source_convention_ids[] (one or more)
  - resulting_rule (testable)
  - scope
  - policy_used (OVERRIDE|PARTITION|MERGE|VETO)
  - owner_genre_tag (optional)
  - notes
- CONFLICT RESOLUTION (minimum):
  - conflict_id
  - convention_a_id
  - convention_b_id
  - policy_used
  - resolution_text (testable)
  - partition_scope (optional; required if policy=PARTITION)
  - severity_if_ignored (S0|S1|S2|S3)
- VALIDATION:
  - every conflict has policy_used and resolution_text
  - if PARTITION used, partition_scope defined
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GENRE_BLEND/HYBRID_CONVENTION_SET.md

ARTIFACT: BLEND_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_DOMINANCE_MISSING (S0)
  - G2_CONFLICT_UNRESOLVED (S0)
  - G3_TOO_MANY_ACTIVE_GENRES (S2)
  - G4_SCOPE_PARTITION_MISSING (S1)
  - G5_DRIFT_DETECTED (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GENRE_BLEND/BLEND_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load GENRE_PROFILE + convention set.
2) Identify genre set and detect convention collisions.
3) Define dominance schedule by scope.
4) Resolve conflicts:
   - choose policy (override/partition/merge/veto)
   - produce resolved rule text
5) Build hybrid convention set.
6) Run gates (dominance missing, unresolved conflicts, too many genres).
7) Emit: blend profile + hybrid convention set + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: no GLOBAL dominance schedule entry.
- S0-2: any detected conflict remains unresolved.
- S0-3: hybrid convention set missing required schema fields.
- S0-4: hidden dependencies (requires other engines but not declared).
- S0-5: partition policy used without partition scope definition.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- Genre engine provides base profile and conventions.

Downstream:
- Format Adaptation engine maps hybrid conventions into book/series/short/youtube/game constraints.
- Narrative engines can be validated against hybrid conventions (but still own content decisions).
- Style engines may align tone/mood for the hybrid (separate ownership).

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
