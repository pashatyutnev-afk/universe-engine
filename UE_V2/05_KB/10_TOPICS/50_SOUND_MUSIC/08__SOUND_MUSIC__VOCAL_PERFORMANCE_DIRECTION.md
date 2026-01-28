# TOPIC — VOCAL PERFORMANCE DIRECTION (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/08__SOUND_MUSIC__VOCAL_PERFORMANCE_DIRECTION.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.VOCAL_DIRECTION.001
OWNER: SYSTEM
ROLE: Atomic method to direct vocal performance for generated songs: role-based delivery (rap vs melodic), articulation, energy arc, emotion palette, adlibs, and clarity controls; includes Vocal Direction Card and pass/fail QA tests

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created vocal performance direction module: delivery specs, articulation rules, energy arc, adlibs, and QA tests for clarity and contrast."
- REASON: "Generators often output flat or samey vocals; explicit direction improves intelligibility and emotional impact."
- IMPACT: "Entities can produce more distinctive, readable, and dynamic vocal performances across A/B roles."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.008

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- vocal_direction
- performance
- clarity
- contrast
- maturity_seed

---

## 1) PURPOSE
Сделать вокал управляемым:
- роли A/B различимы,
- рэп читается, припев поётся,
- эмоция и динамика растут,
- есть адлибы/шоты без мусора,
- вокал не тонет в миксе.

---

## 2) WHEN TO USE
- Вокал “одинаковый” везде.
- Речь мямлит, слова не разобрать.
- Припев не “поднимается”.
- Нужны агрессия + чистота (nu metal / industrial / rap rock).

## 3) WHEN NOT TO USE
- Инструментальный трек.

---

## 4) DEFINITIONS (STRICT)
### Delivery
Манера подачи: rap / melodic / shout / whisper.

### Articulation
Чёткость согласных и атака слогов.

### Energy arc
Рост/спад энергии по секциям (verse → chorus → final).

### Adlibs / shots
Короткие вставки (“СЕЙЧАС!”, “РЕЖИМ!”) для акцентов.

---

## 5) VOCAL DIMENSIONS (CONTROL AXES)
Управляй по осям:
1) Role: A/B
2) Delivery: rap / melodic / shout
3) Register: low / mid / high
4) Texture: clean / gritty / distorted
5) Articulation: crisp / relaxed
6) Emotion: cold / angry / defiant / tired / manic
7) Dynamics: restrained → explosive
8) Space: dry / slight room / wide chorus
9) Phrase shape: staccato / legato
10) Breath/noise: controlled / raw

---

## 6) ROLE CONTRACTS (A vs B)
### Role A (melodic hook lead)
- цель: запоминаемость и “подъём”
- требования:
  - больше legato
  - ясный слоган (hook line)
  - шире в миксе, но без утопления

### Role B (rap/attack)
- цель: драйв, давление, смысл
- требования:
  - crisp articulation
  - staccato, percussive consonants
  - плотнее в центре (mono-safe)

---

## 7) ENERGY ARC RULES (STRICT)
- verse 1: restrained / controlled
- chorus 1: lift (выше энергия)
- verse 2: больше давления или ускорение подачи
- final chorus: peak (самый высокий уровень)
- outro: коротко, “tag” крик/шот

---

## 8) ADLIBS & SHOTS (CONTROLLED)
### Allowed
- 1–2 слова, крик/вставка:
  “СБО́И!”, “РЕЖИМ!”, “СЕЙЧАС!”
- микро-эхо, стуттер, фраза-обрыв

### Forbidden
- длинные разговорные монологи
- адлибы, которые забивают основной вокал
- слишком много повторов (каждые 2 секунды)

Rule:
- адлибы появляются в местах напряжения/поворота, не везде.

---

## 9) CLARITY CONTROLS (RAP READABILITY)
- избегать спорных ударений (stress-safe words)
- избегать скороговорок > 1 на 8 строк
- короткие окончания строк (чтобы “сбивало” ритм меньше)
- в куплетах: меньше “широких” эффектов на голос

---

## 10) PROCEDURE (VOCAL DIRECTION CARD)
### Step 1 — Assign roles A/B (voice profiles)
### Step 2 — Define delivery per section
- verse: B rap
- chorus: A melodic
- bridge: A/B call-response
### Step 3 — Define energy arc
### Step 4 — Define articulation notes
### Step 5 — Define adlibs/shots list (3–7)
### Step 6 — Add negative spec
- avoid flat delivery, avoid same timbre as last track, avoid mumbling
### Step 7 — QA tests
- see §11

---

## 11) QA TESTS (PASS/REWORK)
- T1: Verse intelligibility
  куплет читается на earbuds/phone
- T2: Chorus lift
  припев ощущается “выше” и шире
- T3: Role contrast
  A и B различимы за 10 секунд
- T4: Adlib discipline
  адлибы не мешают словам
- T5: Stress safety
  нет спорных ударений в hook

RESULT:
- PASS / REWORK

---

## 12) VOCAL DIRECTION CARD (COPY)
VOCAL DIRECTION CARD:
- Track:
- Roles:
  - A (hook): voice profile + delivery:
  - B (verse): voice profile + delivery:
- Section delivery:
  - Intro:
  - Verse1:
  - Chorus1:
  - Verse2:
  - Bridge:
  - Final chorus:
  - Outro:
- Energy arc:
- Articulation notes:
- Adlibs/shots (3–7):
  - 1)
  - 2)
- Negative spec:
- QA:
  - Verse intelligibility:
  - Chorus lift:
  - Role contrast:
  - Adlib discipline:
  - Stress safety:
- Result: PASS/REWORK

---

## 13) EXAMPLES (MANDATORY)
### 13.1 PASS EXAMPLE (industrial nu metal)
A:
- clean melodic, mid-high, defiant, slight width
B:
- gritty rap, mid, percussive consonants, centered
Shots:
- “СБО́И!” (intro/outro), “СЕЙЧАС!” (bridge)
WHY PASS:
- роли различимы, припев поднимает энергию.

### 13.2 FAIL EXAMPLE
- оба голоса clean mid, одинаковая артикуляция
- припев не отличается от куплета
WHY FAIL:
- нет контраста и lift.

---

## 14) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/02__SOUND_MUSIC__VOICE_DIVERSITY_RULES.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/06__SOUND_MUSIC__LYRICS_RHYME_METER_TOOLKIT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/05__SOUND_MUSIC__MIX_TRANSLATION_QA.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 15) COMPLIANCE
- SOURCE_LOCK: required (roles must contrast; clarity tests mandatory; adlibs controlled)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
