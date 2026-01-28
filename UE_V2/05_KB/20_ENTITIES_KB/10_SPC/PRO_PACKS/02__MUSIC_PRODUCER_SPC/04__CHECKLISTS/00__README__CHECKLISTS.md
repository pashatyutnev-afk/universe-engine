# 00__README__CHECKLISTS — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/04__CHECKLISTS/00__README__CHECKLISTS.md
SCOPE: KB — SPC Pro Pack — Music Producer — Checklists (README)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.README.001
OWNER: SPC (Music Producer)
ROLE: Defines checklist set, order, and how checklist results route into gates/playbooks.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Checklists README initialized for Music Producer SPC pack."
- REASON: "Make pre-gate validation deterministic."
- IMPACT: "Defines checklist order and pass/rework rules."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CHK.README.001

---

## PURPOSE (LAW)
Checklists — это быстрый контроль перед гейтами.
Они ловят:
- отсутствие входных данных,
- дырки в структуре,
- нарушения scope,
до того как мы идём в более строгие gates.

---

## CHECKLIST SET (THIS PACK)
- CHK-01: READINESS (inputs & scope readiness)
  - FILE: 01__CHK__READINESS.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
- CHK-02: QUALITY (structure/clarity/testability)
  - FILE: 02__CHK__QUALITY.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
- CHK-03: COMPLIANCE (limits & forbidden outputs)
  - FILE: 03__CHK__COMPLIANCE.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001

---

## REQUIRED ORDER
Always run:
1) CHK-READINESS
2) CHK-QUALITY
3) CHK-COMPLIANCE

Then proceed to gates.

---

## RESULT CODES
- PASS: checklist satisfied
- REWORK: fix required via PB-02 (one-axis)
- FAIL: hard stop (usually compliance hard-limit)

---

## ROUTING RULES
- If CHK-READINESS = REWORK:
  - STOP and request missing inputs (do not invent)
- If CHK-QUALITY = REWORK:
  - PB-02 axis = clarity or structure or completeness
- If CHK-COMPLIANCE = FAIL:
  - remove forbidden parts + rerun
  - if legal/engineering claims present → treat as FAIL until removed

---

## TRACE REQUIREMENT
Any run must record:
- CHECKLISTS_RUN:
  - <UID>: <PASS|REWORK|FAIL>
  - <UID>: <PASS|REWORK|FAIL>
  - <UID>: <PASS|REWORK|FAIL>
- NEXT_ACTION:
  - proceed to gates / rework / stop

---

## REQUIRED UID REFERENCES
- PLAYBOOKS:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.CORE.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---
END
