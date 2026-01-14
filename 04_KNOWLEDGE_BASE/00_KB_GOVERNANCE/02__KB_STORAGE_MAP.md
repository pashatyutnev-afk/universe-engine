# KB STORAGE MAP — WHERE EVERY KB UNIT LIVES (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__KB_STORAGE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: STORAGE_MAP_STANDARD (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.STORAGE_MAP.001
OWNER: SYSTEM
ROLE: Define canonical folder placement for all KB unit types (PILLARS/TOPICS/LIBRARIES/ENTITIES_KB/REL_XREF) without creating a second NAV/EXISTENCE index

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB storage map: deterministic placement rules for all KB unit types; prevents drift and duplication."
- REASON: "KB must be universal quality library; consistent structure is required for scaling."
- IMPACT: "Any KB unit can be placed unambiguously; entities can connect to KB without guessing."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STORAGE.001

---

## 0) PURPOSE (LAW)
Этот документ фиксирует: **где** должны лежать любые KB-единицы.
Это STORAGE MAP, не NAV/EXISTENCE индекс.

NAV/EXISTENCE (что существует) определяется только:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

---

## 1) ABSOLUTE RULES
### 1.1 One-index operational mode (reminder)
- В подпапках KB запрещено создавать второй operational entrypoint.
- Здесь только “куда класть”, без реестра существования.

### 1.2 Single source of truth by type
- Каждый тип KB-единицы имеет **единственный** canonical storage location.
- Дубликаты в других папках запрещены (вместо копии — ссылка через PATH/RAW в KB_SOURCES/RELATED).

### 1.3 Naming rules reference
Имена файлов/папок должны соответствовать KB naming rules:
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_NAMING_RULES.md`

---

## 2) REALM MAP (TOP-LEVEL STORAGE)
Все KB файлы живут только в этих ветках:

- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`  — законы/шаблоны/контроль KB
- `04_KNOWLEDGE_BASE/01_PILLARS/`        — фундаментальные тома знаний
- `04_KNOWLEDGE_BASE/10_TOPICS/`         — атомарные модули знаний
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/`    — коннекторы сущностей + SPC PRO PACK
- `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/` — активы качества (checklists/rubrics/templates/patterns/examples/prompt_lib)
- `04_KNOWLEDGE_BASE/40_RELATION_XREF/`  — карты маршрутов/связей (task→scope, rel/xref maps)

---

## 3) STORAGE RULES BY KB ENTITY TYPE (CANON)
### 3.1 GOVERNANCE (RULES / SPECS / TEMPLATES)
Все управленческие документы KB:
PATH:
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/<NN__...>.md`

Назначение:
- RULES / SPECS / TEMPLATES / DOC CONTROL / CHANGELOG / TAGS / REL / XREF правила

Запрещено:
- хранить доменные знания здесь (для этого PILLARS/TOPICS/LIBRARIES).

---

### 3.2 PILLAR (FOUNDATION TOMES)
PILLAR — фундаментальные тома (широкие области).
PATH:
- `04_KNOWLEDGE_BASE/01_PILLARS/<NN__PILLAR__NAME>.md`

Примеры:
- `01__PILLAR__NARRATIVE_CRAFT.md`
- `05__PILLAR__SOUND_MUSIC.md`

Назначение:
- базовые принципы, “книга домена”, широкие обзоры

---

### 3.3 TOPIC (ATOMIC MODULES)
TOPIC — атомарный модуль знания (одна тема/метод/правило).
PATH:
- `04_KNOWLEDGE_BASE/10_TOPICS/<DOMAIN>/TOPIC__<NAME>.md`

Домены:
- `10_NARRATIVE/`
- `20_CHARACTER/`
- `30_WORLD/`
- `40_VISUAL/`
- `50_SOUND_MUSIC/`
- `60_PRODUCTION/`
- `70_MARKETING/`
- `90_REFERENCE/`

