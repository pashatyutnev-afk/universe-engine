# TOPIC — DISTRIBUTION & CHANNEL STRATEGY (MARKETING / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/04__MARKETING__DISTRIBUTION_CHANNEL_STRATEGY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MKT.DISTRIBUTION.001
OWNER: SYSTEM
ROLE: Atomic method to choose and run a distribution strategy across channels: channel roles, content formats, cadence, CTAs, and metrics; includes Channel Plan template and pass/fail QA gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created distribution/channel strategy module: role of each channel, format mapping, cadence, CTAs, and KPI checks."
- REASON: "Posting the same thing everywhere is inefficient; channels must have roles and content adapted to behavior."
- IMPACT: "Entities can publish consistently, grow discovery, and convert viewers into listeners/followers with less drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MKT.004

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_marketing
- type_topic
- distribution
- channels
- cadence
- kpi
- maturity_seed

---

## 1) PURPOSE
Сделать каналы осмысленными:
- у каждого канала есть роль,
- контент подстраивается под поведение аудитории,
- есть частота и план,
- есть CTA и метрики.

---

## 2) WHEN TO USE
- Есть треки/шорты, но нет роста.
- Посты одинаковые везде.
- Нужно понять: где shorts, где full, где комьюнити.
- Нужно запланировать релиз-окно на 7–30 дней.

## 3) WHEN NOT TO USE
- Разовая публикация без продолжения.

---

## 4) DEFINITIONS (STRICT)
### Channel role
Зачем канал существует в системе:
- discovery / retention / community / conversion / archive.

### Cadence
Частота публикаций (в неделю) и ритм.

### KPI
Показатели успеха, минимально достаточные.

---

## 5) CHANNEL ROLES (DEFAULT MAP)
- C1: Shorts/TikTok/Reels — DISCOVERY (вход, охват)
- C2: YouTube (full) — CONVERSION (в полные треки, подписки)
- C3: Community (посты/опросы) — RETENTION (удержание)
- C4: Streaming/catalog — ARCHIVE+CONVERSION (глубина)
- C5: Messenger/Discord/Telegram (если есть) — COMMUNITY (ядро)

Правило:
- один канал может иметь 2 роли, но одна — главная.

---

## 6) FORMAT MAPPING (WHAT TO POST WHERE)
### Shorts/TikTok/Reels
- 15/30/60 variants, loop-safe
- 1 сильный момент + 1 CTA
- текст на экране (опционально)

### YouTube full
- official audio / lyric video / visualizer
- описание полное + credits/rights
- закреплённый комментарий (CTA)

### Community posts
- цитата из текста (1 строка)
- “выбери вариант” (A/B)
- behind-the-scenes (prompt delta, voice profiles — коротко)

---

## 7) CADENCE (STARTER PLAN)
Минимальный устойчивый план на 2 недели:
- Shorts: 3–7 / week
- YouTube full: 1 / week (или 1 релиз + 1 бэкстейдж)
- Community: 2–3 / week

Правило:
- лучше стабильность, чем “залить 20 и пропасть”.

---

## 8) CTA LIBRARY (BY ROLE)
Discovery (shorts):
- “Сохрани, если поймал хук”
- “Какой режим? Напиши в комменты”
- “Слушай полный трек — ссылка в профиле”

Conversion (full):
- “Подпишись / следующий трек через ___”
- “Слова/текст в описании”
- “Выбери лучший куплет: 1 или 2”

Community:
- “Какой тег сделать фирменным?”
- “Какой голос A/B сильнее?”

---

## 9) METRICS (MINIMUM KPIs)
Shorts:
- 3s hold (есть ли удержание)
- loop rate / повтор (если видно)
- comments per 1k views

YouTube full:
- CTR title/thumbnail (если есть)
- avg view duration
- subscribers gained

Community:
- comment rate
- poll participation

Rule:
- отслеживать 2–3 KPI на канал, не 20.

---

## 10) PROCEDURE (BUILD CHANNEL PLAN)
### Step 1 — Choose channels used now
Список каналов.

### Step 2 — Assign role per channel
DISCOVERY/CONVERSION/RETENTION/COMMUNITY/ARCHIVE.

### Step 3 — Map formats to channels
Что куда.

### Step 4 — Set cadence (2 weeks)
План-график.

### Step 5 — Choose CTAs
1–2 CTA на канал.

### Step 6 — Define KPIs + thresholds
Минимальные пороги: PASS/REWORK.

### Step 7 — Weekly review
- что сработало (moment type, hook line)
- что не сработало (late hook, weak CTA)
- правки следующей недели

---

## 11) CHANNEL PLAN TEMPLATE (COPY)
CHANNEL PLAN:
- Period (dates):
- Channels:
  - Channel:
    - Role:
    - Formats:
    - Cadence (per week):
    - CTA set:
    - KPI set:
    - Thresholds:
- Content queue (7–14 items):
  - Item:
    - Type (short/full/post):
    - Hook/moment:
    - CTA:
    - Target channel:
- Review notes:
- Result: PASS/REWORK

---

## 12) QA GATES (PASS/FAIL)
PASS IF:
- у каждого канала есть роль
- форматы соответствуют роли
- cadence реалистичный и стабильный
- CTA конкретные
- KPI выбраны и измеримы

REWORK IF:
- план есть, но нет KPI или cadence “слишком много”

FAIL IF:
- “везде одно и то же” и нет роли/метрик

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/02__MARKETING__AUDIENCE_SEGMENTS_PERSONAS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/03__MARKETING__CONTENT_PACKAGING_TITLES_HOOKS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/09__SOUND_MUSIC__UGC_SHORTS_VARIANTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (each channel must have a role + cadence + KPI; no copy-paste strategy)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
