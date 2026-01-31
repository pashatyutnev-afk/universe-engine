# ENG ENGINES — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__README__ENGINES_REALM.md
SCOPE: Universe Engine (Games volume) / System Entities / ENGINES (ENG)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
ENTITY_GROUP: ENGINES (ENG)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.REALM.001
OWNER: SYSTEM
ROLE: Canonical realm boundaries + navigation laws + contract enforcement for the entire ENG layer (RAW-only).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "DOC CONTROL normalization: structured header, hardened boundaries, explicit KB scope + RAW interfaces. No semantic change."
- REASON: "Make realm file readable/auditable and consistent with boot-first runtime."
- IMPACT: "ENG realm becomes stable for routing, stamping, and gate checks."
- CHANGE_ID: UE.CHG.2026-01-20.ENG.REALM.002

---

## 0) PURPOSE (LAW)
ENG слой описывает движки — детерминированные контрактные модули, которые:
- CONSUME входные артефакты
- PRODUCE выходные артефакты
- имеют явные границы (boundaries)
- подключаются в пайплайны через зависимости и карты (XREF)

ENG — это не “просто тексты”. Это исполняемая спецификация, по которой можно штамповать документы одинаково, без дрейфа.

---

## 1) SCOPE (BOUNDARY)
ENG слой включает только:
- семейства движков внутри `03_SYSTEM_ENTITIES/10_ENG__ENGINES/`
- README семейства (family realm)
- шаблоны (engine template + family templates, если есть)
- engine файлы `NN__..._ENG.md`
- индексы/реестры, если они принадлежат ENG слою

ENG слой НЕ включает:
- ORC / SPC / CTL / VAL / QA сущности (у них отдельные слои/реестры)
- артефакты проекта/саги (это выходы движков и лежат в других слоях)

---

## 2) CANON EXISTENCE (ABSOLUTE)
- Если движка/семейства/шаблона нет в каноническом ENG INDEX — он не существует.
- Файл, лежащий в репо, но не зарегистрированный индексом — NON-CANON / ignored.

---

## 3) NAVIGATION LAW (RAW-ONLY)
Все ссылки внутри индексов/реестров/README ENG слоя должны быть:
- RAW ONLY (`raw.githubusercontent.com/...`)
- без GitHub UI ссылок
- индекс должен читаться “вне репозитория”

---

## 4) NAMING + NUMBERING (MANDATORY)
Family folder:
- `NN__..._ENGINES` (NN = глобальный порядок семейств)

Family README:
- `00__README__..._ENGINES.md`

Engine file:
- `NN__..._ENG.md` (NN начинается с 01 внутри семьи)
- номер в имени == номер в списке индекса внутри семьи

---

## 5) STATUS / LOCK (STRICT)
STATUS допускается только один и только из:
- DRAFT | ACTIVE | DEPRECATED | ARCHIVED

LOCK допускается только один:
- OPEN | FIXED

Запрещено:
- дублировать второй STATUS/LOCK в конце файла
- держать “полу-канон”: если LOCK: FIXED — это закон/канон

---

## 6) MINI-CONTRACT (ENGINE LAW)
Каждый Engine файл обязан иметь MINI-CONTRACT:
- CONSUMES (1–7 входных артефактов, конкретно)
- PRODUCES (1–7 выходных артефактов, переиспользуемо)
- DEPENDS_ON (явно или [])
- OUTPUT_TARGET (куда кладётся результат)

Если MINI-CONTRACT отсутствует или расплывчатый → INCOMPLETE (не рабочий движок).

---

## 7) TEMPLATES (STAMPING LAW)
Новый движок создаётся только так:
1) выбрать FAMILY
2) использовать template (семейный или общий TPL)
3) заполнить placeholders строго
4) зарегистрировать RAW link в индексе
5) если canon-impacting → governance pipeline + audit

---

## 8) BOUNDARIES (ANTI-DUPLICATION)
Каждый движок обязан явно указать:
- IN SCOPE
- OUT OF SCOPE (HARD)
- COLLISION RULE (куда маршрутизировать пересечения)

---

## 9) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- законы/стандарты, влияющие на структуру и контроль (Naming, UID, Doc Control, Index Structure)
- доменные стандарты, если движок доменный

KB OUTPUTS:
- none (ENG не хранит знания как KB модуль)

BOUNDARIES:
- ENG формирует метод/контракт и схему результата, но не является хранилищем контента

---

## 10) INTERFACES (RAW ONLY)
- ENG GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md
- ENG RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md
- ENGINE TEMPLATE (global TPL):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/10__TPL__ENGINE.md

--- END.
