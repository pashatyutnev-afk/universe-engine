# KB GOVERNANCE — REALM README (ORIENTATION TOME)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
INDEX_TYPE: REALM_ORIENTATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.GOV.README.001
OWNER: SYSTEM
ROLE: Orientation tome for KB Governance realm; explains how KB rules/tables/templates work without creating a second operational entrypoint

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB Governance realm README as orientation tome aligned with ONE-INDEX KB master model."
- REASON: "Provide human/assistant guidance without introducing a second index-entrypoint."
- IMPACT: "Governance docs become easier to apply; operational NAV remains single-source in KB master index."
- CHANGE_ID: UE.CHG.2026-01-14.KB.GOV.README.001

---

## 0) PURPOSE (WHAT THIS REALM IS)
`00_KB_GOVERNANCE/` — это управляющий контур KB.
Здесь лежат:
- правила качества KB
- правила навигации и существования (existence)
- запрет фантазии (source-lock)
- правила памяти (memory policy)
- стандарты связей (REL/XREF)
- шаблоны модулей и коннекторов (templates)
- контроль изменений (doc control, changelog)

Этот документ — "том ориентации" (как пользоваться governance), а не operational index.

---

## 1) OPERATIONAL ENTRYPOINT (ABSOLUTE)
Единственный operational entrypoint для KB NAV/EXISTENCE:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

Правило:
- Если файл KB не зарегистрирован в master-index — он не существует оперативно.
- Этот README не должен заменять master-index и не должен становиться вторым entrypoint.

---

## 2) WHAT TO DO HERE (MAP OF ACTIONS)
В Governance realm выполняются только эти типы работ:
1) Фиксация законов KB (quality, usage gate, source-lock, memory).
2) Определение типов KB-единиц и правил именования.
3) Описание storage map (куда что кладём).
4) Определение REL/XREF правил (как связывать модули).
5) Док-контроль KB (изменения, версии, журнал).
6) Поддержка шаблонов (templates) для:
   - KB modules (topics/policies/rubrics/checklists/examples)
   - shared library items
   - entity KB connectors
   - SPC PRO PACK

Запрещено:
- писать доменный контент (это TOPICS / PILLARS / LIBRARIES),
- создавать под-индексы как “вторую навигацию”.

---

## 3) GOVERNANCE FILES (WHAT EXISTS IN THIS REALM)
Набор файлов этого realm фиксируется и навигируется через KB master-index.
Внутри realm обычно используются:

- RULES: базовые правила KB (что такое KB и как ей пользоваться)
- STORAGE MAP: где что лежит
- ENTITY TYPES: типы KB-единиц
- NAMING RULES: формат имён модулей/файлов
- TAGS: единые теги KB
- REL TYPES: типы связей
- XREF RULES: правила перекрёстных карт
- DOC CONTROL: правила версий/изменений/статусов для KB
- CHANGELOG: журнал изменений KB
- QUALITY LAWS: “как держим качество”
- USAGE GATE: “без KB — FAIL”
- SOURCE-LOCK: “никакой фантазии”
- MEMORY POLICY: что можно/нельзя помнить
- MODULE STATE SYSTEM: UNREAD/READ_ONCE/VERIFIED/DEPRECATED
- TEMPLATES: шаблоны модулей и коннекторов

---

## 4) STRICT NO-FANTASY REMINDER (ABSOLUTE)
KB — библиотека фактов/процедур/стандартов.
Запрещено:
- выдумывать,
- расширять смысл,
- “улучшать” правила без источника.

Использование допускается только:
- из открытого KB источника (source-locked), или
- Memory-OK (ранее открыто и воспроизведено без искажений).

При сомнении — переоткрыть модуль. Иначе STOP.

---

## 5) HOW THIS REALM IS USED BY ENTITIES
Сущности не “хранят знания” внутри себя.
Сущности подключаются к KB через коннектор:
- KB_SOURCES (REQUIRED/OPTIONAL)
- KB_GATES (обязательные проверки)
- OUTPUT CONTRACT (шаблон результата)
- STOP CONDITIONS

Governance realm даёт:
- правила как оформлять эти коннекторы
- шаблоны для коннекторов
- законы качества и гейты, которые сущности обязаны применять

---

## 6) COMMON FAILURE MODES (WHY KB BREAKS)
KB ломается, если:
- появляются файлы не зарегистрированные в master-index (drift)
- появляются “вторые индексы” в подпапках (второй entrypoint)
- источники не открываются, а данные додумываются (fantasy)
- нет usage gate (сущности игнорируют KB)
- нет doc control (версии/изменения неуправляемы)

---

## 7) QUICK START (WHAT TO READ FIRST)
Если KB новая и пустая:
1) KB master-index (правила NAV/EXISTENCE)
2) KB RULES
3) KB SOURCE-LOCK / NO FANTASY
4) KB USAGE GATE
5) KB QUALITY LAWS
6) KB MODULE TEMPLATE + ENTITY CONNECTOR TEMPLATE
7) STORAGE MAP + NAMING RULES + REL/XREF

--- END.
