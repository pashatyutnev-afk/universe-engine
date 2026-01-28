# QUALITY (QA) — CREATE FLOW

FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/03__CREATE_FLOW__QA.md
SCOPE: Universe Engine (Games volume) / Quality (QA) / Create workflow
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: WORKFLOW
ENTITY_GROUP: QUALITY (QA)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.QA.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Defines canonical order to create a QA entity or QA check: UID → file → registry entry → ORC gate integration.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + clarified registry-first law + RAW-only interfaces."
- REASON: "Prevent non-registered QA checks from being treated as canon."
- IMPACT: "QA creation becomes deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.QA.CREATE.001

---

## 0) CORE LAW
QA-check или QA entity считается существующим в каноне только после:
1) создан файл по template
2) добавлена запись в QA Global Registry (SoT)

## 1) STEPS (CANON ORDER)
1) Выбери FAMILY (пример: NAT / STY / TXT / AUD / VIS / GEN) если слой использует семейства
2) Назначь UID по UID rules (LAW)
3) Создай файл QA entity (или QA check) по соответствующему template
4) Зарегистрируй в `02__INDEX_ALL_QA.md`
5) Подключи в нужный ORC step как `GATE: QA`
6) (Опционально) добавь примеры эталонов/порогов в доменные QA документы, если стандарт это требует

## 2) STOP CONDITIONS
- UID не назначен → STOP
- QA объект не зарегистрирован → STOP (NON-CANON)
- отсутствуют обязательные секции template → STOP

## 3) INTERFACES (RAW ONLY)
- QA Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md
- QA Entity Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_ENTITY.md
- QA Check Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_CHECK.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
