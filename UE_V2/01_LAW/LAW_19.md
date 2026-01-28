# LAW_19

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW
UID: UE.V2.LAW.19.ROUTE_VIA_XREF_REG_KB.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Выбор маршрута и сущностей только через REG+XREF+KB_SCOPE. "По памяти" запрещено.

---

## [M] INTENT
Убрать хаос при сотнях сущностей: система выбирает совместимых и нужных участников детерминированно.

---

## [M] RULES
1) ORC обязан выбирать участников через:
   - REG_ENTITY_CATALOG (существование, роль, cap, io, stage)
   - XREF карты (pipeline, validation, compat, coverage)
   - KB_SCOPE bindings (границы и разрешённые темы)
2) Прямое "возьми релевантных" без REG/XREF запрещено.
3) Сущность без записи в REG не может участвовать в цепочке.
4) Сущность без KB_SCOPE_ID не может участвовать в цепочке (кроме bootstrap-ядра).
5) Если нужной сущности/карты нет — GAP (создать/добавить запись).
6) Участие обязано быть экономным (см. LAW_20).

---

## [M] GATES
PASS если:
- в TRACE_TOKEN есть ссылки на REG/XREF/KB_SCOPE для выбранных участников
REWORK если:
- участники выбраны без обоснования совместимости
STOP если:
- отсутствуют XREF/REG ядро при запуске
