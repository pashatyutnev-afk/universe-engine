# MIX / MASTER ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/13__MIX_MASTER_ENG.md
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
UID: UE.ENG.SOUND.MIX.MASTER.001
OWNER: SYSTEM
ROLE: Defines deterministic mix/master targets and QC: loudness targets (abstract), dynamic range policy, spectral balance guardrails, stem deliverables, and validation gates. Consumes arrangement/vocal/sound design artifacts; does not own production placement or edit decisions.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Mix/Master Engine created: loudness/dynamics/spectral policies, stem deliverable spec, QC gates."
- REASON: "Deep audio finishing needs deterministic targets and quality gates for stamping."
- IMPACT: "Audio outputs become consistent, measurable, and deliverable-ready."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.MIX.MASTER.001

---

## 0) PURPOSE (LAW)
This engine owns **MIX / MASTER finishing constraints**:
- loudness targets and tolerances (abstract; can be mapped to LUFS later)
- dynamic range policy and peak/crest guardrails (abstract)
- spectral balance guardrails (low/mid/high energy constraints)
- stem deliverable specification (what stems to export)
- QC gates to detect clipping risk, masking risk, and inconsistent loudness across assets

Hard rule:
- This engine finishes audio; it does NOT place audio on edit timelines (production sound engine) and does NOT decide montage.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- compose music (composition/harmony/melody engines)
- arrange instruments (arrangement engine)
- define vocal performance (vocal engine)
- place audio in scenes or align to EDL (production sound engine)
- define editing/montage (editing engine)

FORBIDDEN:
- vendor-specific plugin chains as mandatory output (keep abstract, policy-based)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- INSTRUMENTATION_PALETTE (optional)
- SECTION_ROLE_ASSIGNMENT (optional)
- VOCAL_STYLE_PROFILE (optional)
- SONIC_MOTIF_LIBRARY / SFX_PALETTE_SPEC (optional)
- AUDIO_LAYER_PLAN (optional; from production layer for context only)
- MIX_MASTER_REQUEST (optional)

PRODUCES:
- LOUDNESS_DYNAMIC_POLICY
- SPECTRAL_BALANCE_GUARDRAILS
- STEM_DELIVERABLE_SPEC
- MIX_MASTER_QC_REPORT
- MIX_MASTER_GATES_REPORT

