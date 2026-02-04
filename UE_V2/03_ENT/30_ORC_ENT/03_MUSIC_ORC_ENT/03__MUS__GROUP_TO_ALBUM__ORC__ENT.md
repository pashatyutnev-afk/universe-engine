FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/03__MUS__GROUP_TO_ALBUM__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.GROUP_TO_ALBUM.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_GROUP_TO_ALBUM
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.GROUP_TO_ALBUM.001
- SCOPE_TAGS: [MUS, ID, ALBUM, POSITIONING, ROUTING]
- OUTPUT_ARTIFACT: ALBUM_CONCEPT_TOKEN

---

## [M] PURPOSE
Сшивает identity (artist/group/project) с концептом релиза (album/ep/playlist).
Фиксирует позиционирование, серию, тон, визуальные и текстовые рамки, чтобы дальше планировать треки без расползания смысла.

---

## [M] INPUTS / OUTPUTS
### Inputs
- MUS_BRIEF (обязателен)
  - target: album|ep|playlist|single_track
  - theme?: free text
  - audience?: free text
  - language?: ru|en|other|auto
  - platform?: streaming|youtube|tiktok|mixed|auto
  - duration_total_min?: int|auto
  - constraints?: { explicit_content?, banned_topics?, cover_style?, references? }
- STYLE_ROUTE_TOKEN (обязателен)
- IDENTITY_TOKEN (опционально, если уже собран MUS.IDENTITY_BUILD)
  - artist_name, project_name, alias_set, brand_notes, canon_flags

### Outputs
- ALBUM_CONCEPT_TOKEN (обязателен при PASS)
- FAIL_CODE? (при FAIL)

---

## [M] TOKEN SCHEMA
### ALBUM_CONCEPT_TOKEN (v1)
- route_id: UE.V2.MUS.ALBUM_CONCEPT.v1
- domain: MUS
- release_type: album|ep|playlist|single_track
- identity:
  - artist_display: <string>
  - artist_canonical: <string>
  - brand_family: <string|empty>
  - alias: [<string>...]
- positioning:
  - one_liner: <string>
  - mood_axis: [<string>...]
  - genre_primary: <string>
  - era_hint: <string|empty>
  - audience: <string|empty>
- concept:
  - title_working: <string>
  - concept_core: <string>
  - story_frame: <string|empty>
  - keywords: [<string>...]
  - banned_topics: [<string>...]
- packaging_defaults:
  - cover_direction: minimal|photo_real|illustration|abstract|auto
  - text_policy: no_exclamation
  - language: ru|en|other|auto
  - platform_focus: streaming|youtube|tiktok|mixed|auto
- track_plan_defaults:
  - slots_count: <int>
  - avg_track_sec: <int>
  - total_target_min: <int>
  - variability: low|mid|high
- constraints_lock:
  - lock_level: soft|medium|hard
  - reasons: [<string>...]
- handoff_next_keys:
  - next_orc: MUS.ALBUM_TO_TRACK|MUS.LYRIC_BRIEF_FACTORY|MUS.TRACK_BUILD_STEP
- evidence_notes:
  - inputs_seen: [brief, style_route, identity]
  - decision: PASS|FAIL
  - reason: <short>

---

## [M] DETERMINISTIC RULES
### Step 0: Preconditions
- Если MUS_BRIEF отсутствует -> FAIL (UE.FAIL.INPUT_ABSENT)
- Если STYLE_ROUTE_TOKEN отсутствует -> FAIL (UE.FAIL.INPUT_ABSENT)

### Step 1: Resolve release_type
- release_type = MUS_BRIEF.target
- Если target=single_track:
  - всё равно собираем ALBUM_CONCEPT_TOKEN, но slots_count=1 и next_orc=MUS.TRACK_BUILD_STEP (или MUS.LYRIC_BRIEF_FACTORY если нужны слова)

### Step 2: Resolve identity
Приоритет:
1) IDENTITY_TOKEN.artist_display / artist_canonical
2) MUS_BRIEF.artist_name / project_name (если есть в brief)
3) default:
   - artist_display="UE Studios HQ"
   - artist_canonical="UE Studios HQ"

alias_set:
- если есть alias в IDENTITY_TOKEN -> взять
- иначе пусто

