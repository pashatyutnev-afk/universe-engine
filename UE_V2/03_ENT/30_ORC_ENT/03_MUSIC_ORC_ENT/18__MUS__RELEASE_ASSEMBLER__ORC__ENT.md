FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/18__MUS__RELEASE_ASSEMBLER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.RELEASE_ASSEMBLER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_RELEASE_ASSEMBLER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.RELEASE_ASSEMBLER.001

---

## [M] PURPOSE
Собирает релизный артефакт из FINAL_PACK и связанных результатов: аудио-цели, лирика, метаданные, кредиты, заметки.
Цель — подготовить единый RELEASE_ARTIFACT, который можно сразу передать в упаковку и дистрибуцию без догадок и без пропусков.
Фокус: консистентность identity и метаданных, правильные форматы, наличие обязательных файлов и evidence.

---

## [M] HARD_RULES
- NO EXCLAMATION: символ `!` запрещён в любых текстовых полях.
- NO FABRICATION: не придумывать факты про релиз, права, лейблы, фиты, даты.
- LOCKS WIN: IDENTITY_LOCKS и STYLE_LOCKS имеют приоритет над любыми вариантами.
- TRACEABLE: в выходе должен быть ASSEMBLY_REPORT с перечнем включённых элементов.
- STRICT COMPLETENESS: если обязательного не хватает — FAIL, а не "примерно готово".
- SAFE DEFAULTS: если формат не указан, выбирать безопасные и массово совместимые.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- FINAL_PACK (from MUS.MERGE_SYNTHESIS)
- TARGET_SPEC:
  - distribution_mode: "distro|youtube|both"
  - platform_safe: true|false
  - audio_targets: ["wav","mp3", ...] (optional, overrides)
- LOCKS:
  - IDENTITY_LOCKS
  - STYLE_LOCKS (optional)
  - QA_LOCKS (optional)

### Inputs (optional)
- SOURCE_AUDIO_POINTERS (если есть путь/идентификатор исходников)
- COVER_POINTER (если есть обложка)
- TEST_EVIDENCE (если тест-док уже собран)
- CREDITS_HINTS (если пользователь дал доп. кредиты)

### Outputs
- RELEASE_ARTIFACT
- ASSEMBLY_REPORT
- ASSEMBLY_STATUS: PASS | FAIL
- ASSEMBLY_WARNINGS
- NEXT_ACTION (обычно -> MUS.RELEASE_PACK)

---

## [M] RELEASE_ARTIFACT (canonical schema)

RELEASE_ARTIFACT:
- identity:
  - artist: "<string>"
  - project: "<string or empty>"              # если используете бренд/проект
  - identifiers: {uid: "<...>", route: "<...>"}
  - locks_applied: ["..."]
- audio:
  - masters:
    - {format: "wav", spec: "24bit|16bit", sr: "44.1|48", file_id: "<id|empty>"}
    - {format: "mp3", spec: "320k", file_id: "<id|empty>"}
  - stems: [{name: "<string>", file_id: "<id|empty>"}]
  - notes: ["..."]
- lyrics:
  - lyrics_txt: "<text>"
  - language: "<string|auto>"
  - structure: {verses: n, chorus: n, bridge: yes|no}
- metadata:
  - title: "<string>"
  - artist: "<string>"
  - album: "<string>"
  - release_type: "single|ep|album|compilation"
  - tags: ["..."]
  - credits:
    - writers: ["..."]
    - producers: ["..."]
    - performers: ["..."]
    - ai_assist: ["..."]                     # опционально, без спорных утверждений
  - notes_public: "<string>"
  - notes_internal: "<string>"
- cover:
  - cover_required: true|false
  - cover_file_id: "<id|empty>"
  - cover_specs: {min_size_px: 3000, aspect: "1:1"}
- packaging:
  - outputs_expected: ["audio_wav","audio_mp3","lyrics_txt","metadata_json","cover"]
  - checksums: [{file: "<name>", sha256: "<optional>"}]
- evidence:
  - qa_passed: true|false
  - test_doc_attached: true|false
  - test_doc_id: "<id|empty>"
  - issues: ["..."]

---

## [M] ASSEMBLY STEPS (deterministic)

