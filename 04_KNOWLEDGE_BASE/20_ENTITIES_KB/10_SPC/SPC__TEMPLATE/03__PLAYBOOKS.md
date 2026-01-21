# 03__PLAYBOOKS — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/03__PLAYBOOKS.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (method playbooks)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.PLAYBOOKS.001
OWNER: SYSTEM
ROLE: Canonical playbook contract template (repeatable workflows + diagnose/rework loops + validation binding).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial playbooks template for SPC Pro Packs."
- REASON: "Make packs executable: steps + checkpoints + validation gates."
- IMPACT: "All SPC packs must include at least one CORE playbook and one REWORK playbook."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.PLAYBOOKS.001

---

## PURPOSE (LAW)
Этот документ содержит **операционные плейбуки**: повторяемые процессы SPC.
Каждый плейбук обязан:
- объявить inputs/outputs,
- дать пошаговый workflow,
- иметь checkpoints (где проверяем),
- связать проверку с gates/checklists (UID-only),
- описать fail modes и быстрые фиксы.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## PLAYBOOK INDEX (README)
- PB-01: CORE_WORKFLOW
- PB-02: ONE_AXIS_PATCH_LOOP
- PB-03: DIAGNOSE_AND_REWORK
- PB-04: QUALITY_POLISH_AND_FINALIZE
- PB-05: ESCALATION_AND_ROUTING (optional)

> RULE: В реальном паке можно держать 3–12 плейбуков, но минимум: PB-01 + PB-02.

---

# PLAYBOOK CONTRACT (MUST USE THIS SHAPE)
## FIELDS
- PLAYBOOK_ID
- GOAL
- REQUIRED_INPUTS / OPTIONAL_INPUTS
- OUTPUTS
- PRECHECK (readiness)
- STEPS
- CHECKPOINTS (with UID-only validation)
- FAIL MODES + FIXES
- STOP / ESCALATE RULES
- ARTIFACT TRACE (what this updates/produces)
- NOTES

---

## PB-01 — CORE_WORKFLOW
- PLAYBOOK_ID: PB-01
- GOAL: <produce primary outputs with baseline quality>
- REQUIRED_INPUTS:
  - <input_1>
  - <input_2>
- OPTIONAL_INPUTS:
  - <input_3>
- OUTPUTS:
  - <primary_output_1>
  - <primary_output_2>

### PRECHECK (READINESS)
- Must have:
  - PACK_UID, TARGET_LEVEL, defined PRIMARY_OUTPUTS
  - Required inputs present (passport)
- If missing → STOP + request inputs.

### STEPS
1) Intake normalize (inputs → canonical form).
2) Identify target outputs + success signals (from skill tree outcomes).
3) Execute workflow steps specific to domain (fill in real pack).
4) Produce draft outputs.
5) Run validation checkpoints in order.
6) Finalize outputs + attach minimal trace.

### CHECKPOINTS (UID-ONLY)
- CP-01: Input readiness
  - VALIDATED_BY: <CHK_UID_READINESS> / <GATE_UID_INPUT>
  - PASS: continue
  - REWORK: request missing inputs / normalize
  - FAIL: stop
- CP-02: Output clarity
  - VALIDATED_BY: <CHK_UID_QUALITY> / <GATE_UID_CLARITY>
- CP-03: Scope compliance
  - VALIDATED_BY: <CHK_UID_COMPLIANCE> / <GATE_UID_SCOPE>

### FAIL MODES + FIXES
- FM: <failure>
  - SYMPTOM: <...>
  - ONE-AXIS FIX: <...>
  - VALIDATE_AFTER: <GATE/CHK UID>

### STOP / ESCALATE
- If request violates EXCLUDES → STOP + route.
- If same gate fails twice after one-axis fixes → ESCALATE.

### ARTIFACT TRACE
- Produces/updates:
  - <artifact_name_or_uid_placeholder>

---

## PB-02 — ONE_AXIS_PATCH_LOOP
- PLAYBOOK_ID: PB-02
- GOAL: <repair output by changing only one axis per iteration>
- REQUIRED_INPUTS:
  - Current output draft
  - Failed gate/check identifiers (UID-only)

### STEPS
1) Identify failed validation (gate/check UID).
2) Select ONE axis to change:
   - axis options: <clarity|structure|density|tone|compliance|consistency|etc>
3) Apply minimal change only on that axis.
4) Re-run the same gate/check.
5) If pass → return to CORE workflow finalization.
6) If fail → pick next axis (max N iterations) or escalate.

### CHECKPOINTS
- CP-01: Axis selection declared
  - EVIDENCE: “AXIS_CHANGED: <axis>”
- CP-02: Re-validate same gate
  - VALIDATED_BY: <FAILED_GATE_UID>

### STOP / ESCALATE
- If N iterations exceeded → ESCALATE with repair note.

---

## PB-03 — DIAGNOSE_AND_REWORK
- PLAYBOOK_ID: PB-03
- GOAL: <diagnose root cause and route to correct fix path>
- INPUTS:
  - Output draft
  - Symptoms list
  - Failed validations list (UID-only)

### STEPS
1) Symptom clustering (group similar fails).
2) Map symptom → likely cause (from skill tree fail modes).
3) Choose fix path:
   - Patch (one-axis)
   - Rebuild section
   - Change constraints (only if allowed)
4) Apply fix.
5) Validate with the most specific gate first, then broad quality gate.

### CHECKPOINTS
- CP-01: Cause hypothesis stated
- CP-02: Fix path selected
- CP-03: Validation passes

---

## PB-04 — QUALITY_POLISH_AND_FINALIZE
- PLAYBOOK_ID: PB-04
- GOAL: <bring output from passable to publish-ready>
- INPUTS:
  - Output that passed core gates

### STEPS
1) Readability/clarity polish pass.
2) Consistency pass (terminology/format).
3) Edge-case scan (if applicable).
4) Final validation set.
5) Produce final + minimal trace.

### CHECKPOINTS
- VALIDATED_BY:
  - <GATE_UID_FINAL_SET> (or list)

---

## PB-05 — ESCALATION_AND_ROUTING (OPTIONAL)
- PLAYBOOK_ID: PB-05
- GOAL: <stop safely + handoff to another entity/pack>

### WHEN TO USE
- Missing required inputs
- Scope violation
- Repeated gate failures
- Contradictory constraints

### OUTPUT (ESCALATION NOTE)
- Include:
  - What was attempted
  - Which gates failed (UID-only)
  - Suggested next owner (SPC/ENG/CTL/VAL) if known

---
END
