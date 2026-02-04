FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/20__MUS__PORTFOLIO_PLANNER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.PORTFOLIO_PLANNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PORTFOLIO_PLANNER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.PORTFOLIO_PLANNER.001

---

## [M] PURPOSE
Планирует портфель релизов: серии, тематики, разнообразие жанров/настроений, ритм публикаций, правила “что делать дальше”.
Работает после релиза (OUTPUT_PACK) и строит понятный, устойчивый план без случайностей.

---

## [M] HARD_RULES
- INPUT IS KING: не выдумывать новые факты про аудиторию/рынок/метрики, если их нет во входе.
- NO EXCLAMATION: символ `!` запрещён в выходных текстах.
- NO GUARANTEE TEXT: никаких обещаний “точно залетит”, “гарантия результата”.
- DETERMINISTIC: одинаковый вход -> одинаковый план (использовать фиксированные правила выбора).
- SHORT BUT ACTIONABLE: план без лирики, только шаги и параметры.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- OUTPUT_PACK (from MUS.RELEASE_PACK) OR RELEASE_ARTIFACT (from MUS.RELEASE_ASSEMBLER)
- PACK_REPORT (if exists)

### Inputs (optional)
- cadence_hint: "daily" | "weekly" | "biweekly" | "monthly"
- portfolio_mode: "single_artist" | "multi_project" | "mood_library"
- constraints:
  - platform_targets
  - max_parallel_series
  - preferred_genres
  - forbidden_genres
  - language_rules
  - naming_rules
- current_catalog_snapshot:
  - recent_releases: [{title, date, genre, mood}]
  - active_series: [{series_id, theme, rules}]
  - backlog: [{concept_id, status}]

### Outputs
- PORTFOLIO_PLAN
- NEXT_RELEASE_BRIEF (optional)
- PLAN_REPORT
- NEXT_KEY: MUS.GROUP_TO_ALBUM | MUS.ALBUM_TO_TRACK | END

---

## [M] PORTFOLIO_PLAN (canonical)
PORTFOLIO_PLAN:
- portfolio_id
- mode: "<portfolio_mode>"
- cadence:
  - target: "<cadence_hint or default>"
  - next_release_window: "<relative>"
- series:
  - series_list:
    - series_id
    - theme
    - genre_band
    - mood_band
    - tempo_band
    - rules:
      - title_style
      - recurring_motifs
      - instrumentation_limits (optional)
- diversification_rules:
  - avoid_repeat_genre_within_n: 2
  - avoid_repeat_mood_within_n: 2
  - max_same_tempo_band_in_row: 2
- next_actions:
  - action_queue:
    - step: 1
      key: "<NEXT_KEY>"
      intent: "<one-line>"
      parameters:
        genre: ""
        mood: ""
        bpm_range: ""
        vibe_refs: []
- catalog_update:
  - add_release: true
  - update_series_stats: true
- governance:
  - deterministic_seed: "<derived from artist/project token>"

---

## [M] DEFAULTS (when optional inputs missing)
- cadence_hint default: weekly
- portfolio_mode default:
  - if identity indicates one artist/group -> single_artist
  - else -> mood_library
- max_parallel_series default: 2
- series themes default library:
  - S1: "Night Drive" (mid tempo, darker tone)
  - S2: "Bright Day" (upbeat, clean tone)
(если у пользователя уже есть бренд/серии во входе — использовать их вместо дефолтов)

---

## [M] DETERMINISTIC ROUTING LOGIC
R0) Extract identity token:
- from OUTPUT_PACK.identity.artist/project_or_group
- if missing -> PLAN_REPORT.warn + proceed with "UNKNOWN_ID"

R1) Choose portfolio_mode:
- if provided -> use it
- else:
  - if project_or_group exists -> single_artist
  - else -> mood_library

R2) Choose cadence:
- if cadence_hint provided -> use it
- else -> weekly

R3) Build/Update series list:
- if current_catalog_snapshot.active_series exists -> keep, cap by max_parallel_series
- else create up to max_parallel_series defaults

R4) Diversification:
- pick next slot to avoid repeats using diversification_rules against recent_releases
- if no snapshot -> alternate series S1/S2

R5) Compose NEXT_RELEASE_BRIEF:
- produces a minimal brief for the next pipeline handoff:
  - target series_id
  - genre_band, mood_band, tempo_band
  - title_style constraints
  - banned items (if any)

R6) Select NEXT_KEY:
- if mode implies album flow -> MUS.GROUP_TO_ALBUM
- else -> MUS.ALBUM_TO_TRACK
(если нет входных признаков альбома — по умолчанию MUS.ALBUM_TO_TRACK)

---

## [M] NEXT_RELEASE_BRIEF (format)
NEXT_RELEASE_BRIEF:
- identity:
  - artist
  - project_or_group
- target_series:
  - series_id
  - theme
- style_constraints:
  - genre_band
  - mood_band
  - tempo_band
- naming_constraints:
  - title_style
- banned:
  - words: []
  - symbols: ["!"]
- notes: ""

---

## [M] VALIDATION (gate)
PASS если:
- сформирован PORTFOLIO_PLAN
- присутствует action_queue (минимум 1 действие)
FAIL если:
- отсутствует любой обязательный объект (plan empty) -> MUS.FAIL.PORTFOLIO.EMPTY

---

## [M] FAIL CODES
- MUS.FAIL.PORTFOLIO.EMPTY
- MUS.FAIL.PORTFOLIO.MISSING_IDENTITY (hard only if strict mode is required by task)

---

## [M] PLAN_REPORT (format)
PLAN_REPORT:
- identity: "<artist/project token>"
- mode: "<portfolio_mode>"
- cadence: "<cadence>"
- series_count: N
- next_key: "<NEXT_KEY>"
- warnings: ["..."]
- status: "PASS|FAIL"
- fail_code: "<optional>"

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA] (only for catalog completeness checks if provided)
- Receives from: MUS.RELEASE_PACK / MUS.RELEASE_ASSEMBLER
- Returns to: MUS.GROUP_TO_ALBUM or MUS.ALBUM_TO_TRACK

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 deterministic routing, portfolio defaults, diversification rules, NEXT_RELEASE_BRIEF, validation/fail codes
