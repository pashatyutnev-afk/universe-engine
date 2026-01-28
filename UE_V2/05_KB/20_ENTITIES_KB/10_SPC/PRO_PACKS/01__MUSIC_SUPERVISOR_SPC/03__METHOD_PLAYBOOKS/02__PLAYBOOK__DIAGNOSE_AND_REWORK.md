# 02__PLAYBOOK__DIAGNOSE_AND_REWORK — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/03__METHOD_PLAYBOOKS/02__PLAYBOOK__DIAGNOSE_AND_REWORK.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Diagnose & Rework
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: PLAYBOOK
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.DIAG_REWORK.001
OWNER: SPC (Music Supervisor)
ROLE: Root-cause diagnosis + deterministic repair routing (one-axis first), with escalation format.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Diagnose & Rework playbook initialized for Music Supervisor SPC pack."
- REASON: "Standardize failure handling and avoid multi-axis chaos."
- IMPACT: "Defines PB-02 repair router + escalation note contract."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.PB.DIAG.001

---

## PLAYBOOK_ID
- ID: PB-02
- NAME: DIAGNOSE_AND_REWORK

---

## GOAL
При провале чеклистов/гейтов:
1) определить **корневую причину**,
2) выбрать **минимальный путь ремонта**,
3) применить **one-axis** правку,
4) повторно провалидировать,
5) при необходимости — эскалация по стандарту.

---

## REQUIRED INPUTS
- TASK_ID: <id or date>
- CURRENT_OUTPUT: <draft output or summary>
- FAILED_VALIDATIONS (UID-only):
  - CHECKLISTS: <CHK_UID list>
  - GATES: <GATE_UID list>
- SYMPTOMS (observed):
  - <symptom_1>
  - <symptom_2>

## OPTIONAL INPUTS
- PRIOR_PATCH_LOG: <what was already tried>
- CONSTRAINTS: <time/format/platform etc>
- RELATED_CASES: <CASE ids if available>

---

## OUTPUTS
- REPAIR_PLAN (selected path + axis)
- PATCHED_OUTPUT (or diff summary)
- VALIDATION_RERUN_LOG
- ESCALATION_NOTE (only if escalated)

---

## PRECHECK
- Confirm FAILED_VALIDATIONS list is present (at least one UID).
- If none → STOP and request which gate/check failed.

---

## DIAGNOSIS STEPS

### STEP 1 — Collect Failure Snapshot
Create a compact snapshot:

- FAILED_CHECKLISTS: <uids>
- FAILED_GATES: <uids>
- MAIN_SYMPTOMS: <bullets>
- WHAT_CHANGED_LAST: <axis or "none">

Output:
- FAILURE_SNAPSHOT

### STEP 2 — Cluster Symptoms
Group symptoms into one of the buckets:

- B1: CLARITY / READABILITY
- B2: CONSISTENCY / CONTRADICTIONS
- B3: COMPLETENESS / MISSING SECTIONS
- B4: SCOPE / COMPLIANCE / HARD LIMITS
- B5: EDGE CASES / ROBUSTNESS
- B6: INPUT QUALITY / MISSING INPUTS

Output:
- SYMPTOM_CLUSTER: <B#>

### STEP 3 — Hypothesize Root Cause
Write one root cause statement:

- ROOT_CAUSE_HYPOTHESIS: <one sentence>
- CONFIDENCE: <low|med|high>
- EVIDENCE: <what in output proves it>

Output:
- ROOT_CAUSE_CARD

---

## REPAIR ROUTING (SELECT ONE PATH)
> Выбирай самый “малый” путь, который может закрыть провал.

### PATH A — One-Axis Patch (DEFAULT)
Use when:
- Issue is localized and fixable without scope change.

- AXIS: <clarity|structure|density|consistency|compliance|edge>
- ACTION: apply minimal change only on this axis
- VALIDATE_AFTER: re-run the failed gate/check first

### PATH B — Section Rebuild
Use when:
- Core section is broken, patching causes cascading edits.

- TARGET_SECTION: <name>
- REBUILD_RULE: keep constraints constant; rebuild only this section
- VALIDATE_AFTER: failed gate/check + quality checklist

### PATH C — Input Correction
Use when:
- Failure comes from missing/dirty inputs.

- ACTION: request/normalize missing inputs
- VALIDATE_AFTER: CHK-READINESS then rerun core workflow

### PATH D — Routing / Out-of-Scope
Use when:
- Task violates EXCLUDES or hard limits.

- ACTION: stop + produce routing note
- VALIDATE_AFTER: <GATE_UID_SCOPE_COMPLIANCE> (must pass by removing out-of-scope content)

---

## EXECUTE REPAIR

### STEP 4 — Declare Repair Decision (MANDATORY)
- REPAIR_PATH: <A|B|C|D>
- AXIS_CHANGED (if A/B): <one axis>
- TARGET: <which section/output>
- EXPECTED EFFECT: <one sentence>

Output:
- REPAIR_DECISION

### STEP 5 — Apply Fix
- Apply chosen repair with minimal edits.
- Log what changed in 1–5 bullets.

Output:
- PATCH_LOG

### STEP 6 — Re-run Validations (ORDER MATTERS)
1) Re-run the **same failed** validation(s) first:
   - <FAILED_GATE_UID or FAILED_CHK_UID>
2) If pass → run broader checks:
   - CHK-QUALITY
   - GATE-CONSISTENCY
   - (EDGE gate if applicable)

Output:
- VALIDATION_RERUN_LOG (PASS/REWORK/FAIL list)

---

## DECISION RULES
- If PASS → return control to PB-01 (continue) or PB-03 (polish).
- If REWORK:
  - You may try up to N loops with one-axis changes (recommend 2–4).
  - Each loop must change ONE axis and record it.
- If FAIL:
  - Escalate using the standard note below.

---

## ESCALATION NOTE (STANDARD OUTPUT)
> Используется когда: повторные провалы, конфликт ограничений, out-of-scope, невозможность исправить one-axis.

### ESCALATION_NOTE
- TASK_ID: <...>
- SUMMARY: <1–2 lines>
- FAILED_VALIDATIONS (UID-only):
  - <uid>: <fail reason>
- ATTEMPTS:
  - Attempt 1: AXIS <...> → result <...>
  - Attempt 2: AXIS <...> → result <...>
- ROOT_CAUSE_HYPOTHESIS: <...>
- BLOCKER_TYPE:
  - missing_input | scope_violation | hard_limit | contradiction | unknown
- REQUIRED_DECISION:
  - <what user/owner must decide>
- SUGGESTED NEXT OWNER (if known):
  - <SPC/ENG/CTL/VAL/QA> + UID
- SAFE NEXT STEP:
  - <what can be done without violating scope>

---

## SAFETY / STOP RULES
STOP immediately if:
- Hard limit violation is unavoidable
- Out-of-scope is central and cannot be removed
- Missing required inputs prevent any meaningful work

---

## ARTIFACT TRACE (MINIMUM)
Record at end:

- TASK_ID
- FAILURE_SNAPSHOT
- REPAIR_DECISION
- PATCH_LOG
- VALIDATION_RERUN_LOG
- NEXT_ACTION: <PB-01|PB-03|ESCALATED>

---
END
