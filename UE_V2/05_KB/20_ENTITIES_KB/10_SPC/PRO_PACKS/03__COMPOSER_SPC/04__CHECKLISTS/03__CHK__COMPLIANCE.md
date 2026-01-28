# 03__CHK__COMPLIANCE — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/04__CHECKLISTS/03__CHK__COMPLIANCE.md
SCOPE: KB — SPC Pro Pack — Composer — Checklist (Compliance)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: CHECKLIST
CHECKLIST_TYPE: COMPLIANCE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.CHK.COMPLIANCE.001
OWNER: SPC (Composer)
ROLE: Enforce composer scope boundaries and forbid engineering recipes / legal determinations / prompt takeover.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Compliance checklist initialized for Composer SPC pack."
- REASON: "Prevent out-of-scope claims and unsafe guidance."
- IMPACT: "Defines hard-limit violations and routing behavior."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.CHK.COMP.001

---

## RESULT RULE
- PASS: no hard-limit violations found
- REWORK: minor scope drift, fixable by removal + routing notes
- FAIL: hard-limit violation present (must remove before proceeding)

---

## HARD-LIMIT VIOLATIONS (FAIL)
If any true → FAIL (stop and remove):
[ ] C1 Engineering recipes / numeric mix-master guidance:
    - EQ Hz/dB, compressor ratio, LUFS, limiter settings, etc.
[ ] C2 Legal determinations / certainty claims:
    - "точно можно", "без прав проблем не будет" и т.п.
[ ] C3 Prompt authoring takeover (if prompt role is separated):
    - final prompt dump instead of composition decisions
[ ] C4 Advice to bypass platform rules or mislead attribution
[ ] C5 Claims of certainty about rights/ownership/clearance

---

## SCOPE DISCIPLINE (REWORK)
If any true → REWORK:
[ ] S1 Composer output includes “mix fix steps” (even without numbers)
[ ] S2 Composer output includes distribution/legal/credits conclusions
[ ] S3 Composer output bloats scope (too many non-composer deliverables)
[ ] S4 Missing routing notes where role split exists

---

## REQUIRED COMPLIANCE MARKERS (MUST)
[ ] M1 Composer stays decision-level:
    - motif/harmony/melody/form intent (not engineering)
[ ] M2 Out-of-scope items are routed (prompt/mix/legal) and not executed here
[ ] M3 Variants keep one lever rule (no chaotic rewrite)
[ ] M4 No contradictions introduced by compliance edits

---

## OUTPUT OF THIS CHECKLIST
Record:
- COMPLIANCE_STATUS: <PASS|REWORK|FAIL>
- VIOLATIONS:
  - <C# list>
- SCOPE_DRIFT:
  - <S# list>
- FIX_ACTION:
  - remove forbidden parts
  - add routing note
  - rerun this checklist
- NEXT_ACTION:
  - if PASS: proceed to gates
  - if REWORK: PB-02 axis=compliance
  - if FAIL: STOP until removed

---

## REQUIRED UID REFERENCES
- PRINCIPLES:
  - UE.KB.SPC.PACK.COMPOSER.PRINCIPLES.001
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001

---
END
