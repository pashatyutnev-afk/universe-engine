# 02__CASE__BAD — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/02__CASE__BAD.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case (BAD)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: CASE
CASE_TYPE: BAD
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001
OWNER: SPC (Music Producer)
ROLE: Exemplar of failure due to clutter, no layer hierarchy, and scope drift into engineering.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "BAD case initialized."
- REASON: "Provide fail anchor for scope + clarity breaches."
- IMPACT: "Used to detect violations quickly."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASE.BAD.001

---

## CONTEXT
Task asks for hook readability, but producer output piles layers and includes engineering tips.

---

## INPUTS (MIN)
- TASK_GOAL: "Make hook pop."
- PLATFORM_INTENT: "shorts"
- CONSTRAINTS:
  - hook early

---

## OUTPUTS (WHAT WENT WRONG)
- No layer hierarchy (everything is “on”)
- No lead space plan
- No contrast lever definition
- Mentions EQ/levels/limiter (scope violation)
- No routing to mix role

---

## CHECKLIST / GATE OUTCOME
- CHK-READINESS: PASS
- CHK-COMPLIANCE: FAIL (engineering)
- GATES: blocked (cannot proceed)

---

## WHY THIS IS BAD
- violates scope
- increases clutter, kills hook readability
- not testable, no clear transitions

---

## AXIS (FOR REPAIR)
- compliance (first), then arrangement hierarchy

---

## MIN PATCH (ONE AXIS)
Axis=compliance:
- remove all numeric/engineering mentions
- add routing to Mix Engineer
- rerun COMPLIANCE + CONSISTENCY

---

## RERUN SET
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---
END
