# 03__CHK__COMPLIANCE — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/04__CHECKLISTS/03__CHK__COMPLIANCE.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Compliance Checklist
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: CHECKLIST
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001
OWNER: SPC (Music Supervisor)
ROLE: Scope boundary + hard limits compliance checklist (final pre-acceptance).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Compliance checklist initialized for Music Supervisor SPC pack."
- REASON: "Prevent scope creep and hard limit violations."
- IMPACT: "Hard stop on violations."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.CHK.COMPLIANCE.001

---

## PURPOSE
Проверить, что output:
- внутри границ COVERS/EXCLUDES,
- не нарушает hard limits,
- корректно маршрутизируется при out-of-scope,
- готов к финальной приёмке гейтами.

---

## REQUIRED INPUTS (FOR THIS CHECK)
- Candidate outputs (post-quality)
- Pack boundaries:
  - COVERS
  - EXCLUDES
  - HARD LIMITS (from passport)
- Constraints summary (if any)

---

## CHECK ITEMS

### C-01 Scope boundary (covers/excludes)
- No content that belongs to EXCLUDES.
Result:
- PASS if clean
- REWORK if minor scope creep removable
- FAIL if out-of-scope is central

### C-02 Hard limits
- Zero hard limit violations.
Result:
- PASS if none
- REWORK if localized removable violation
- FAIL if central / repeated violation

### C-03 Correct routing when out-of-scope appears
- If a user request includes excluded part, output must include routing note instead of producing forbidden content.
Result:
- PASS if routing is correct
- REWORK if routing note missing
- FAIL if forbidden output provided

### C-04 Constraint fit
- Output respects constraints (format/platform/length) without adding new assumptions.
Result:
- PASS / REWORK / FAIL

### C-05 Trace minimum
- Output includes minimal trace (inputs summary + validations list) OR is ready to attach it.
Result:
- PASS if present
- REWORK if missing but easy to add
- FAIL if cannot be reproduced at all

---

## RESULT LOGIC
- PASS: C-01 and C-02 PASS, others at least REWORK
- REWORK: any REWORK but none FAIL in C-01/C-02
- FAIL: any FAIL in C-01 or C-02

---

## REWORK ACTION MENU
- If C-01 REWORK:
  - Remove out-of-scope block; keep only in-scope deliverables
- If C-02 REWORK:
  - Remove violating lines; replace with safe alternative or routing note
- If C-03 REWORK:
  - Add routing note (PB-02 escalation format)
- If C-05 REWORK:
  - Add minimum trace (PB-03 trace section)

After fix:
- Re-run this checklist, then run gates.

---

## FAIL ACTION (HARD STOP)
- If C-01 FAIL:
  - STOP → PB-02 routing/escalation note
- If C-02 FAIL:
  - STOP → PB-02 escalation note (hard limit)

---

## EVIDENCE OUTPUT (MANDATORY)
- CHECKLIST_UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001
- RESULT: <PASS|REWORK|FAIL>
- FAILED_ITEMS:
  - <C-xx list>
- NEXT_ACTION: <GATES|PB-02|STOP>

---
END
