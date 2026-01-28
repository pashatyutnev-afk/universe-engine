# TOPIC — LAUNCH CAMPAIGN & RELEASE WINDOW (MARKETING / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/05__MARKETING__LAUNCH_CAMPAIGN_RELEASE_WINDOW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MKT.LAUNCH_WINDOW.001
OWNER: SYSTEM
ROLE: Atomic method to run launches as a structured release window (pre/launch/post): content queue, channel schedule, CTAs, KPI thresholds, and post-mortem; includes Release Window Plan template and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created launch/release window module: pre-launch warmup, launch day actions, post-launch amplification, KPI gates, and post-mortem."
- REASON: "Single posts underperform; a release window multiplies exposure and improves conversion with repeatable steps."
- IMPACT: "Entities can execute consistent launches, learn from metrics, and scale publishing operations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MKT.005

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_marketing
- type_topic
- launch
- release_window
- campaign
- kpi
- maturity_seed

---

## 1) PURPOSE
Сделать запуск не “одним постом”, а окном:
- PRE: подогрев
- LAUNCH: день релиза
- POST: усиление и конверсия
с измеримыми гейтами.

---

## 2) WHEN TO USE
- Выход трека/альбома/клипа.
- Хочешь максимальный эффект без рекламы.
- Нужно стандартизировать релизы.

## 3) WHEN NOT TO USE
- Внутренний тестовый релиз (но можно облегчённую версию).

---

## 4) DEFINITIONS (STRICT)
### Release window
Период 7–14 дней (минимум 3–5) вокруг релиза.

### Amplification
Вторая волна контента: клипы, реакции, цитаты, варианты.

### KPI gates
Пороги: продолжать/переделать упаковку/сменить клип.

---

## 5) RELEASE WINDOW PHASES (DEFAULT)
### Phase A — PRE (D-7 to D-1)
Цель: подготовить внимание и ожидание.
Контент:
- тизер 10–15с (UGC moment)
- пост “цитата из хука”
- опрос A/B (вариант строки/тега)
- бэкстейдж (1 факт)

### Phase B — LAUNCH (D0)
Цель: максимальный первый импульс.
Действия:
- full релиз (YouTube/full)
- 1–2 shorts в тот же день
- закреплённый комментарий + CTA
- community пост: “что сильнее — куплет 1 или 2?”

### Phase C — POST (D+1 to D+7)
Цель: добить охват и перевести в подписку/каталог.
Контент:
- 3–7 shorts (разные моменты)
- lyric quote cards (1 строка)
- “loop clip” 15/30
- “версия/альт-микс” (если есть)

---

## 6) CONTENT QUEUE (REQUIRED ITEMS)
Минимальный набор на 7 дней:
- 1 full релиз
- 5 shorts (минимум)
- 2 community posts
- 1 “behind-the-scenes” заметка

Rule:
- shorts должны быть разные по моментам (не один и тот же кусок).

---

## 7) KPI GATES (SIMPLE)
### Shorts KPIs
- hold 3s: PASS/REWORK
- comments per 1k views: PASS/REWORK

### Full KPIs
- CTR (если доступно): PASS/REWORK
- avg view duration: PASS/REWORK
- subs gained: PASS/REWORK

Decision rules:
- If shorts hold low → менять старт (tag/момент) и заголовок
- If full CTR low → менять title packaging + thumbnail
- If comments low → усилить CTA (вопрос/вызов)

---

## 8) PROCEDURE (RUN A RELEASE WINDOW)
### Step 1 — Choose window length
- 7 дней (default) или 14 (альбом)

### Step 2 — Define assets ready
- full
- shorts variants (V15/V30/V60)
- packaging (titles/desc/tags)
- credits/rights

### Step 3 — Build schedule by channel
- день/время/формат/CTA

### Step 4 — Execute and log
- фиксировать метрики daily (5 минут)

### Step 5 — Mid-window adjustments (D+2/D+3)
- сменить момент/хук/упаковку, если KPI REWORK

### Step 6 — Post-mortem (D+7)
- что сработало (момент, фраза, CTA)
- что не сработало
- какие дельты в следующий запуск

---

## 9) RELEASE WINDOW PLAN (TEMPLATE)
RELEASE WINDOW PLAN:
- Release:
- Window dates:
- Channels used:
- Assets:
  - Full:
  - Shorts (V15/V30/V60):
  - Packaging:
  - Credits/Rights:
- Schedule (7–14 items):
  - Day:
    - Item:
    - Type:
    - Channel:
    - CTA:
    - KPI to watch:
- KPI thresholds:
- Mid-window review notes:
- Post-mortem notes:
- Result: PASS/REWORK

---

## 10) QA (PASS/FAIL)
PASS IF:
- есть PRE/LAUNCH/POST
- есть queue минимумом (full + 5 shorts + 2 posts)
- упаковка и кредиты готовы
- KPI выбраны и есть правило реагирования

REWORK IF:
- план есть, но нет mid-window корректировок или KPI

FAIL IF:
- релиз “одним постом” и без контента окна

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/04__MARKETING__DISTRIBUTION_CHANNEL_STRATEGY.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/03__MARKETING__CONTENT_PACKAGING_TITLES_HOOKS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/09__SOUND_MUSIC__UGC_SHORTS_VARIANTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (launch must be executed as a window with KPI gates and post-mortem)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
