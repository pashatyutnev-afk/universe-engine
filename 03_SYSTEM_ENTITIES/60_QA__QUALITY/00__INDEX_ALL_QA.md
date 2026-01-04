# ALL SYSTEM ENTITIES INDEX
00__INDEX_ALL_SYSTEM_ENTITIES.md

SCOPE: Universe Engine
INDEX_TYPE: GLOBAL_ENTITY_REGISTRY
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Canonical entry point for all System Entity classes

---

## PURPOSE

Этот INDEX — единая точка входа для ВСЕХ классов сущностей системы.

Правило:
> Если сущности нет в реестре своего класса — она не существует для системы.

---

## ENTITY CLASSES (ROOT MAP)

### 00_ENG__ENGINES (ENG)
- PURPOSE: Производство смыслов / контента / моделей
- INDEX: `00_ENG__ENGINES/00__INDEX/00__INDEX_ENGINES.md`

### 01_ORC__ORCHESTRATORS (ORC)
- PURPOSE: Маршрутизация и план выполнения (пайплайны)
- INDEX: `01_ORC__ORCHESTRATORS/00__INDEX/00__INDEX_ORCHESTRATORS.md`

### 02_SPC__SPECIALISTS (SPC)
- PURPOSE: Роли-исполнители (профили компетенций)
- INDEX: `02_SPC__SPECIALISTS/00__INDEX/00__INDEX_SPECIALISTS.md`

### 03_CTL__CONTROLLERS (CTL)
- PURPOSE: Управление системой (канон, изменения, решения, риски, версии)
- INDEX: `03_CTL__CONTROLLERS/00__INDEX/00__INDEX_CONTROLLERS.md`

### 04_VAL__VALIDATORS (VAL)
- PURPOSE: Проверка и сигнал (без правок канона)
- INDEX: `04_VAL__VALIDATORS/00__INDEX/00__INDEX_VALIDATORS.md`

### 05_QA__QUALITY (QA)
- PURPOSE: Тест-наборы, регресс, бенчмарки, quality gates
- INDEX: `05_QA__QUALITY/00__INDEX/00__INDEX_QA.md`

---

## FINAL RULE
> Этот документ — мастер-указатель.  
> Истина по сущностям хранится в индексах соответствующих классов.

OWNER: Universe Engine
STATUS: FIXED
