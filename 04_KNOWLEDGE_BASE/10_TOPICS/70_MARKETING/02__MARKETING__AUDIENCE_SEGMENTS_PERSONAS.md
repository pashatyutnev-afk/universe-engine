# TOPIC — AUDIENCE SEGMENTS & PERSONAS (MARKETING / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/02__MARKETING__AUDIENCE_SEGMENTS_PERSONAS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MKT.AUDIENCE_SEGMENTS.001
OWNER: SYSTEM
ROLE: Atomic method to define audience segments and personas for a project/group/catalog: segment logic, persona cards, pain→promise mapping, channel fit, and QA checks to prevent “for everyone” marketing

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created audience segmentation and persona module: segments, persona templates, messaging hooks, channel fit, and pass/fail QA."
- REASON: "Positioning drifts when audience is vague; segments make copy, titles, and releases targeted and consistent."
- IMPACT: "Entities can generate better descriptions, teasers, hashtags, and content plans with lower drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MKT.002

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_marketing
- type_topic
- audience
- personas
- segmentation
- channel_fit
- maturity_seed

---

## 1) PURPOSE
Сегменты и персоны фиксируют:
- кому мы говорим,
- какой боли касаемся,
- какое обещание даём,
- какие триггеры/слова работают,
- где это продвигать (каналы),
чтобы маркетинг не был “для всех”.

---

## 2) WHEN TO USE
- Пишешь описание трека/альбома/группы и выходит “как у всех”.
- Нужны точные заголовки, хэштеги, клипы, тизеры.
- Нужно решить: Shorts/YouTube/соцсети/сообщества — что куда.

## 3) WHEN NOT TO USE
- Разовая публикация “просто скинуть трек” (но для стабильного бренда всё равно лучше иметь минимум 1–2 персоны).

---

## 4) DEFINITIONS (STRICT)
### Segment
Группа аудитории по общей мотивации/контексту, а не по “возрасту ради возраста”.

### Persona
Конкретный представитель сегмента: цель, боль, триггеры, сценарий потребления.

### Job-to-be-done (JTBD)
Зачем человек включает это прямо сейчас (контекст + задача + эмоция).

---

## 5) INPUTS (MINIMUM)
- Positioning Card (promise + archetype + differentiators).
- 3–7 ключевых “сигналов” бренда (style + темы).
- Платформы/каналы (куда публикуем).

## 6) OUTPUTS (MINIMUM)
- 3–5 audience segments.
- 1 persona card на каждый сегмент (минимум 3).
- Message hooks + channel fit.
- PASS/REWORK/FAIL.

---

## 7) SEGMENTATION AXES (CHOOSE 2–4)
Выбирай оси, которые реально влияют на текст и канал:
- A1: Motivation (самоутверждение / разрядка / вдохновение / протест)
- A2: Context (дорога/зал/работа/ночь/стресс)
- A3: Taste (heavy / industrial / rap / electronic)
- A4: Content focus (lyrics-first vs vibe-first)
- A5: Platform behavior (shorts loopers vs full-track listeners)
- A6: Identity need (быть “не как все”, принадлежность к сцене)

Запрет:
- делать сегменты только по демографии без мотивации.

---

## 8) PROCEDURE (SEGMENTS → PERSONAS → MESSAGING)
### Step 1 — Draft 3–5 segments
Каждый сегмент = 1 строка:
- “Люди, которые ___, потому что ___, и хотят ___.”

### Step 2 — For each segment define JTBD (1 sentence)
- “Когда ___, я включаю это, чтобы ___.”

### Step 3 — Build persona card (template below)
Минимум поля: pain / desire / triggers / blockers / content fit / channel.

### Step 4 — Map message hooks (3 per persona)
Для каждой персоны:
- Hook 1: короткий слоган
- Hook 2: “боль → решение”
- Hook 3: “образ/сцена”

### Step 5 — Channel fit
Назначить:
- Primary channel (лучший)
- Secondary channel
- формат (short/full/post)

### Step 6 — QA checks
См. §10.

---

## 9) PERSONA CARD TEMPLATE (COPY)
PERSONA CARD:
- Persona name:
- Segment:
- JTBD (when/why):
- Pain (top 3):
  1)
- Desire (top 3):
  1)
- Triggers (words/images that work):
- Forbidden triggers (what repels):
- Content fit:
  - hook type:
  - lyric density:
  - aggression level:
- Channels:
  - Primary:
  - Secondary:
- CTA style:
  - comment/share/save/listen full
- Notes:

---

## 10) QA (PASS/FAIL)
- T1: Distinctness
  Сегменты не дублируются? (разные мотивации/контексты)
- T2: Messaging difference
  Для каждого сегмента можно написать разные 2 строки описания?
- T3: Channel fit
  Понятно, где этот сегмент реально живёт?
- T4: No “for everyone”
  Нет сегмента “всем, кому нравится музыка”.

PASS IF:
- T1–T4 PASS.

REWORK IF:
- сегменты есть, но тексты для них получаются одинаковые.

FAIL IF:
- аудитория не определена, канал “любой”.

---

## 11) EXAMPLES (MANDATORY / GENERIC)
### Example segments (for industrial nu metal + rap rock project)
S1: “Сцена/тяжёлый вайб” — хотят тяжесть + протест, слушают фулл-треки.
S2: “Шорты-луперы” — ловят 15–30с моменты, любят стоп/крик/слоган.
S3: “Lyrics-first” — им важен текст, смысл, строки-цитаты.
S4: “Workout/drive” — нужен ритм/стомп/удар, минимум воды.

WHY PASS:
- сегменты отличаются контекстом и поведением.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/01__MARKETING__POSITIONING_BRAND_ARCHETYPE.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/09__SOUND_MUSIC__UGC_SHORTS_VARIANTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no “for everyone” segments; each persona must have JTBD + channel fit)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
