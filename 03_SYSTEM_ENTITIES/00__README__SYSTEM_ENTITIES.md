# SYSTEM ENTITIES REALM
00__README__SYSTEM_ENTITIES.md

SCOPE: Universe Engine
LAYER: SYSTEM_ENTITIES
LEVEL: L0
STATUS: ACTIVE
ROLE: Root realm for all system entities (ENG/ORC/SPC/CTL/VAL/QA + registries/templates/xref)

---

## PURPOSE

Этот слой хранит **сущности системы** и их реестры:
- ENG: движки (правила/логика)
- ORC: оркестраторы (сборка движков в пайплайны)
- SPC: специалисты (исполнители/роли)
- CTL: контроллеры (управление/гавернанс)
- VAL: валидаторы (проверки)
- QA: качество (тесты/чеклисты/метрики)
- REG: реестры (глобальные индексы/списки)
- TPL: шаблоны (унифицированные формы)
- XREF: сквозные карты связей

---

## RULE

> Если сущность или документ не зарегистрированы в индексах —  
> они не существуют для системы.

---

NAVIGATION: `00__INDEX__SYSTEM_ENTITIES.md`

OWNER: Universe Engine
STATUS: FIXED
