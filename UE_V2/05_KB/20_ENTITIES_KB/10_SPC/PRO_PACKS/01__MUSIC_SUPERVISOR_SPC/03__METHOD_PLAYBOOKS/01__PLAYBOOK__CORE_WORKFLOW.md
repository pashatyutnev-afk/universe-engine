# 01__PLAYBOOK__CORE_WORKFLOW — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_WORKFLOW.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Core Workflow
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: PLAYBOOK
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.CORE.001
OWNER: SPC (Music Supervisor)
ROLE: Primary workflow to produce pack outputs and run baseline validations.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Core workflow playbook initialized for Music Supervisor SPC pack."
- REASON: "Deterministic end-to-end run with checkpoints and validation hooks."
- IMPACT: "Defines PB-01 run order + required evidence."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.PB.CORE.001

---

## PLAYBOOK_ID
- ID: PB-01
- NAME: CORE_WORKFLOW

---

## GOAL
Произвести **PRIMARY_OUTPUTS** пака Music Supervisor SPC в рамках scope и провести базовую приёмку через чеклисты/гейты.

---

## PACK BINDINGS (MUST MATCH PACK PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>
- PRIMARY_OUTPUTS:
  - <output_1>
  - <output_2>

---

## REQUIRED INPUTS
> Минимальные входы для любого задания.

- TASK_ID: <id or date>
- TASK_BRIEF: <что нужно получить>
- TARGET_PLATFORM/FORMAT: <e.g., short/album/scene/game/etc>
- CONSTRAINTS (if any): <time, length, style, compliance>
- EXISTING_ARTIFACTS (if any): <what already exists>

## OPTIONAL INPUTS
- REFERENCES (RAW NAV): <raw links>
- TOPIC_UIDS (UID-only): <topic uid list>
- PRIOR_RUN_TRACE (if iteration): <previous trace summary>

---

## OUTPUTS
- REQUIRED:
  - <primary_output_1>
  - <primary_output_2>
- OPTIONAL:
  - <secondary_output_1>

---

## PRECHECK (READINESS)
Run and record:
- CHK_UID: <CHK_UID_READINESS>  (expected: 04__CHECKLISTS/01__CHK__READINESS.md)
- PASS → proceed
- REWORK/FAIL → STOP and request missing inputs (no further work)

Evidence to record:
- INPUTS_SUMMARY (1–5 bullets)
- Scope confirmed (covers/excludes)

---

## STEPS (RUN ORDER)

### STEP 1 — Intake Normalize
- Normalize inputs into canonical bullets:
  - goal
  - deliverables
  - constraints
  - scope boundaries
- Declare “assumption list” ONLY if user did not provide the info (keep minimal).

Output:
- NORMALIZED_TASK_CARD

### STEP 2 — Scope Check (Hard Boundary)
- Confirm task is IN-SCOPE:
  - Not in EXCLUDES
- If out-of-scope:
  - STOP → produce routing note (see PB-02 escalation format)

Output:
- SCOPE_DECISION: IN / OUT

### STEP 3 — Output Mapping (Outputs ↔ Outcomes)
- Map required deliverables to skill-tree outcomes:
  - OUTPUT → supporting outcomes (IDs)
- Choose validations that must pass:
  - CHK_UID / GATE_UID list (UID-only)

Output:
- OUTPUT_TRACE_MAP

### STEP 4 — Draft Production Pass
- Produce draft versions of required outputs.
- Keep them minimal but complete enough for validation.

Output:
- DRAFT_OUTPUTS

### STEP 5 — Baseline Quality Check (Checklist Layer)
Run in order:
1) CHK_UID: <CHK_UID_QUALITY> (expected: 04__CHECKLISTS/02__CHK__QUALITY.md)
2) CHK_UID: <CHK_UID_COMPLIANCE> (expected: 04__CHECKLISTS/03__CHK__COMPLIANCE.md)

Record result:
- PASS / REWORK / FAIL for each

