# TOPIC — HOOK ENGINEERING (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.HOOK_ENGINEERING.001
OWNER: SYSTEM
ROLE: Atomic method to design hooks for generated tracks: hook types, timing targets, melodic/lyric/rhythm patterns, contrast rules, repetition control, and QA tests (scroll-stop/recognition/loop); includes Hook Card templates and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created hook engineering module: hook taxonomy, timing targets, pattern recipes, contrast rules, and QA tests for viral/retention performance."
- REASON: "Generated songs often fail from weak or late hooks; hook design must be explicit and testable."
- IMPACT: "Entities can systematically increase hook rate, reduce filler, and produce UGC-ready loops."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.003

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- hook_design
- ugc_ready
- qa_tests
- maturity_seed

---

## 1) PURPOSE
Хук делается инженерно:
- выбрать тип хука,
- поставить его рано (тайминг),
- задать паттерны (мелодия/ритм/текст),
- дать контраст и повтор,
- проверить тестами (scroll-stop / recognition / loop).

---

## 2) WHEN TO USE
- Хук появляется поздно или “никакой”.
- Трек звучит ровно и не цепляет.
- Нужны короткие версии (15/30/60) и UGC loops.
- Нужно повысить удержание в первые 10 секунд.

## 3) WHEN NOT TO USE
- Если задача — чисто атмосферный трек без хука (но всё равно можно иметь минимальный “signal”).

---

## 4) DEFINITIONS (STRICT)
### Hook
Фрагмент, который:
- узнаётся быстро,
- хочется повторить,
- выделяет трек.

### Hook timing target
Появление хука:
- first 5s (ideal for shorts)
- first 10–15s (standard)
- max 25s (дальше обычно поздно для UGC)

---

## 5) HOOK TYPES (TAXONOMY)
- H1: Lyric hook (слоган/фраза)
- H2: Melodic hook (мелодия)
- H3: Rhythm hook (stomp pattern / groove)
- H4: Sound-design hook (glitch tag / signature hit)
- H5: Call-response hook (A/B)
- H6: Harmonic hook (аккордовый поворот)
- H7: Drop-less hook (хук без “дропа”, сразу в лоб)

Рекомендуемо:
- комбинировать 2 типа (например H1 + H4).

---

## 6) HOOK BUILDING BLOCKS (RECIPES)
### Recipe A — Slogan + contour
- 6–10 слогов
- 2 повторения с микровариацией
- контур мелодии: вверх → вниз (или наоборот)
Пример форма:
- line A
- line A' (вариация 1–2 слова)

### Recipe B — Stomp + tag
- half-time stomp (kick/snare)
- 1 фирменный glitch-tag на 2 и/или 4
- пауза/стоп на 1 долю (stutter) = “перехват внимания”

### Recipe C — Call/response
- A: короткий вопрос/вызов
- B: короткий ответ/крик
(идеально для интро/бриджа)

### Recipe D — Hook loop (15s)
- 4 такта хука
- 1 такт “дышит” (пауза/срез)
- 4 такта повтор
(готовый loop)

---

## 7) CONTRAST RULES (MAKE HOOK POP)
Хук должен иметь минимум 2 контраста:
- динамика (тише→громче или наоборот)
- плотность (пусто→плотно)
- тембр (синт vs гитара)
- голос (rap vs melodic)
- ритм (прямо vs синкопа)
Без контраста хук “тонет”.

---

## 8) REPETITION CONTROL (ANTI-BORING)
Правило:
- повтор обязателен, но копипаста запрещена.

Допустимая вариация:
- слово 1–2 меняется
- окончание строки меняется
- один такт “ломается” стуттером
- добавляется второй голос/гарм

---

## 9) PROCEDURE (HOOK CARD)
### Step 1 — Choose hook types (H1..H7)
### Step 2 — Set timing target
- 0:05 / 0:10 / 0:15

### Step 3 — Write hook lyric (if H1)
- 1 основная строка + 1 вариация

### Step 4 — Specify musical hook markers
- contour, rhythm, sound tag, stop moment

### Step 5 — Define contrast plan
- какие 2 контраста включаем

### Step 6 — Define loop plan (15s)
- как зациклить

### Step 7 — QA tests
Пройти тесты §10.

---

## 10) QA TESTS (MANDATORY)
- T1: Scroll-stop 5s
  Через 5 секунд уже “что-то происходит” (signal/hook).
- T2: Recognition 10s
  Через 10 секунд слушатель может напеть/повторить фразу.
- T3: Loop 15s
  15 секунд можно зациклить без провала энергии.
- T4: Anti-repeat
  Нет ощущения “одна и та же строка 10 раз”.

RESULT:
- PASS / REWORK

---

## 11) HOOK CARD TEMPLATE (COPY)
HOOK CARD:
- Track:
- Hook types (H1..H7):
- Timing target:
- Hook lyric (A / A'):
- Sound tag:
- Rhythm marker:
- Contrast plan (2+):
- Loop plan (15s):
- QA:
  - Scroll-stop 5s:
  - Recognition 10s:
  - Loop 15s:
  - Anti-repeat:
- Result: PASS/REWORK

---

## 12) EXAMPLES (MANDATORY)
### 12.1 PASS EXAMPLE (industrial nu metal)
Hook types:
- H1 lyric hook + H4 glitch tag
Timing:
- 0:10
Hook lyric:
- “Сбо́и в голове — но я вижу маршрут”
Tag:
- stutter hit on 2, glitch “zap” on 4
Contrast:
- chorus opens wider + vocal jumps to melodic
QA:
- recognition in 10s PASS
WHY PASS:
- фраза запоминается, тег узнаваем, есть контраст.

### 12.2 FAIL EXAMPLE
Hook появляется на 0:45 и без отличий от куплета.
WHY FAIL:
- поздно и нет контраста.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (hook timing + tests mandatory; no late hook without justification)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
