FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/12__MUS__LYRICS_FOCUS_LOOP__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.LYRICS_FOCUS_LOOP.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_LYRICS_FOCUS_LOOP
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.LYRICS_FOCUS_LOOP.001

---

## [M] PURPOSE
Итеративно доводит текст до финала без смены концепта трека.
Фокус: смысл, образность, поток речи, читаемость, структура секций, повторяемость хуков, чистота формулировок.
Держит стиль и голос персонажа стабильными. Контролирует запреты и формальные правила текста.

---

## [M] HARD_RULES
- CONCEPT LOCK: тема, POV, главный образ, жанр-стиль и тональность подачи фиксированы на входе.
- STRUCTURE LOCK: набор секций (verse/chorus/bridge/outro) не меняем, допускается только микро-перестановка строк внутри секции.
- NO EXCLAMATION: символ `!` запрещён в любых строках. При обнаружении заменить на точку, тире или многоточие.
- NO FILLER: избегать пустых слов, клише и общих фраз без картинки.
- ONE-EDIT-PASS: в одной итерации правим 1 доминирующую проблему, максимум 2 если связаны.
- KEEP HOOK: хук должен оставаться узнаваемым. Меняем максимум 20 процентов слов в хуке за итерацию.
- EVIDENCE REQUIRED: каждая итерация пишет scorecard и rationale, фиксирует winner.

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- LOCKS (immutable)
  - theme
  - POV
  - voice_tone
  - genre/substyle
  - section_map (structure)
- LYRIC_BRIEF (from MUS.LYRIC_BRIEF_FACTORY)
- DRAFT_LYRICS (current version)

### Inputs (optional)
- USER_FEEDBACK (например: “слишком просто”, “нужно больше образов”, “сделай мрачнее”)
- BANNED_ITEMS (extra banned words/topics)
- RHYME_HINT (none | light | consistent)
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE

### Outputs
- LYRICS_WINNER
  - lyrics_id
  - change_focus
  - applied_moves (bullets)
  - hook_preserved_note
- LYRICS_EVIDENCE_PACK
  - variants_list
  - scorecards
  - decision_rationale (1–2 строки)
- NEXT_ACTION
  - return_to: MUS.TRACK_BUILD_STEP
  - or handoff: MUS.LYRIC_EDITOR (если нужен жёсткий тех-редакт)

---

## [M] QUALITY TARGETS (canonical)
LYRICS_TARGETS:
- meaning_clarity: смысл понятен с первого прослушивания
- imagery_density: в каждой секции есть минимум 1 сильный образ
- singability: фразы поются, нет ломанных ударений и тяжёлых стыков
- hook_strength: хук короткий, липкий, повторяемый
- coherence: все секции про одно, нет случайных скачков
- originality: минимум клише, максимум своих формулировок
- language_clean: без мусора и лишних слов

---

## [M] LOOP CANON (step-run)

### L0) PRECHECK
- verify LOCKS present
- verify LYRIC_BRIEF present
- verify DRAFT_LYRICS present
- normalize: удалить `!` и иные агрессивные знаки, если они ломают подачу
- detect section boundaries (verse/chorus/bridge)

If missing:
- FAIL or GAP (см Fail Conditions)

### L1) DIAGNOSE
Собрать DIAG_MAP (кратко):
- biggest_problem: смысл | образы | flow | структура | хук | клише | рифма | повторы
- where: секции и строки-мишени (1–3 зоны)
- risk: что нельзя трогать из LOCKS

### L2) VARIANT PLAN (up to 5)
Сгенерировать V1..Vn.
Каждый вариант обязан объявить:
- change_focus: MEANING | IMAGERY | FLOW | HOOK | COHERENCE | ORIGINALITY
- micro_moves: 3–8 буллетов
- what_stays: что сохраняем дословно (минимум: хук или ключ-строка)
- risk_note: 1 строка

Шаблоны вариантов:
- Pattern A: meaning-first (ясность, логика, причинность)
- Pattern B: imagery-first (метафоры, предметность, сенсорика)
- Pattern C: flow-first (ритм речи, длина строк, связки)
- Pattern D: hook-first (липкость, повторяемость, простота)
- Pattern E: originality-first (антиклише, свежие связки)

### L3) SCORE
Оценка 0–5 по шкалам:
- meaning_clarity
- imagery_density
- singability
- hook_strength
- coherence
- originality
- constraint_fit (соблюдение LOCKS)

### L4) SELECT + STABILIZE
- выбрать winner по сумме и constraint_fit
- допускается взять 1 микро-приём из runner-up, если не меняет концепт
- собрать LYRICS_WINNER и evidence

### L5) EXIT CHECK
Выход когда:
- meaning_clarity >= 4
- hook_strength >= 4
- coherence >= 4
- constraint_fit = 5
- и нет `!`

Вернуть winner + evidence + next action.

---

## [M] MODE_HINT BEHAVIOR

### FAST
- 1 итерация
- 1–2 варианта
- цель: читабельно и поётся, без глубоких метафор

### RELEASE_READY
- до 2 итераций
- до 4 вариантов
- обязательны scorecard и фиксирование хуков

### MASTERPIECE
- до 3 итераций
- до 5 вариантов
- минимум 3 разные семьи паттернов (A–E) за цикл
- финальный проход на плотность образов и точность формулировок

---

## [M] OUTPUT FORMATS

### LYRICS_WINNER (canonical)
LYRICS_WINNER:
- lyrics_id: <L001>
- change_focus: <MEANING|IMAGERY|FLOW|HOOK|COHERENCE|ORIGINALITY>
- applied_moves:
  - "<move1>"
  - "<move2>"
  - "<move3>"
- hook_preserved_note: "<short>"
- notes: "<one line>"

### LYRICS_EVIDENCE_PACK (canonical)
LYRICS_EVIDENCE_PACK:
- iteration: <1..n>
- variants:
  - id: <V1> score: {meaning_clarity: x, imagery_density: y, singability: z, hook_strength: a, coherence: b, originality: c, constraint_fit: d}
  - id: <V2> ...
- winner: <V?>
- rationale: "<1–2 lines>"

---

## [M] FAIL CONDITIONS
- FAIL_CODE: MUS.FAIL.LYRICS_LOOP.MISSING_LOCKS
  - отсутствуют LOCKS или они неполные
- FAIL_CODE: MUS.FAIL.LYRICS_LOOP.MISSING_BRIEF
  - нет LYRIC_BRIEF
- FAIL_CODE: MUS.FAIL.LYRICS_LOOP.MISSING_DRAFT
  - нет DRAFT_LYRICS
- FAIL_CODE: MUS.FAIL.LYRICS_LOOP.INVALID_PUNCT
  - найден символ `!` после нормализации
- FAIL_CODE: MUS.FAIL.LYRICS_LOOP.NON_LOCKED_CHANGE
  - попытка изменить тему, POV, тон или структуру секций

---

## [M] GATES
PASS если:
- LOCKS подтверждены
- есть минимум 2 варианта (FAST допускает 1)
- есть scorecard на каждый вариант
- выбран winner
- нет символа `!`

FAIL если:
- сработало любое FAIL condition

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Receives from:
  - MUS.TRACK_BUILD_STEP
  - MUS.LYRIC_DRAFTER
- Returns to:
  - MUS.TRACK_BUILD_STEP
- Optional handoff:
  - MUS.LYRIC_EDITOR

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 loop canon, targets, patterns, strict locks, no-exclamation enforcement
