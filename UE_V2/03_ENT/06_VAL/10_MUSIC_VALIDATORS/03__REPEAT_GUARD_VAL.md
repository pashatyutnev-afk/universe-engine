# VAL — REPEAT GUARD (LYRICS / HOOK / PATTERN) (CANON)

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 50_VAL__VALIDATORS
FAMILY: 10_MUSIC_VALIDATORS
LEVEL: L2
DOC_TYPE: VAL (VALIDATOR)
ENTITY_TYPE: VALIDATOR
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUSIC.REPEAT_GUARD.001
OWNER: SYSTEM
ROLE: Detects excessive repetition inside a track candidate (lyrics lines, hook phrases, adlibs, structural loops) and flags catalog-risk patterns. Produces deterministic violation records with clear remediation routes. Does not require audio fingerprint tooling; operates on declared prompt/lyrics artifacts and track cards.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt repeat guard: explicit repetition thresholds, violation codes, and patch actions with one-axis discipline."
- REASON: "Repetition is the most common quality failure and creates catalog monotony."
- IMPACT: "Pipelines can block or rework candidates before release; quality becomes enforceable."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.REPEAT.001

---

## 0) PURPOSE (LAW)
Этот валидатор ловит повторы:
- одинаковых строк/фраз (lyrics)
- одинаковых hook-формул
- adlibs/слогов/“нанананий”
- чрезмерное копирование 1–2 строк во всех секциях

Цель: остановить “зацикливание” и заставить rework по одному изменяемому параметру.

---

## 1) ABSOLUTE RULES
### 1.1 Validator uses declared text artifacts
VAL работает по тем артефактам, где текст виден:
- MUSIC_TRACK_PROMPT (lyrics plan / excerpts)
- TRACK_CARD (hook notes / structure)
- (optional) MUSIC_TRACK_RELEASE (если там есть lyrics snippet)

Если отсутствуют любые текстовые представления и невозможно проверить — FAIL_CLASS: input absent.

### 1.2 One-axis fix discipline
При FAIL валидатор обязан требовать **одну ось исправления**:
- LYRICS_VARIATION
- HOOK_REWRITE
- SECTION_DIVERSIFICATION
- ADLIB_REDUCTION
- STRUCTURE_REBALANCE

### 1.3 Deterministic thresholds
Повтор считается нарушением только по порогам из секции 4.

---

## 2) APPLICABILITY
### 2.1 Artifact contexts
- MUSIC_TRACK_PROMPT (primary)
- TRACK_CARD
- MUSIC_TRACK_RELEASE (secondary)

### 2.2 Invocation points
- ALBUM_TO_TRACK_ORC (before packaging)
- TRACK_TEST_DOC_GATE_ORC (if matrix requires)

---

## 3) REQUIRED REFERENCES (RAW)
NEGATIVE SPEC LIBRARY (context)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

FINGERPRINT THRESHOLDS (context)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

Default repair route ORC  
ALBUM_TO_TRACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 4) THRESHOLDS (CANON)
Пороговые правила применяются к “видимому тексту” (lines/phrases) из артефакта.

### 4.1 Line repetition (hard)
- Одна и та же строка встречается > 4 раз во всём тексте → VIOLATION (S1)
- Одна и та же строка встречается > 6 раз → VIOLATION (S0)

### 4.2 Phrase repetition (medium)
- Одна и та же короткая фраза (2–6 слов) встречается > 8 раз → VIOLATION (S1)
- > 12 раз → VIOLATION (S0)

### 4.3 Section dominance (structure)
Если > 60% строк трека — вариации одной и той же строки/фразы (минимальные изменения) → VIOLATION (S1)

### 4.4 Placeholder / nonsense
Если присутствуют “placeholder” паттерны (nanana, lalala, yeah×N, hey×N) и они занимают:
- > 20% строк → VIOLATION (S1)
- > 35% строк → VIOLATION (S0)

### 4.5 Hook loop abuse
Если hook заявлен как “одна строка” и повторяется без вариаций в каждой секции + в бридже/аутро → VIOLATION (S1)

---

## 5) REQUIRED EVIDENCE (MINIMUM)
Для каждого нарушения фиксировать:
- repeated_line_or_phrase: exact snippet
- count: integer
- where_seen: sections if available (verse/chorus/etc)
- note: short

Если невозможно собрать evidence (нет текста) → FAIL_CLASS: input absent.

---

## 6) VIOLATION RECORD FORMAT (REQUIRED)
- VAL_ID: UE.VAL.MUSIC.REPEAT_GUARD.001
- TARGET_ARTIFACT_TYPE: (MUSIC_TRACK_PROMPT | TRACK_CARD | MUSIC_TRACK_RELEASE | OTHER)
- TARGET_RAW: (raw link)
- VIOLATION_CODE: (section 7)
- SEVERITY: S0 | S1 | S2 | S3
- EVIDENCE:
  - bullets (from section 5)
- REQUIRED_FIX:
  - bullets
- REQUIRED_PATCH_AXIS:
  - one of (section 8)
- RETURN_TO:
  - raw link route

---

## 7) VIOLATION CODES (CANON)
- LINE_REPEAT_OVERLIMIT (S0/S1)
- PHRASE_REPEAT_OVERLIMIT (S0/S1)
- SECTION_DOMINANCE_REPEAT (S1)
- PLACEHOLDER_NONSENSE_OVERUSE (S0/S1)
- HOOK_LOOP_ABUSE (S1)
- NO_TEXT_FOR_VALIDATION (S0)  (treated as input absent)

---

## 8) REQUIRED PATCH AXES (ONE ONLY)
Choose exactly one:
- LYRICS_VARIATION (rewrite lines keeping theme)
- HOOK_REWRITE (new hook concept / different wording)
- SECTION_DIVERSIFICATION (ensure verses differ, add bridge contrast)
- ADLIB_REDUCTION (remove filler, replace with meaning)
- STRUCTURE_REBALANCE (reduce hook frequency, add instrumental breaks)

---

## 9) VERDICT RULES
PASS:
- no violations

FAIL:
- any S0 or S1 violation

---

## 10) DEFAULT RETURN ROUTE (RAW)
ALBUM_TO_TRACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 11) CHANGE POLICY (LOCK)
- Пороги менять только PATCH
- При изменении порогов синхронизировать QA regression rubric and matrix if required

---

END.
