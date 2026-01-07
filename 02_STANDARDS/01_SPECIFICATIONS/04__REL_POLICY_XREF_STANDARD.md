# REL POLICY + XREF STANDARD (SoT) (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.REL_XREF.104
OWNER: SYSTEM
ROLE: Source-of-Truth specification for relationship policy and cross-references (XREF/REL). Defines allowed relation types, UID-first linking, and anti-duplication linking rules across the Universe Engine.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован REL/XREF SoT: UID-first, типы связей, формат записи, правила anti-dup, deprecation links"
- REASON: "Устранение хаоса ссылок и конфликтов смысла между документами"
- IMPACT: "All layers, registries, KB governance, standards modules"

---

## 0) PURPOSE (LAW)
Этот документ — SoT-спека о том:
- как документы/сущности связываются друг с другом,
- как оформлять XREF,
- какие типы отношений разрешены,
- как избегать дублей смысла через REL policy,
- как оформлять deprecation и “источник истины”.

---

## 1) AUTHORITY & XREF (UID-first)
Primary authority:
- `01_SYSTEM_LAW/02__UID_RULES.md` (UID primary)
- `01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md` (hard constraints)
- `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md` (XREF section format support)

XREF:
- XREF: UE.LAW.UID.002 | defines | UID as primary identity | 01_SYSTEM_LAW/02__UID_RULES.md
- XREF: UE.REG.CONSTRAINTS.MASTER.006 | enforces | UID-first linking constraint | 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md
- XREF: UE.STD.SPEC.DOC_CONTROL.103 | defines | standard doc structure for XREF blocks | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

---

## 2) DEFINITIONS
- **REL** — отношение между двумя объектами системы (документ/сущность/пайплайн/схема).
- **XREF** — текстовая запись ссылки на другой объект системы.
- **SOURCE** — объект, который содержит XREF.
- **TARGET** — объект, на который указывает XREF.
- **UID-first** — ссылка считается валидной только если содержит UID target.

---

## 3) PRIME RULES (ABSOLUTE)
### 3.1 UID-first (ABSOLUTE)
Любая межслойная/междокументная связь обязана содержать:
- `UID_TARGET`

Путь/URL — опциональны и вторичны.

### 3.2 No hidden duplication
Если документ B переопределяет смысл документа A, это запрещено.
Вместо этого:
- A остаётся SoT,
- B либо module (extends), либо guide (references), либо deprecated-by link.

### 3.3 One primary SoT per meaning
Один смысл имеет один первичный SoT.
Все остальные документы должны связываться через REL types (extends/references/etc.).

---

## 4) CANONICAL XREF RECORD FORMAT
### 4.1 Standard line format
Единый формат строки XREF:

`XREF: <UID_TARGET> | <REL_TYPE> | <WHY> | <PATH_OR_RAW(optional)>`

Где:
- `<UID_TARGET>` — обязательный UID цели
- `<REL_TYPE>` — из разрешённого списка (см. раздел 5)
- `<WHY>` — кратко зачем ссылка (one line)
- `<PATH_OR_RAW>` — опционально (путь в репо или raw-ссылка)

Примеры:
- `XREF: UE.LAW.UID.002 | depends_on | UID format/stability rules | 01_SYSTEM_LAW/02__UID_RULES.md`
- `XREF: UE.STD.SPEC.DOC_CONTROL.103 | references | header compliance rules | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`
- `XREF: UE.STD.SPEC.UID_MARKING.101 | extends | module details for marking | 02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md`

### 4.2 Where XREF lives
Рекомендуемое место:
- отдельный раздел `## XREF (UID-first)` рядом с верхней частью документа
- либо `## References` если документ не нормативный, но тогда формат строки всё равно сохраняется

---

## 5) REL TYPES (CONTROLLED ENUM)
Разрешённые типы отношений:

### 5.1 Authority / logic
- `defines` — SOURCE определяет TARGET как сущность/понятие (редко используется в XREF, чаще наоборот)
- `governs` — TARGET управляет SOURCE (законы/правила)
- `depends_on` — SOURCE зависит от TARGET
- `implements` — SOURCE реализует контракт TARGET (пайплайн/протокол)
- `extends` — SOURCE расширяет TARGET (module → SoT)

### 5.2 Reference / info
- `references` — SOURCE ссылается как на справку
- `maps_to` — SOURCE показывает соответствие/маппинг (например local id -> uid)

### 5.3 Canon lifecycle
- `deprecated_by` — SOURCE устарел из-за TARGET (TARGET заменяет SOURCE)
- `replaced_by` — синоним deprecated_by (использовать deprecated_by предпочтительно)
- `supersedes` — SOURCE заменяет TARGET (использовать осторожно, только при MAJOR)

### 5.4 Integrity / duplication control
- `single_sot` — TARGET является единственным SoT по смыслу, SOURCE обязан подчиняться (используется как метка)
- `non_canon_alias_of` — SOURCE является alias pointer на TARGET (legacy файлы)

NOTE:
Если нужен новый REL_TYPE — это изменение SoT (MINOR/MAJOR) и проходит Canon Protocol.

---

## 6) ANTI-DUPLICATION LINKING POLICY
### 6.1 Если документ “про то же самое”
Если ты видишь два документа про один смысл:
- выбирается один SoT (primary)
- второй:
  - либо становится module (extends)
  - либо guide/reference (references)
  - либо deprecated (deprecated_by)

### 6.2 Modules must extend
Каждый module обязан иметь XREF:
- `XREF: <SoT_UID> | extends | ... | <SoT_PATH>`

### 6.3 No circular authority
Запрещено делать так, чтобы:
- SoT “depends_on” module (модуль не должен быть выше SoT)
- law documents “govern” core law (обратная власть)

---

## 7) DEPRECATION LINK STANDARD (REQUIRED)
Если `STATUS: DEPRECATED`:
- в header: `DEPRECATED_BY: <UID_TARGET>`
- в XREF: строка:
  - `XREF: <UID_TARGET> | deprecated_by | migration target | <path>`

---

## 8) VALIDATION (COMPLIANCE)
XREF считается валидным, если:
- содержит UID_TARGET
- REL_TYPE в разрешённом enum
- WHY не пустой
- (если указан PATH) путь выглядит как repo path и не противоречит master-index

Невалидно:
- ссылка без UID
- REL_TYPE не из списка
- XREF “на файл, которого нет в каноне” (если это не явный external reference)

---

## 9) MIGRATION NOTES (CURRENT REPO)
S0:
- В модулях `06_MARKING_STANDARDS/*` добавить XREF extends на соответствующие SoT спеки.
- В legacy alias pointers использовать REL_TYPE: `non_canon_alias_of`.

S1:
- Для KB governance добавить XREF связи между индексом, storage map и create flow.

---

## FINAL RULE (LOCK)
REL/XREF — SoT по связям системы.
Любая правка enum типов или базовых правил UID-first = MAJOR по умолчанию.
--- END.
