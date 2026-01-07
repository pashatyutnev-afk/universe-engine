# INDEX TEMPLATE (CANON)
FILE: 02_STANDARDS/03_TECHNICAL/INDEX_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.TPL.INDEX_TEMPLATE.301
OWNER: SYSTEM
ROLE: Canonical template for creating Index documents (master-indexes, sub-indexes, registries indexes). Defines required sections, existence rule, ordering, and link policy.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Унифицирован INDEX template: purpose, existence, how-to-use, tree map, link policy, lock rule"
- REASON: "Нужен единый формат индексов, чтобы канон был навигируемым"
- IMPACT: "All layers, KB realms, standards registries"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header + required fields | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.STORAGE_MAP.102 | references | placement and entrypoint rules | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first references | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

# INDEX — COPY TEMPLATE (INSTANCE)
> Инструкция: копируй и заполняй.
> Индекс — это навигационный закон. Он определяет существование объектов в своей области.

---

## DOC CONTROL (INSTANCE HEADER)
FILE: <path-to-your-index.md>
SCOPE: Universe Engine
LAYER: <layer-name>
DOC_TYPE: INDEX
INDEX_TYPE: <MASTER|SUB|REGISTRY_INDEX|MAP>
LEVEL: L1
STATUS: <ACTIVE|DEPRECATED>
LOCK: FIXED
VERSION: 1.0.0
UID: <INDEX_UID>
OWNER: <owner/team>
ROLE: Canonical navigation + registry entrypoint for <scope>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для области `<scope>`.

Он фиксирует:
- полный список объектов (файлов/реалмов/шаблонов/протоколов) в зоне действия
- строгий порядок навигации (by folder + number)
- канонические пути (FILE/PATH) и (опционально) raw-ссылки
- правило существования объектов

---

## 1) EXISTENCE RULE (ABSOLUTE)
> Если объекта нет в этом INDEX — он **не существует** для области `<scope>`.  
> Если файл есть, но не зарегистрирован здесь — **ignored / non-canon**.

---

## 2) HOW TO USE (MANDATORY FLOW)
1) Сначала читаешь entrypoint/overview (если есть).
2) Затем выбираешь нужный раздел (SPEC / PROTOCOL / TEMPLATE / TERMS / REALMS).
3) Любой новый объект:
   - сначала добавляется в этот INDEX,
   - потом создаётся файл/папка,
   - потом фиксируется через Canon Protocol / change policy.

---

## 3) ORDER OF AUTHORITY (PRIORITY) (OPTIONAL)
> Если индекс управляет сложной областью — зафиксируй приоритет.

1) `<core law / governance>`
2) `<master-index>`
3) `<registries>`
4) `<content artifacts>`

---

## 4) CANON MAP — TREE
> Здесь дерево объектов. Стиль: папка → список файлов по номеру.
> Используй одинаковый формат везде.

# <SECTION NAME 1> (folder/file)
**Folder:** `<path>/`  
**Rule:** `<one-line rule>`

00 — <Title> — PATH: <path> — RAW: <raw(optional)>
01 — <Title> — PATH: <path> — RAW: <raw(optional)>

---

# <SECTION NAME 2>
**File:** `<path/file.md>`  
UID: <UID optional>  
ROLE: <one line>

---

## 5) LINK POLICY (STANDARD)
- Primary reference: `PATH` (repo path)
- UID-first: если это внутренняя связь, всегда приоритет UID
- RAW links — опционально (reference), но не источник истины

---

## 6) NO-DUPLICATION RULE
- Один смысл → один SoT/объект.
- Дубли запрещены.
- Детализация — через modules/sections, а не через второй “такой же” файл.

---

## FINAL RULE (LOCK)
> Этот INDEX — единственная точка истины о составе и порядке `<scope>`.  
> Любая правка INDEX = изменение канона и проходит Canon Protocol.

--- END OF TEMPLATE
