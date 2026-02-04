FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/06__MUS__LYRIC_DRAFTER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.LYRIC_DRAFTER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_LYRIC_DRAFTER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.LYRIC_DRAFTER.001
- SCOPE_TAGS: [MUS, LYRICS, DRAFT, STRUCTURE, HOOK]
- OUTPUT_ARTIFACT: LYRIC_DRAFT_TOKEN

---

## [M] PURPOSE
Пишет черновик текста песни из LYRIC_BRIEF_TOKEN.
Выдаёт структурированный текст по секциям (V1/CH/V2/BR/OUTRO) с соблюдением:
- формы и длины секций
- “без восклицательных знаков”
- must_include_words и запретов
- понятности и “певучести” в рамках стиля

---

## [M] INPUTS / OUTPUTS
### Inputs
- LYRIC_BRIEF_TOKEN (обязателен)
- OPTIONAL: draft_params
  - variant_count? (default 1)
  - hook_alt_count? (default 2)
  - density? low|mid|high
  - rhyme_strictness? low|mid|high
  - imagery_intensity? low|mid|high
  - avoid_repeats? true|false (default true)

### Outputs
- LYRIC_DRAFT_TOKEN (обязателен при PASS)
- FAIL_CODE? (при FAIL)

---

## [M] TOKEN SCHEMA
### LYRIC_DRAFT_TOKEN (v1)
- route_id: UE.V2.MUS.LYRIC_DRAFT.v1
- brief_ref:
  - route_id: UE.V2.MUS.LYRIC_BRIEF.v1
  - slot_id: <string>
- variants:
  - variant_id: v1|v2|v3|...
    sections:
      - name: V1|CH|V2|BR|OUTRO
        lines: [<string>...]
    hook_candidates:
      - hook_id: h1|h2|h3|...
        lines: [<string>...]
    notes:
      - must_words_used: [<string>...]
      - banned_hits: [<string>...]
      - rhyme_mode_used: <string>
      - issues: [<string>...]
- selection_hint:
  - best_variant_id: <string>
  - best_hook_id: <string>
  - why: <short>
- qa_snapshot:
  - no_exclamation: true
  - structure_ok: true|false
  - must_words_ok: true|false
  - banned_ok: true|false
  - clarity_ok: true|false
- evidence_notes:
  - decision: PASS|FAIL
  - reason: <short>

---

## [M] DRAFT RULES (DETERMINISTIC)
### Preconditions
- Если LYRIC_BRIEF_TOKEN отсутствует -> FAIL (UE.FAIL.INPUT_ABSENT)

### Global hard rules
- Запрещены символы "!" (включая "!!", "!?" и т.п.). Всегда заменять на "." или "…" по смыслу.
- Нельзя копировать известные тексты. Только оригинальная формулировка.
- Если brief.content_policy.banned_words/banned_topics -> не допускать попаданий.

### Section construction rules
- Соблюдать structure_frame.form и structure_frame.lines_target.
- Каждая строка — самостоятельная, без “командных междометий” в начале.
- В хуке:
  - 1 ключевая фраза повторяется (если repeat_hook=yes)
  - простые ударные слова, короткие строки, высокая “запоминаемость”
- В куплетах:
  - развитие темы + конкретика
  - 1–2 образа на 4 строки (не перегружать)
  - избегать тавтологии (avoid_repeats=true)

### Rhyme / meter heuristics (soft constraints)
- rhyme_mode:
  - tight/internal -> больше созвучий в концах строк, допускаются внутренние
  - simple/none -> рифма вторична, важнее смысл и flow
- meter_hint:
  - even -> похожая длина строк
  - swing/free -> допускаются перепады, но без “ломки” чтения

### Must / Banned enforcement
- must_include_words:
  - если список не пуст: распределить минимум 70% слов по песне,
    минимум 1 must-слово в CH или возле CH (если CH есть)
- banned_words:
  - ноль попаданий (case-insensitive), иначе FAIL
- banned_topics:
  - если тема случайно всплыла — переформулировать сразу, без спорных намёков

---

## [M] ALGORITHM (STEP-RUN)
S1) Read brief, lock constraints (no_exclamation, language_policy, content_policy)
S2) Build hook_candidates (hook_alt_count, 6–8 lines max)
S3) Build section skeleton by form
S4) Draft V1/V2/BR/OUTRO using imagery_bank + theme_core + pov
S5) Insert must_include_words distribution
S6) Run self-check (structure, bans, no_exclamation, clarity)
S7) Produce variants list + selection_hint

---

## [M] SELF-CHECKS (QA SNAPSHOT)
- no_exclamation == true
- structure_ok:
  - секции в нужном порядке
  - строки в пределах lines_target ±2
- must_words_ok:
  - если must_words пусто -> true
  - иначе: использовано >= ceil(0.7 * len(must_words)) и минимум 1 в CH/HOOK зоне
- banned_ok:
  - banned_words hits == 0
- clarity_ok:
  - нет бессмысленных строк
  - нет “мутных” метафор без опоры

---

## [M] KB SCOPE
- KB Inputs: [hook patterns, structure templates, rhyme heuristics, repetition avoidance]
- KB Outputs: [LYRIC_DRAFT_TOKEN]
- KB Boundaries:
  - не использовать цитаты защищённых текстов
  - не добавлять RAW/URL
  - не нарушать no_exclamation

---

## [M] GATES
### PASS
- variants[0] существует и содержит секции по форме
- qa_snapshot.no_exclamation = true
- banned_ok = true
- structure_ok = true
- decision = PASS

### FAIL
- нет brief
- найден banned_words hit
- не удаётся собрать структуру

FAIL_CODE:
- UE.FAIL.INPUT_ABSENT | UE.FAIL.RULE_VIOLATION | UE.FAIL.DRAFT_UNRESOLVED

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [MUS.LYRIC_EDITOR, MUS.LYRICS_FOCUS_LOOP, MUS.QA_CHECKS]
- Handoff:
  - LYRIC_DRAFT_TOKEN -> MUS.LYRIC_EDITOR (tighten)
  - LYRIC_DRAFT_TOKEN -> MUS.LYRICS_FOCUS_LOOP (если MODE_HINT=MASTERPIECE или hook слабый)

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 deterministic draft algorithm, must/banned enforcement, hook candidate generation, QA snapshot
