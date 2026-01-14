# TOPICS REALM — ATOMIC KNOWLEDGE MODULES README (ORIENTATION)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
INDEX_TYPE: REALM_ORIENTATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPICS.README.001
OWNER: SYSTEM
ROLE: Orientation tome for TOPICS realm; defines atomic KB module rules, naming, quality requirements, and how entities consume topics under source-lock without creating a secondary index

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created TOPICS realm README: atomic module rules, naming convention, mandatory structure, and anti-duplication guidance."
- REASON: "TOPICS are the main unit of reusable knowledge; they must be deterministic, auditable, and easy to navigate from the KB master index."
- IMPACT: "All topics become consistent, searchable, and enforceable via KB usage gate."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.README.001

---

## 0) PURPOSE (WHAT TOPICS ARE)
`10_TOPICS/` — это атомарные модули знаний (one topic = one job):
- один метод / правило / техника / определение / процедура
- минимальная применимость: “прочитал → применил” без догадок
- обязательные примеры PASS/FAIL

TOPICS — главный слой, который поднимает качество контента в системе.
PILLARS дают рамку, LIBRARIES дают инструменты контроля, а TOPICS дают “кирпичи” знаний.

---

## 1) OPERATIONAL ENTRYPOINT (ABSOLUTE)
Оперативная навигация и existence для KB работает только через:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

Этот README не является индексом существования и не регистрирует файлы.

---

## 2) TOPIC = ATOMIC (ABSOLUTE)
### 2.1 One topic = one skill
Топик обязан отвечать на один вопрос/задачу.
Если файл начинает отвечать на 3–5 разных вопросов — значит он должен быть разбит.

### 2.2 No duplication (SoT)
Одно знание — один источник истины.
Дубликаты запрещены. Если нужно “повторить” — делаем ссылку (PATH) через RELATED/KB_SOURCES.

---

## 3) NAMING CONVENTION (FOR THIS REALM)
TOPICS в текущей структуре называются так:

`NN__<DOMAIN>__<TOPIC_NAME>.md`

Где:
- `NN` — порядок (01..99)
- `<DOMAIN>` — доменный якорь (см. список ниже)
- `<TOPIC_NAME>` — кратко и по делу (UPPER_SNAKE_CASE)

Примеры:
- `01__NARRATIVE__SCENE_CRAFT.md`
- `02__CHARACTER__MOTIVATION.md`
- `03__VISUAL__LIGHTING.md`

---

## 4) DOMAIN ANCHORS (CANON SET)
Используем один из доменных якорей:
- NARRATIVE
- CHARACTER
- WORLD
- VISUAL
- SOUND_MUSIC
- PRODUCTION
- MARKETING
- RESEARCH
- REFERENCE

Правило:
- Если тема не очевидна — выбираем домен по “главному применению” (где чаще используется).
- Если реально “поперёк” — делаем отдельный REFERENCE topic и связываем REL/XREF.

---

## 5) MANDATORY TOPIC STRUCTURE (MINIMUM)
Каждый TOPIC обязан следовать KB module template:
- PURPOSE
- WHEN TO USE / WHEN NOT TO USE
- PROCEDURE / CHECKLIST / RUBRIC (хотя бы один)
- EXAMPLES: PASS + FAIL (EDGE если применимо)
- RELATED: REL/XREF (PATH only)
- COMPLIANCE: source-lock + memory rules

Если у топика нет процедуры и примеров — он не считается KB topic (FAIL).

---

## 6) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
Запрещено:
- додумывать,
- “улучшать” смысл,
- писать “как обычно делают” без проверяемых критериев.

Разрешено:
- только source-locked применение (по KB источникам),
- Memory-OK только для VERIFIED модулей без искажений смысла.

Если нужного источника нет — STOP (не писать “как-то так”).

---

## 7) HOW ENTITIES CONSUME TOPICS
Любая сущность (SPC/ENG/ORC/CTL/VAL/QA/XREF) использует TOPICS через:
- KB_SOURCES (REQUIRED/OPTIONAL)
- KB_GATES (rubrics/checklists/validators)
- OUTPUT CONTRACT (TPL__)

Топики не “переписываются” внутрь сущностей.
Сущность подключается ссылками и применяет по процедуре.

---

## 8) QUALITY RULES FOR TOPICS (FAST GATES)
TOPIC считается годным, если:
- имеет один фокус (atomic)
- имеет процедуру/чеклист/рубрику
- имеет PASS/FAIL примеры
- имеет PATH-only связи (REL/XREF)
- не конфликтует с другими нормами, либо конфликт разрешён policy/решением
- не содержит фантазии

---

## 9) HOW TO ADD A NEW TOPIC (CONTROLLED FLOW)
1) Создай файл по naming convention: `NN__DOMAIN__TOPIC_NAME.md`
2) Заполни по KB module template (процедура + примеры обязательны)
3) Проставь TAGS: domain_* и type_topic минимум
4) Зарегистрируй файл в KB master-index (иначе “оперативно не существует”)
5) Запиши изменение в KB_CHANGELOG (impact note если затронуты сущности/гейты)

---

## 10) COMMON FAILURE MODES (TOPICS)
- “топик-статья” без процедуры и примеров
- “топик-свалка” из 5 тем
- дублирование существующей темы под другим именем
- размытые формулировки (“обычно/часто/примерно”) без порогов/гейтов
- ссылки без PATH (невозможно воспроизводимо навигировать)

--- END.
