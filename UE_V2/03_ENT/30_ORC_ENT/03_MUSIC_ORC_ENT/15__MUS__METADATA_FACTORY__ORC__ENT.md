FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/15__MUS__METADATA_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.METADATA_FACTORY.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_METADATA_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.METADATA_FACTORY.001

---

## [M] PURPOSE
Собирает и нормализует метаданные релиза (track/album/single/compilation) в единый METADATA_PACK.
Формирует: title/artist/album, credits, year/date, language, genre/mood tags, short description, release notes, ISRC placeholder policy, cover requirements, platform-ready поля.
Не придумывает канон, а упаковывает его из LOCKS, IDENTITY, ALBUM_PLAN, TRACK_PLAN и USER_REQUIREMENTS.

---

## [M] HARD_RULES
- NO EXCLAMATION: символ `!` запрещён в title, notes, description и любых текстовых полях.
- CANON OVER VIBES: если конфликт — LOCKS/IDENTITY важнее художественных формулировок.
- PLATFORM_SAFE: не использовать запрещённые слова/символы, не превышать лимиты длины.
- CONSISTENCY: Artist/Album/Track пишутся одинаково во всех полях и артефактах.
- NO LEGAL CLAIMS: не заявлять чужие права, фичеринги, лейблы, если это не задано входом.
- DETERMINISTIC: одинаковый вход даёт одинаковый выход (без случайных вариантов названий).

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- LOCKS (genre, mood, tempo, language, banned_items, duration targets)
- IDENTITY_TOKENS (artist_name, brand_label if any, aliases if any)
- RELEASE_CONTEXT
  - release_type: "single|album|ep|compilation|playlist_series"
  - primary_platforms: ["..."] (optional but recommended)
- SOURCE_ARTIFACTS
  - lyrics_final (если есть)
  - prompt_pack_final
  - audio_notes (если есть)
  - album_plan / track_plan (если есть)

### Inputs (optional)
- USER_REQUIREMENTS (title constraints, naming style, explicit/clean preference)
- DATE_HINT (YYYY-MM-DD) или "today"
- COVER_HINTS (image concept tokens)

### Outputs
- METADATA_PACK (normalized)
- META_STATUS: PASS | FAIL
- META_WARNINGS (list)
- NEXT_ACTION (обычно -> MUS.RELEASE_ASSEMBLER)

---

## [M] METADATA_PACK SCHEMA (canonical)

METADATA_PACK:
- core:
  - artist_name: "<string>"
  - release_title: "<string>"          # album/ep/compilation title
  - track_title: "<string>"            # for single or track context
  - release_type: "single|album|ep|compilation|playlist_series"
  - language: "<ru|en|...>"
  - explicit: "clean|explicit|unknown"
  - primary_genre: "<string>"
  - mood_tags: ["<tag>", "<tag>"]
  - tempo_bpm: "<number or empty>"
  - duration_sec: "<number or empty>"
- dates:
  - release_date: "YYYY-MM-DD"
  - year: "YYYY"
- credits:
  - writer: ["<name>"]
  - producer: ["<name>"]
  - performer: ["<name>"]
  - ai_assist: "yes|no|unknown"
  - additional: ["<one line optional>"]
- identifiers:
  - isrc: ""                           # placeholder by policy
  - upc: ""                            # placeholder by policy
- descriptions:
  - short_description: "<max 240 chars>"
  - release_notes: "<max 800 chars>"
  - keywords: ["<k>", "<k>"]
- packaging:
  - cover_art:
    - required: true
    - format: "1:1"
    - min_size_px: 3000
    - text_on_cover: "allowed|not_allowed"   # default not_allowed for clean cover
    - concept_tokens: ["<token>", "<token>"]
  - lyrics_included: true|false
  - credits_included: true|false
- validation:
  - no_exclamation_check: true|false
  - consistency_check: true|false
  - length_limits_check: true|false
  - banned_items_check: true|false

---

