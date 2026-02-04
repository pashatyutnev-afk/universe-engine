FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/05__MUS__LYRIC_BRIEF_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.LYRIC_BRIEF_FACTORY.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_LYRIC_BRIEF_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.LYRIC_BRIEF_FACTORY.001
- SCOPE_TAGS: [MUS, LYRICS, BRIEF, CONSTRAINTS, SAFETY, STYLE]
- OUTPUT_ARTIFACT: LYRIC_BRIEF_TOKEN

---

## [M] PURPOSE
Собирает единый LYRIC_BRIEF_TOKEN для конкретного трека (слота) из TRACK_PLAN_TOKEN + STYLE_ROUTE_TOKEN + IDENTITY_TOKEN.
Фиксирует: тему, POV, образность, структуру, ограничения языка, запреты, слова-якоря, требования к хуку и чистоту правила “без восклицательных знаков”.

---

## [M] INPUTS / OUTPUTS
### Inputs
- TRACK_SLOT (из TRACK_PLAN_TOKEN.slots[i]) (обязателен)
- TRACK_PLAN_TOKEN (обязателен — для глобальных целей)
- STYLE_ROUTE_TOKEN (обязателен)
- OPTIONAL: IDENTITY_TOKEN (artist/brand/лейбл/серия)
- OPTIONAL: constraints_override
  - language?
  - explicit_content?
  - banned_topics?
  - ban_words?
  - must_words?
  - rhyme_mode?
  - meter_hint?
  - structure_hint?
  - hook_hint?

### Outputs
- LYRIC_BRIEF_TOKEN (обязателен при PASS)
- FAIL_CODE? (при FAIL)

---

## [M] TOKEN SCHEMA
### LYRIC_BRIEF_TOKEN (v1)
- route_id: UE.V2.MUS.LYRIC_BRIEF.v1
- domain: MUS
- slot_ref:
  - slot_id: <string>
  - role: <string>
  - title_seed: <string>
- identity_ref:
  - artist_canonical: <string>
  - project_brand: <string|empty>
  - series_tag: <string|empty>
- language_policy:
  - language: ru|en|other|auto
  - allowed_mixing: none|light|free
  - profanity: none|soft|allowed|auto
  - no_exclamation: true
- content_policy:
  - explicit_content: true|false|auto
  - banned_topics: [<string>...]
  - banned_words: [<string>...]
  - must_include_words: [<string>...]
  - safety_notes: [<string>...]
- creative_frame:
  - theme_core: <string>
  - pov: 1p|2p|3p|auto
  - setting: <string>
  - time_of_day: day|night|dawn|dusk|auto
  - emotional_color: [<string>...]
  - imagery_bank: [<string>...]
  - metaphors: [<string>...]
  - anchor_phrases: [<string>...]
- structure_frame:
  - form: verse_chorus|hook_song|story|rap|spoken|auto
  - sections:
    - V1: <rules>
    - CH: <rules>
    - V2: <rules>
    - BR: <rules|optional>
    - OUTRO: <rules|optional>
  - lines_target:
    - verse_lines: <int>
    - chorus_lines: <int>
  - hook_requirements:
    - hook_length_lines: <int>
    - repeat_hook: yes|no
    - catchiness_target: low|mid|high
- style_frame:
  - genre_tags: [<string>...]
  - mood_tags: [<string>...]
  - bpm_target: <int>
  - energy: low|mid|high
  - vocal_style: rap|sing|mixed|spoken|auto
  - rhyme_mode: none|simple|tight|internal|auto
  - meter_hint: free|even|swing|auto
  - diction: simple|poetic|street|cinematic|auto
- qa_targets:
  - clarity: low|mid|high
  - originality: low|mid|high
  - singability: low|mid|high
  - memorize_hook: low|mid|high
- handoff_next_keys:
  - drafter: MUS.LYRIC_DRAFTER
  - editor: MUS.LYRIC_EDITOR
  - focus_loop: MUS.LYRICS_FOCUS_LOOP
  - qa_gate: MUS.QA_CHECKS
- evidence_notes:
  - inputs_seen: [track_slot, track_plan, style_route, identity?]
  - decision: PASS|FAIL
  - reason: <short>

---

## [M] DETERMINISTIC RULES
### Step 0: Preconditions
- Если TRACK_SLOT отсутствует -> FAIL (UE.FAIL.INPUT_ABSENT)
- Если TRACK_PLAN_TOKEN отсутствует -> FAIL (UE.FAIL.INPUT_ABSENT)
- Если STYLE_ROUTE_TOKEN отсутствует -> FAIL (UE.FAIL.INPUT_ABSENT)

### Step 1: Language & exclamation lock
- language := constraints_override.language ? else TRACK_PLAN_TOKEN.global_targets.language ? else auto
- no_exclamation := true (всегда)
- allowed_mixing:
  - default none
  - если STYLE_ROUTE_TOKEN.language_mixing = light/free -> принять, но не нарушать clarity

### Step 2: Explicit/profanity policy
- explicit_content := constraints_override.explicit_content ? else TRACK_PLAN_TOKEN.global_targets.explicit_content ? else auto
- profanity:
  - если explicit_content=false -> none|soft (default soft)
  - если explicit_content=true -> allowed
  - auto -> soft

