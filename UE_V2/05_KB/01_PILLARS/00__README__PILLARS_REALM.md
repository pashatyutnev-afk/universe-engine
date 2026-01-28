# PILLARS REALM — FOUNDATION TOMES README (ORIENTATION)
FILE: 04_KNOWLEDGE_BASE/01_PILLARS/00__README__PILLARS_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
INDEX_TYPE: REALM_ORIENTATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.PILLARS.README.001
OWNER: SYSTEM
ROLE: Orientation tome for PILLARS realm; defines what pillars are, how they differ from topics/libraries, and how entities must use them under source-lock without creating a secondary index

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created PILLARS realm README: defines foundation tomes usage rules and boundaries."
- REASON: "Pillars are the base knowledge layer; must remain clean and non-duplicative."
- IMPACT: "Entities can reference pillars as foundational SoT while detailed knowledge stays in topics/libraries."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PILLARS.README.001

---

## 0) PURPOSE (WHAT PILLARS ARE)
PILLARS — это фундаментальные “тома” знаний (foundation tomes).
Они дают:
- базовые принципы домена,
- крупные рамки и модели мышления,
- высокоуровневые процедуры,
- словарь и определения уровня “домен”.

PILLARS не предназначены для мелких техник и тонких правил — это TOPICS.

---

## 1) OPERATIONAL ENTRYPOINT (ABSOLUTE)
Оперативная навигация и existence для KB выполняются только через:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

Этот README — том ориентации, не индекс существования.

---

## 2) WHAT MUST LIVE IN PILLARS (IN-SCOPE)
PILLAR должен содержать:
- PURPOSE (зачем этот домен)
- PRINCIPLES (ядро)
- HIGH-LEVEL PROCEDURES (крупные шаги)
- QUALITY FRAME (что такое “хорошо/плохо” на уровне домена)
- COMMON FAILURES (типовые провалы)
- REFERENCES (PATH на TOPICS/LIBRARIES для деталей)

---

## 3) WHAT MUST NOT LIVE IN PILLARS (OUT-OF-SCOPE)
Запрещено хранить в PILLARS:
- атомарные методы и конкретные техники (это TOPICS)
- чеклисты/рубрики/шаблоны (это SHARED LIBRARIES)
- карты задач/маршрутов (это RELATION_XREF)
- KB политики/законы (это KB GOVERNANCE)
- дублирование контента, который уже существует в TOPICS/LIBRARIES

---

## 4) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
PILLARS — часть KB, поэтому:
- никаких домыслов и “логических дополнений”
- только source-locked применение
- при Memory-OK использовать только VERIFIED модули без искажений

При сомнении — переоткрыть источник или остановить run.

---

## 5) HOW ENTITIES USE PILLARS
PILLARS используются сущностями как “база”:
- SPC: базовые рамки профессии + принципы и big-picture
- ENG: базовые определения/модели домена
- ORC: понимание “что строим” и “какие критерии качества”
- CTL/VAL/QA: определения и high-level нормы (детали — в соответствующих модулях)

Правило:
- сущности не копируют PILLAR внутрь себя,
- они ссылаются (KB_SOURCES) и применяют.

---

## 6) QUALITY STANDARD FOR PILLARS
PILLAR считается годным, если:
- даёт ясные принципы и рамки,
- не раздувается в энциклопедию (детали вынесены в TOPICS),
- имеет ссылки на конкретные TOPICS/LIBRARIES для применения,
- не содержит противоречий и фантазии.

---

## 7) QUICK START (AUTHORING A NEW PILLAR)
1) Создай `NN__PILLAR__<DOMAIN>.md`
2) Заполни:
   - принципы (core)
   - high-level процедуры
   - common failures
3) Добавь ссылки на TOPICS/LIBRARIES (PATH) для деталей
4) Зарегистрируй файл в KB master-index (CANON MAP)
5) Логируй изменение в KB_CHANGELOG

--- END.
