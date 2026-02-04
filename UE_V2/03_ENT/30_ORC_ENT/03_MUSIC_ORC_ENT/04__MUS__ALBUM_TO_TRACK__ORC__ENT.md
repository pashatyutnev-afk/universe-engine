FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/04__MUS__ALBUM_TO_TRACK__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.ALBUM_TO_TRACK.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_ALBUM_TO_TRACK
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.ALBUM_TO_TRACK.001
- SCOPE_TAGS: [MUS, ALBUM, TRACK, PLAN, SLOTS, VARIANTS]
- OUTPUT_ARTIFACT: TRACK_PLAN_TOKEN

---

## [M] PURPOSE
Разбивает ALBUM_CONCEPT_TOKEN на детерминированный план треков.
Создаёт слоты (интро, хук-трек, баллада, бэнгер и т.д.), правила вариативности, требования к тексту/вокалу/инструменталу и готовит handoff в Lyric Brief / Track Build.

---

## [M] INPUTS / OUTPUTS
### Inputs
- ALBUM_CONCEPT_TOKEN (обязателен)
- STYLE_ROUTE_TOKEN (обязателен)
- OPTIONAL: PORTFOLIO_TOKEN (если есть серия/каденс/матрица разнообразия)
- OPTIONAL: constraints_override
  - slots_count?
  - avg_track_sec?
  - include_instrumentals?
  - vocal_ratio?
  - explicit_content?
  - banned_topics?

### Outputs
- TRACK_PLAN_TOKEN (обязателен при PASS)
- FAIL_CODE? (при FAIL)

---

## [M] TOKEN SCHEMA
### TRACK_PLAN_TOKEN (v1)
- route_id: UE.V2.MUS.TRACK_PLAN.v1
- domain: MUS
- identity_ref:
  - artist_canonical: <string>
  - release_type: album|ep|playlist|single_track
  - title_working: <string>
- global_targets:
  - slots_count: <int>
  - total_target_min: <int>
  - avg_track_sec: <int>
  - bpm_range: [<int>, <int>]
  - energy_curve: low_to_high|high_to_low|wave|stable|auto
  - vocal_policy: none|mostly_vocal|mixed|mostly_instrumental
  - language: ru|en|other|auto
  - explicit_content: true|false|auto
- slot_rules:
  - slot_types_allowed: [intro, hook, anthem, ballad, groove, interlude, outro, instrumental, story]
  - repetition_limits:
    - hook_like_max: <int>
    - ballad_max: <int>
    - instrumental_max: <int>
- slots: [TRACK_SLOT...]
- variants_policy:
  - per_slot_variants: 1|2|3
  - explore_axes: [arrangement, melody, hook, lyrics, tempo, sound_palette]
  - keep_fixed: [identity, banned_topics, text_policy, language]
- handoff_next_keys:
  - per_slot_default: MUS.LYRIC_BRIEF_FACTORY|MUS.TRACK_BUILD_STEP
  - qa_gate: MUS.QA_CHECKS
- evidence_notes:
  - inputs_seen: [album_concept, style_route, portfolio?]
  - decision: PASS|FAIL
  - reason: <short>

### TRACK_SLOT (v1)
- slot_id: T01|T02|...
- role: intro|hook|anthem|ballad|groove|interlude|outro|instrumental|story
- title_seed: <string>
- mood: [<string>...]
- bpm_target: <int>
- energy: low|mid|high
- duration_sec_target: <int>
- vocal: none|vocal|vocal_hooks|rap|spoken|auto
- lyric_need: yes|no
- lyrical_frame:
  - pov: 1p|2p|3p|auto
  - imagery: [<string>...]
  - topic_focus: <string>
  - banned_topics: [<string>...]
- production_frame:
  - instrumentation: [<string>...]
  - banned_sounds: [<string>...]
  - mix_targets: [<string>...]
- constraints_lock:
  - lock_level: soft|medium|hard
  - reasons: [<string>...]

---

## [M] DETERMINISTIC RULES
### Step 0: Preconditions
- Если нет ALBUM_CONCEPT_TOKEN -> FAIL (UE.FAIL.INPUT_ABSENT)
- Если нет STYLE_ROUTE_TOKEN -> FAIL (UE.FAIL.INPUT_ABSENT)

### Step 1: Resolve counts and durations
- base_slots_count = ALBUM_CONCEPT_TOKEN.track_plan_defaults.slots_count
- base_avg_sec = ALBUM_CONCEPT_TOKEN.track_plan_defaults.avg_track_sec
- Если constraints_override.slots_count задан -> принять и повысить lock_level
- Если constraints_override.avg_track_sec задан -> принять и повысить lock_level
- total_target_min = round(slots_count * avg_sec / 60)
- Если ALBUM_CONCEPT_TOKEN.track_plan_defaults.total_target_min задан и != total_target_min:
  - принять total_target_min из concept и пересчитать avg_sec = round(total_target_min*60/slots_count)

