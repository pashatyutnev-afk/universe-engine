# 03__CHK__COMPLIANCE — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/04__CHECKLISTS/03__CHK__COMPLIANCE.md
SCOPE: KB — SPC Pro Pack — Music Producer — Checklist (Compliance)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: CHECKLIST
CHECKLIST_TYPE: COMPLIANCE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001
OWNER: SPC (Music Producer)
ROLE: Enforce role boundaries and forbid engineering recipes / legal determinations / prompt takeover.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Compliance checklist initialized for Music Producer SPC pack."
- REASON: "Prevent out-of-scope claims and unsafe guidance."
- IMPACT: "Defines hard-limit violations and routing behavior."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CHK.COMP.001

---

## RESULT RULE
- PASS: no hard-limit violations found
- REWORK: minor scope drift, fixable by removal + routing notes
- FAIL: hard-limit violation present (must remove before proceeding)

---

## HARD-LIMIT VIOLATIONS (FAIL)
If any true → FAIL (stop and remove):
[ ] C1 Engineering recipes presented as instructions/truth:
    - exact EQ/Hz/dB values, compressor ratios, LUFS targets, limiter settings, etc.
[ ] C2 Legal determinations:
    - "это точно можно", "прав не будет", "гарантировано без проблем" и т.п.
[ ] C3 Prompt authoring takeover (if prompt role is separated):
    - final prompt dump instead of producer direction
[ ] C4 Claims of certainty about rights/ownership/clearance
[ ] C5 Advice to bypass platform rules or to mislead attribution

---

## SCOPE DISCIPLINE (REWORK)
If any true → REWORK:
[ ] S1 Producer output includes “mix fix steps” (even without numbers) instead of decision-level notes
[ ] S2 Producer output includes distribution/legal/credits conclusions
[ ] S3 Producer output includes too many non-producer deliverables (scope bloat)
[ ] S4 Missing routing notes where role split exists

---

## REQUIRED COMPLIANCE MARKERS (MUST)
[ ] M1 Explicit “decision-level only” stance is maintained
[ ] M2 Out-of-scope items are routed (mix/prompt/legal) and not executed here
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
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001

---
END
