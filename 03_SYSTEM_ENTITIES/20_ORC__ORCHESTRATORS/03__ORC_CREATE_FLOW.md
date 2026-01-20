# ORC CREATE FLOW — BOOTSTRAP

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/03__ORC_CREATE_FLOW.md
SCOPE: Universe Engine (Games volume) / Orchestrators (ORC) / Create workflow
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: WORKFLOW
ENTITY_GROUP: ORCHESTRATORS (ORC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.ORC.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Canonical creation order for an ORC entity: UID → file → registry entry → pipeline gate usage.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Expanded stub into full create workflow with stop-conditions, registry-first discipline, and RAW-only interfaces."
- REASON: "Avoid non-registered ORC files and incomplete contracts."
- IMPACT: "ORC creation becomes deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.CREATE.001

---

## 0) CORE LAW
ORC считается существующим в каноне только после двух условий:
1) создан ORC файл по template
2) добавлена запись в ORC Global Registry (SoT)

Если отсутствует пункт (2) → NON-CANON.

## 1) STEPS (CANON ORDER)
1) Определи задачу/семейство:
   - выбери FAMILY папку в `20_ORC__ORCHESTRATORS/` (или создай новую family по правилам слоя)
2) Назначь UID по UID rules
3) Создай ORC файл по template `00__TEMPLATE__ORC_ENTITY.md`
4) Заполни MINI-CONTRACT (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
5) Заполни PIPELINE STEPS (каждый шаг по step schema)
6) Добавь CHECKPOINTS (где обязателен CTL/VAL/QA)
7) Зарегистрируй ORC в `02__INDEX_ALL_ORCHESTRATORS.md`:
   - FAMILY block (если новый)
   - номер в порядке (01..NN)
   - RAW ссылка
8) Интегрируй ORC в пайплайн:
   - ORC должен быть выбран ROUTING шагом в runtime
   - gates должны быть соблюдены (CTL → VAL → QA)
9) (Опционально) Добавь зависимости/совместимость в доменной документации, если требуется

## 2) STOP CONDITIONS (ONLY THESE)
- UID не назначен → STOP (input absent)
- ORC не зарегистрирован в Global Registry → STOP (marker not confirmed)
- отсутствует mini-contract или шаги без обязательных полей → STOP (marker not confirmed)
- RAW ссылки отсутствуют или требуют угадывания → STOP (RAW missing)

## 3) MINIMUM DELIVERABLES OF A NEW ORC
- ORC entity file (complete)
- registry entry (RAW link)
- gate placement documented (CTL/VAL/QA where applicable)

## 4) INTERFACES (RAW ONLY)
- ORC Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md
- ORC Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md
- ORC Entity Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_ENTITY.md
- ORC Step Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_PIPELINE_STEP.md
