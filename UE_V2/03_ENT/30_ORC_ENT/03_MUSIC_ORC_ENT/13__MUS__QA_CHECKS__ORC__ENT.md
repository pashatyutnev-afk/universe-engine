FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/13__MUS__QA_CHECKS__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.QA_CHECKS.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_QA_CHECKS
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.QA_CHECKS.001

---

## [M] PURPOSE
Запускает единый QA-гейт для музыкальных артефактов на выходе пайпа.
Проверяет: структуру, соответствие правилам текста, целостность концепта, полноту метаданных, упаковку промптов и доказательства теста.
Возвращает PASS или FAIL с точными причинами и списком исправлений.

---

## [M] HARD_RULES
- QA IS A GATE: без PASS нельзя собирать релиз-пак.
- NO EXCLAMATION: символ `!` запрещён в лирике и текстовых материалах артефакта.
- CONCEPT LOCK: тема, POV, тон и жанровые ограничения не должны самовольно меняться на QA-стадии.
- EVIDENCE REQUIRED: если заявлен тест, должен быть evidence pack, иначе FAIL.
- ONE SOURCE OF TRUTH: QA пишет единый REPORT, без разрозненных комментариев.
- DETERMINISTIC OUTPUT: одинаковый вход даёт одинаковый результат и структуру отчёта.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- LOCKS (immutable)
- ARTIFACT_PACK (current)
  - lyrics_final
  - prompt_pack (если есть)
  - metadata_draft
  - generation_notes (если есть)
  - test_doc (если есть)

### Inputs (optional)
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE
- USER_REQUIREMENTS (коротко)
- PLATFORM_TARGETS (например: SUNO, YouTube, Streaming)

### Outputs
- QA_REPORT
- QA_STATUS: PASS | FAIL
- QA_ACTIONS (fix list)
- NEXT_ACTION
  - PASS -> MUS.TRACK_TEST_DOC_GATE или MUS.RELEASE_ASSEMBLER (по ROUTE_TOKEN)
  - FAIL -> возвращение в точный модуль (lyrics, metadata, prompt, mix)

---

## [M] CHECKLIST (canonical)

### A) LYRICS CHECKS
LYRICS_A1: structure_present
- есть секции согласно LOCKS.section_map
- секции не перемешаны, порядок допустим

LYRICS_A2: clarity_and_coherence
- смысл читается, нет случайных скачков темы
- каждая секция связана с общей идеей

LYRICS_A3: singability
- строки поются, нет сверхтяжёлых конструкций
- нет явных “ломанных” стыков фраз

LYRICS_A4: hook_integrity
- хук узнаваем, повторяется по правилам
- нет деградации смысла ради рифмы

LYRICS_A5: banned_items
- соблюдены BANNED_ITEMS
- нет `!`

### B) PROMPT PACK CHECKS
PROMPT_B1: pack_complete
- есть нужные поля для выбранной платформы
- нет конфликтов constraints (темп vs длительность, стиль vs жанр)

PROMPT_B2: constraint_alignment
- соответствует LOCKS и ROUTE_TOKEN
- не добавляет новые жанры или “случайные” инструменты без основания

PROMPT_B3: determinism
- промпт не содержит взаимоисключающих требований
- явно указаны duration, mood, tempo (если нужны)

### C) METADATA CHECKS
META_C1: required_fields
- artist_name, track_title, album/series (если есть), credits, tags
- язык/локаль согласованы

META_C2: naming_rules
- названия читабельны
- нет запрещённых символов в ключевых полях (при необходимости нормализация)

META_C3: consistency
- совпадают artist/album между блоками
- единый стиль капитализации

### D) TEST + EVIDENCE CHECKS
TEST_D1: test_doc_presence
- если стадия требует тест, test_doc обязателен

TEST_D2: evidence_pack
- есть список версий/вариантов или отметка о прогоне
- есть критерии и короткий вывод

### E) PACKAGING CHECKS
PACK_E1: output_pack_ready
- структура пакета соответствует пайпу (lyrics + metadata + prompt + notes)
- есть понятный “что загружать куда”

PACK_E2: release_notes
- есть короткие release notes
- указаны особенности версии (если были варианты)

---

## [M] SCORING + SEVERITY

### Severity levels
- BLOCKER: релиз невозможен
- MAJOR: качество/соответствие падает, релиз нежелателен
- MINOR: косметика, можно релизить при ограничениях

### Scoring (0–5)
- lyrics_quality
- prompt_quality
- metadata_completeness
- evidence_strength
- overall_constraint_fit

PASS threshold (default):
- overall_constraint_fit = 5
- metadata_completeness >= 4
- lyrics_quality >= 4
- BLOCKER = 0

FAST exception:
- допускается evidence_strength = 3, если test_doc не обязателен по ROUTE_TOKEN

---

## [M] QA RUN CANON (step-run)

### Q0) PRECHECK
- verify inputs present
- verify LOCKS present
- normalize punctuation rules (включая запрет `!`)

### Q1) EXEC CHECKLIST
- прогнать A–E
- собрать Findings

### Q2) BUILD QA_REPORT
- summary: PASS/FAIL
- scorecard
- blockers/majors/minors
- fix list с точным “куда вернуть” (module key)

### Q3) ROUTE NEXT
- если FAIL: handoff в точный модуль
- если PASS: next gate по ROUTE_TOKEN

---

## [M] OUTPUT FORMAT (canonical)

QA_REPORT:
- qa_status: PASS|FAIL
- scores:
  - lyrics_quality: <0..5>
  - prompt_quality: <0..5>
  - metadata_completeness: <0..5>
  - evidence_strength: <0..5>
  - overall_constraint_fit: <0..5>
- blockers:
  - id: <B1>
    area: <LYRICS|PROMPT|META|TEST|PACK>
    rule: <rule_name>
    reason: "<one line>"
    fix: "<one line>"
    return_to_key: <MUS.*>
- majors:
  - ...
- minors:
  - ...
- actions_ordered:
  - "<step1>"
  - "<step2>"
- next_action:
  - on_pass: <MUS.*>
  - on_fail: <MUS.*>

---

## [M] FAIL CONDITIONS
- FAIL_CODE: MUS.FAIL.QA.MISSING_INPUTS
- FAIL_CODE: MUS.FAIL.QA.MISSING_LOCKS
- FAIL_CODE: MUS.FAIL.QA.BLOCKER_FOUND
- FAIL_CODE: MUS.FAIL.QA.INVALID_PUNCT
  - найден `!` в лирике или обязательных текстовых блоках
- FAIL_CODE: MUS.FAIL.QA.CONCEPT_DRIFT
  - обнаружен дрейф темы, POV, тона или жанра

---

## [M] GATES
PASS если:
- checklist выполнен
- blockers отсутствуют
- thresholds соблюдены
- отчёт сформирован детерминированно

FAIL если:
- сработало любое FAIL condition

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.TRACK_BUILD_STEP
  - MUS.LYRIC_EDITOR
  - MUS.METADATA_FACTORY
  - MUS.PROMPT_PACKAGER
- Returns to:
  - MUS.TRACK_TEST_DOC_GATE (если нужен тест-док)
  - MUS.RELEASE_ASSEMBLER (если всё готово)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 canonical checklist, scoring, deterministic report, strict punctuation rule
