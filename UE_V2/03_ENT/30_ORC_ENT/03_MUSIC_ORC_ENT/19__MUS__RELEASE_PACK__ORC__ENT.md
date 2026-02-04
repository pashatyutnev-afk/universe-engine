FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/19__MUS__RELEASE_PACK__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.RELEASE_PACK.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_RELEASE_PACK
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.RELEASE_PACK.001

---

## [M] PURPOSE
Финальная упаковка релиза в OUTPUT_PACK для загрузки/дистрибуции.
Делает пакет самодостаточным: аудио-экспорт цели, лирика, метаданные, кредиты, заметки, чеклист публикации, ссылки на доказательства QA/теста.
После этого пакет можно отдавать в дистрибьютор/платформы без пересборки.

---

## [M] HARD_RULES
- INPUT IS KING: берет только RELEASE_ARTIFACT (из MUS.RELEASE_ASSEMBLER) и приложенные pointers, не выдумывает ничего.
- NO EXCLAMATION: `!` запрещён в любых текстовых полях пакета.
- NO GUARANTEE TEXT: не добавлять “гарантии/обещания” в публичные тексты.
- ONE SOURCE OF TRUTH: identity/metadata фиксируются как есть; если неполно — FAIL или WARN (по правилам).
- OUTPUT-FIRST: генерировать готовые файлы/блоки текста, без “объяснений как сделать”.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- RELEASE_ARTIFACT (from MUS.RELEASE_ASSEMBLER)
- ASSEMBLY_REPORT

### Inputs (optional)
- platform_targets: ["spotify","apple_music","yandex_music","youtube"] (if provided by task)
- release_date (only if provided, else empty)
- isrc_upc (only if provided)
- user_upload_profile (optional)
- distribution_notes (optional)

### Outputs
- OUTPUT_PACK
- PACK_REPORT
- PACK_STATUS: PASS | FAIL
- NEXT_KEY: MUS.PORTFOLIO_PLANNER (optional) or END

---

## [M] OUTPUT_PACK (canonical structure)
OUTPUT_PACK:
- pack_id
- identity:
  - artist
  - project_or_group
- titles:
  - track_title
  - album_title (optional)
- audio_delivery:
  - required_formats: ["wav","mp3"] (or from RELEASE_ARTIFACT)
  - targets:
    - wav: {spec: "...", file_id: "<optional>"}
    - mp3: {spec: "...", file_id: "<optional>"}
  - loudness (optional)
- lyrics_delivery:
  - lyrics_text_final
  - lyrics_plain_txt (generated)
- metadata_delivery:
  - metadata_json (generated)
  - metadata_human_readable (generated)
- credits_delivery:
  - credits_text (only if exists)
- artwork_delivery:
  - cover_file_id (optional)
  - cover_notes (optional)
- compliance:
  - no_exclamation: true
  - fabricated_fields: "forbidden"
- evidence:
  - qa_summary
  - test_doc_id (optional)
  - reports: [assembly_report_id, qa_report_id]
- distribution:
  - platform_targets (optional)
  - upload_checklist (generated)
  - release_notes (generated, sanitized)
- pointers:
  - files: [{kind, file_id, role}]
- status:
  - pass_fail
  - fail_code (optional)
  - warnings: []

---

## [M] PACKAGING STEPS (deterministic)
P0) Validate RELEASE_ARTIFACT present and PASS.
- if RELEASE_ARTIFACT.status.pass_fail != PASS -> FAIL_CODE: MUS.FAIL.PACK.UPSTREAM_FAIL

P1) Sanitize all generated texts:
- remove `!`
- trim whitespace
- ensure no invented fields

P2) Generate deliverables:
- lyrics_plain_txt: чистый текст без разметки
- metadata_json: JSON-структура метаданных (строго из RELEASE_ARTIFACT.metadata)
- metadata_human_readable: короткая карточка для человека (title/artist/album/genre/tags/credits if exist)
- upload_checklist: список шагов загрузки (универсальный) + проверки целостности

P3) Build release_notes:
- если есть METADATA_DRAFT.release_notes -> sanitize and include
- иначе пусто (не выдумывать)

P4) Validate minimal delivery:
- audio formats present in required_formats
- lyrics_text_final non-empty
- metadata has title and artist
- else FAIL_CODE: MUS.FAIL.PACK.MISSING_DELIVERY

P5) Assemble OUTPUT_PACK and PACK_REPORT.

---

## [M] UPLOAD_CHECKLIST (generated template)
UPLOAD_CHECKLIST:
- verify audio export formats match required_formats
- verify file naming: "<artist> - <track_title>.<ext>" (if allowed by platform)
- verify lyrics present and match final version
- verify metadata title/artist correct and locked
- verify cover art attached if required
- verify QA summary included
- verify no `!` characters in public texts
- verify release date exists only if provided by user
- archive OUTPUT_PACK and reports

---

## [M] VALIDATION (gate)
PASS if:
- upstream PASS
- minimal delivery present
- sanitation ok (no `!`)
FAIL otherwise.

---

## [M] FAIL CODES
- MUS.FAIL.PACK.UPSTREAM_FAIL
- MUS.FAIL.PACK.MISSING_DELIVERY
- MUS.FAIL.PACK.HYGIENE

---

## [M] PACK_REPORT (format)
PACK_REPORT:
- route: "<ROUTE_TOKEN short>"
- upstream: "PASS|FAIL"
- generated:
  - lyrics_plain_txt: true|false
  - metadata_json: true|false
  - metadata_human_readable: true|false
  - upload_checklist: true|false
- warnings: ["..."]
- status: "PASS|FAIL"
- fail_code: "<optional>"
- next: "<NEXT_KEY>"

---

## [M] ROUTE BACK (on fail)
- upstream_fail -> return to MUS.RELEASE_ASSEMBLER
- missing_delivery -> return to MUS.TRACK_BUILD_STEP or MUS.METADATA_FACTORY
- hygiene -> return to MUS.LYRIC_EDITOR or rerun sanitation only

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from: MUS.RELEASE_ASSEMBLER
- Returns to: Distribution/upload operator (outside UE) or MUS.PORTFOLIO_PLANNER

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 deterministic packaging, strict upstream gate, generated deliverables templates, stronger hygiene and fail routing
