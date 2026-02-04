FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/02__MUS__GENRE_STYLE_ROUTER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.GENRE_STYLE_ROUTER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_GENRE_STYLE_ROUTER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.GENRE_STYLE_ROUTER.001
- SCOPE_TAGS: [MUS, ROUTER, STYLE, CONSTRAINTS]
- OUTPUT_ARTIFACT: STYLE_ROUTE_TOKEN

---

## [M] PURPOSE
Детерминированно маршрутизирует музыкальный запрос в жанр/поджанр/стилевой профиль.
Выдаёт ограничения (tempo band, energy band, instrumentation profile, vocal profile, structure defaults), чтобы все следующие модули работали в одном “коридоре”.

---

## [M] INPUTS / OUTPUTS
### Inputs
- MUS_BRIEF (обязателен)
  - target: single_track|ep|album|playlist
  - mood?: free text
  - genre?: free text
  - energy?: low|mid|high|auto
  - tempo_hint?: slow|mid|fast|auto
  - language?: ru|en|other
  - constraints?: { duration_sec?, platform?, explicit_tempo_bpm?, vocal?, instruments?, era?, bans? }
- SOURCE_POLICY_TOKEN (обязателен)
  - named_artist_as_principle_only
  - specificity_cap
  - banned_request_flags

### Outputs
- STYLE_ROUTE_TOKEN (обязателен при PASS)
- FAIL_CODE? (при FAIL)

---

## [M] TOKEN SCHEMA
### STYLE_ROUTE_TOKEN (v1)
- route_id: UE.V2.MUS.STYLE_ROUTE.v1
- domain: MUS
- genre_primary: <string>
- genre_secondary: <string|empty>
- mood_tags: [<string>...]
- tempo:
  - bpm_target: <int|empty>
  - bpm_min: <int>
  - bpm_max: <int>
  - band: slow|mid|fast
- energy:
  - band: low|mid|high
  - notes: <short>
- instrumentation:
  - core: [<string>...]
  - optional: [<string>...]
  - banned: [<string>...]
- vocal:
  - type: none|male|female|duet|choir|spoken|auto
  - delivery: intimate|neutral|power|airy|gritty|auto
  - language: ru|en|other|auto
- structure_defaults:
  - form: verse_chorus|aaba|through_composed|loop_based|auto
  - sections: [intro, verse, chorus, verse, chorus, bridge, chorus, outro] (example)
  - hook_density: low|mid|high
- mix_targets:
  - loudness_target: streaming_safe|club_hot|cinematic_wide
  - low_end: tight|wide|sub_heavy
  - brightness: dark|balanced|bright
- constraints_lock:
  - lock_level: soft|medium|hard
  - reasons: [<string>...]
- handoff_next_keys:
  - next_orc: MUS.GROUP_TO_ALBUM|MUS.ALBUM_TO_TRACK|MUS.LYRIC_BRIEF_FACTORY|MUS.TRACK_BUILD_STEP
- evidence_notes:
  - inputs_seen: [genre, mood, energy, tempo_hint, constraints]
  - decision: PASS|FAIL
  - reason: <short>

---

## [M] ROUTING RULES (deterministic)
### Step 0: Pre-check
- Если SOURCE_POLICY_TOKEN.banned_request_flags содержит COPY_EXACT|MELODY_MATCH|LYRICS_REWRITE -> FAIL (handoff to policy rewrite outside this module)
- Если MUS_BRIEF отсутствует -> FAIL

### Step 1: Normalize (strings -> tags)
- genre_text = lower(trim(MUS_BRIEF.genre or ""))
- mood_text = lower(trim(MUS_BRIEF.mood or ""))
- tempo_hint = MUS_BRIEF.tempo_hint or "auto"
- energy_hint = MUS_BRIEF.energy or "auto"

### Step 2: Choose genre_primary (priority)
1) Если genre_text явно содержит один из canonical buckets (см. таблицу ниже) -> взять его
2) Иначе если mood_text сильно указывает на bucket -> взять его
3) Иначе default -> "pop"

### Step 3: Determine tempo band
- Если explicit_tempo_bpm задан -> band по bpm, bpm_min=bpm-5, bpm_max=bpm+5
- Иначе:
  - slow: 70–95
  - mid: 96–125
  - fast: 126–160
