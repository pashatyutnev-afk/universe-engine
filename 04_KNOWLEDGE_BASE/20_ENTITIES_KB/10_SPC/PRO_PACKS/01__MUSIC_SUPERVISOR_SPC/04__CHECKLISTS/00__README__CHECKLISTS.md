# 00__README__CHECKLISTS — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/04__CHECKLISTS/00__README__CHECKLISTS.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Checklists
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.README.001
OWNER: SPC (Music Supervisor)
ROLE: Entry point for checklists; defines usage order and PASS/REWORK/FAIL semantics.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Checklists README initialized for Music Supervisor SPC pack."
- REASON: "Deterministic verification flow."
- IMPACT: "Standardized run order: readiness → quality → compliance."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.CHK.README.001

---

## PURPOSE (LAW)
Этот README — точка входа в чеклисты пака Music Supervisor SPC.
Он фиксирует:
- какие чеклисты существуют,
- в каком порядке прогоняются,
- что означает PASS/REWORK/FAIL,
- какие плейбуки вызываются при REWORK/FAIL.

---

## PACK BINDINGS (MUST MATCH PACK PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## CHECKLISTS LIST
- 01__CHK__READINESS.md
  - ID: CHK-01
  - PURPOSE: готовность входов и рамки scope перед запуском

- 02__CHK__QUALITY.md
  - ID: CHK-02
  - PURPOSE: базовое качество результата (ясность/полнота/структура)

- 03__CHK__COMPLIANCE.md
  - ID: CHK-03
  - PURPOSE: границы scope + hard limits + финальная комплаенс-проверка

---

## DEFAULT RUN ORDER
1) CHK-01 READINESS
2) CHK-02 QUALITY
3) CHK-03 COMPLIANCE

---

## RESULT SEMANTICS
- PASS:
  - Можно продолжать по нормальному пайплайну (PB-01 → gates → PB-03).
- REWORK:
  - Требуется исправление. По умолчанию: PB-02 (one-axis repair).
- FAIL:
  - Работа останавливается, требуется диагностика/эскалация:
    - PB-02 DIAGNOSE_AND_REWORK (с escalation note при необходимости)

---

## PLAYBOOK ROUTING
- If CHK-01 is REWORK/FAIL:
  - STOP and request missing inputs (do not proceed)
- If CHK-02 is REWORK:
  - PB-02, prefer one-axis: clarity/structure/density
- If CHK-03 is REWORK:
  - PB-02, prefer one-axis: compliance/scope cleanup
- If any is FAIL:
  - PB-02 + escalation format if not fixable

---

## EVIDENCE FORMAT (MANDATORY)
При прогоне любого чеклиста фиксируй:

- CHECKLIST_UID: <...>
- RESULT: <PASS|REWORK|FAIL>
- NOTES:
  - <1–5 bullets: что не так / что исправить>
- NEXT_ACTION: <PB-01|PB-02|PB-03|STOP>

---
END
