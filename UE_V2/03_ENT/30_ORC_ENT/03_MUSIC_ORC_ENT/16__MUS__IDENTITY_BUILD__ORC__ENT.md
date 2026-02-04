FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/16__MUS__IDENTITY_BUILD__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.IDENTITY_BUILD.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_IDENTITY_BUILD
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.IDENTITY_BUILD.001

---

## [M] PURPOSE
Собирает и фиксирует идентичность артиста и релиза в виде IDENTITY_TOKENS и IDENTITY_LOCKS.
Устраняет разнобой в написании, решает алиасы, формирует стабильные значения artist_name, brand_label, release_series и credit defaults.
Цель — чтобы во всех дальнейших шагах (metadata, packaging, release) использовались одинаковые канонические строки.

---

## [M] HARD_RULES
- DETERMINISTIC: одинаковый вход даёт одинаковые токены.
- NO EXCLAMATION: символ `!` запрещён во всех текстовых полях.
- NO INVENTED CLAIMS: не выдумывать лейблы, фиты, страны, годы, роли.
- CANON FIRST: если задано пользователем или в LOCKS — это канон.
- ONE PRIMARY: один primary artist_name на релиз, остальное только aliases.
- STABLE CASE: не делать случайный CAPS, сохранять заданный стиль бренда.
- SAFE CHARS: избегать мусорных символов, двойных пробелов, нестандартных кавычек.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- USER_IDENTITY (минимум одно из):
  - artist_name
  - brand_label
  - group_name
  - project_name
- RELEASE_CONTEXT:
  - release_type: "single|album|ep|compilation|playlist_series"
  - language_hint (optional)
- LOCKS (optional but recommended):
  - language
  - banned_items

### Inputs (optional)
- EXISTING_IDENTITY (если уже есть ранее)
- ALIAS_HINTS:
  - artist_aliases: ["..."]
  - translit_rules: "keep|translit|mixed"
- CREDIT_DEFAULTS_HINTS:
  - writer_default
  - producer_default
  - performer_default

### Outputs
- IDENTITY_TOKENS
- IDENTITY_LOCKS
- IDENTITY_STATUS: PASS | FAIL
- IDENTITY_WARNINGS (list)
- NEXT_ACTION (обычно -> MUS.METADATA_FACTORY)

---

## [M] IDENTITY_TOKENS SCHEMA (canonical)

IDENTITY_TOKENS:
- primary:
  - artist_name: "<string>"
  - brand_label: "<string or empty>"
  - project_id: "<stable id token>"
- aliases:
  - artist_aliases: ["<string>"]
  - brand_aliases: ["<string>"]
- localization:
  - language: "<ru|en|...>"
  - translit_mode: "keep|translit|mixed"
  - display_variants:
    - artist_display: "<string>"
    - artist_sort: "<string>"
- series:
  - series_name: "<string or empty>"       # если это линейка сборников
  - series_slot: "<string or empty>"       # например "Vol. 01" по правилам
- credits_defaults:
  - writer: ["<name>"]
  - producer: ["<name>"]
  - performer: ["<name>"]
  - ai_assist: "yes|no|unknown"

---

## [M] IDENTITY_LOCKS (what becomes immutable downstream)
- lock_artist_name: true|false
- lock_brand_label: true|false
- lock_language: true|false
- lock_translit_mode: true|false
- lock_credit_defaults: true|false
- lock_series_rules: true|false

---

## [M] CANON RESOLUTION ORDER
1) USER_IDENTITY.artist_name (если есть)
2) USER_IDENTITY.group_name / project_name (если явно указано как артист)
3) EXISTING_IDENTITY.primary.artist_name (если подтверждён как канон)
4) FAIL если ни один источник не дал артиста

Для brand_label:
1) USER_IDENTITY.brand_label (если есть)
2) EXISTING_IDENTITY.primary.brand_label (если подтверждён)
3) пусто (это не ошибка)

---