- tempo_hint overrides:
  - slow -> slow, mid -> mid, fast -> fast

### Step 4: Determine energy band
- Если energy_hint задан -> использовать
- Иначе:
  - slow -> low|mid (по mood_tags)
  - mid -> mid
  - fast -> high|mid

### Step 5: Build constraints_lock
- hard если задан explicit_tempo_bpm, duration_sec, platform, vocal.type, core instruments
- medium если задан genre_text и 1–2 строгих ограничения
- soft если только mood

### Step 6: Decide handoff_next_keys
- target=album|playlist -> MUS.GROUP_TO_ALBUM
- target=single_track -> если нужны слова -> MUS.LYRIC_BRIEF_FACTORY, иначе MUS.TRACK_BUILD_STEP
- target=ep -> MUS.GROUP_TO_ALBUM

---

## [M] CANONICAL BUCKETS (minimal set)
- pop
- hiphop
- rnb
- rock
- metal
- electronic
- house
- techno
- trance
- synthwave
- edm
- drum_and_bass
- lo-fi
- ambient
- cinematic
- folk
- reggae
- latin
- kpop
- phonk

---

## [M] DEFAULT PROFILES (by bucket)
### pop
- instrumentation.core: [drums, bass, synth/piano]
- structure_defaults.form: verse_chorus
- hook_density: high
- mix_targets: streaming_safe, low_end=tight, brightness=balanced

### hiphop
- instrumentation.core: [drum_machine, bass, sample_or_keys]
- vocal.type: male|female|auto, delivery=neutral
- structure_defaults.form: loop_based
- hook_density: mid
- mix_targets: streaming_safe, low_end=sub_heavy, brightness=dark|balanced

### electronic
- instrumentation.core: [drums, bass, synths]
- structure_defaults.form: auto
- hook_density: mid
- mix_targets: club_hot|streaming_safe, brightness=bright|balanced

### lo-fi
- instrumentation.core: [soft_drums, bass, keys]
- structure_defaults.form: loop_based
- hook_density: low
- mix_targets: streaming_safe, brightness=dark

### cinematic
- instrumentation.core: [strings, pads, percussion]
- structure_defaults.form: through_composed
- hook_density: low|mid
- mix_targets: cinematic_wide, low_end=wide, brightness=balanced

---

## [M] OUTPUT BUILD (assembly)
STYLE_ROUTE_TOKEN собирается так:
- genre_primary из Step 2
- genre_secondary: если genre_text содержит уточнение (например "pop rock") -> secondary="rock"
- mood_tags: из mood_text split по запятым/точкам, максимум 6 тегов
- tempo, energy из Step 3-4
- instrumentation/mix/structure: взять default по bucket и применить constraints overrides:
  - если пользователь явно запретил инструмент -> убрать и добавить в banned
  - если пользователь явно требует инструмент -> добавить в core и повысить lock_level
- vocal:
  - если MUS_BRIEF.constraints.vocal задан -> принять и lock_level минимум medium
  - иначе auto
- handoff_next_keys из Step 6
- evidence_notes.decision = PASS

---

## [M] KB SCOPE
- KB Inputs: [bucket rules, default profiles, tempo/energy bands]
- KB Outputs: [STYLE_ROUTE_TOKEN]
- KB Boundaries:
  - не ссылаться на конкретные треки как на шаблон
  - не выдавать “копию” стиля конкретного артиста, только высокоуровневые принципы

---

## [M] GATES
### PASS
- STYLE_ROUTE_TOKEN сформирован
- constraints_lock заполнен
- handoff_next_keys заполнен
- decision = PASS

### FAIL
- нет MUS_BRIEF
- SOURCE_POLICY_TOKEN блокирует запрос
- не удалось определить bucket даже по default (теоретически не должно случаться)

FAIL_CODE:
- UE.FAIL.INPUT_ABSENT | UE.FAIL.RULE_VIOLATION | UE.FAIL.ROUTER_UNRESOLVED

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff:
  - STYLE_ROUTE_TOKEN -> MUS.GROUP_TO_ALBUM or MUS.LYRIC_BRIEF_FACTORY or MUS.TRACK_BUILD_STEP
  - STYLE_ROUTE_TOKEN -> MUS.PROMPT_PACKAGER (как стабильный коридор ограничений)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 add deterministic rules, token schema, bucket defaults, lock logic
