# SPC PRO PACK — XREF BINDINGS (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/11__XREF_BINDINGS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: XREF_BINDINGS
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.2
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.XREF.DRAFT.001
OWNER: SYSTEM
ROLE: UID-only integration map: who calls PROMPT_ARCHITECT SPC, what handoffs are expected, what validators/gates apply, and which ORC/PIPELINE steps commonly consume its outputs. Placeholders must be replaced with real UIDs from 03_SYSTEM_ENTITIES and KB registries.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: PATCH
- SUMMARY: "Bound real Prompt Compiler ENG UID (UE.ENG.TG.PROMPT_COMPILER.001) and removed ENG placeholder."
- REASON: "Operational binding must be non-fiction and UID-anchored."
- IMPACT: "G2B reduced: prompt compilation ENG binding now deterministic."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.PROMPT.XREF.003

---

## 0) STRICT RULES
- UID-only references in all operational bindings.
- If a UID is unknown/not created yet → keep PLACEHOLDER and treat as GAP during runs.
- This file is an integration map, NOT a navigation index.

BOUND SPC ENTITY:
- SPC_ENTITY_UID: UE.SPC.SND.PROMPT_ARCHITECT.001

---

## 1) WHO CALLS THIS SPC (CALLERS) — UID-ONLY
CALLERS_UID_ONLY:
- ORC (music pipeline):
  - UE.ORC.MUS.GROUP_TO_ALBUM.001 | WHY: upstream identity/album plan produces planning artifacts that Prompt Architect compiles into prompt packs
  - UE.ORC.MUS.ALBUM_TO_TRACK.001 | WHY: track slot execution loop; calls Prompt Architect per slot/variant
  - UE.ORC.MUS.TRACK_TEST_DOC_GATE.001 | WHY: after QA/VAL, prompts may be patched for PASS path
  - UE.ORC.MUS.RELEASE_PACK.001 | WHY: release packaging requires frozen prompt pack snapshot references

- ENG (prompt compilation):
  - UE.ENG.TG.PROMPT_COMPILER.001 | WHY: compiles deterministic platform-native prompt packs (Suno/Udio) from taxonomy/fingerprint/hook/UGC/duration/negatives

---

## 2) WHAT THIS SPC RETURNS (HANDOFF CONTRACT)
HANDOFF_CONTRACT:
- PRIMARY_OUTPUT:
  - PROMPT_CONTRACT (STYLE/STRUCTURE/VOCALS/NEGATIVES/CONSTRAINTS)
- SECONDARY_OUTPUTS:
  - VARIANT_SET (2–5; one-axis)
  - PATCH_PROMPT (minimal delta for failed gate)
  - RECHECK_MINI (what to verify)
  - RUN_TRACE_NOTES (UID-only + memory/web flags)

Handoff fields for ORC Step Contract (COPY):
- OUTPUTS_PRODUCED:
  - prompt_contract_text
  - variant_set_text (optional)
  - patch_prompt_text (optional)
  - recheck_checklist_text
  - trace_notes

Acceptance criteria (recommended):
- must PASS Gate 01 (prompt contract clarity)
- if vocals in scope: Gate 02
- if lyrics present/full song: Gate 03
- if fusion/drift risk: Gate 04
- if iteration exists: Gate 05

---

## 3) WHERE THIS SPC SITS IN PIPELINES (PLACEMENT PATTERNS)
PLACEMENT_PATTERNS:
- Pattern A (New track from scratch):
  1) ORC step: define track brief
  2) CALL: PROMPT_ARCHITECT (PB-01 CORE WORKFLOW)
  3) RUN: Gate 01 (+ relevant others)
  4) ORC step: generation run
  5) QA/VAL → rework loop (PB-03/PB-04)

- Pattern B (After QA fail):
  1) ORC step: collect failed criteria
  2) CALL: PROMPT_ARCHITECT (PB-03 DIAGNOSE)
  3) Produce patch prompt + recheck plan
  4) ORC step: rerun generation + gates

