# TOPIC — VOICE DIVERSITY RULES (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/02__SOUND_MUSIC__VOICE_DIVERSITY_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.VOICE_DIVERSITY.001
OWNER: SYSTEM
ROLE: Atomic method to enforce voice diversity across generated tracks: vocal identity dimensions, collision guards, assignment matrix for A/B roles, and QA checks to prevent same-voice repetition; includes Voice Profile template and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created voice diversity standard: vocal identity dimensions, collision guards, and assignment matrix to prevent same-voice repetition across catalog."
- REASON: "Generators tend to converge to similar vocals; diversity rules are required for believable groups and multi-artist catalogs."
- IMPACT: "Entities can produce consistent but distinct voices, reduce vocal collisions, and improve perceived quality."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.002

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- voice_diversity
- collision_guard
- qa_gates
- maturity_seed

---

## 1) PURPOSE
Запретить “один и тот же голос везде” и сделать разнообразие управляемым:
- голос = профиль по измерениям,
- каждый трек получает назначение A/B (rap/melodic),
- есть collision guard (порог сходства),
- есть QA проверка “голоса различимы”.

---

## 2) WHEN TO USE
- У группы 2+ ролей (A/B) или много треков подряд.
- Замечаешь одинаковый тембр/манеру/артикуляцию у разных песен.
- Нужно удержать узнаваемость, но не копирование.

## 3) WHEN NOT TO USE
- Одиночный трек без каталога (но всё равно полезно как задел).

---

## 4) DEFINITIONS (STRICT)
### Voice profile
Карточка голоса: набор параметров, которые делают голос узнаваемым.

### Collision
Слишком похожий голос/манера на другой трек или другого “артиста”.

### A/B roles
Роли внутри трека:
- A: melodic lead / hook
- B: rap verse / aggression
(можно инвертировать, но фиксировать в профиле)

---

## 5) VOICE IDENTITY DIMENSIONS (10 AXES)
Профиль голоса задаётся по осям:

1) Timbre: bright / dark / nasal / chesty  
2) Pitch range: low / mid / high  
3) Delivery: spoken / rap / sung / scream  
4) Articulation: crisp / slurred / percussive  
5) Aggression: calm / tense / aggressive  
6) Texture: clean / gritty / distorted  
7) Accent/phonetics: мягкость/твёрдость, “р” и т.д.  
8) Phrasing: staccato / legato / broken (stutter)  
9) Vibrato: none / light / heavy  
10) Persona: cold / manic / tired / heroic / cynical

Правило:
- Чтобы два голоса считались “разными”, они должны различаться минимум по 3–4 осям.

---

## 6) COLLISION GUARDS (STRICT RULES)
### CG1 — No adjacent duplicates
В соседних треках каталога:
- нельзя повторять один и тот же voice profile.

### CG2 — A/B contrast inside a track
Внутри трека:
- A и B должны различаться минимум по 3 осям (например: pitch+texture+persona).

### CG3 — “Same signature phrase” ban
Запрещено повторять одинаковые вокальные паттерны:
- одинаковый темп фраз, одинаковая интонационная дуга, одинаковая “подача” припева.

### CG4 — Similarity threshold (operational)
Если слушатель “перепутает” голос в первые 10–15 секунд — это collision.
Результат: REWORK.

---

## 7) PROCEDURE (ASSIGN VOICES)
### Step 1 — Create 4–8 voice profiles for catalog
Сделай пул голосов:
- VP1..VP8

### Step 2 — Assign roles per track
Для каждого трека:
- A = VPx
- B = VPy

### Step 3 — Write voice spec into prompt contract
Вставить в VOICE SPEC:
- timbre, range, delivery, texture, persona
и добавить negative spec:
- “avoid voice similar to VPx (nasal bright mid)”

### Step 4 — Run Voice QA
После генерации:
- 10s recognition test (различимость)
- compare to last 3 tracks
- если collision → менять оси (не весь промпт)

---

## 8) VOICE PROFILE TEMPLATE (COPY)
VOICE PROFILE (VP):
- VP_ID:
- Role fit: A|B|Both
- Timbre:
- Pitch range:
- Delivery:
- Articulation:
- Aggression:
- Texture:
- Accent/phonetics:
- Phrasing:
- Vibrato:
- Persona:
- Forbidden similarities (avoid):
  - like VP_? because:
- Prompt snippet (copy):
  - "russian male vocals, <timbre>, <range>, <delivery>, <texture>, <persona>, ..."

---

## 9) VOICE ASSIGNMENT MATRIX (COPY)
VOICE ASSIGNMENT MATRIX:
| TRACK_ID | TRACK_NAME | ROLE A (VP) | ROLE B (VP) | Contrast axes (3+) | Collision check vs last 3 | Result |
|---|---|---|---|---|---|---|

Result:
- PASS / REWORK

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] есть пул VP (4–8)
- [ ] у каждого трека назначены A/B
- [ ] A/B различаются по 3+ осям
- [ ] есть negative spec “avoid similar to”
- [ ] пройден 10–15s recognition test
- [ ] нет adjacent duplicates

PASS IF:
- все пункты true

REWORK IF:
- голоса различаются, но есть 1 collision с соседним треком

FAIL IF:
- слушатель путает голоса; A/B внутри трека одинаковы

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (A/B contrast)
A (VP1):
- dark chesty, low range, melodic, clean, heroic
B (VP3):
- bright nasal, mid range, rap, gritty, cynical
Contrast:
- timbre + delivery + texture + persona
WHY PASS:
- голоса очевидно разные.

### 11.2 FAIL EXAMPLE
A и B:
- оба mid range, clean, одинаковая артикуляция и фразировка
WHY FAIL:
- нет контраста, слушатель слышит “одного человека”.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (A/B must differ; collisions must trigger rework)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
