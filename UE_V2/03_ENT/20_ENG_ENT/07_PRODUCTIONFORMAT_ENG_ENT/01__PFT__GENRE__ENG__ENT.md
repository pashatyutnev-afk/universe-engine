# GENRE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG.md
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
UID: UE.ENG.PROD.FORMAT.GENRE.001
OWNER: SYSTEM
ROLE: Defines deterministic genre selection and constraint packaging for production formats: genre tags, required conventions, forbidden conventions, and validation gates without writing content.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Genre Engine created: genre profile schema, convention sets, and validation gates."
- REASON: "Production format layer needs a stable genre constraint package to drive blending/adaptation and downstream production planning."
- IMPACT: "Projects can lock genre constraints and validate drift across formats."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.GENRE.001

---

## 0) PURPOSE (LAW)
This engine owns **GENRE constraints for production**:
- selects/declares genre tags (controlled vocabulary)
- defines genre conventions as constraints (must/forbidden/allowed)
- packages genre into reusable GENRE_PROFILE that downstream engines can consume
- emits gates that detect genre drift

Hard rule:
- Genre here is a constraint package, not a writing prompt and not style ownership.
- Style “how it feels” remains in `06_GENRE_STYLE_ENGINES`; this engine locks “what kind of product rules apply”.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write plot, scenes, dialogue (narrative/character own)
- define world laws/civilizations (world family owns)
- define editing/camera/sound implementation (production media engines own)
- define tone/mood/atmosphere palettes (style family owns)
- define distribution/marketing strategy (outside this family)

Also forbidden:
- “genre = vibes only” without conventions and constraints.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- PROJECT_INTENT
- STYLE_BRIEF (optional)
- WORLD_CONTEXT_BRIEF (optional)
- FORMAT_TARGET (optional: book/series/short/youtube/game)

PRODUCES:
- GENRE_PROFILE
- GENRE_CONVENTION_SET
- GENRE_GATES_REPORT

DEPENDS_ON:
- []  (base production-format primitive)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/GENRE/
OPTIONAL:
- KB/FORMAT/GENRE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Genre Tag: controlled label (e.g., SCI_FI, HORROR, THRILLER, DRAMA, FANTASY, MYSTERY).
- Convention: constraint rule tied to genre expectations (must/forbidden).
- Drift: project outputs violate conventions or introduce forbidden conventions.
- Hybrid: explicit multi-genre profile (handled deeper by Genre Blending engine, but can be declared here).

Enums (baseline):
- scope: GLOBAL|ARC|EPISODE|SCENE_WINDOW
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- genre tag selection and packaging
- convention sets as constraints
- drift validation gates

OUT OF SCOPE (HARD):
- style palettes (tone/mood/atmosphere) → style engines
- story structure engineering → narrative engines
- editing rhythm (screen-time) → editing/montage engine

COLLISION RULE:
- If request is “blend multiple genres” → `02__GENRE_BLENDING_ENG`
- If request is “adapt to book/series/game rules” → `03__FORMAT_ADAPTATION_ENG` and specific format engines
- If request is “tone/mood palette” → `06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG`

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: GENRE_PROFILE declares primary genre and optional secondary genres.
R2 (HARD) MUST: GENRE_CONVENTION_SET lists MUST/FORBIDDEN conventions (non-empty).
R3 (HARD) MUST: conventions are testable and scoped (GLOBAL/ARC/EPISODE).
R4 (HARD) FORBIDDEN: conventions that are actually production implementation recipes (camera/editing).
R5 (HARD) MUST: GENRE_GATES_REPORT checks drift against conventions.
R6 (SOFT) SHOULD: include “audience promise” as constraints (not marketing copy).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: GENRE_PROFILE
- MUST:
  - genre_profile_id
  - version
  - primary_genre_tag (controlled)
  - secondary_genre_tags[] (optional)
  - scope (GLOBAL)
  - promise_constraints[] (optional but recommended)
  - convention_set_ref
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- VALIDATION:
  - primary_genre_tag present
  - convention_set_ref present
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GENRE/GENRE_PROFILE.md

ARTIFACT: GENRE_CONVENTION_SET
- MUST:
  - convention_set_id
  - version
  - conventions[] (non-empty)
  - checks[] (non-empty)
- CONVENTION (minimum):
  - convention_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - statement (testable)
  - scope (GLOBAL|ARC|EPISODE|SCENE_WINDOW)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - conventions non-empty
  - at least one MUST and one FORBIDDEN
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GENRE/GENRE_CONVENTION_SET.md

ARTIFACT: GENRE_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_PRIMARY_GENRE_MISSING (S0)
  - G2_CONVENTIONS_EMPTY (S0)
  - G3_IMPL_RECIPE_LEAK (S1) (conventions contain camera/editing directions)
  - G4_DRIFT_DETECTED (S1)
  - G5_CONFLICT_UNRESOLVED (S2)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GENRE/GENRE_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Read PROJECT_INTENT + optional context briefs.
2) Select primary/secondary genre tags (controlled set).
3) Build convention set (must/forbidden/allowed) with scope.
4) Define conflict rules for secondary genres (if any).
5) Run gates (empties, recipe-leak, drift).
6) Emit: genre profile + convention set + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing primary_genre_tag.
- S0-2: conventions empty or missing MUST/FORBIDDEN.
- S0-3: produced artifacts missing required schema fields.
- S0-4: hidden dependencies (requires other engines but not declared).
- S0-5: conventions violate boundary (implementation recipes, not constraints).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- project intent and target format

Downstream:
- Genre Blending engine (resolves multi-genre conflicts)
- Format Adaptation engine (maps genre constraints into format rules)
- Book/Series/Short/YouTube/Game format engines (apply conventions per medium)
- Style engines may align tone/mood with genre promise but remain separate owners

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
