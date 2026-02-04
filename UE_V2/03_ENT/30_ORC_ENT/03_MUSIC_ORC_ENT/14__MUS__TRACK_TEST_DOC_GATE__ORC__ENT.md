FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/14__MUS__TRACK_TEST_DOC_GATE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.TRACK_TEST_DOC_GATE.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_TRACK_TEST_DOC_GATE
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.TRACK_TEST_DOC_GATE.001

---

## [M] PURPOSE
Гейт перед релизом, который требует и валидирует TEST_DOC.
Создаёт (если можно) или проверяет (если уже есть) тестовый документ: что именно прогоняли, какие варианты сравнивали, по каким критериям, и почему выбран финал.
Блокирует релиз при отсутствии доказательств или при конфликте с LOCKS и QA_REPORT.

---

## [M] HARD_RULES
- TEST DOC IS EVIDENCE: без TEST_DOC релиз не проходит, если ROUTE_TOKEN требует тест.
- NO EXCLAMATION: символ `!` запрещён в TEST_DOC и текстовых блоках.
- LOCKS IMMUTABLE: жанр, тон, POV, ключевые ограничения не переписываются в тесте.
- TRACEABLE CHOICES: выбор финальной версии должен ссылаться на критерии и наблюдения, а не на эмоции.
- MINIMUM NOISE: TEST_DOC короткий, но доказательный. Никаких длинных эссе.
- DETERMINISTIC TEMPLATE: одинаковый вход даёт одинаковую структуру документа.

---

## [M] WHEN REQUIRED
Гейт включается если:
- ROUTE_TOKEN.REQUIRED_CHECKS содержит TEST_DOC
или
- MODE_HINT = RELEASE_READY | MASTERPIECE
или
- QA_REPORT.evidence_strength < 4 (и требуется укрепить доказательность)

Гейт может быть пропущен если:
- ROUTE_TOKEN явно разрешает NO_TEST_DOC
и
- MODE_HINT = FAST
и
- QA_REPORT без блокеров

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- LOCKS (immutable)
- QA_REPORT (последний)
- ARTIFACT_PACK
  - lyrics_final
  - prompt_pack
  - metadata_draft
  - generation_notes (если есть)
  - variants_summary (если есть)

### Inputs (optional)
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE
- PLATFORM_TARGETS
- USER_REQUIREMENTS (коротко)

### Outputs
- TEST_DOC (created or validated)
- TEST_STATUS: PASS | FAIL
- TEST_FINDINGS (короткий список)
- NEXT_ACTION
  - PASS -> MUS.RELEASE_ASSEMBLER (обычно)
  - FAIL -> возврат в точный модуль (MUS.*)

---

## [M] TEST_DOC TEMPLATE (canonical)

TEST_DOC:
- header:
  - route_token_id: "<id or short token>"
  - date: "YYYY-MM-DD"
  - mode_hint: "<FAST|RELEASE_READY|MASTERPIECE>"
  - platform_targets: ["..."]
- locks_snapshot:
  - genre: "<...>"
  - mood: "<...>"
  - tempo: "<...>"
  - duration: "<...>"
  - pov: "<...>"
  - banned_items: ["..."]
- candidates:
  - id: "A"
    type: "audio|lyrics|prompt|mix|full"
    notes: "<one line>"
  - id: "B"
    type: "audio|lyrics|prompt|mix|full"
    notes: "<one line>"
- criteria (0..5):
  - hook_catchiness
  - lyrical_clarity
  - energy_fit
  - mix_balance (если есть аудио)
  - uniqueness
  - platform_fit
- results:
  - candidate_scores:
    - id: "A"
      scores: {hook_catchiness: 0..5, lyrical_clarity: 0..5, energy_fit: 0..5, mix_balance: 0..5, uniqueness: 0..5, platform_fit: 0..5}
      observations: ["<one line>", "<one line>"]
    - id: "B"
      scores: { ... }
      observations: [ ... ]
  - winner:
    - id: "A|B|..."
    - reason: "<one line>"
    - kept_from_others: ["<optional one line>"]
- qa_alignment:
  - blockers_resolved: true|false
  - no_exclamation_check: true|false
  - concept_drift_check: true|false
- next:
  - proceed_to: "<MUS.RELEASE_ASSEMBLER|MUS.MERGE_SYNTHESIS|...>"
  - notes: "<one line>"

---

## [M] VALIDATION CHECKS (gate)

### V1) presence
- TEST_DOC существует если требуется
- содержит header, locks_snapshot, candidates, criteria, results, qa_alignment, next

### V2) locks_alignment
- locks_snapshot совпадает с LOCKS (по ключевым полям)
- нет дрейфа жанра/тона/POV/ограничений

### V3) qa_alignment
- QA_REPORT.blockers отсутствуют или помечены resolved с доказательством
- no_exclamation_check = true
- concept_drift_check = true

### V4) evidence_strength
- есть минимум 2 кандидата (если не указано иначе в ROUTE_TOKEN)
- критерии заполнены, есть хотя бы 3 наблюдения суммарно
- winner выбран и объяснён

### V5) hygiene
- нет `!`
- краткость: каждая заметка 1 строка
- нет противоречий (winner не может иметь ниже по всем главным критериям без объяснения)

---

## [M] PASS / FAIL

PASS если:
- все V1–V5 выполнены
- выбран победитель и указан next.step
- QA alignment подтверждён

FAIL если:
- отсутствует TEST_DOC при требовании
- найден `!`
- дрейф концепта или LOCKS mismatch
- отсутствуют критерии или winner
- QA blockers не закрыты

---

## [M] FAIL CODES
- FAIL_CODE: MUS.FAIL.TESTDOC.MISSING_REQUIRED
- FAIL_CODE: MUS.FAIL.TESTDOC.INVALID_PUNCT
- FAIL_CODE: MUS.FAIL.TESTDOC.LOCKS_MISMATCH
- FAIL_CODE: MUS.FAIL.TESTDOC.NO_WINNER
- FAIL_CODE: MUS.FAIL.TESTDOC.QA_BLOCKERS_UNRESOLVED

---

## [M] ROUTE BACK (on fail)
Возвращать строго в модуль по причине:
- locks_mismatch -> MUS.GENRE_STYLE_ROUTER (если неверные constraints) или MUS.IDENTITY_BUILD (если дрейф идентичности)
- qa_blockers_unresolved -> MUS.QA_CHECKS
- lyrics issues -> MUS.LYRIC_EDITOR или MUS.LYRICS_FOCUS_LOOP
- prompt issues -> MUS.PROMPT_PACKAGER
- metadata issues -> MUS.METADATA_FACTORY
- need merge between candidates -> MUS.MERGE_SYNTHESIS

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.QA_CHECKS
  - MUS.MERGE_SYNTHESIS (если делали сборку из вариантов)
- Returns to:
  - MUS.RELEASE_ASSEMBLER (обычно)
  - MUS.TRACK_BUILD_STEP (если тест выявил фундаментальные проблемы)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 canonical template, validation checks, deterministic rules, strict punctuation rule
