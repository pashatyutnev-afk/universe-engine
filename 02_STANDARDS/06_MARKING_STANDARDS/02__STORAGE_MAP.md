# STORAGE MAP (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.STORAGE_MAP.602
OWNER: SYSTEM
ROLE: Marking module that details how documents declare their storage placement (layer/folder/realm), how to mark entrypoints, and how to create legacy alias pointers. Extends Storage Map SoT.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль Storage Map: поля маркировки размещения, правила entrypoint/realm, alias pointers, запрет альтернативных канонических путей"
- REASON: "Нужно чётко понимать 'где живёт документ' и как чинить legacy файлы"
- IMPACT: "All layers and indices, KB governance, migration/alias handling"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.STORAGE_MAP.102 | extends | this module details placement marking | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header fields | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first referencing | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.MOD.MARKING.ID.601 | references | UID vs path vs local id clarity | 02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md

---

## 0) PURPOSE
Этот модуль задаёт практические правила маркировки размещения:
- как в документе явно указывать layer/folder/realm
- как помечать entrypoint индексы
- как маркировать “alias pointer” файлы (legacy)
- как писать storage-map метки без дублей

---

## 1) PLACEMENT MARKERS (STANDARD FIELDS)
Эти поля используются для ясного указания “где живёт объект”.

### 1.1 Required markers (already in Doc Control)
- `FILE` — канонический путь документа
- `LAYER` — слой системы

### 1.2 Optional placement markers (allowed)
- `FOLDER: <path>` — если документ является контейнером подпапки/реалма
- `REALM: <name>` — если документ относится к KB realm или доменной зоне
- `ENTRYPOINT: true|false` — если документ является точкой входа (обычно index)

NOTE:
Эти поля не обязательны для всех документов, но рекомендуются для индексов/реестров/realm-artefacts.

---

## 2) ENTRYPOINT MARKING RULES
### 2.1 Entrypoint definition
Entrypoint — главный index области (layer or realm).

### 2.2 Marking
Для entrypoint документов рекомендуется:
- `DOC_TYPE: INDEX`
- `INDEX_TYPE: MASTER`
- `ENTRYPOINT: true`

### 2.3 Anti-dup rule
В одной области (слой/realm) допускается только один entrypoint MASTER.
Любая попытка создать второй = INVALID.

---

## 3) REALM MARKING RULES (KB + Domains)
Если документ относится к realm:
- указывай `REALM: <RealmName>`
- указывай `FOLDER: <realm folder>` если realm папочный
- если realm “файлом” (например `02_CHARACTER_CRAFT.md`), то `FILE` уже достаточно, но REALM всё равно полезен.

---

## 4) STORAGE DECLARATION BLOCK (OPTIONAL SECTION)
Для сложных документов допускается секция:

`## STORAGE (DECLARATION)`
- HOME_PATH: `<path>`
- SCOPE_AREA: `<layer/realm>`
- ENTRYPOINT_REF: `<UID or path>`

Это НЕ заменяет header, а дополняет.

---

## 5) LEGACY ALIAS POINTERS (NON-CANON) (CRITICAL)
### 5.1 What is alias pointer
Alias pointer — файл, оставленный для обратной совместимости (старые ссылки/имена).

Он не содержит нормативного контента.

### 5.2 Required fields for alias pointer
Alias pointer должен иметь:
- `STATUS: DEPRECATED` (или ARCHIVED, если совсем старое)
- `LOCK: FIXED` (если канонично как указатель) или OPEN (если временно)
- `CANON_TARGET: <path-to-canon-doc>`
- `CANON_TARGET_UID: <UID>`
- XREF: `non_canon_alias_of` или `deprecated_by` (по ситуации)

### 5.3 Minimal alias pointer body
Тело файла (минимум):
- одна строка “THIS FILE IS A LEGACY ALIAS POINTER”
- куда переехать (path + uid)
- причина (optional)

Пример:
- `CANON_TARGET: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- `CANON_TARGET_UID: UE.KB.IDX.MASTER.001`

---

## 6) PATH VS RAW LINK POLICY
- PATH (repo path) — первичный указатель местоположения
- RAW link — опциональная reference ссылка
- если RAW ломается — чинится ссылка, канон не меняется

---

## 7) COLLISION HANDLING GUIDANCE
Если в папке обнаружена коллизия имен/номеров:
- выбираем один канонический файл
- остальные → alias pointers (non-canon)
- индекс обновляется так, чтобы канон был один

---

## 8) MIGRATION NOTES
S0:
- там где есть альтернативные `00_*` или `INDEX_*`, перевести их в alias pointers
- в канонических индексах добавить PATH + UID (если известно) и единый формат

---

## FINAL RULE (LOCK)
Этот модуль расширяет Storage Map SoT и задаёт правила маркировки размещения.
Любая правка, меняющая entrypoint/alias контракт = MAJOR по умолчанию.
--- END.