## [M] TITLE & NAMING POLICY
- Title source order:
  1) USER_REQUIREMENTS.title
  2) TRACK_PLAN/ALBUM_PLAN title
  3) Derived from hook/theme tokens (только если разрешено ROUTE_TOKEN)
- Запрещено:
  - `!`
  - CAPSLOCK везде (кроме намеренно заданного бренда)
  - спецсимволы мусорного вида (###, ~~~, etc.)
- Рекомендуемо:
  - 2–5 слов
  - ясный образ + уникальный якорь (одно редкое слово)

---

## [M] TAGGING RULES
- primary_genre берётся из LOCKS.genre
- mood_tags берутся из LOCKS.mood и TRACK_BRIEF (если есть)
- keywords:
  - 5–12 слов/фраз
  - без повторов artist_name/release_title
  - без `!`
  - без запрещённых тем из banned_items

---

## [M] DATE POLICY
- Если DATE_HINT задан — использовать его.
- Иначе:
  - release_date = текущая дата рантайма (YYYY-MM-DD) только если явно разрешено ROUTE_TOKEN.AUTO_DATE
  - иначе оставить пустым и поставить warning META.WARN.DATE_MISSING

---

## [M] IDENTIFIERS POLICY
- isrc/upc не генерировать и не выдумывать.
- Разрешено: пусто + comment в warnings, что заполняется на стороне дистрибуции.

---

## [M] VALIDATION CHECKS (gate)

### V1) presence
- есть core.artist_name
- есть release_type
- есть language
- есть primary_genre
- есть release_date или корректный warning

### V2) hygiene
- no_exclamation_check = true (глобально по всем текстовым полям)
- длины:
  - short_description <= 240
  - release_notes <= 800
  - keywords 5..12

### V3) consistency
- artist_name одинаковый во всех местах
- release_title/track_title не противоречат release_type
- language совпадает с LOCKS.language (если задан)

### V4) banned_items
- нет запрещённых слов/тем из LOCKS.banned_items в description/notes/keywords/title

### V5) packaging minimal
- cover_art.required = true
- cover format = 1:1
- concept_tokens не пустые (минимум 2) если ROUTE_TOKEN требует cover concept

---

## [M] PASS / FAIL

PASS если:
- V1–V5 выполнены
- validation flags выставлены
- META_WARNINGS либо пустой, либо только информационный

FAIL если:
- нет artist_name или genre/language
- найден `!`
- нарушены banned_items
- явный конфликт identity (artist_name/brand) с IDENTITY_TOKENS
- title пустой при требовании ROUTE_TOKEN.REQUIRE_TITLE

---

## [M] FAIL CODES
- FAIL_CODE: MUS.FAIL.META.MISSING_REQUIRED
- FAIL_CODE: MUS.FAIL.META.INVALID_PUNCT
- FAIL_CODE: MUS.FAIL.META.BANNED_ITEMS
- FAIL_CODE: MUS.FAIL.META.IDENTITY_CONFLICT
- FAIL_CODE: MUS.FAIL.META.LENGTH_LIMIT

---

## [M] ROUTE BACK (on fail)
- missing_required -> MUS.IDENTITY_BUILD (если artist tokens не собраны) или MUS.ALBUM_TO_TRACK (если нет названий)
- banned_items -> MUS.LYRIC_EDITOR (если слова тянутся из лирики) и повтор METADATA_FACTORY
- identity_conflict -> MUS.IDENTITY_BUILD
- length_limit -> MUS.MERGE_SYNTHESIS (сжать описание) или повтор METADATA_FACTORY с trimming
- invalid_punct -> MUS.LYRIC_EDITOR (если пришло из текста) или повтор METADATA_FACTORY (очистка)

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.IDENTITY_BUILD
  - MUS.ALBUM_TO_TRACK
  - MUS.QA_CHECKS
- Returns to:
  - MUS.RELEASE_ASSEMBLER
  - MUS.RELEASE_PACK (через assembler)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 canonical schema, strict validation, deterministic naming, identifier policy
