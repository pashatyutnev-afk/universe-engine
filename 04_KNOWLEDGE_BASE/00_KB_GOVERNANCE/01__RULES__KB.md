# KB RULES (CANON)

FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 04_KNOWLEDGE_BASE
REALM: 00_KB_GOVERNANCE
DOC_TYPE: RULES
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULES.001
OWNER: SYSTEM
ROLE: Canon rules for Knowledge Base layer: navigation, structure, provenance, state, and how runtime entities consume KB safely. Enforces Source Lock and prevents non-auditable content use.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt KB rules to align with Source Lock: RAW-only, mandatory provenance markers, module state discipline, and deterministic consumption interface for ORC/CTL/VAL."
- REASON: "Stop uncontrolled ingestion and ensure KB can be used by pipelines without guessing."
- IMPACT: "KB becomes enforceable contract: content is auditable and validator-compatible."
- CHANGE_ID: UE.CHG.2026-01-20.KB.RULES.001

---

## 0) PURPOSE (LAW)
KB — это слой знаний, который:
- хранит проверяемые материалы, правила, таксономии, методики и корпуса,
- даёт системе разрешённые источники и “пакеты компетенций”,
- обеспечивает происхождение (provenance) и границы использования.

KB не “поисковик” и не “память по ощущениям”.
KB — контролируемое хранилище с правилами входа и выхода.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
- Все ссылки в KB и на KB — только RAW.
- Запрещено угадывать пути/файлы.

### 1.2 Source Lock is absolute
- Нельзя использовать non-user content, если он не представлен как KB-tracked source.
- Применяется закон Source Lock:

KB SOURCE LOCK / NO FANTASY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

### 1.3 Provenance is mandatory for external content
- Любой KB источник, из которого берётся non-user content, обязан содержать:
  - KB_SOURCE_RAW
  - SOURCE_STATUS (PD_CONFIRMED | LICENSE_CONFIRMED)
  - SOURCE_NOTE
  - FULL_TEXT_ALLOWED (только если нужен полный текст)

Если маркеры отсутствуют → нарушение границы (marker not confirmed).

### 1.4 Deterministic consumption
- ORC/CTL/VAL/QA должны потреблять KB только через:
  - KB index entrypoints,
  - явные KB scope pointers,
  - явные provenance markers.
Никаких “вроде бы это из…”.

---

## 2) KB ENTRYPOINTS (RAW)
KB MASTER INDEX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

KB REALM README  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

---

## 3) KB SCOPE (KB inputs, outputs, boundaries)
### 3.1 KB Inputs
- KB modules/items/records stored as repo documents.
- User original content can be referenced, but it must be explicitly marked as user original (no provenance required).

### 3.2 KB Outputs
- KB-tracked sources usable by runtime (with provenance markers).
- Topic modules, playbooks, checklists, rubric sets, domain rules.
- Competence packs bound to entities (SPC/ENG/ORC/CTL/VAL/QA) when applicable.

### 3.3 KB Boundaries
- KB does not accept “external truth” without recording.
- Any non-user content must be representable as KB object + provenance markers.
- If the required KB source is missing → task must STOP or create KB object via templates.

---

## 4) KB STRUCTURE RULES (CANON)
KB хранится как набор модулей и библиотечных объектов.

### 4.1 Module (KB_MODULE)
Модуль — атомарный контейнер знаний под одну тему/роль/область.
Использовать шаблон:

TEMPLATE: KB MODULE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/20__TEMPLATE__KB_MODULE.md

### 4.2 Library item (KB_LIBRARY_ITEM)
Элемент библиотеки — атомарный объект (источник, кейс, инструмент, эталон, список).
Использовать шаблон:

TEMPLATE: KB LIBRARY ITEM  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/21__TEMPLATE__KB_LIBRARY_ITEM.md

### 4.3 Atomicity (no mega-docs)
- Один модуль = одна тема.
- Если документ растёт и содержит несколько тем → split.

---

## 5) KB MODULE STATE SYSTEM (REQUIRED)
Каждый KB модуль обязан иметь состояние (state) и фиксированный жизненный цикл.

MODULE STATE SYSTEM  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/14__KB_MODULE_STATE_SYSTEM.md

Правило:
- если модуль не в состоянии ACTIVE/APPROVED (как определено системой состояний) — использовать его в прод-пайплайнах запрещено.

---

## 6) PROVENANCE RULES (STRICT)
### 6.1 Where provenance must appear
Provenance обязателен:
- в KB источниках (source items),
- в любых downstream документах, которые включают non-user content (цитаты/выдержки/корпуса).

### 6.2 Minimal provenance fields (repeat)
- KB_SOURCE_RAW
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE
- FULL_TEXT_ALLOWED (если используется полный текст)

### 6.3 Excerpt rule (default)
Если FULL_TEXT_ALLOWED отсутствует:
- использовать только короткие выдержки
- полный текст запрещён

---

## 7) KB CONSUMPTION INTERFACE (HOW RUNTIME USES KB)
### 7.1 Required “KB scope” pointer
Любой пайплайн, который потребляет KB, обязан иметь явный вход:
- KB_SCOPE_RAW: raw link(s) на модуль(и)/элементы KB

Если KB_SCOPE_RAW не дан → STOP: input absent

### 7.2 No outside lookup in runtime by default
Если нужен внешний материал:
- сначала создать/зарегистрировать KB объект (с provenance)
- только потом использовать

### 7.3 Domain policy hooks (example: music poetry)
Для поэзии/корпуса применяются доменные CTL/VAL:

POET PD POLICY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

PD ONLY (VAL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

---

## 8) INDEXING & NAVIGATION RULES
### 8.1 Canon entrypoint
Единственная точка входа в KB слой — `00__INDEX__KNOWLEDGE_BASE.md` (RAW).
Все новые модули/под-индексы должны быть зарегистрированы там по правилам KB.

### 8.2 No duplicate entrypoints
Запрещено создавать параллельные “главные индексы” KB.

### 8.3 UID / naming
KB документы обязаны соответствовать системным правилам UID/названий (глобальные правила тома).

---

## 9) QA / CONSISTENCY (MINIMUM)
KB модуль считается пригодным для использования только если:
- имеет корректный DOC CONTROL header,
- имеет state (и state разрешён для использования),
- имеет корректные RAW pointers,
- для источников: имеет provenance markers,
- не нарушает Source Lock.

---

## 10) STOP CONDITIONS (KB CONTEXT)
KB блокирует выполнение (через контракты пайплайна), если:
- RAW missing (невозможно открыть KB pointer)
- marker not confirmed (нет provenance/status/state)
- input absent (нет KB scope / нет нужного KB объекта)

---

## 11) CHANGE POLICY (LOCK)
Изменения правил KB:
- только PATCH
- обязательно обновить CHANGE_NOTE
- если меняются provenance/status markers — синхронизировать доменные CTL/VAL и Validation Matrix.

---

END.
