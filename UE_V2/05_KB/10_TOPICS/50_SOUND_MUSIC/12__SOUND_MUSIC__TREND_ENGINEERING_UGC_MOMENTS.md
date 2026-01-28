# TOPIC — TREND ENGINEERING & UGC MOMENTS (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/12__SOUND_MUSIC__TREND_ENGINEERING_UGC_MOMENTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.TREND_UGC_MOMENTS.001
OWNER: SYSTEM
ROLE: Atomic method to design “UGC moments” inside tracks: meme lines, stop-cuts, call-response, drop-less hooks, and 2–5s attention spikes to improve short-form performance; includes UGC Moment Map template and pass/fail tests

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created UGC moment engineering: design attention spikes and meme-ready moments with repeatable patterns and QA tests."
- REASON: "Short-form growth depends on shareable moments; tracks need deliberate moment hooks beyond the chorus."
- IMPACT: "Entities can produce more clip-worthy songs with multiple viral entry points."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.012

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- ugc_moments
- trend_engineering
- shareability
- shortform
- maturity_seed

---

## 1) PURPOSE
Сделать в треке 2–6 “моментов”, которые легко нарезать и повторять:
- мем-строка,
- стоп/стуттер,
- call-response,
- резкий контраст,
- короткий крик-тег,
- “drop-less hook” (без ожидания дропа).

---

## 2) WHEN TO USE
- Хочешь рост через Shorts/Reels/TikTok.
- Трек качает, но “нарезать нечего”.
- Нужны несколько точек входа (не только припев).
- Нужны моменты 2–5 секунд, которые цепляют.

## 3) WHEN NOT TO USE
- Если релиз строго альбомный/кинематографический без ориентирования на шорты (но даже там 1–2 момента полезны).

---

## 4) DEFINITIONS (STRICT)
### UGC moment
Короткий участок 2–8 секунд, который:
- понятен без контекста,
- эмоционально “щёлкает”,
- повторяем и лупится,
- имеет фразу/звуковой тег/резкий поворот.

### Attention spike
Пик внимания (резкий контраст, стоп, крик, смена ритма).

---

## 5) UGC MOMENT TYPES (TAXONOMY)
- U1: Meme line (короткая цитата)
- U2: Call-response (“Скажи… — СЕЙЧАС!”)
- U3: Stop-cut / stutter (обрыв + удар)
- U4: Tag shout (1 слово крик)
- U5: Rhythm switch (half-time ↔ double-time)
- U6: Texture flip (чисто ↔ грязь / узко ↔ широко)
- U7: “Drop-less hook” (хук без ожидания, сразу)

Рекомендуемо:
- 1–2 из U2/U3/U4 обязательно.

---

## 6) DESIGN RULES (STRICT)
- DR1: момент должен быть понятен без 30 секунд подводки
- DR2: длительность 2–8 секунд (для шортов)
- DR3: должен быть 1 “якорь”: фраза или звук-тег
- DR4: не должен ломать основную песню (встроен органично)
- DR5: минимум 2 момента на трек, лучше 3–5

---

## 7) PROCEDURE (UGC MOMENT MAP)
### Step 1 — Choose 2–6 slots in structure
Где вставлять:
- early (0:00–0:15)
- pre-chorus/chorus entry
- bridge/breakdown
- final chorus entry

### Step 2 — Assign moment type per slot (U1..U7)
### Step 3 — Write anchors (phrase/sound tag)
- 1–2 слова или 1 строка

### Step 4 — Engineer contrast
- стоп, пауза, стуттер
- смена тембра/ширины
- ударный хит

### Step 5 — Check loopability
- момент должен резаться в луп (2 цикла)

### Step 6 — QA tests
см. §9

---

## 8) UGC MOMENT MAP TEMPLATE (COPY)
UGC MOMENT MAP:
| MOMENT_ID | Time/Section | Type (U1..U7) | Anchor (phrase/tag) | Contrast mechanism | Clip length (s) | Loop-safe (Y/N) | Notes |
|---|---|---|---|---|---|---|---|

---

## 9) QA TESTS (PASS/REWORK)
- T1: 3-second clarity
  Момент понятен за 3 секунды?
- T2: Repeat desire
  Хочется повторить фразу/ритм?
- T3: Loop-safe
  2 цикла подряд звучит норм?
- T4: Doesn’t break song
  В полной версии не выглядит как “вставка ради вставки”?

PASS IF:
- T1–T3 PASS, T4 PASS

REWORK IF:
- момент хороший, но не лупится или непонятен без контекста

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (your style)
U2 call-response:
- “Сейчас — назови мой режим…” / “СЕЙЧАС!”
U3 stop-cut:
- stutter before chorus entry
U4 tag:
- “СБО́И!”
WHY PASS:
- 3 разные точки входа, легко нарезать.

### 10.2 FAIL EXAMPLE
Момент:
- 12 секунд длинной подводки без якоря
WHY FAIL:
- не режется и не цепляет быстро.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/09__SOUND_MUSIC__UGC_SHORTS_VARIANTS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/07__SOUND_MUSIC__STRUCTURE_SONG_BLUEPRINTS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (>=2 UGC moments per track; loop-safe; QA tests mandatory)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