### Step 3: Collect bans and musts
- banned_topics := unique( TRACK_SLOT.lyrical_frame.banned_topics + TRACK_PLAN_TOKEN.global_targets.banned_topics? + constraints_override.banned_topics )
- banned_words := unique( constraints_override.ban_words + STYLE_ROUTE_TOKEN.banned_words? )
- must_include_words := unique( constraints_override.must_words + STYLE_ROUTE_TOKEN.must_words? )
- safety_notes:
  - если есть self-harm/violence/extremism references в теме -> запретить и FAIL (UE.FAIL.RULE_VIOLATION)

### Step 4: Theme core and POV
- theme_core:
  - если TRACK_SLOT.lyrical_frame.topic_focus задан -> использовать его
  - иначе взять 1 ядро из ALBUM_CONCEPT (если доступно через TRACK_PLAN_TOKEN.identity_ref.title_working + keywords)
- pov:
  - default auto
  - если role=story -> 3p|1p (default 3p)
  - если role=hook/anthem/ballad -> 1p|2p (default 1p)
- setting/time_of_day:
  - если STYLE_ROUTE_TOKEN содержит setting/time hints -> применить
  - иначе auto

### Step 5: Imagery bank
- imagery_bank:
  - взять 6–12 образов из:
    - TRACK_SLOT.lyrical_frame.imagery
    - STYLE_ROUTE_TOKEN.imagery_palette?
    - ALBUM_CONCEPT keywords (если доступны)
- metaphors:
  - 2–4 метафоры максимум, чтобы не “перегрузить”
- anchor_phrases:
  - 2–5 коротких фраз, без "!"

### Step 6: Structure selection
- form:
  - если TRACK_SLOT.vocal=rap -> rap
  - если role=story -> story
  - если role=hook -> hook_song
  - иначе verse_chorus
- sections:
  - verse_chorus:
    - V1, CH, V2, CH, (BR optional), CH, OUTRO optional
  - hook_song:
    - V1 short, CH/HOOK repeated, V2 short, CH/HOOK
  - story:
    - V1, V2, V3, (CH optional короткий рефрен), OUTRO
  - rap:
    - V1 (16), V2 (16), HOOK (8) optional
- lines_target:
  - verse_lines default 12 (rap 16)
  - chorus_lines default 8 (hook 6–8)
- hook_requirements:
  - hook_length_lines:
    - hook_song: 6–8
    - verse_chorus: 8
    - rap: 0–8 (optional)
  - repeat_hook:
    - hook/anthem: yes
    - ballad/story: no|yes (default no)
  - catchiness_target:
    - hook/anthem: high
    - groove: mid
    - ballad/story: mid

### Step 7: Style frame mapping
- genre_tags/mood_tags:
  - взять из STYLE_ROUTE_TOKEN (primary + secondary)
- bpm_target := TRACK_SLOT.bpm_target
- energy := TRACK_SLOT.energy
- vocal_style:
  - если TRACK_SLOT.vocal=rap -> rap
  - если vocal_hooks -> mixed
  - если spoken -> spoken
  - иначе sing|auto (default sing)
- rhyme_mode/meter_hint/diction:
  - constraints_override > STYLE_ROUTE_TOKEN > defaults
  - defaults:
    - hook/anthem: rhyme_mode=tight, diction=cinematic, meter_hint=even|auto
    - ballad: rhyme_mode=simple|tight, diction=poetic
    - rap: rhyme_mode=internal|tight, diction=street

### Step 8: QA targets
- clarity:
  - default high
  - если diction=poetic -> mid (но без “тумана”)
- singability:
  - hook/anthem: high
  - story: mid
  - rap: mid|high
- memorize_hook:
  - hook/anthem: high
  - groove: mid
  - ballad/story: low|mid

---

## [M] KB SCOPE
- KB Inputs: [genre/mood mappings, structure templates, rhyme/meter heuristics, safety/bans lists]
- KB Outputs: [LYRIC_BRIEF_TOKEN]
- KB Boundaries:
  - не использовать защищённые тексты песен как копии
  - не добавлять RAW/URL
  - не нарушать правило “без восклицательных знаков”

---

## [M] GATES
### PASS
- theme_core заполнен
- no_exclamation = true
- sections определены для выбранной формы
- imagery_bank 6+ элементов
- banned_topics / banned_words / must_include_words присутствуют (могут быть пустыми массивами)
- decision = PASS

### FAIL
- отсутствуют обязательные входы
- обнаружены запрещённые темы/запросы, нарушающие safety rules

FAIL_CODE:
- UE.FAIL.INPUT_ABSENT | UE.FAIL.RULE_VIOLATION | UE.FAIL.BRIEF_UNRESOLVED

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff:
  - LYRIC_BRIEF_TOKEN -> MUS.LYRIC_DRAFTER
  - LYRIC_BRIEF_TOKEN -> MUS.LYRIC_EDITOR
  - LYRIC_BRIEF_TOKEN -> MUS.LYRICS_FOCUS_LOOP (если MODE_HINT=MASTERPIECE или hook слабый)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 add deterministic brief rules, safety/bans consolidation, structure templates, QA targets
