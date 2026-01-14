# KB RULES — UNIVERSAL KNOWLEDGE BASE LAW (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULE
INDEX_TYPE: KB_GOVERNANCE_RULESET
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.RULES.001
OWNER: SYSTEM
ROLE: Define KB as universal library used by all entities; enforce one-index operation, existence rule, source-lock/no-fantasy, and mandatory usage gate

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB rules: one-index operational mode, existence registry, source-lock/no-fantasy, memory policy, usage gate, and minimal module standards."
- REASON: "KB must control content quality and prevent drift/invention."
- IMPACT: "All KB usage becomes deterministic; unregistered files ignored; fantasy banned."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULES.001

---

## 0) PURPOSE (LAW)
Knowledge Base (KB) — универсальная библиотека знаний, стандартов и процедур.
KB служит контрольной плоскостью качества: любая сущность обязана использовать KB.

Эти RULES определяют:
- как KB устроена,
- как осуществляется навигация и существование (existence),
- как запрещается фантазия (source-lock),
- как применяется память (memory policy),
- как работает обязательный KB Usage Gate.

---

## 1) OPERATIONAL ENTRYPOINT (ABSOLUTE)
Единственный operational entrypoint KB:
`04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

Запрещено:
- использовать другие индексы как entrypoint,
- строить “вторую систему навигации” внутри подпапок.

Разрешено в подпапках:
- README (orientation tome),
- taxonomy/catalog (справочник, не SoT),
- templates (шаблоны),
но NAV/EXISTENCE всегда решает только master-index.

---

## 2) EXISTENCE RULE (ABSOLUTE)
- Если KB файла нет в CANON MAP master-index — он не существует оперативно для KB.
- Если файл есть в репо, но не зарегистрирован — NON-CANON / ignored.
- NAV работает только по RAW ссылкам (PATH — человекочитаемая метка).

---

## 3) NO-FANTASY / SOURCE-LOCK (ABSOLUTE)
### 3.1 No invention
Запрещено:
- додумывать “как должно быть”,
- добавлять детали, которых нет в источнике,
- “улучшать” смысл правил/процедур.

### 3.2 Allowed knowledge sources
Любое утверждение/правило/процедура для сущностей допускается только:
A) из открытого KB модуля по RAW/PATH (source-locked), или
B) из памяти (Memory-OK), если модуль уже открывали ранее и воспроизводим без искажений смысла.

### 3.3 Hard stop
Run обязан остановиться (HARD FAIL), если:
- нужный модуль не открыт и нет Memory-OK уверенности,
- обнаружена попытка “додумать” вместо чтения,
- RAW недоступен/битый.

---

## 4) MEMORY POLICY (UNIVERSAL)
### 4.1 Memory-OK (allowed)
Разрешено использовать из памяти только если:
- модуль ранее открывался,
- смысл воспроизводится без изменений,
- модуль считается VERIFIED (по KB module state system),
- при сомнении — переоткрыть модуль.

### 4.2 Memory-NO (forbidden)
Запрещено:
- расширять смысл,
- менять формулировки так, что меняется смысл,
- смешивать источники в “единое правило” без фиксации,
- выдавать предположения как данные.

---

## 5) KB USAGE GATE (ABSOLUTE)
KB Usage Gate — обязательное условие PASS результата.

Результат FAIL, если:
- не указаны KB_SOURCES (какие KB модули использованы),
- не указаны KB_GATES (какие проверки/рубрики применены),
- результат противоречит KB политике/рубрикам/правилам.

---

## 6) KB ENTITY TYPES (HIGH LEVEL)
KB состоит из типов единиц:
- PILLAR: фундаментальные тома знаний (широкие области)
- TOPIC: атомарные модули (одна тема/метод/правило)
- LIBRARY ITEM: переиспользуемые активы (checklist/rubric/template/pattern/example/prompt)
- ENTITY KB: коннекторы и пакеты использования KB сущностями (включая SPC PRO PACK)
- REL/XREF MAP: карты связей и маршрутов

Конкретный перечень и определения фиксируются в `KB_ENTITY_TYPES` и master-index.

---

## 7) MINIMUM STANDARD FOR ANY KB MODULE (MANDATORY)
Любой KB модуль (topic/library/policy/rubric/checklist/example) должен иметь:
- PURPOSE (что это и зачем)
- WHEN TO USE / WHEN NOT TO USE
- PROCEDURE / CHECKLIST (или rubric/формат)
- EXAMPLES (минимум PASS/FAIL; EDGE если применимо)
- RELATED (REL/XREF по PATH)

Если модуль не применим — он не является KB.

---

## 8) ENTITIES CONNECT TO KB (MANDATORY)
Любая сущность (SPC/ENG/ORC/CTL/VAL/QA/XREF) обязана подключаться к KB через:
- KB_SOURCES (REQUIRED/OPTIONAL, PATH/RAW)
- KB_GATES (обязательные проверки/рубрики/валидаторы)
- OUTPUT CONTRACT (какой шаблон результата)
- STOP CONDITIONS (когда стоп)

Сущности не должны переписывать знания внутрь себя. Они используют KB как SoT.

---

## 9) CHANGE CONTROL (REQUIRED)
Изменения KB должны быть управляемыми:
- версия документа (SemVer)
- changelog записи (KB_CHANGELOG)
- impact note: какие сущности/пайплайны задеты

---

## 10) FAILURE MODES (STRICT)
Система KB считается сломанной (FAIL), если:
- появились файлы не зарегистрированные в master-index,
- сущности делают результат без KB_SOURCES/KB_GATES,
- используется “фантазия” вместо source-lock,
- отсутствуют примеры и проверяемость в модулях,
- нарушен one-index operational mode.

--- END.
