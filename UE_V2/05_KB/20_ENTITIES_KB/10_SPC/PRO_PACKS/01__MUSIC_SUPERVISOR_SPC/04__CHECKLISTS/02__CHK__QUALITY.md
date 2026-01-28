# 02__CHK__QUALITY — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/04__CHECKLISTS/02__CHK__QUALITY.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Quality Checklist
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: CHECKLIST
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
OWNER: SPC (Music Supervisor)
ROLE: Baseline output quality checklist (clarity/completeness/consistency/structure).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Quality checklist initialized for Music Supervisor SPC pack."
- REASON: "Fast acceptance test before gates."
- IMPACT: "Routes to PB-02 on REWORK/FAIL."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.CHK.QUALITY.001

---

## PURPOSE
Проверить, что черновые OUTPUTS достаточно качественные для приёмки гейтами и дальнейшего полиша.

---

## REQUIRED INPUTS (FOR THIS CHECK)
- DRAFT_OUTPUTS (all PRIMARY_OUTPUTS for task)
- Constraints summary (if any)
- Any prior patch log (optional)

---

## CHECK ITEMS

### Q-01 Clarity (no guessing)
- Reader can understand what was produced and why.
- No ambiguous statements that change decisions.
Result:
- PASS if clear
- REWORK if minor ambiguity fixable with one-axis clarity
- FAIL if output unusable / unclear core meaning

### Q-02 Completeness (required parts present)
- All required sections/fields for the task are present.
- No unresolved placeholders that should be resolved now.
Result:
- PASS / REWORK / FAIL

### Q-03 Structure (easy to scan)
- Headings and order make sense.
- Information grouped logically.
Result:
- PASS / REWORK / FAIL

### Q-04 Consistency (terms + rules stable)
- Same term means the same thing everywhere.
- No internal contradictions.
Result:
- PASS / REWORK / FAIL

### Q-05 Constraint fit (respects constraints)
- Output respects provided constraints (format/length/platform).
Result:
- PASS / REWORK / FAIL

### Q-06 Minimal scope (no extra creep)
- No extra content beyond what is required to satisfy the task.
Result:
- PASS / REWORK / FAIL

---

## RESULT LOGIC
- PASS: Q-01..Q-04 all PASS (critical), others at least REWORK
- REWORK: any REWORK in critical items but none FAIL
- FAIL: any FAIL in Q-01..Q-04

---

## ONE-AXIS REWORK MENU (DEFAULT)
Choose ONE axis only:

- AXIS: clarity
  - ACTION: rewrite core statements, reduce optional text
- AXIS: structure
  - ACTION: reorder sections, add headings, remove duplicates
- AXIS: consistency
  - ACTION: unify terms, remove contradictions
- AXIS: completeness
  - ACTION: fill missing required section only (no other edits)

After fix:
- Re-run this checklist, then run:
  - GATE-CORE-QUALITY (if available)

---

## ROUTING
- If RESULT = REWORK:
  - PB-02 (one-axis repair), then re-run CHK-QUALITY
- If RESULT = FAIL:
  - PB-02 with failure snapshot (root cause hypothesis)

---

## EVIDENCE OUTPUT (MANDATORY)
- CHECKLIST_UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
- RESULT: <PASS|REWORK|FAIL>
- FAILED_ITEMS:
  - <Q-xx list>
- AXIS_CHANGED (if rework): <one axis>
- NEXT_ACTION: <PB-02|PB-03|GATES>

---
END
