# TOPIC — UGC / SHORTS VARIANTS (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/09__SOUND_MUSIC__UGC_SHORTS_VARIANTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.UGC_VARIANTS.001
OWNER: SYSTEM
ROLE: Atomic method to produce UGC-ready short variants (15/30/60s) from a full track: hook selection, loop engineering, beat drops, caption-safe hooks, and QA tests; includes Shorts Variant Card and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created UGC shorts variant module: pick hook segment, engineer loops, build 15/30/60 variants, and validate scroll-stop/loop readiness."
- REASON: "Short-form performance depends on immediate hooks and loopability; naive cutting ruins retention."
- IMPACT: "Entities can systematically generate viral-ready variants without damaging the core track."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.009

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- ugc
- shorts
- variants
- loop_design
- maturity_seed

---

## 1) PURPOSE
Сделать шорты/UGC варианты не “обрезком”, а продуктом:
- выбрать лучший фрагмент,
- сделать луп (loop-safe),
- усилить первые секунды,
- сделать 15/30/60 версий,
- пройти QA тесты удержания.

---

## 2) WHEN TO USE
- Выпускаешь трек и хочешь сразу шорты.
- Хочешь рост через TikTok/Reels/Shorts.
- Нужен “hook segment” для UGC.
- Трек хороший, но “не цепляет” в первые секунды (в коротком формате).

## 3) WHEN NOT TO USE
- Трек намеренно атмосферный без хука (тогда делать “mood clip” по другому контракту).

---

## 4) DEFINITIONS (STRICT)
### Hook segment
Фрагмент 8–20 секунд, где максимум узнаваемости.

### Loop-safe
Конец фрагмента звучит так, что можно вернуть в начало без “провала”.

### Scroll-stop
Первые 1–3 секунды дают сигнал “стоит слушать”.

---

## 5) VARIANT TYPES (STANDARD)
- V15: 15s micro hook
- V30: 30s hook loop (main)
- V60: 60s mini-story (hook + verse bite + hook)
- VCAP: caption-friendly (слова понятны, нет перегруза)

---

## 6) LOOP ENGINEERING RULES
- L1: start on strong beat (1)
- L2: end on compatible chord/texture
- L3: use a stop/stutter before loop (помогает “склейке”)
- L4: avoid long reverb tails at the end (или обрезать)
- L5: keep hook vocal centered (mono-safe)

---

## 7) HOOK SEGMENT SELECTION (PROCEDURE)
### Step 1 — Pick 2–3 candidate segments
Кандидаты:
- припев 1 (ранний)
- финальный припев (самый мощный)
- bridge call-response (если вирусный)

### Step 2 — Choose main segment (V30)
Критерии:
- узнаётся за 5–10 секунд
- есть слоган/фраза
- есть signature hit/tag

### Step 3 — Design V15
- tag + 1 строка хука + stop
(минимализм)

### Step 4 — Design V60
- hook → короткий кусок куплета (1–2 строки) → hook
(мини-история)

### Step 5 — Caption-friendly decisions
- если текст сложный: выбрать более ясные строки
- убрать слишком быстрые “скороговорки”

---

## 8) SHORTS VARIANT CARD (COPY)
SHORTS VARIANT CARD:
- Track:
- Candidates (time ranges):
  - C1:
  - C2:
- Main V30 segment:
- Loop engineering:
  - Start point:
  - End point:
  - Stop/stutter:
- Variants:
  - V15:
  - V30:
  - V60:
  - VCAP:
- QA:
  - Scroll-stop 3s:
  - Recognition 10s:
  - Loop-safe:
  - Caption clarity:
- Result: PASS/REWORK

---

## 9) QA TESTS (MANDATORY)
- T1: 3-second scroll-stop
  первые 3 секунды должны иметь tag/удар/фразу.
- T2: 10-second recognition
  через 10 секунд хочется повторить строку/ритм.
- T3: Loop-safe
  2 цикла подряд не утомляют и не “проваливаются”.
- T4: Caption clarity (optional)
  выбранная строка понятна и краткая.

PASS IF:
- все T1–T3 PASS (T4 если делаем captions)

---

## 10) COMMON FAIL MODES
- “отрезали кусок” без подводки → Fix: добавить tag/стоп
- хвост реверба ломает луп → Fix: обрезать/стуттер
- в 15s слишком много слов → Fix: одна строка + крик-тег
- хук поздно → Fix: стартовать с хука (cold open)

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (your track concept)
V15:
- “СБО́И!” + “Сбо́и в голове — но я вижу маршрут” + stutter
V30:
- 2 строки припева + glitch tag + stop
WHY PASS:
- узнаваемо и лупится.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/07__SOUND_MUSIC__STRUCTURE_SONG_BLUEPRINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (variants must be loop-safe; no naive cuts; QA tests mandatory)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