If REWORK:
- Go to STEP 6 (one-axis patch loop)
If FAIL:
- STOP → handoff to PB-02 (diagnose/rework) with failure evidence

### STEP 6 — One-Axis Patch Loop (Minimal Repair)
- Choose ONE axis:
  - clarity OR structure OR density OR consistency OR compliance
- Apply minimal change only on that axis.
- Re-run the specific checklist that failed.
- Max iterations: <N> (recommend 2–4)

If still REWORK after N:
- STOP → PB-02 with escalation note

Output:
- PATCH_LOG (axis changed + what changed)

### STEP 7 — Gate Layer (Acceptance)
Run gates in order:
1) <GATE_UID_CORE_OUTPUT_QUALITY> (expected: 05__KB_GATES/01__GATE__CORE_OUTPUT_QUALITY.md)
2) <GATE_UID_CONSISTENCY> (expected: 05__KB_GATES/02__GATE__CONSISTENCY.md)
3) <GATE_UID_EDGE_CASES> (expected: 05__KB_GATES/03__GATE__EDGE_CASES.md) — only if applicable

Decision:
- PASS → proceed
- REWORK → STEP 6 (one-axis) then re-run the failed gate
- FAIL → PB-02 (diagnose/rework)

---

## CHECKPOINTS (MANDATORY EVIDENCE)
- CP-01: Readiness checklist executed
  - UID: <CHK_UID_READINESS>
  - RESULT: <PASS|REWORK|FAIL>
- CP-02: Quality checklist executed
  - UID: <CHK_UID_QUALITY>
  - RESULT: <...>
- CP-03: Compliance checklist executed
  - UID: <CHK_UID_COMPLIANCE>
  - RESULT: <...>
- CP-04: Gate results recorded
  - GATES:
    - <GATE_UID_CORE_OUTPUT_QUALITY>: <...>
    - <GATE_UID_CONSISTENCY>: <...>
    - <GATE_UID_EDGE_CASES>: <... if used>

---

## FAIL MODES + QUICK FIXES (EXAMPLES)
> В реальном паке заменить на реальные fail modes из skill tree. Тут — шаблон.

### FM-CORE-001 — Output unclear
- SYMPTOM: key intent/steps ambiguous
- AXIS: clarity
- QUICK FIX: rewrite the minimal core statements, reduce optional text
- VALIDATE_AFTER: <CHK_UID_QUALITY>, <GATE_UID_CORE_OUTPUT_QUALITY>

### FM-CORE-002 — Contradiction detected
- SYMPTOM: conflicting rules/claims inside output
- AXIS: consistency
- QUICK FIX: enforce one meaning per term; remove conflicting sentence
- VALIDATE_AFTER: <GATE_UID_CONSISTENCY>

### FM-CORE-003 — Scope creep
- SYMPTOM: out-of-scope sections appear
- AXIS: compliance
- QUICK FIX: remove out-of-scope block; add routing note if needed
- VALIDATE_AFTER: <CHK_UID_COMPLIANCE>, <GATE_UID_CORE_OUTPUT_QUALITY>

---

## STOP / ESCALATE RULES
STOP immediately if:
- Required inputs missing after CHK-READINESS
- Task is OUT-OF-SCOPE
- Hard limit violation is central (cannot be removed)
ESCALATE to PB-02 if:
- Same gate/check fails twice after one-axis fixes
- Contradictions cannot be resolved without changing scope

---

## ARTIFACT TRACE (MINIMUM OUTPUT LOG)
Record at end:

- TASK_ID: <...>
- INPUTS_SUMMARY:
  - <...>
- OUTPUTS_PRODUCED:
  - <...>
- VALIDATIONS:
  - PASSED: <UID list>
  - REWORK/FAILED: <UID list>
- AXIS_CHANGED (if any): <one axis>
- NEXT_ACTION: <NONE|PB-02|PB-03|...>

---
END