S1) Validate minimal inputs
- FINAL_PACK present
- identity/title/artist present
- artifact_target coverage ok (full_pack or distro relevant)
If missing -> FAIL_CODE: MUS.FAIL.ASM.MISSING_INPUT

S2) Apply locks
- identity fields forced from IDENTITY_LOCKS or IDENTITY_TOKENS
- style notes do not override locks
Record locks_applied list.

S3) Determine output targets
Default:
- distribution_mode=distro -> ["wav","mp3"] + "metadata_json" + "lyrics_txt" + "cover_if_required"
- youtube -> ["mp3"] + "lyrics_txt" + "metadata_json" + "cover_if_required"
If TARGET_SPEC.audio_targets provided -> use it (but keep wav preferred for distro).

S4) Compose metadata block
- normalize title/artist/album lengths
- tags <= 20 if platform_safe=true
- remove illegal characters and `!`
- credits: keep minimal, do not invent

S5) Compose audio block
- if masters not present as file ids -> allow placeholders as empty file_id but mark as warning
- always specify intended formats and specs

S6) Cover requirements
- cover_required true for distro by default
- if missing cover pointer -> warning for youtube, FAIL for distro if QA_LOCKS demand cover

S7) Evidence link
- if TEST_EVIDENCE present -> attach id, set test_doc_attached true
- else -> mark test_doc_attached false and warning, unless QA_LOCKS require it (then FAIL)

S8) Emit RELEASE_ARTIFACT + ASSEMBLY_REPORT

---

## [M] PLATFORM SAFE NORMALIZATION
Если platform_safe=true:
- title <= 60 chars
- artist <= 60 chars
- album <= 60 chars
- tags count <= 20
- notes_public <= 500 chars
- remove `!`
- collapse whitespace, remove double punctuation

---

## [M] VALIDATION CHECKS (gate)

### V1) required fields
- metadata.title present
- metadata.artist present
- lyrics.lyrics_txt present (если target включает lyrics)
- audio.masters contains at least one target format for intended mode

### V2) locks respected
- identity fields match locks
- no locked fields overwritten

### V3) hygiene
- no `!`
- no fabricated claims in notes_public

### V4) distro readiness (if distribution_mode includes distro)
- wav target present in outputs_expected OR explicit override given
- cover_required true and cover_file_id not empty unless explicitly allowed by locks

PASS если V1–V3 ok, и V4 ok когда нужен.
FAIL если V1 или V2 fail, или V4 fail в режиме distro.

---

## [M] FAIL CODES
- FAIL_CODE: MUS.FAIL.ASM.MISSING_INPUT
- FAIL_CODE: MUS.FAIL.ASM.LOCK_VIOLATION
- FAIL_CODE: MUS.FAIL.ASM.COVER_REQUIRED_MISSING
- FAIL_CODE: MUS.FAIL.ASM.EVIDENCE_REQUIRED_MISSING
- FAIL_CODE: MUS.FAIL.ASM.HYGIENE

---

## [M] ASSEMBLY_REPORT (format)
ASSEMBLY_REPORT:
- route: "<ROUTE_TOKEN short>"
- outputs_expected: ["..."]
- included:
  - audio: ["wav","mp3","stems(optional)"]
  - lyrics: ["lyrics_txt"]
  - metadata: ["metadata_json"]
  - cover: ["cover"]
  - evidence: ["test_doc(optional)"]
- locks_applied: ["..."]
- warnings: ["..."]
- status: "PASS|FAIL"
- fail_code: "<optional>"

---

## [M] ROUTE BACK (on fail)
- missing_input -> MUS.MERGE_SYNTHESIS (rebuild FINAL_PACK)
- lock_violation -> MUS.IDENTITY_BUILD or MUS.GENRE_STYLE_ROUTER (repair locks) then retry
- cover_required_missing -> add cover source then retry
- evidence_required_missing -> MUS.TRACK_TEST_DOC_GATE then retry
- hygiene -> rerun assembly with sanitation only

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.MERGE_SYNTHESIS
  - MUS.TRACK_TEST_DOC_GATE (optional)
- Returns to:
  - MUS.RELEASE_PACK

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 deterministic steps, distro vs youtube targets, validation gates, stricter cover and evidence handling
