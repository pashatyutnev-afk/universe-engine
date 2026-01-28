# TOPIC — ALBUM BLUEPRINT & PLANNING (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/13__SOUND_MUSIC__ALBUM_BLUEPRINT_PLANNING.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.ALBUM_BLUEPRINT.001
OWNER: SYSTEM
ROLE: Atomic method to plan albums as coherent but varied catalogs: album thesis, energy arc, track roles, voice allocation, anti-collision rules, hook slotting, and QA/release readiness; includes Album Blueprint template and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created album blueprint planning: thesis/arc, track role map, voice matrix, anti-collision constraints, and QA/release pack integration."
- REASON: "Albums fail when tracks blur together; planning enforces variety and cohesion simultaneously."
- IMPACT: "Entities can build stronger catalogs, reduce repeats, and speed up production with deterministic planning."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.013

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- album_planning
- catalog_strategy
- voice_matrix
- anti_collision
- maturity_seed

---

## 1) PURPOSE
Построить альбом как систему:
- общая идея/атмосфера (thesis),
- дуга энергии (energy arc),
- роли треков (opener, hit, deep, closer),
- распределение голосов A/B,
- защита от повторов/коллизий,
- план шортов и релиз-паков.

---

## 2) WHEN TO USE
- Планируешь альбом/EP (4–12 треков).
- Генерируешь много треков подряд и получаются похожие.
- Нужна “карта” до генерации, чтобы не тратить попытки.
- Нужны разные типы хитов (UGC, стадионный припев, мрачный трек).

## 3) WHEN NOT TO USE
- Один сингл без каталога.

---

## 4) DEFINITIONS (STRICT)
### Album thesis
Одна фраза: “про что этот релиз” (эмоционально/идеей).

### Track role
Функция трека в альбоме: старт/пик/контраст/пауза/финал.

### Energy arc
Профиль энергии по трекам (рост/спады/второй пик).

---

## 5) TRACK ROLES (TOOLBOX)
- TR1: Opener (быстро цепляет, задаёт стиль)
- TR2: Lead single (самый липкий хук)
- TR3: Aggro banger (максимум давления)
- TR4: Mood/Atmospheric (передышка)
- TR5: Story track (больше текста/сюжета)
- TR6: Experiment slot (безопасная новизна)
- TR7: Closer (итог/последний удар)
- TR8: UGC killer (короткие моменты, мемность)

Правило:
- роли должны различаться, иначе “все треки одинаковые”.

---

## 6) ALBUM CONSTRAINTS (ANTI-DRIFT / ANTI-COLLISION)
- AC1: no adjacent voice duplicates (A/B профили не повторять подряд)
- AC2: no adjacent hook contour duplicates
- AC3: alternate tempo feel (±6 bpm или смена грува каждые 2 трека)
- AC4: alternate arrangement signature (tag/sound design отличать)
- AC5: each track must have unique “image set” (метафоры/словарь)

---

## 7) PROCEDURE (ALBUM BLUEPRINT)
### Step 1 — Write album thesis (1 line)
### Step 2 — Choose 4–12 track count
### Step 3 — Draw energy arc
Пример:
- T1 high → T2 peak → T3 mid → T4 low → T5 peak2 → T6 closer

### Step 4 — Assign track roles (TR1..TR8)
Каждому треку 1 роль.

### Step 5 — Allocate voice profiles A/B
Использовать VP пул:
- A: VP1/VP2/...
- B: VP3/VP4/...
и соблюсти AC1.

### Step 6 — Hook slotting
Для каждого трека:
- hook type (H1..H7)
- hook phrase (1 строка)
- UGC moments count (2–5)

### Step 7 — Anti-collision plan
Проверить AC1..AC5 на соседях.

### Step 8 — Release plan
Для каждого трека:
- variants: V15/V30/V60
- release pack readiness

---

## 8) ALBUM BLUEPRINT TEMPLATE (COPY)
ALBUM BLUEPRINT:
- Album title:
- Thesis (1 line):
- Style fingerprint:
- Track count:
- Energy arc (by track):
- Track list (plan):
| Track # | Working title | Role (TR) | BPM/feel | Hook type | Hook line | Voice A (VP) | Voice B (VP) | UGC moments | Notes |
|---|---|---|---|---|---|---|---|---|---|

Constraints check:
- AC1 voice adjacency: PASS/REWORK
- AC2 hook contour adjacency: PASS/REWORK
- AC3 tempo/groove alternation: PASS/REWORK
- AC4 arrangement tag variety: PASS/REWORK
- AC5 image set variety: PASS/REWORK

Release plan:
- For each track: variants + pack status

Result:
- PASS / REWORK

---

## 9) QA GATES (PASS/FAIL)
PASS IF:
- роли треков разнообразны
- energy arc имеет минимум 1 спад и 2 пика (для 7+ треков)
- voice A/B не повторяются подряд
- хуки различимы по типу/контур/фразе
- у каждого трека 2+ UGC моменты
- есть план variants + release pack

REWORK IF:
- 1–2 коллизии по соседним трекам (AC1..AC4)

FAIL IF:
- большинство треков в одной роли и звучат одинаково

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (7-track album)
T1 opener (style statement)
T2 lead single (липкий слоган)
T3 aggro banger
T4 mood track (спад)
T5 story track
T6 experiment slot
T7 closer
WHY PASS:
- есть дуга, роли и контрасты.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/07__SOUND_MUSIC__STRUCTURE_SONG_BLUEPRINTS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/04__SOUND_MUSIC__REPEAT_GUARD_ANTI_COLLISION.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/02__SOUND_MUSIC__VOICE_DIVERSITY_RULES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/09__SOUND_MUSIC__UGC_SHORTS_VARIANTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (anti-collision constraints mandatory; blueprint required before bulk generation)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
