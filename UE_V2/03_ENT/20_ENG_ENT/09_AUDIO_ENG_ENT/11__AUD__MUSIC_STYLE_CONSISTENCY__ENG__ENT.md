# MUSIC STYLE CONSISTENCY ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/11__MUSIC_STYLE_CONSISTENCY_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: SOUND (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.SOUND.MUSIC.CONSISTENCY.001
OWNER: SYSTEM
ROLE: Defines deterministic consistency validation and enforcement for music: invariant registry, drift detection rules, cue-to-cue coherence checks, and gates. Consumes composition/harmony/melody/rhythm/arrangement artifacts; outputs consistency reports and repair directives.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Music Style Consistency Engine created: invariant registry schema, drift rules, coherence checks, and gates."
- REASON: "Deep music assets drift easily across cues; system needs deterministic consistency enforcement."
- IMPACT: "Music remains stylistically coherent across episodes/scenes and versions."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.MUSIC.CONSISTENCY.001

---

## 0) PURPOSE (LAW)
This engine owns **MUSIC CONSISTENCY enforcement**:
- defines music invariants (what must stay constant across cues)
- defines drift detection rules across themes/motifs/harmony/rhythm/arrangement
- produces consistency reports and repair directives (what to change upstream)
- gates against “random cue syndrome” and style fragmentation

Hard rule:
- This engine validates and prescribes repairs; it does NOT rewrite composition outputs silently.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- create themes/motifs from scratch (composition engine)
- define harmony language (harmony engine)
- write melodies (melody engine)
- define groove (rhythm engine)
- arrange instruments (arrangement engine)
- mix/master audio (mix/master engine)
- do production placement/sync (production layer)

FORBIDDEN:
- changing upstream artifacts without explicit repair directives (must be declarative).

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- THEME_MOTIF_BIBLE (recommended)
- TONAL_DIRECTION_POLICY (optional)
- CHORD_LEXICON / PROGRESSION_RULESET (optional)
- GROOVE_PALETTE / TEMPO_METER_POLICY (optional)
- INSTRUMENTATION_PALETTE (optional)
- CUE_SET_INDEX (optional: list of cues in project)
- MUSIC_ASSET_SET (optional)

PRODUCES:
- MUSIC_INVARIANT_REGISTRY
- DRIFT_DETECTION_RULESET
- CONSISTENCY_REPORT
- REPAIR_DIRECTIVE_SET
- CONSISTENCY_GATES_REPORT