## [M] NORMALIZATION RULES
- Trim: убрать пробелы по краям, заменить двойные пробелы на один.
- Quotes: привести кавычки к простым (") или убрать, если они декоративные.
- Punct: убрать `!`, заменить на точку или тире, если нужно.
- Case:
  - если пользователь дал стиль (например ВЕРХНИЙ РЕГИСТР) — сохранять.
  - иначе Title Case для латиницы, нормальный регистр для кириллицы.
- Forbidden:
  - запрещены control chars, эмодзи в ключевых полях (artist_name, brand_label) если ROUTE_TOKEN требует platform_safe.

---

## [M] ALIASES POLICY
- aliases только если:
  - пользователь явно дал альтернативные названия
  - или EXISTING_IDENTITY хранит подтверждённые алиасы
- нельзя:
  - генерить алиасы из воздуха
  - добавлять переводные версии без указания пользователя

---

## [M] TRANSLIT POLICY
- translit_mode по умолчанию: keep
- если пользователь требует англ версию:
  - mixed: artist_display может быть оригинал, artist_sort может быть транслит
- транслит делается только если есть явный ALIAS_HINTS.translit_rules или user requirement в ROUTE_TOKEN

---

## [M] SERIES POLICY (for playlist_series / compilation lines)
- series_name заполняется только если:
  - release_type = playlist_series
  - и пользователь/план дал название серии
- series_slot:
  - формат: "Vol. 01" или "Episode 01" только если это задано правилами серии
  - не изобретать нумерацию без входа

---

## [M] CREDIT DEFAULTS POLICY
- defaults берутся так:
  1) CREDIT_DEFAULTS_HINTS
  2) EXISTING_IDENTITY.credits_defaults
  3) writer/producer/performer = [artist_name]
- ai_assist:
  - default unknown, менять только по явному входу

---

## [M] VALIDATION CHECKS (gate)

### V1) presence
- primary.artist_name не пустой
- project_id не пустой (детерминированный)

### V2) hygiene
- нет `!` в любых строках
- нет двойных пробелов
- нет запрещённых тем из LOCKS.banned_items в artist_name/brand_label (если LOCKS задан)

### V3) stability
- если EXISTING_IDENTITY и lock_artist_name=true, то artist_name должен совпасть, иначе FAIL

### V4) platform_safe (если ROUTE_TOKEN.PLATFORM_SAFE=true)
- artist_name <= 60 chars
- brand_label <= 60 chars
- без мусорных символов

---

## [M] PASS / FAIL

PASS если:
- V1–V4 выполнены
- warnings допустимы (например brand_label пустой)

FAIL если:
- artist_name отсутствует
- конфликт с lock_artist_name
- найден `!` после нормализации
- обнаружены banned_items в ключевых полях

---

## [M] FAIL CODES
- FAIL_CODE: MUS.FAIL.IDENTITY.MISSING_ARTIST
- FAIL_CODE: MUS.FAIL.IDENTITY.LOCK_CONFLICT
- FAIL_CODE: MUS.FAIL.IDENTITY.INVALID_PUNCT
- FAIL_CODE: MUS.FAIL.IDENTITY.BANNED_ITEMS
- FAIL_CODE: MUS.FAIL.IDENTITY.PLATFORM_LIMIT

---

## [M] ROUTE BACK (on fail)
- missing_artist -> MUS.GROUP_TO_ALBUM (если нужен выбор артист-проекта) или запрос USER_IDENTITY
- lock_conflict -> MUS.MERGE_SYNTHESIS (если надо выбрать канон из вариантов) или ручной выбор
- invalid_punct -> повтор MUS.IDENTITY_BUILD (очистка входа)
- banned_items -> правка USER_IDENTITY и повтор
- platform_limit -> повтор MUS.IDENTITY_BUILD (укоротить display variants)

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.GROUP_TO_ALBUM
  - USER (identity hints)
- Returns to:
  - MUS.METADATA_FACTORY
  - MUS.RELEASE_ASSEMBLER (через metadata)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 deterministic schema, locks, platform-safe validation, strict punctuation policy