### Step 2: Resolve BPM and energy curve from style
- bpm_range:
  - если STYLE_ROUTE_TOKEN содержит bpm_range -> взять
  - иначе:
    - slow mood -> [70, 95]
    - mid -> [90, 120]
    - fast -> [115, 150]
- energy_curve:
  - album/ep: wave (default)
  - playlist: stable|wave (default stable)
  - single_track: stable

### Step 3: Resolve vocal policy
- Если STYLE_ROUTE_TOKEN.vocal.type = none -> vocal_policy=mostly_instrumental
- Иначе:
  - album/ep: mixed
  - playlist: mostly_vocal (если не указано include_instrumentals)
- vocal_ratio (если задан):
  - mostly_vocal: 80% слотов vocal
  - mixed: 60% vocal
  - mostly_instrumental: 20% vocal

### Step 4: Slot template selection by release_type
- single_track:
  - slots_count=1
  - slot roles: [hook] или [anthem] (по mood_axis)
- ep (5 default):
  - [intro, hook, groove, ballad, anthem] (если 4 -> drop intro)
- album (9 default):
  - [intro, hook, groove, anthem, story, ballad, groove, hook, outro]
- playlist (30 default):
  - repeating macro-cycle of 6:
    - [hook, groove, anthem, hook, instrumental(optional), story(optional)]
  - каждые 5–7 треков вставить low-energy слот (ballad|chill groove)

### Step 5: Generate per-slot targets
- duration_sec_target:
  - base_avg_sec +/- 15% по роли
  - intro/interlude/outro: base_avg_sec - 25..40%
  - anthem/hook: base_avg_sec - 0..10%
  - ballad/story: base_avg_sec + 10..25%
- bpm_target:
  - выбрать внутри bpm_range
  - wave curve: чередовать низкий/средний/высокий каждые 2–3 слота
- energy:
  - low: intro/ballad/interlude/outro
  - high: hook/anthem
  - mid: groove/story

### Step 6: Title seeds and topic focus
- title_seed:
  - из ALBUM_CONCEPT_TOKEN.keywords (1–2 слова) + роль
  - без знаков "!"
- topic_focus:
  - один фокус на слот (любовь/дорога/ночь/память/свет/город/север и т.д.) из concept_core/story_frame
- banned_topics:
  - объединить: ALBUM_CONCEPT_TOKEN.concept.banned_topics + constraints_override.banned_topics

### Step 7: Lyric need and handoff
- lyric_need=yes если vocal != none и release_type != instrumental-only
- per_slot_default:
  - если lyric_need=yes -> MUS.LYRIC_BRIEF_FACTORY
  - если lyric_need=no -> MUS.TRACK_BUILD_STEP

### Step 8: Variants policy
- per_slot_variants:
  - FAST: 1
  - RELEASE_READY: 2
  - MASTERPIECE: 3
  - default: 2
- explore_axes:
  - всегда: arrangement, hook
  - если lyric_need=yes: lyrics
  - если playlist: tempo, sound_palette
- keep_fixed:
  - identity, banned_topics, text_policy=no_exclamation, language

---

## [M] KB SCOPE
- KB Inputs: [slot templates, bpm/energy mapping, duration heuristics, vocal policy]
- KB Outputs: [TRACK_PLAN_TOKEN]
- KB Boundaries:
  - не добавлять RAW
  - не тянуть чужие конкретные песни как копипаст-референсы

---

## [M] GATES
### PASS
- slots_count > 0
- каждый слот имеет: slot_id, role, duration_sec_target, bpm_target, vocal, lyric_need
- banned_topics заполнен (может быть пустым массивом)
- decision = PASS

### FAIL
- отсутствует ALBUM_CONCEPT_TOKEN или STYLE_ROUTE_TOKEN

FAIL_CODE:
- UE.FAIL.INPUT_ABSENT | UE.FAIL.RULE_VIOLATION | UE.FAIL.PLAN_UNRESOLVED

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff:
  - TRACK_PLAN_TOKEN -> MUS.LYRIC_BRIEF_FACTORY (по слотам с lyric_need=yes)
  - TRACK_PLAN_TOKEN -> MUS.TRACK_BUILD_STEP (по слотам instrumental/no-lyric)
  - TRACK_PLAN_TOKEN -> MUS.METADATA_FACTORY (для черновых названий/таймингов)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 add slot templates, deterministic planning rules, variants policy, gates