README домена:
- `04_KNOWLEDGE_BASE/10_TOPICS/<DOMAIN>/00__README__TOPICS_<DOMAIN>.md`

Назначение:
- маленькие, прикладные, переиспользуемые модули
- обязательны примеры PASS/FAIL (по KB module template)

---

### 3.4 SHARED LIBRARIES (QUALITY ASSETS)
LIBRARY ITEM — переиспользуемые активы качества.
PATH:
- `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/<LIB_TYPE>/<ITEM_PREFIX>__<NAME>.md`

LIB_TYPE → PREFIX:
- `10_CHECKLISTS/`   → `CL__`
- `20_RUBRICS/`      → `RUBRIC__`
- `30_TEMPLATES/`    → `TPL__`
- `40_PATTERNS/`     → `PATTERN__` и `ANTI__`
- `50_EXAMPLES/`     → `EXAMPLE__`
- `60_PROMPT_LIB/`   → `PROMPT__`

Назначение:
- чеклисты принятия решений
- рубрики качества PASS/FAIL/REWORK
- шаблоны выходов (output contract)
- паттерны/анти-паттерны
- эталоны/примеры
- промпт-активы (если применимо)

---

### 3.5 ENTITIES_KB (CONNECTORS + PRO PACK)
Этот realm хранит **не знания**, а **подключение знаний** сущностями.

#### A) ENTITY-LEVEL RULES & MAPS
PATH:
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/01__ENTITY_KB_RULES.md`
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/02__ENTITY_TO_KB_SCOPE_MAP.md`
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/03__COVERAGE__ENTITY_KB_STATUS.md`
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/04__COVERAGE__SPC_PROFICIENCY_MATRIX.md`

#### B) SPC PRO PACK (mandatory)
PATH:
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__<SPC_NAME>/...`

Минимальный набор файлов SPC PRO PACK фиксируется стандартом:
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/00__README__SPC_PRO_PACK_STANDARD.md`

#### C) CONNECTOR STANDARDS + TEMPLATES (ENG/ORC/CTL/VAL/QA/XREF)
PATH:
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/<CLASS>/00__README__<CLASS>_KB_CONNECTOR_STANDARD.md`
- `04_KNOWLEDGE_BASE/20_ENTITIES_KB/<CLASS>/<CLASS>__TEMPLATE/<files...>.md`

Где `<CLASS>`:
- `20_ENG/`
- `30_ORC/`
- `40_CTL/`
- `50_VAL/`
- `60_QA/`
- `90_XREF/`

---

### 3.6 RELATION_XREF (ROUTES / MAPS)
Карты связей и маршрутов (не knowledge modules):
PATH:
- `04_KNOWLEDGE_BASE/40_RELATION_XREF/<NN__...>.md`

Назначение:
- task → KB scope
- rel graph
- xref maps
- canonical term lists (если нужно)

---

## 4) “WHERE DOES THIS GO?” DECISION TABLE (FAST)
Если ты создаёшь…

- фундаментальный том домена → `01_PILLARS/`
- маленький модуль знания → `10_TOPICS/<DOMAIN>/`
- чеклист/рубрику/шаблон/паттерн/пример → `30_SHARED_LIBRARIES/<TYPE>/`
- правила KB/шаблон/контроль изменений → `00_KB_GOVERNANCE/`
- коннектор сущности или SPC PRO PACK → `20_ENTITIES_KB/`
- карту маршрутов/связей → `40_RELATION_XREF/`

---

## 5) ANTI-DRIFT RULES (WHY STORAGE BREAKS)
Storage считается нарушенным, если:
- TOPIC лежит не в `10_TOPICS/`
- RUBRIC/CL/TPL/PATTERN/EXAMPLE лежит не в `30_SHARED_LIBRARIES/`
- доменные знания попали в `00_KB_GOVERNANCE/`
- сущности начали хранить знания вместо подключения (дубликаты вместо KB_SOURCES)

--- END.