brand_family:
- если в identity есть “серия/бренд/лейбл” -> short token
- иначе empty

### Step 3: Build positioning
- genre_primary = STYLE_ROUTE_TOKEN.genre_primary
- mood_axis = STYLE_ROUTE_TOKEN.mood_tags (max 6)
- audience = MUS_BRIEF.audience or ""
- era_hint:
  - если brief содержит “80s/90s/2000s/retro/modern” -> записать
  - иначе empty

one_liner (формула):
- "<genre_primary> <mood_axis[0..2]> для <platform_focus>"

### Step 4: Build concept
title_working:
- если MUS_BRIEF.theme задан -> сжать до 2–4 слов
- иначе:
  - если release_type=playlist -> "<genre_primary> mood pack"
  - если release_type=album|ep -> "<mood_axis[0]> <genre_primary>"
  - если release_type=single_track -> "<mood_axis[0]>"

concept_core:
- 1–2 предложения: что за релиз и в чём крючок
- без указания “копировать артиста”, без точных трек-референсов

story_frame:
- optional: короткая рамка (путь/город/ночь/дорога/свет/память и т.д.) из theme

keywords:
- собрать: genre_primary + mood_axis + 2–4 слова из theme
- максимум 12

banned_topics:
- MUS_BRIEF.constraints.banned_topics + STYLE_ROUTE_TOKEN.instrumentation.banned + explicit_content guardrails

### Step 5: Packaging defaults
cover_direction:
- если MUS_BRIEF.constraints.cover_style задан -> маппинг:
  - "photo" -> photo_real
  - "illustration" -> illustration
  - "minimal" -> minimal
  - иначе auto
- иначе auto

text_policy:
- no_exclamation (всегда)

platform_focus:
- MUS_BRIEF.platform or STYLE_ROUTE_TOKEN.mix_targets.loudness_target mаппинг:
  - club_hot -> streaming|mixed (по brief)
  - cinematic_wide -> youtube|mixed
  - streaming_safe -> streaming

language:
- MUS_BRIEF.language or STYLE_ROUTE_TOKEN.vocal.language or auto

### Step 6: Track plan defaults
slots_count:
- album: 7–12 (default 9)
- ep: 4–6 (default 5)
- playlist: 20–60 (default 30)
- single_track: 1

avg_track_sec:
- slow: 175–220 (default 195)
- mid: 155–205 (default 185)
- fast: 140–195 (default 170)

total_target_min:
- round(slots_count * avg_track_sec / 60)
- если MUS_BRIEF.duration_total_min задан -> принять и повысить lock_level

variability:
- playlist: high
- album: mid
- ep: low|mid
- single_track: low

### Step 7: constraints_lock
hard если задано: duration_total_min, slots_count override, конкретный язык, конкретный cover_direction, explicit_content=false с жёстким баном
medium если задан theme + platform + 1–2 запрета
soft если только genre/mood

### Step 8: handoff_next_keys
- album|ep|playlist -> MUS.ALBUM_TO_TRACK
- single_track:
  - если нужен лирик (vocal.type != none и brief предполагает текст) -> MUS.LYRIC_BRIEF_FACTORY
  - иначе -> MUS.TRACK_BUILD_STEP

---

## [M] KB SCOPE
- KB Inputs: [identity resolution rules, naming compression, release defaults]
- KB Outputs: [ALBUM_CONCEPT_TOKEN]
- KB Boundaries:
  - не добавлять RAW
  - не копировать конкретных артистов, только общие принципы позиционирования

---

## [M] GATES
### PASS
- identity заполнен (artist_display и artist_canonical)
- release_type определён
- track_plan_defaults заполнен
- handoff_next_keys.next_orc заполнен
- decision = PASS

### FAIL
- отсутствует MUS_BRIEF или STYLE_ROUTE_TOKEN

FAIL_CODE:
- UE.FAIL.INPUT_ABSENT | UE.FAIL.RULE_VIOLATION | UE.FAIL.CONCEPT_UNRESOLVED

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff:
  - ALBUM_CONCEPT_TOKEN -> MUS.ALBUM_TO_TRACK
  - ALBUM_CONCEPT_TOKEN -> MUS.METADATA_FACTORY (для раннего черновика метаданных)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 add deterministic identity/concept rules, token schema, defaults, gates
