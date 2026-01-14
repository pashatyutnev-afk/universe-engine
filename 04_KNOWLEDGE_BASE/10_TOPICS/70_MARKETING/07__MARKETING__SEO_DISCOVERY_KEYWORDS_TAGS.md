# TOPIC — SEO & DISCOVERY: KEYWORDS, TAGS & SEARCH INTENT (MARKETING / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/07__MARKETING__SEO_DISCOVERY_KEYWORDS_TAGS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MKT.SEO_DISCOVERY.001
OWNER: SYSTEM
ROLE: Atomic method to improve discovery via keywords/tags without spam: keyword buckets, intent mapping, title/description/tag placement, and QA gates for YouTube/Shorts/social; includes Keyword Set templates and pass/fail checks

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created SEO/discovery module: keyword buckets, search intent mapping, tag placement rules, and anti-spam QA."
- REASON: "Discovery depends on matching search intent; random hashtags create noise and hurt consistency."
- IMPACT: "Entities can publish with better findability and less drift across platforms."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MKT.007

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_marketing
- type_topic
- seo
- discovery
- keywords
- tags
- anti_spam
- maturity_seed

---

## 1) PURPOSE
Сделать “находимость” системной:
- ключевые слова соответствуют намерению поиска,
- теги структурированы по корзинам,
- placement (куда что вставлять) фиксирован,
- нет спама и случайных слов.

---

## 2) WHEN TO USE
- YouTube/Shorts публикации без трафика из поиска.
- Нужны стабильные теги для каталога.
- Хочешь, чтобы “жанр/вайб” находили по запросам.
- Много релизов → нужен повторяемый шаблон.

## 3) WHEN NOT TO USE
- Канал чисто для “своих” (но даже там полезно для порядка каталога).

---

## 4) DEFINITIONS (STRICT)
### Search intent
Намерение запроса:
- genre discovery (“industrial rap rock”)
- mood (“aggressive workout music”)
- theme (“glitch cyber song”)
- format (“short loop”, “lyric video”)

### Keyword bucket
Группа ключей по смыслу, чтобы не мешать всё в кучу.

---

## 5) KEYWORD BUCKETS (STANDARD)
Используй 4 корзины:

B1 — Genre/style
- nu metal, industrial rock, rap rock, electronic metal

B2 — Mood/energy
- aggressive, heavy, dark, workout, stomp

B3 — Theme/imagery
- glitch, signal, noise, system, reboot, control

B4 — Format/platform
- shorts, loop, lyric video, official audio

Rule:
- 60% B1+B2, 40% B3+B4.

---

## 6) PLACEMENT RULES (WHERE TO PUT WHAT)
### Title
- 1–2 ключа из B1 (жанр) или B2 (энергия)
- не перегружать

### First 2 lines of description
- 1 promise line + 2–4 ключа (B1/B2/B3)

### Hashtags (Shorts)
- 5–12, микс корзин

### Keywords/tags (YouTube internal)
- 5–12 ключей, без мусора

Rule:
- важнее первые строки описания, чем “простыня тегов”.

---

## 7) ANTI-SPAM RULES (STRICT)
- AS1: не ставить нерелевантные трендовые теги
- AS2: не повторять одно и то же слово 10 раз
- AS3: не делать 50 хэштегов
- AS4: теги должны отражать реальный звук/вайб
- AS5: 1–2 brand tags максимум (не засорять)

---

## 8) PROCEDURE (BUILD KEYWORD SET)
### Step 1 — Choose 5–12 keywords total
- B1: 3–5
- B2: 2–4
- B3: 2–4
- B4: 1–2

### Step 2 — Validate relevance
Каждое слово должно быть слышно/видно в релизе.

### Step 3 — Insert into packaging
- title + first lines + hashtags + tags

### Step 4 — Run QA gates
см. §10

---

## 9) KEYWORD SET TEMPLATE (COPY)
KEYWORD SET:
- B1 Genre/style:
- B2 Mood/energy:
- B3 Theme/imagery:
- B4 Format/platform:
Placement:
- Title keywords:
- First 2 lines keywords:
- Hashtags (5–12):
- YouTube tags (5–12):
Result: PASS/REWORK

---

## 10) QA GATES (PASS/FAIL)
PASS IF:
- 4 корзины заполнены
- теги релевантны реальному контенту
- hashtags ≤ 12
- нет спама и мусора
- первые 2 строки описания содержат ключи

REWORK IF:
- теги слишком общие или не сбалансированы по корзинам

FAIL IF:
- нерелевантные теги, 30+ хэштегов, “ловля трендов” без связи

---

## 11) EXAMPLES (MANDATORY / GENERIC)
B1:
- nu metal, industrial rock, rap rock
B2:
- aggressive, half-time stomp
B3:
- glitch, signal, reboot
B4:
- shorts, loop
Hashtags:
- #numetal #industrialrock #raprock #electronicmetal #glitch #signal #reboot #shorts #loop #heavy #aggressive
WHY PASS:
- баланс корзин, релевантно.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/03__MARKETING__CONTENT_PACKAGING_TITLES_HOOKS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/04__MARKETING__DISTRIBUTION_CHANNEL_STRATEGY.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/10__SOUND_MUSIC__CREDITS_METADATA_POLICY.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no spam; must use buckets; must place keywords in first description lines)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
