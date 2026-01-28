# TOPIC — KB MASTER INDEX NAVIGATION STANDARD (META / NAV LAW)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/02__META__KB_INDEX_NAVIGATION_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: META_NAV_STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.META.NAV.002
OWNER: SYSTEM
ROLE: Standardize KB navigation: single master index contains ALL RAW links; sub-indexes are non-authoritative maps (guidance only). Enforces PATH label vs RAW mechanism, no-dup entrypoints, and deterministic lookup behavior.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB navigation standard: master index is the only RAW link registry; sub-indexes serve as action maps and orientation docs."
- REASON: "Operational navigation must work from one file; prevents link loss and silent drift."
- IMPACT: "KB becomes executable via one entrypoint; entities can deterministically find any KB module."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.META.002

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_meta
- knowledge_base
- navigation
- index
- raw_only
- existence_rule
- maturity_seed

---

## 1) PURPOSE
Зафиксировать навигацию KB как “one-file operation”:
- **один** мастер-индекс хранит **все RAW** ссылки на все KB документы,
- подпапочные индексы — **не** источники истины, а “карта/ориентиры/правила действий”,
- PATH используется только как метка, RAW — единственный механизм открытия.

---

## 2) DEFINITIONS (STRICT)
### Master Index (SoT)
Единственный файл, который:
- содержит каноническую карту KB
- содержит RAW-ссылки на **каждый** KB документ
- задаёт existence rule

### Sub-index (Map / Guidance)
Индекс подпапки/направления, который:
- объясняет назначение папки
- даёт “как пользоваться” + приоритеты + связи
- **не** является SoT для существования документов
- **может** содержать PATH (метки), но **не должен** быть единственным местом, где есть RAW

### PATH vs RAW
- PATH: человекочитаемая метка
- RAW: механизм открытия и доказательство существования

---

## 3) CORE RULES (ABSOLUTE)
R1 — One Master Index
- В KB есть ровно **один** master-index уровня папки `04_KNOWLEDGE_BASE/` (entrypoint).

R2 — RAW links live ONLY in master index
- Все RAW ссылки на документы KB должны быть собраны в master-index.
- Допускается дублирование RAW в “connector standard” (технические случаи), но это не заменяет master-index.

R3 — Sub-indexes are maps, not registries
- Подпапочные индексы не могут определять существование файлов.
- Если файл есть в подпапке, но его RAW нет в master-index → он считается “оперативно не существующим”.

R4 — No duplicate entrypoints
- Никаких альтернативных “главных индексов” KB.
- Любой дублёр должен быть удалён или превращён в POINTER.

R5 — Deterministic lookup
- Любая навигация начинается с master-index → поиск нужного RAW → открытие.
- Не искать “на глаз” по дереву.

---

## 4) EXISTENCE RULE (ABSOLUTE)
- Документ KB существует операционно **только если** он зарегистрирован в master-index (с RAW).
- Файл в репо без записи в master-index = NON-CANON / ignored for operations.

---

## 5) RECOMMENDED MASTER INDEX STRUCTURE
Master-index должен содержать:
- PURPOSE + rules
- Existence rule
- Canonical entrypoints inside KB (readmes, sub-indexes)
- Полный CANON MAP по темам/разделам
- (опционально) Quick Find: “hot paths” / “most used”

Формат записи:
NN — <Title>
PATH: <path label>
RAW: <raw link>

---

## 6) SUB-INDEX CONTENT STANDARD (WHAT THEY MUST CONTAIN)
Sub-index (внутри темы/папки) должен быть “action-map” и включать:
- PURPOSE / scope папки
- When to use this domain
- Recommended flow: how entities should consult modules
- Priority list: какие модули читать первыми
- Relations: depends_on / complements (PATH only)
- Navigation tips: как находить в master-index

Запрещено:
- объявлять “единственную точку истины” кроме master-index
- хранить RAW ссылки как единственный источник (RAW must be in master-index)

---

## 7) NAVIGATION BEHAVIOR (OPERATIONAL)
Default:
1) Open KB master-index
2) Use search (keyword/UID/TAG)
3) Copy RAW link
4) Open module
5) Apply method
6) Emit KB_SOURCES trace

Memory use:
- если модуль уже был открыт ранее → MEMORY_REUSE: YES (без изменения смысла)
- если не был открыт → нужно открыть по RAW (или создать модуль)

---

## 8) FAILURE MODES (WHAT BREAKS KB)
- RAW ссылки размазаны по подпапкам и отсутствуют в master-index
- несколько “главных” индексов
- подпапочный индекс начинает играть роль реестра существования
- сущности “помнят” не то, что было в модуле, и допридумывают

---

## 9) QA (PASS/FAIL)
PASS IF:
- master-index содержит RAW на каждый файл KB
- подпапочные индексы объясняют навигацию и приоритеты
- нет альтернативных entrypoint файлов

REWORK IF:
- master-index неполный
- подпапочные индексы содержат критичные RAW, которых нет в master-index

FAIL IF:
- есть 2+ master-entrypoints
- existence rule нарушен (файлы не зарегистрированы)

---

## 10) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/01__META__KNOWLEDGE_BASE_USAGE_PROTOCOL.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/99__README__TOPICS_REALM.md

---

## 11) COMPLIANCE
- MASTER_INDEX_SOT: absolute
- RAW_LINKS: must exist in master-index
- SUB_INDEX_ROLE: map/guidance only
- NO_DUP_ENTRYPOINTS: strict
- MEMORY_REUSE: allowed without drift

--- END.
