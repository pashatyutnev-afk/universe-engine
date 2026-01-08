# ENG ENGINES REALM (README) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__README__ENGINES_REALM.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: REALM_README
INDEX_ROLE: ROOT_REALM
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.REALM.001
OWNER: SYSTEM
ROLE: Canonical realm boundaries + navigation rules for the entire ENG layer.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "ENG realm file created: hard boundaries, navigation law, and engine contract enforcement."
- REASON: "Root ENG realm was empty; required for stable stamping across families."
- IMPACT: "ENG layer becomes self-describing and executable as a deterministic documentation system."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.REALM.001

---

## 0) PURPOSE (LAW)
ENG слой описывает **движки** — детерминированные “контрактные модули”, которые:
- CONSUME входные артефакты
- PRODUCE выходные артефакты
- имеют явные границы (boundaries)
- подключаются в пайплайны через зависимости и xref

ENG — это НЕ “просто тексты”. ENG — это **исполняемая спецификация**: по нему можно штамповать документы одинаково, без дрейфа.

---

## 1) SCOPE (BOUNDARY)
ENG слой включает только:
- Семейства движков внутри `03_SYSTEM_ENTITIES/10_ENG__ENGINES/`
- README семейства (realm family)
- Templates (README template + Engine template)
- Engine файлы (NN__..._ENG.md)
- Индексы/реестры, если они в семье governance

ENG слой НЕ включает:
- ORC / SPC / CTL / VAL / QA сущности (у них отдельные реестры)
- Артефакты проекта/саги (это уже выходы движков и лежат в других слоях/папках)

---

## 2) CANON EXISTENCE (ABSOLUTE)
- Если движка/семейства нет в каноническом ENG INDEX — он **не существует**.
- Файл, лежащий в репо, но не зарегистрированный индексом — non-canon / ignored.

---

## 3) NAVIGATION LAW (RAW-ONLY)
Все ссылки внутри индексов/реестров ENG слоя должны быть:
- RAW ONLY (`raw.githubusercontent.com/...`)
- без GitHub UI ссылок
- индекс должен читаться “вне репозитория”.

---

## 4) NAMING + NUMBERING (MANDATORY)
Family folder:
- `NN_<FAMILY_NAME>_ENGINES` (NN = глобальный порядок семейств)

Family README:
- `00__README__<FAMILY_NAME>_ENGINES.md`

Engine file:
- `NN__<ENGINE_NAME>_ENG.md` (NN начинается с 01 внутри семьи)
- номер в имени == номер в списке индекса

---

## 5) STATUS / LOCK (STRICT)
STATUS допускается только один и только из множества:
- DRAFT | ACTIVE | DEPRECATED | ARCHIVED

LOCK допускается только один:
- OPEN | FIXED

Запрещено:
- дублировать второй STATUS/LOCK в конце файла
- держать “полу-канон”: если LOCK: FIXED — это закон/канон.

---

## 6) MINI-CONTRACT (ENGINE LAW)
Каждый Engine файл ОБЯЗАН иметь MINI-CONTRACT:
- CONSUMES (1–7 входных артефактов, конкретно)
- PRODUCES (1–7 выходных артефактов, переиспользуемо)
- DEPENDS_ON (явно или [])
- OUTPUT_TARGET (куда класть результат)

Если MINI-CONTRACT отсутствует или “вода” → движок incomplete (non-canon по смыслу).

---

## 7) TEMPLATES (STAMPING LAW)
Новый движок создаётся только так:
1) выбрать FAMILY
2) копировать ENGINE TEMPLATE именно этой семьи
3) заполнить placeholders строго
4) зарегистрировать raw-link в индексе
5) если canon-impacting → governance pipeline + audit

Шаблоны — “производственная оснастка”. Движки должны совпадать по каркасу.

---

## 8) BOUNDARIES (ANTI-DUPLICATION)
Каждый движок обязан явно указать:
- IN SCOPE
- OUT OF SCOPE (HARD)
- COLLISION RULE (куда маршрутизировать пересечения)

Критические разграничения:
- story-time pacing (Narrative) ≠ screen-time editing rhythm (Production)
- production audio (Production) ≠ deep music (Sound & Music)

---

## 9) GOVERNANCE COMPATIBILITY (PIPELINE)
Любое изменение ENG канона (индекс, порядок, статусы, LOCK, контракты):
- проходит через governance Change Control
- фиксируется через Audit Log (append-only)

---

## 10) QUICK START (FAST)
Хочешь “штамповать”:
- выбирай семью по задаче
- бери template
- заполняй: PURPOSE → NON-GOALS → MINI-CONTRACT → BOUNDARIES → OUTPUT SCHEMAS → PIPELINE → S0
- регистрируй в индексе raw-link
- не прячь зависимости

---

## 11) REFERENCES (RAW ONLY)
- ENG INDEX_ALL_ENGINES (global registry):
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

--- END.
