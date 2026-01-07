# UNIVERSE ENGINE — VERSIONING & CHANGE POLICY
FILE: 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

SCOPE: Universe Engine
LAYER: SYSTEM LAW
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Политика версий и изменений. Определяет, как менять VERSION, когда это обязательно, и как различать patch/minor/major (breaking).

---

## 0) PURPOSE
Эта политика:
- предотвращает “тихие” правки без следа
- делает изменения читаемыми и управляемыми
- фиксирует правила совместимости

---

## 1) WHAT IS A CHANGE (DEFINITION)
Изменение (meaningful change) — это любое действие, которое меняет хотя бы одно:
- смысл правила / требования
- структуру формата
- порядок или состав INDEX/реестра
- mini-contract сущности (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- зависимости или связи (REL/XREF)
- обязательные поля / шапки / маркировки

Не считается meaningful change:
- исправление опечаток без изменения смысла
- перенос строк/форматирование без изменения требований

---

## 2) VERSION FORMAT (CANON)
VERSION используется в формате:

MAJOR.MINOR.PATCH

Пример: 1.4.2

Запрещено:
- версии вида “vFinal”
- версии без чисел
- “уникальные” схемы в разных слоях

---

## 3) WHEN TO BUMP VERSION (MANDATORY)
### PATCH bump (x.y.Z)
- правка текста без изменения смысла
- исправление формата/читабельности
- уточнение примеров

### MINOR bump (x.Y.z)
- добавили новые пункты без ломки старого поведения
- добавили новые опции (не обязательные)
- расширили список допустимых значений

### MAJOR bump (X.y.z) = BREAKING
- изменили обязательные требования
- переименовали ключи/поля в форматах
- изменили правила существования/индексации
- изменили порядок, который влияет на работу пайплайна
- удалили или заменили SoT документ

---

## 4) BREAKING CHANGE MARK (MANDATORY)
Если change = MAJOR:
- в документе добавляется строка (в начале раздела про изменения):
  BREAKING: YES
- обязательно описывается MIGRATION:

MIGRATION:
- what breaks
- who is affected (layers/entities)
- how to update old docs

---

## 5) COMPATIBILITY RULES
### 5.1 Backward Compatible
Если MINOR/PATCH:
- старые документы остаются валидными
- новые поля (если добавлены) имеют default/optional режим

### 5.2 Not Compatible
Если MAJOR:
- старые документы могут стать invalid
- обязателен MIGRATION план

---

## 6) CHANGE RECORD (LIGHTWEIGHT)
Для любого meaningful change обязателен короткий блок:

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "что изменили"
- REASON: "зачем"
- IMPACT: "что затронуто"

Это может храниться:
- либо в Audit/Log сущности
- либо в отдельном log файле
(как удобно, но факт должен существовать)

---

## 7) INDEX VERSION RULE
Если меняется INDEX (состав/порядок/реестр):
- VERSION индекс-документа обязателен к обновлению
- это считается минимум MINOR,
- а если ломает порядок/пути — MAJOR.

---

## 8) ENTITY VERSION RULE
Если меняется ENT mini-contract или DEPENDS_ON:
- это минимум MINOR
- а если меняется интерфейс CONSUMES/PRODUCES — MAJOR

---

## 9) FINAL LAW
> Версия — это контракт.  
> Если контракт изменился — версия обязана измениться.

OWNER: Universe Engine  
LOCK: FIXED

---
END.
