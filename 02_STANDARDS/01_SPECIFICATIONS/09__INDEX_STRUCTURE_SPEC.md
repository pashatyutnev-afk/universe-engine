# INDEX STRUCTURE SPEC (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.STD.SPEC.INDEX_STRUCTURE.001
OWNER: SYSTEM
ROLE: Defines what an index is, what is SoT for existence/navigation, and how to avoid index proliferation

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "Added STRICT SINGLE-INDEX model. Clarified 'registry/readme' vs 'index'. Banned sub-indexes in strict layers."
- REASON: "Совместить стандарты с режимом KB: один индекс — единственный SoT."
- IMPACT: "Индексы больше не размножаются как паразиты."

---

## 0) PURPOSE
Дать строгие определения:
- что такое INDEX (SoT для NAV/EXISTENCE)
- что такое REGISTRY/CATALOG (справочник, не SoT)
- что такое README (локальное описание, не SoT)
и как запрещать sub-indexes.

---

## 1) DEFINITIONS

### 1.1 MASTER INDEX (SoT)
INDEX документ, который:
- является единственным SoT для NAV/EXISTENCE в своём слое/области
- содержит CANON MAP (список файлов) и правила существования

### 1.2 REGISTRY / CATALOG (NOT SoT)
Документ-справочник/словарь, который:
- не вводит файлы в канон
- не определяет NAV/EXISTENCE
- может перечислять типы/теги/таблицы/категории
Рекомендуемое имя: REGISTRY / CATALOG, НЕ INDEX.

### 1.3 README (NOT SoT)
Локальное описание папки/подсистемы:
- предназначено для людей
- не вводит файлы в канон
Рекомендуемое имя: README.

---

## 2) MODELS

### 2.1 DEFAULT MODEL (MULTI-FOLDER ALLOWED)
Слой может иметь:
- 1 master-index слоя
- локальные README в подпапках
- registry/словари
НО только master-index определяет NAV/EXISTENCE.

### 2.2 STRICT SINGLE-INDEX MODEL (NO SUB-INDEX) — RECOMMENDED FOR KB
Правила:
1) В слое ровно один master-index (единственный SoT).
2) Sub-indexes запрещены:
   - любые `*/00__INDEX__*.md`
   - любые `*/INDEX*.md` как попытка создать второй entrypoint
3) В подпапках допускаются только:
   - README (локальное объяснение)
   - REGISTRY/CATALOG (словари)
4) Любые “старые индексы” должны быть:
   - удалены, или
   - превращены в POINTER (DEPRECATED) на master-index.

---

## 3) NAMING POLICY (RECOMMENDED)
- NAV/EXISTENCE index: `00__INDEX__<LAYER>.md` или `00__MASTER_INDEX__<NAME>.md` (один)
- справочники: `__REGISTRY__`, `__CATALOG__`
- README: `00__README__*.md`

--- END.
