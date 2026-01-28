# ENTITIES KB REALM — README (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/00__README__ENTITIES_KB_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.ENTITIES_REALM.001
OWNER: SYSTEM
ROLE: Orientation for Entities KB realm: what entity-specific knowledge connectors are, how entities must use them, and how the realm is structured (SPC/ENG/ORC/CTL/VAL/QA/XREF). Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created Entities KB realm README: purpose, usage order, structure map, and strict boundaries for entity-specific knowledge packs."
- REASON: "Entities need consistent, role-specific competence packs and connectors to the universal KB without mixing domains or inventing rules."
- IMPACT: "More deterministic entity performance, easier QA/certification, less drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.ENT.README.001

---

## 0) PURPOSE (KB)
`20_ENTITIES_KB` — это слой **профессиональной базы знаний для сущностей**.

Он отвечает за:
- что именно должен “знать и уметь” каждый класс сущностей (SPC/ENG/ORC/CTL/VAL/QA/XREF)
- как собирать **пакеты компетенций** (pro packs / connector packs)
- как связывать сущности с универсальными доменными знаниями из `10_TOPICS`
- как проверять готовность (гейты/рубрики/кейсы)

---

## 1) WHAT THIS REALM IS / IS NOT
### IS
- Коннекторы и пакеты компетенций по классам сущностей.
- Стандарты “как упаковать знания для сущности”, чтобы она работала стабильно.

### IS NOT
- НЕ доменные знания (сюжет/визуал/музыка/маркетинг) — они в `10_TOPICS`.
- НЕ общий склад шаблонов/чеклистов — это `30_SHARED_LIBRARIES`.
- НЕ навигационный реестр RAW ссылок.

---

## 2) NAVIGATION RULE (STRICT)
- Единственная точка навигации/существования для всей KB: `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`.
- Этот README — ориентация и правила пользования realm, без RAW-карты.

---

## 3) HOW ENTITIES USE ENTITIES_KB (DETERMINISTIC)
Порядок использования:
1) Governance minimum set (KB rules / XREF / REL / trace).
2) Выбрать класс сущности (SPC/ENG/ORC/CTL/VAL/QA/XREF).
3) Загрузить соответствующий **connector standard** (README/правила коннектора).
4) Использовать шаблон структуры пакета (TEMPLATE folders) для конкретной сущности/профиля.
5) Подтянуть минимально-нужные доменные топики из `10_TOPICS` (не больше, чем надо).
6) Проверить гейтами/рубриками/кейсами (если предусмотрено).
7) Выдать RUN_TRACE (UID-only источники + reuse памяти).

---

## 4) REALM STRUCTURE (WHAT LIVES HERE)
Этот realm организован по классам сущностей:

- `10_SPC/` — Specialists: пакеты “супер-профи” по специализациям, деревья навыков, принципы, плейбуки, кейсы, рубрики.
- `20_ENG/` — Engines: метод/параметры/edge cases/примеры + гейты, чтобы “движки” работали детерминированно.
- `30_ORC/` — Orchestrators: pipeline steps, handoffs, gates placement, failover.
- `40_CTL/` — Controllers: policy, limits/thresholds, примеры.
- `50_VAL/` — Validators: проверочные критерии, валидаторы, матрицы ошибок, примеры.
- `60_QA/` — Quality: QA гейты/рубрики/натуральность/регрессии.
- `90_XREF/` — Crossref: правила связей между сущностями и KB scope, карты соответствий.

В каждом классе:
- есть “connector standard” README (что обязан знать этот класс о KB)
- есть TEMPLATE структура для паков

---

## 5) WHAT A “PRO PACK” MUST CONTAIN (HIGH-LEVEL)
Любой пакет компетенции для сущности должен:
- иметь паспорт (KB_PASSPORT)
- иметь дерево навыков/зон ответственности (SKILL_TREE или аналог)
- иметь принципы/ограничения (GOLDEN_PRINCIPLES / POLICY)
- иметь плейбуки/метод (METHOD / PLAYBOOKS / PIPELINE_STEPS)
- иметь чеклисты/гейты (CHECKLISTS / KB_GATES)
- иметь кейсы/примеры (CASE_LIBRARY / EXAMPLES)
- иметь рубрику оценки (EVALUATION_RUBRIC) где применимо
- иметь источники (KB_SOURCES) если знания основаны на внешних материалах

---

## 6) STRICT BOUNDARIES (ANTI-DRIFT)
Запрещено:
- хранить здесь доменные топики (они в `10_TOPICS`)
- превращать connector README в “второй master index”
- создавать “профессию” без skill tree и без гейтов (пак будет неиспользуем)
- выдавать знания как факт без trace/источников (если знание заимствовано)

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- сущность использует незарегистрированную KB информацию как “знание”
- пак не имеет паспорта и минимальной структуры
- отсутствует минимальный набор проверки (гейты/чеклист/рубрика)
- источники не задокументированы там, где они обязательны

---

## 8) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: KB governance rules apply everywhere
- UE.KB.README.TOPICS.REALM.001 | WHY: topics realm is the domain knowledge source
- UE.KB.STD.GATE_DEF.088 | WHY: measurable gates standard
- UE.KB.STD.QA_RUBRIC.096 | WHY: rubric standard for consistent scoring
- UE.KB.PROC.QA_SCORE_CONSIST.098 | WHY: scoring consistency protocol

--- END.
