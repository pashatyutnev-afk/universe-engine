# TOPIC — KNOWLEDGE BASE USAGE PROTOCOL (META / OPERATIONAL LAW)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/01__META__KNOWLEDGE_BASE_USAGE_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: META_PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.META.USAGE.001
OWNER: SYSTEM
ROLE: Operational protocol for using Knowledge Base deterministically: RAW-only usage, memory reuse constraints, no-fantasy rule, citation/trace requirements, and KB_SOURCES formatting; defines hard FAIL conditions

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB usage protocol: RAW-only retrieval, controlled memory reuse, no invention, and mandatory KB_SOURCES trace."
- REASON: "KB is the quality backbone; without a protocol assistants drift into improvisation and inconsistency."
- IMPACT: "All entities use KB the same way; outputs become auditable, repeatable, and canon-safe."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.META.001

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_meta
- knowledge_base
- protocol
- raw_only
- no_fantasy
- traceability
- maturity_seed

---

## 1) PURPOSE
Сделать работу с KB детерминированной:
- знания берутся строго из KB (или из памяти только если уже открывалось и смысл не изменён),
- запрещена фантазия/добавление “от себя”,
- всегда есть трассировка: какие KB-модули применены и зачем.

---

## 2) CORE PRINCIPLES (ABSOLUTE)
P1 — KB is Source of Truth (SoT) for methods
P2 — RAW-only or trusted memory reuse
P3 — No invention / no drift
P4 — Every output must show KB_SOURCES trace
P5 — If KB is missing for a required method → stop or create KB module first

---

## 3) DEFINITIONS (STRICT)
### KB Module
Один документ в KB (TOPIC / CONNECTOR / MAP / POLICY), который описывает метод/правило/шаблон.

### RAW-only usage
Использовать содержимое KB только если:
- файл был открыт по RAW (в run), или
- он уже был открыт раньше и используется из памяти без искажений (см. §4).

### Trusted memory reuse
Разрешено применить знание из памяти только если:
- оно уже было извлечено ранее из KB,
- смысл не меняется,
- нет “новых деталей” придуманных сверху.

---

## 4) MEMORY RULE (STRICT)
Allowed:
- повторить правило/шаги/шаблон из ранее открытого KB
- адаптировать параметры под задачу (без изменения метода)

Forbidden:
- допридумывать новые правила, которых не было в KB
- “улучшать” метод без KB-основания
- смешивать несколько методов без указания источников

Memory marker:
- если используешь память, явно отмечай: MEMORY_REUSE: YES

---

## 5) NO-FANTASY RULE (ABSOLUTE)
- Запрещено добавлять “психологические”, “маркетинговые”, “музыкальные” советы,
  если они не закреплены в KB модуле/источнике.
- Если нет KB модуля — создаём модуль или делаем HARD STOP.

---

## 6) REQUIRED TRACE: KB_SOURCES (MANDATORY)
Каждый серьёзный deliverable (план/шаблон/док/процедура) должен содержать блок:

KB_SOURCES:
- PATH: <kb file 1> — used for <what>
- PATH: <kb file 2> — used for <what>
MEMORY_REUSE: YES/NO

Rule:
- Использовать PATH как метку.
- RAW ссылки живут в master-index KB, а не размазываются по контенту (если таков стандарт слоя).

---

## 7) USAGE FLOW (DEFAULT)
Step 1 — Identify task class
- marketing / narrative / sound / production / meta

Step 2 — Find required KB modules
- минимум 1 “основной” topic + (если нужно) policy/connector/map

Step 3 — Apply method
- следовать шагам KB, не изобретать

Step 4 — Emit trace
- KB_SOURCES + MEMORY_REUSE

Step 5 — QA gate
- проверить fail conditions (§9)

---

## 8) KB GAP HANDLING (WHAT IF MODULE MISSING)
If required method is missing in KB:
- Option A: Create missing KB module first (preferred)
- Option B: HARD STOP (if user wants strict mode only)

Never:
- “просто сделать как умею” без KB.

---

## 9) HARD FAIL CONDITIONS
FAIL IF any:
- отсутствует KB_SOURCES trace
- добавлены правила/советы без KB основания
- memory reuse с изменением смысла
- KB module required but ignored
- попытка “фантазии” вместо ссылочного знания

---

## 10) QUICK CHECKLIST (OPERATIONAL)
[ ] KB modules selected
[ ] Methods followed exactly
[ ] No invention
[ ] KB_SOURCES present
[ ] MEMORY_REUSE marked correctly
[ ] Fail conditions checked

---

## 11) RELATED (PATH ONLY)
REL:
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/00__README__ENTITIES_KB.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (RAW-only or trusted memory reuse)
- NO_FANTASY: absolute
- TRACE: mandatory (KB_SOURCES)
- KB_GAP: create module or hard stop

--- END.
