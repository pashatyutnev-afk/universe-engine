# 🏭 PRODUCTION ORCHESTRATOR ENGINE
## Canonical Orchestrator Specification  
**LEVEL: L3 · ORCHESTRATOR · OUTPUT PIPELINE · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__PRODUCTION_ORCHESTRATOR_ENG.md
- ENGINE_ID: L3-ORCH-PRODUCTION-ORCHESTRATOR-ENGINE-004
- UID: UE.ENT.ORCH.PRODUCTION
- NAME: Production Orchestrator
- CLASS: Orchestrator
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (release integrity)
- EDITABLE: true
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> If outputs aren’t packaged with gates, production becomes chaos and “final” becomes a lie.

---

## 1. PURPOSE

Production Orchestrator runs the **output production pipeline**.

It converts validated narrative/world/character packages into:
- text artifacts (scripts, outlines, books)
- visual artifacts (shots, images, renders)
- audio artifacts (voice, music, SFX)
- video assemblies (edits, episodes)
- release packages (metadata, checklists)

It enforces quality gates and produces “release-ready” bundles.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Choose production format pipeline (book/short/series/video/game)
- Route assets through production engines
- Enforce QA gates (format, continuity, technical readiness)
- Generate asset manifests and packaging structure
- Emit Production Package and Release Checklist

### OUT-OF-SCOPE (FORBIDDEN)
- Canon authority decisions (Governance)
- Changing world laws/timeline/character cores
- Skipping QA gates
- Silent editing of upstream packages (must request repair upstream)

---

## 3. REQUIRED INPUTS

### INPUT — PRODUCTION_PIPELINE_REQUEST (required fields)
- `pp_id`
- `timestamp`
- `target_format` = BOOK | SERIES | SHORT_CONTENT | YOUTUBE_LONGFORM | GAME_NARRATIVE | OTHER
- `project_goal`
- `constraints_refs` (platform limits, tone, age rating if any)
- `world_package_ref` (recommended)
- `character_package_ref` (recommended)
- `narrative_package_ref` (required for story outputs)
- `trace_id` (recommended)

Missing required fields → REJECT.

---

## 4. PIPELINE ORDER (HARD)

### Stage A — Format Selection & Adaptation
1) Genre Engine (09_PRODUCTION_FORMAT_ENGINES/01) (optional)
2) Genre Blending Engine (09/02) (optional)
3) Format Adaptation Engine (09/03) (required)
4) Target format engine:
   - Book Format Engine (09/04) OR
   - Series & Episode Engine (09/05) OR
   - Short Content Engine (09/06) OR
   - YouTube Longform Engine (09/07) OR
   - Game Narrative Engine (09/08)

**Gate A:** FORMAT_BLUEPRINT exists

### Stage B — Asset Planning
5) Visual Composition Engine (10_KNOWLEDGE_PRODUCTION_ENGINES/01) (optional)
6) Art Style Engine (10/02) (optional)
7) Camera & Cinematography Engine (10/03) (optional)
8) Lighting Engine (10/04) (optional)

**Gate B:** VISUAL_PLAN exists (if visual output required)

### Stage C — Generation
9) Image Generation Engine (10/05) (if images needed)
10) Video Generation Engine (10/06) (if video needed)
11) Sound & Music Engine (10/08) OR Sound Music Realm (12_...) (as chosen)

**Gate C:** RAW_ASSETS exist

### Stage D — Assembly
12) Editing & Montage Engine (10/07) (required for video)
13) Script assembly for text outputs (internal packaging rules)

**Gate D:** ASSEMBLED_OUTPUT exists

### Stage E — QA & Validation
14) Validation Engines (11_...) as selected:
- Language & Linguistics
- Cultural Accuracy
- Historical Accuracy
- Scientific Plausibility
- Fact Consistency (if claims exist)

**Gate E:** QA_REPORT exists and severity acceptable

---

## 5. OUTPUT ARTIFACTS (ASSEMBLED)

### 5.1 OUTPUT — PRODUCTION_PACKAGE
**REQUIRED FIELDS**
- `pp_id`
- `target_format`
- `format_blueprint_ref`
- `asset_manifest_ref` (files, ids, intended usage)
- `raw_assets_refs` (images/audio/video)
- `assembled_output_ref` (final draft/episode)
- `qa_report_ref`
- `release_checklist_ref`
- `trace_id`

### 5.2 OUTPUT — RELEASE_CHECKLIST
**REQUIRED FIELDS**
- `pp_id`
- `technical_checks` (resolution, aspect, audio levels, file naming, etc.)
- `content_checks` (continuity, forbidden content, scope compliance)
- `platform_checks` (duration, subtitles, metadata)
- `approval_requirements` (if governance approvals needed)
- `publish_ready` = true/false

### 5.3 OUTPUT — ORCHESTRATION_VERDICT
- `pp_id`
- `verdict` = PASS | FAIL | PARTIAL
- `missing_artifacts` (list)
- `qa_issues` (list)
- `repair_plan` (ordered steps)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. ROUTING RULES (HARD)

- Production cannot proceed without FORMAT_BLUEPRINT (Gate A).
- If visual outputs are required, VISUAL_PLAN must exist.
- Assembly cannot proceed without RAW_ASSETS when required.
- QA gate is mandatory before “final”.
- If QA severity HIGH/CRITICAL → FAIL and emit repair plan.
- Orchestrator must not “fix” upstream world/character/narrative; it must request upstream repair.

---

## 7. DEPENDENCIES

### REQUIRED (depending on target_format)
- Production format engines (09_)
- Knowledge production engines (10_)
- Validation engines (11_) for QA

### OPTIONAL
- World Package, Character Package (strongly recommended)
- Governance audit/consistency (if release needs trace)

---

## 8. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing Format Blueprint
- Missing required asset class (e.g., video needs montage)
- No QA report
- QA report returns HIGH/CRITICAL unresolved issues
- Output declared “final” without checklist

Reaction:
- Verdict FAIL (CRITICAL)
- Emit repair plan specifying which stage to rerun and what to regenerate.

---

## 9. TRACE RULES

- trace_id must propagate to all outputs
- if audit log is active, record:
  - stage start/end
  - gate results
  - QA results
  - final package emission

---

## 10. NON-GOALS
- Does not decide canon truth
- Does not replace narrative or world building
- Does not run platform uploads

---

## 11. FINAL STATEMENT

Production is a pipeline, not a wish.
Orchestrator makes “final” real.

---

**STATUS:** Production Orchestrator v1.0  
**LAYER:** ACTIVE
