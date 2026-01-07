# UID RULES — GLOBAL ID LAW (SoT)
FILE: 01_SYSTEM_LAW/02__UID_RULES.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.LAW.UID.RULES.001
OWNER: SYSTEM
ROLE: Single source of truth for UID format, namespaces, uniqueness, stability, and UID migration rules used across all layers

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Зафиксирован единый UID-формат + пространства имён для INDEX/REGISTRY/TEMPLATE/ENTITY, правило уникальности, стабильности и миграции UID"
- REASON: "UID — базовый якорь ссылок и пайплайнов; без единого формата канон не машиночитаем"
- IMPACT: "Все канонические документы и сущности обязаны иметь валидный UID"

---

## 0) PURPOSE (LAW)
UID — это **канонический системный идентификатор** документа/сущности, используемый для:
- ссылок между документами (REL/XREF)
- existence rule в master-index слоя
- dependency записей
- пайплайнов валидации
- audit/change логов

Если UID невалиден или неуникален → документ/сущность считается **NON-CANON**.

---

## 1) UID FORMAT (STRICT)

### 1.1 General pattern
UID строится из сегментов, разделённых точками:

`UE.<DOMAIN>.<GROUP>.<NAME>.<NNN>`

Где:
- `UE` — фиксированный префикс Universe Engine
- `<DOMAIN>` — класс пространства имён (см. §2)
- `<GROUP>` — подгруппа/категория внутри домена (см. §2)
- `<NAME>` — короткое имя (см. §1.2)
- `<NNN>` — трёхзначный номер `000..999` для уникальности серии

### 1.2 Allowed characters (hard)
- В UID разрешены только: `A-Z`, `0-9`, `_`, `.`
- `<NAME>` и `<GROUP>` должны быть в `UPPER_SNAKE_CASE`
- Запрещено: пробелы, дефисы `-`, кириллица, скобки, спецсимволы

---

## 2) UID NAMESPACE MAP (CANON)

### 2.1 Master Index / Layer Indexes
Формат:
`UE.IDX.<LAYER_ALIAS>.MASTER.<NNN>`

Примеры:
- `UE.IDX.LAW.MASTER.000`
- `UE.IDX.STD.MASTER.000`
- `UE.IDX.ENG.MASTER.000`
- `UE.IDX.KB.MASTER.000`
- `UE.IDX.PRJ.MASTER.000`
- `UE.IDX.AST.MASTER.000`
- `UE.IDX.DB.MASTER.000`

`<LAYER_ALIAS>` — краткий алиас слоя (LAW/STD/ENG/KB/PRJ/AST/DB/MODEL/OUT/LOG).

---

### 2.2 Laws (System Law)
Формат:
`UE.LAW.<TOPIC>.<NAME>.<NNN>`

Примеры:
- `UE.LAW.UID.RULES.001`
- `UE.LAW.NAMING.RULES.001`

---

### 2.3 Standards / Specs (SoT внутри STANDARDS)
Формат:
`UE.STD.<TOPIC>.<GROUP>.<NNN>`

Примеры:
- `UE.STD.DOC_CONTROL.SOT.001`
- `UE.STD.STORAGE_MAP.SOT.001`

Где `<GROUP>` обычно один из:
- `SOT`
- `MODULE`
- `PROTO`
- `TEMPLATE`

---

### 2.4 Registries (реестры типов/сущностей/связей)
Формат:
`UE.REG.<DOMAIN>.<NAME>.<NNN>`

Примеры:
- `UE.REG.ENG.DEPENDENCY.001`
- `UE.REG.DOC.ALL.001`
- `UE.REG.PATH.MAP.001`

---

### 2.5 Templates (шаблоны)
Формат:
`UE.TPL.<CLASS>.<NAME>.<NNN>`

Примеры:
- `UE.TPL.ENG.ENGINE_BASE.001`
- `UE.TPL.ENG.FAMILY_README_BASE.001`
- `UE.TPL.REGISTRY.BASE.001`

`<CLASS>` — целевой класс: `ENG`, `ORC`, `SPC`, `CTL`, `VAL`, `QA`, `KB`, `PRJ`, `AST`, `DOC`.

---

### 2.6 Entities (сущности системы)
Формат:
`UE.<CLASS>.<FAMILY>.<NAME>.<NNN>`

Примеры:
- `UE.ENG.GOVERNANCE.AUDIT_LOG.001`
- `UE.ENG.CORE.CORE_IDENTITY.001`
- `UE.ORC.CORE.PIPELINE_ORCHESTRATOR.001`
- `UE.SPC.NARRATIVE.HEAD_WRITER.001`

Где:
- `<CLASS>` ∈ `ENG|ORC|SPC|CTL|VAL|QA|KB|PRJ|AST`
- `<FAMILY>` — семейство/категория внутри класса (`GOVERNANCE`, `CORE`, `NARRATIVE`, `WORLD`, и т.п.)
- `<NAME>` — имя сущности

---

## 3) UNIQUENESS RULE (GLOBAL HARD)
UID должен быть **глобально уникальным** во всём репозитории.

Если один и тот же UID встречается в двух разных файлах:
- оба файла считаются **NON-CANON**
- исправление обязано пройти через Canon Protocol + запись в audit/release (если затрагивает канон)

---

## 4) STABILITY RULE (HARD)
UID **не меняется** при:
- правках текста
- правках структуры документа
- переименовании файла
- переносе файла между папками

UID меняется **только** когда:
- создаётся **новая сущность/документ**, замещающий старый по смыслу
- выполняется официальная миграция UID (см. §5)

---

## 5) UID MIGRATION RULE (CONTROLLED)
Если требуется смена UID (редко):
1) Новый документ получает новый UID.
2) Старый документ переводится в `STATUS: DEPRECATED` и остаётся доступным.
3) Создаётся XREF запись вида: `OLD_UID -> NEW_UID` (в каноническом реестре XREF).
4) Все индексы/реестры/пайплайны обновляются на новый UID.
5) Старый документ можно перевести в `ARCHIVED` только после стабилизации.

Запрещено “тихо” менять UID внутри файла без миграции.

---

## 6) UID ASSIGNMENT RULE (PRACTICE)
- Для MASTER INDEX / реестров: использовать зарезервированные серии `...MASTER.000`, `...REG....001` и т.д.
- Для сущностей: номер `<NNN>` должен отражать серию/порядок внутри семейства, но **не обязан совпадать** с номером `NN__` в имени файла.
  - (Имя файла отвечает за порядок в папке, UID — за глобальную уникальность.)

---

## FINAL RULE (LOCK)
LOCK: FIXED
--- END.
