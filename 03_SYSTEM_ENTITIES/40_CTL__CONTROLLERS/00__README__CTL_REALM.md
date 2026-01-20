# CTL REALM — CONTROLLERS (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__README__CTL_REALM.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
DOC_TYPE: README (REALM)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.2
UID: UE.CTL.REALM.README.001
OWNER: SYSTEM
ROLE: Canonical overview for CTL controllers: what CTL is, how to use CTL entities, and what the default entrypoints are.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "README aligned with restored READINESS_CHECK_CTL semantics + kept canonical RAW navigation links."
- REASON: "START finish chain requires READINESS_CHECK_CTL as a real readiness gate; README must describe it correctly."
- IMPACT: "CTL realm onboarding becomes consistent; readiness gate meaning is explicit."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.README.002

---

## 0) WHAT IS CTL (CONTROLLERS)
CTL (Controllers) — сущности политик и принудительных ограничений.
CTL отвечает за:
- правила допуска (readiness) и блокировки (blockers);
- лимиты/пороги/запреты;
- обязательные гейты и порядок прохождения;
- stop-условия, когда выполнение нельзя продолжать.

CTL не заменяет:
- SPC (намерение и решения),
- ORC (пайплайны),
- ENG (методы),
- VAL (проверки соответствия),
- QA (качество/приёмка).
CTL делает так, чтобы все они работали в рамках законов и стандартов.

---

## 1) ABSOLUTE NAVIGATION LAW
- Навигация в CTL только по RAW.
- Состав контроллеров считается существующим только если зарегистрирован в INDEX_ALL.

---

## 2) DEFAULT ENTRYPOINTS (MANDATORY)
### 2.1 READINESS CHECK (DEFAULT)
Файл:
- 01__READINESS_CHECK_CTL.md  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

Назначение:
- обязательный гейт готовности рантайма перед выполнением и выпуском артефактов;
- выдаёт PASS/FAIL строго по разрешённым STOP-условиям;
- проверяет boot-first дисциплину, наличие минимальных inputs и минимальный trace применения KB scope.

### 2.2 CTL GLOBAL REGISTRY (CANON)
Файл:
- 02__INDEX_ALL_CONTROLLERS.md  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md

Назначение:
- единая точка истины о составе CTL-контроллеров;
- навигационная карта по семействам контроллеров.

---

## 3) CTL RULESET (CANON)
Файл:
- 01__RULES__CTL.md  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md

Назначение:
- общие правила написания и применения CTL;
- общие принципы блокировок, порогов и принудительных гейтов.

---

## 4) WHEN TO CREATE A NEW CTL
Создавай новый CTL, если нужно:
- зафиксировать политику/лимит/порог;
- запретить класс ошибок (blocker);
- сделать обязательный гейт (например: “KB trace required”, “no bare output”, “scope boundary”);
- стабилизировать повторяемое качество (в паре с QA/VAL).

Порядок (строго):
1) выбрать шаблон CTL;
2) создать файл контроллера;
3) зарегистрировать в `INDEX_ALL_CONTROLLERS`;
4) при необходимости обновить этот README.

---

## 5) FINAL NOTES (LOCK)
Этот README — вход в слой CTL.
- OWNER: SYSTEM
- LOCK: FIXED
- Любые изменения: только PATCH с CHANGE_NOTE.

---  
END.
