# 02__GATE__CONSISTENCY — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/05__KB_GATES/02__GATE__CONSISTENCY.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Gate: Consistency
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: GATE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001
OWNER: SPC (Music Supervisor)
ROLE: Acceptance gate for internal consistency (no contradictions; stable terms/rules).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Consistency gate initialized for Music Supervisor SPC pack."
- REASON: "Prevent contradictory guidance and unstable definitions."
- IMPACT: "Blocks acceptance until contradictions removed."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.GATE.CONS.001

---

## GATE_UID
- UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001
- SHORT: GATE-02

---

## NAME
CONSISTENCY_NO_CONTRADICTIONS

---

## TARGET_OUTPUTS
- PRIMARY_OUTPUTS for the task:
  - <output_1>
  - <output_2>

---

## TEST_METHOD
1) Scan outputs for:
   - contradictory rules
   - conflicting constraints
   - term drift (same term used with different meaning)
2) If found, classify severity:
   - local (single line/section)
   - systemic (spreads across outputs)

---

## PASS_CRITERIA
- No contradictions.
- Key terms have one stable meaning.
- Repeated rules are aligned (no “A here, not-A there”).

---

## REWORK_CRITERIA
- Contradictions are localized and removable with one-axis “consistency” patch.
- Term drift can be fixed by standardizing definitions.

---

## FAIL_CRITERIA
- Systemic contradictions where fixing would require scope rewrite.
- Conflicts between required outputs that cannot both be true.
- Repeated reintroduction of contradictions after repair loops.

---

## REWORK_ACTION (PREFERRED)
- PB-02 DIAGNOSE_AND_REWORK
- ONE AXIS: consistency
  - ACTION: unify terms, remove conflicting statement, enforce one meaning per term
After patch:
- Re-run this gate, then re-run CORE_OUTPUT_QUALITY gate (regression guard).

---

## EXEMPLARS (CASE LIBRARY)
- FAIL anchor:
  - CASE-B-001 (to be added)
- BORDERLINE anchor:
  - CASE-BL-001 (to be added)

---

## RELATED_UIDS
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
- PLAYBOOKS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.DIAG_REWORK.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.QUALITY_POLISH.001
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001

---

## EVIDENCE OUTPUT (MANDATORY)
- GATE_UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001
- RESULT: <PASS|REWORK|FAIL>
- CONTRADICTIONS_FOUND:
  - <bullets or "none">
- FIX_APPLIED (if any):
  - AXIS: consistency
  - <bullets>
- NEXT_ACTION: <PB-02|PB-03|READY|STOP>

---
END
