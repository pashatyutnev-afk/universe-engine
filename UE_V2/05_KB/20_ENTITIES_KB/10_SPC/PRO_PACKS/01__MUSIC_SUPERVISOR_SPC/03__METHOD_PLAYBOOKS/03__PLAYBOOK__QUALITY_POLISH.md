# 03__PLAYBOOK__QUALITY_POLISH — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/03__METHOD_PLAYBOOKS/03__PLAYBOOK__QUALITY_POLISH.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Quality Polish
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: PLAYBOOK
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.QUALITY_POLISH.001
OWNER: SPC (Music Supervisor)
ROLE: Post-pass polish + final acceptance prep (clarity/consistency/packaging/trace).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Quality polish playbook initialized for Music Supervisor SPC pack."
- REASON: "Standardize finalization and prevent regressions."
- IMPACT: "Defines PB-03 polish passes + final validation set."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.PB.POLISH.001

---

## PLAYBOOK_ID
- ID: PB-03
- NAME: QUALITY_POLISH

---

## GOAL
Довести результат из состояния “PASS базовых гейтов” до состояния “publish-ready”:
- максимальная ясность,
- стабильная консистентность,
- аккуратная упаковка,
- минимальный trace присутствует.

---

## REQUIRED INPUTS
- TASK_ID: <id or date>
- BASELINE_PASSED_OUTPUTS: <final candidate outputs>
- PASSED_VALIDATIONS (UID-only):
  - <gate/check uid list>

## OPTIONAL INPUTS
- TARGET_PLATFORM: <streaming / youtube / game / etc>
- FORMAT_REQUIREMENTS: <length/metadata/etc>
- CASE_EXEMPLARS: <case ids>

---

## OUTPUTS
- POLISHED_OUTPUTS
- FINAL_VALIDATION_LOG
- FINAL_TRACE (minimum required)

---

## PRECHECK
- Confirm baseline passed:
  - <GATE_UID_CORE_OUTPUT_QUALITY> = PASS
  - <GATE_UID_SCOPE_COMPLIANCE> = PASS (if used in pack)
- If not true → STOP and route to PB-02.

---

## POLISH PASSES (ORDER)

### PASS 1 — Clarity & Readability
- Remove ambiguity.
- Ensure “what to do / what it means” is explicit.
- Keep text self-contained; avoid hidden assumptions.

Checkpoint:
- Re-run CHK-QUALITY (clarity section)
- UID: <CHK_UID_QUALITY>

### PASS 2 — Consistency Pass
- Enforce one meaning per term.
- Align formatting, naming, section order.
- Remove contradictions.

Checkpoint:
- Re-run GATE-CONSISTENCY
- UID: <GATE_UID_CONSISTENCY>

### PASS 3 — Packaging / Delivery Fit
- Ensure outputs match intended format and platform.
- Ensure metadata blocks (if any) are present and consistent.
- Remove anything that increases scope or violates constraints.

Checkpoint:
- Re-run CHK-COMPLIANCE
- UID: <CHK_UID_COMPLIANCE>

### PASS 4 — Edge Scan (Only if applicable)
- If task indicates edge-case risk:
  - test edge handling and robustness
Checkpoint:
- Run EDGE gate
- UID: <GATE_UID_EDGE_CASES>

---

## FINAL ACCEPTANCE SET (MANDATORY)
Run and record:

- <GATE_UID_CORE_OUTPUT_QUALITY>: <PASS|REWORK|FAIL>
- <GATE_UID_CONSISTENCY>: <PASS|REWORK|FAIL>
- <CHK_UID_QUALITY>: <PASS|REWORK|FAIL>
- <CHK_UID_COMPLIANCE>: <PASS|REWORK|FAIL>
- <GATE_UID_EDGE_CASES> (if used): <PASS|REWORK|FAIL>

Decision:
- If any REWORK → PB-02 with snapshot
- If any FAIL → PB-02 + escalation format
- If all PASS → finalize trace

---

## MINIMUM TRACE (MANDATORY)
Produce:

- TASK_ID: <...>
- OUTPUTS_PRODUCED:
  - <...>
- VALIDATIONS_PASSED (UID-only):
  - <...>
- CHANGES_MADE:
  - <bullets>
- FINAL_DECISION: READY
- NEXT_ACTION: NONE

---

## REGRESSION GUARD (LIGHT)
- Do not change more than one axis per micro-pass.
- After each pass, re-run the linked checkpoint.
- If a pass breaks a previously passed gate → revert or route to PB-02.

---
END