DEPENDS_ON:
- [] (validator/consistency layer inside music family)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/CONSISTENCY/
OPTIONAL:
- KB/MUSIC/CONSISTENCY (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Invariant: rule that must remain true across all cues (e.g., motif identity, allowed tonal centers).
- Drift: measurable deviation from invariant (e.g., new meter introduced unexpectedly).
- Coherence Check: multi-asset check across cues (e.g., harmonic language consistency).
- Repair Directive: explicit instruction to rerun/adjust upstream engines.

Enums (baseline):
- invariant_scope: GLOBAL|ARC|CUE
- severity: S0|S1|S2|S3
- drift_level: LOW|MED|HIGH

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- invariant registry and drift rules
- consistency reporting and repair directives
- gates for enforcement integrity

OUT OF SCOPE (HARD):
- composing or arranging content
- production placement/sync
- mixing/mastering

COLLISION RULE:
- If request is “change motifs” → composition engine (apply repair directive)
- If request is “change harmony rules” → harmony engine (apply repair directive)
- If request is “change arrangement palette” → arrangement engine
- If request is “fix mix/master” → mix/master engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: MUSIC_INVARIANT_REGISTRY lists invariants with severity and scope.
R2 (HARD) MUST: DRIFT_DETECTION_RULESET defines checks for motifs, tonal policy, groove, and instrumentation.
R3 (HARD) MUST: CONSISTENCY_REPORT lists detected drifts and affected assets.
R4 (HARD) MUST: REPAIR_DIRECTIVE_SET provides explicit actions and target engines.
R5 (HARD) FORBIDDEN: silent auto-changes to upstream artifacts.
R6 (SOFT) SHOULD: include tolerance bands for drift where appropriate.
R7 (HARD) MUST: gates detect missing invariants, missing directives, and report incoherence.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: MUSIC_INVARIANT_REGISTRY
- MUST:
  - registry_id
  - version
  - invariants[] (non-empty)
  - tolerance_bands[] (optional)
  - checks[] (non-empty)
- INVARIANT (minimum):
  - invariant_id
  - scope (GLOBAL|ARC|CUE)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
  - evidence_source_refs[] (optional: motif/harmony/groove refs)
- VALIDATION:
  - invariants non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/CONSISTENCY/MUSIC_INVARIANT_REGISTRY.md

---

ARTIFACT: DRIFT_DETECTION_RULESET
- MUST:
  - ruleset_id
  - version
  - checks[] (non-empty)
  - metrics[] (optional)
- CHECK (minimum):
  - check_id
  - category (MOTIF|TONAL|HARMONY|RHYTHM|INSTRUMENTATION|ARRANGEMENT)
  - pass_condition (testable)
  - fail_condition (testable)
  - severity_if_fail (S0|S1|S2|S3)
  - tolerance (optional)
- VALIDATION:
  - checks non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/CONSISTENCY/DRIFT_DETECTION_RULESET.md

---

ARTIFACT: CONSISTENCY_REPORT
- MUST:
  - report_id
  - version
  - evaluated_assets[] (non-empty)
  - drifts[] (can be empty)
  - overall (PASS|WARN|FAIL)
- DRIFT (minimum):
  - drift_id
  - drift_level (LOW|MED|HIGH)
  - violated_invariant_ids[] (non-empty)
  - affected_assets[] (non-empty)
  - evidence (testable)
  - recommended_repairs_refs[] (optional)
- VALIDATION:
  - evaluated_assets non-empty
  - FAIL if any S0 drift present (via violated invariants)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/CONSISTENCY/CONSISTENCY_REPORT.md

---

ARTIFACT: REPAIR_DIRECTIVE_SET
- MUST:
  - directive_set_id
  - version
  - directives[] (non-empty if drifts exist)
  - checks[] (non-empty)
- DIRECTIVE (minimum):
  - directive_id
  - target_engine (file ref)
  - action (RERUN|ADJUST_RULESET|RESELECT_PALETTE|REGENERATE_CANDIDATES)
  - scope (GLOBAL|ARC|CUE)
  - instruction (testable)
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - if drifts exist, directives non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/CONSISTENCY/REPAIR_DIRECTIVE_SET.md

---

ARTIFACT: CONSISTENCY_GATES_REPORT
- MUST:
  - gates_report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_INVARIANTS_EMPTY (S0)
  - G2_DRIFT_RULESET_EMPTY (S0)
  - G3_EVALUATED_ASSETS_EMPTY (S0)
  - G4_DRIFTS_WITHOUT_DIRECTIVES (S0)
  - G5_SILENT_CHANGE_ATTEMPT (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/CONSISTENCY/CONSISTENCY_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load music identity artifacts (motifs, tonal, harmony, rhythm, arrangement) and cue set list.
2) Build invariant registry (what must stay constant).
3) Build drift detection ruleset (checks and tolerances).
4) Evaluate assets and produce consistency report.
5) Produce repair directives for each violated invariant.
6) Run gates (missing invariants, drifts without directives) and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: invariant registry empty.
- S0-2: drift detection ruleset empty.
- S0-3: evaluated assets list empty.
- S0-4: drifts exist but repair directives missing.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- consumes outputs from composition/harmony/melody/rhythm/arrangement

Downstream:
- repair directives route back to upstream engines (explicit actions)
- mix/master and production placement can run after consistency PASS/WARN

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