- Pattern C (Catalog differentiation / drift):
  1) ORC step: detect drift/collision risk
  2) CALL: PROMPT_ARCHITECT (PB-07 STYLE STABILIZER)
  3) Gate 04 + Gate 01
  4) generate + QA

---

## 4) VALIDATED BY (GATES / CHECKLISTS / RUBRIC) — UID-ONLY
VALIDATED_BY_UIDS:
- Gates:
  - UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001
  - UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001
  - UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001
  - UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001
  - UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001
- Checklists:
  - UE.KB.SPC.CHK.PROMPT_ARCHITECT.READINESS.001
  - UE.KB.SPC.CHK.PROMPT_ARCHITECT.QUALITY.001
  - UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001
- Rubric:
  - UE.KB.SPC.PACK.PROMPT_ARCHITECT.RUBRIC.DRAFT.001

---

## 5) COOPERATES WITH (NEIGHBOR ENTITIES) — UID-ONLY
COOPERATES_WITH_UIDS:
- Peer SPC (music craft):
  - UE.SPC.SOUND_MUSIC.SONGWRITER.001 | WHY: structure/hook plan as input constraints; Prompt Architect compiles into platform pack
  - UE.SPC.SOUND_MUSIC.ARRANGER.001 | WHY: arrangement intent informs instrumentation tags/roles, but ownership stays with Arranger
  - UE.SPC.SOUND_MUSIC.VOCAL_DIRECTOR.001 | WHY: vocal delivery constraints inform vocal intent blocks and intelligibility constraints
  - UE.SPC.SOUND_MUSIC.AUDIO_QA.001 | WHY: QA feedback produces rework signals; Prompt Architect provides minimal patches without drift

---

## 6) CONTROLLERS APPLIED (POLICY CONSTRAINTS) — UID-ONLY
CONTROLLERS_UIDS_APPLIED:
- UE.CTL.MUS.PROMPT_CONTRACT.001 | WHY: mandatory prompt pack schema + limits
- UE.CTL.MUS.NEGATIVE_SPEC_LIBRARY.001 | WHY: reusable negative packs; anti-bloat discipline
- UE.CTL.MUS.DURATION_POLICY.001 | WHY: duration modes + hook timing windows + section budgets
- UE.CTL.MUS.UGC_VIRAL_RULESET.001 | WHY: UGC readiness constraints (clip windows, edit points)
- UE.CTL.MUS.CATALOG_MEMORY.001 | WHY: anti-repeat memory tokens; collision avoidance usage
- UE.CTL.MUS.AUDIENCE_SEGMENTS.001 | WHY: segment-driven constraints for hooks/UGC/duration tone

---

## 7) PIPELINE MAP REFERENCES (XREF ARTIFACTS) — UID-ONLY
PIPELINE_MAP_UIDS (PLACEHOLDERS):
- PLACEHOLDER_UID: UE.KB.XREF.MAP.MUSIC_PIPELINES.??? | GAP: bind when KB XREF map exists
- PLACEHOLDER_UID: UE.KB.XREF.MAP.VALIDATION_MATRIX.??? | GAP: bind when KB validation matrix exists

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- ORC calls this SPC without specifying expected outputs (handoff contract absent)
- gates required by pipeline are skipped silently
- outputs are used without trace notes (memory/web flags)
- placeholders are treated as real UIDs during execution

---

## 9) RELATED (UID-ONLY)
XREF (PLACEHOLDERS WHERE UNKNOWN):
- PLACEHOLDER_UID: UE.KB.ORC.TPL.PIPELINE_CONTRACT.??? | GAP: bind when KB ORC templates are registered
- PLACEHOLDER_UID: UE.KB.ORC.TPL.STEP_CONTRACT.??? | GAP: bind when KB ORC templates are registered
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.REGRESSION.DRAFT.001 | WHY: pack stability after changes

--- END.
