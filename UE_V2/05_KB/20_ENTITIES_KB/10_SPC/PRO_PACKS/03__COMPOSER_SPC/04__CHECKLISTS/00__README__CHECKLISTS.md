# 00__README__CHECKLISTS — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/04__CHECKLISTS/00__README__CHECKLISTS.md
SCOPE: KB — SPC Pro Pack — Composer — Checklists (README)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.CHK.README.001
OWNER: SPC (Composer)
ROLE: Defines checklist set, order, and routing into gates/playbooks for composer outputs.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Checklists README initialized for Composer SPC pack."
- REASON: "Prevent guessing and catch structural defects early."
- IMPACT: "Defines deterministic checklist order and routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.CHK.README.001

---

## PURPOSE (LAW)
Checklists — быстрый контроль перед гейтами.
Они ловят:
- отсутствие входных данных,
- дырки в композиционном плане (форма/мотив/гармония/мелодия),
- нарушения scope,
до запуска строгих gates.

---

## CHECKLIST SET (THIS PACK)
- CHK-01: READINESS (inputs & scope readiness)
  - FILE: 01__CHK__READINESS.md
  - UID: UE.KB.SPC.PACK.COMPOSER.CHK.READINESS.001
- CHK-02: QUALITY (structure/clarity/testability for composition)
  - FILE: 02__CHK__QUALITY.md
  - UID: UE.KB.SPC.PACK.COMPOSER.CHK.QUALITY.001
- CHK-03: COMPLIANCE (limits & forbidden outputs)
  - FILE: 03__CHK__COMPLIANCE.md
  - UID: UE.KB.SPC.PACK.COMPOSER.CHK.COMPLIANCE.001

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
  - STOP and request missing inputs (no guessing)
- If CHK-QUALITY = REWORK:
  - PB-02 axis typically:
    - clarity / structure / motif / harmony / melody
- If CHK-COMPLIANCE = FAIL:
  - remove forbidden parts + rerun
  - scope breach stays FAIL until removed

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
  - UE.KB.SPC.PACK.COMPOSER.PB.CORE.001
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001
- GATES:
  - UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001

---
END