DEPENDS_ON:
- [] (finishing layer; consumes upstream audio design/arrangement)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/MIX_MASTER/
OPTIONAL:
- KB/MUSIC/MIX_MASTER (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Loudness Target: normalized loudness level proxy (or LUFS if defined later).
- Dynamic Range: allowed difference between peaks and average energy (proxy).
- Spectral Balance: energy distribution constraints across bands (LOW/MID/HIGH).
- Stem: separated audio subgroup deliverable (DRUMS, BASS, MUSIC, VOCALS, FX).
- QC Check: measurable/assessable check (proxy) with severity.

Enums (baseline):
- band: LOW|MID|HIGH
- stem_type: DRUMS|BASS|HARMONY|LEAD|VOCALS|FX|AMBIENCE|FULL_MIX
- target_platform: GENERIC|STREAMING|FILM|GAME (abstract)
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- mastering targets/policies and tolerances
- spectral/dynamic guardrails
- stem deliverable requirements
- QC report and gates

OUT OF SCOPE (HARD):
- composition/harmony/melody creation
- arrangement decisions
- production placement/sync
- editing decisions

COLLISION RULE:
- If request is “place music under dialogue in scene” → production sound engine
- If request is “change arrangement to fix masking” → arrangement engine (mix engine outputs repair directive)
- If request is “rewrite vocal takes” → vocal performance engine (mix engine flags issues)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: LOUDNESS_DYNAMIC_POLICY defines targets and tolerances per platform profile.
R2 (HARD) MUST: SPECTRAL_BALANCE_GUARDRAILS define band guardrails and masking avoidance rules.
R3 (HARD) MUST: STEM_DELIVERABLE_SPEC defines required stems and naming rules.
R4 (HARD) MUST: MIX_MASTER_QC_REPORT includes checks and pass/fail states.
R5 (HARD) FORBIDDEN: plugin-specific chain requirements as mandatory.
R6 (SOFT) SHOULD: include repair directives when QC fails (route to arrangement/vocal engines).
R7 (HARD) MUST: gates detect missing policies, missing stems, and QC schema failures.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: LOUDNESS_DYNAMIC_POLICY
- MUST:
  - policy_id
  - version
  - platform_profiles[] (non-empty)
  - checks[] (non-empty)
- PLATFORM PROFILE (minimum):
  - platform (GENERIC|STREAMING|FILM|GAME)
  - loudness_target_proxy (0..100 or labeled)
  - loudness_tolerance (± value proxy)
  - peak_guardrail_proxy (0..100)
  - dynamic_range_target_proxy (0..100)
  - dynamic_tolerance (± value proxy)
- VALIDATION:
  - platform_profiles non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MIX_MASTER/LOUDNESS_DYNAMIC_POLICY.md

---

ARTIFACT: SPECTRAL_BALANCE_GUARDRAILS
- MUST:
  - guardrails_id
  - version
  - band_targets[] (non-empty)
  - masking_rules[] (non-empty)
  - checks[] (non-empty)
- BAND TARGET (minimum):
  - band (LOW|MID|HIGH)
  - energy_target_proxy (0..100)
  - bounds (min,max)
  - notes
- MASKING RULE (minimum):
  - rule_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - band_targets non-empty
  - bounds valid
  - masking_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MIX_MASTER/SPECTRAL_BALANCE_GUARDRAILS.md

---

ARTIFACT: STEM_DELIVERABLE_SPEC
- MUST:
  - deliverable_id
  - version
  - required_stems[] (non-empty)
  - naming_rule (required)
  - export_format_policy (optional; abstract)
  - qc_checks[] (non-empty)
- STEM (minimum):
  - stem_type (DRUMS|BASS|HARMONY|LEAD|VOCALS|FX|AMBIENCE|FULL_MIX)
  - required (bool)
  - notes
- VALIDATION:
  - required_stems non-empty
  - naming_rule present
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MIX_MASTER/STEM_DELIVERABLE_SPEC.md

---

ARTIFACT: MIX_MASTER_QC_REPORT
- MUST:
  - report_id
  - version
  - evaluated_assets[] (non-empty)
  - checks_run[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
  - repair_directives[] (optional; required if FAIL)
- CHECK RUN (minimum):
  - check_id
  - description
  - severity
  - pass (bool)
  - measured_proxy (optional)
- ISSUE (minimum):
  - issue_id
  - type (CLIPPING_RISK|LOUDNESS_OUT|DYNAMIC_OUT|SPECTRAL_IMBALANCE|MASKING_RISK)
  - affected_asset_ref
  - severity (S0|S1|S2|S3)
  - evidence (testable)
- REPAIR DIRECTIVE (optional):
  - directive_id
  - target_engine (ARRANGEMENT|VOCAL|SOUND_DESIGN|MIX)
  - instruction (testable)
  - priority (S0|S1|S2|S3)
- VALIDATION:
  - evaluated_assets non-empty
  - checks_run non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MIX_MASTER/MIX_MASTER_QC_REPORT.md

---

ARTIFACT: MIX_MASTER_GATES_REPORT
- MUST:
  - gates_report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_LOUDNESS_POLICY_MISSING (S0)
  - G2_SPECTRAL_GUARDRAILS_MISSING (S0)
  - G3_STEMS_MISSING (S0)
  - G4_QC_REPORT_SCHEMA_FAIL (S0)
  - G5_PLUGIN_SPECIFIC_LEAK (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MIX_MASTER/MIX_MASTER_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load arrangement/vocal/sound design context and any platform targets.
2) Define loudness + dynamic policy per platform profile.
3) Define spectral balance guardrails and masking rules.
4) Define stem deliverable spec (stems + naming + QC).
5) Run QC checks on evaluated assets (or define QC plan if assets not yet rendered).
6) Emit QC report + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: loudness/dynamic policy missing.
- S0-2: spectral guardrails missing.
- S0-3: stem deliverable spec missing required stems.
- S0-4: QC report schema invalid.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- arrangement/vocal/sound design provide the material and constraints

Downstream:
- production audio engine can place mastered stems in scenes (separate ownership)
- QA/consistency engines can validate cross-asset loudness consistency
- delivery pipelines consume stems and QC report

Boundary:
- placement/sync in 08 production sound, deep finishing here.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Production placement boundary:
  08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
