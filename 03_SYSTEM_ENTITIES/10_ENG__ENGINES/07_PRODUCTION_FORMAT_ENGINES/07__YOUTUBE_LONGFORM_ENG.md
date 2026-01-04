# YouTube Longform Engine
FILE: 07__YOUTUBE_LONGFORM_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines reproducible rules for YouTube longform storytelling and essays (open loops, sectioning, retention mechanics, reset points, payoff cadence, pacing control, and anti-filler gates); produces Longform Bibles, Segment Maps, Open-Loop Specs, Retention Plans, and QC Gates to preserve canon, genre contract, and clarity while maximizing watch time without clickbait betrayal

---

## PURPOSE

YouTube longform — это формат, где:
- зритель терпит дольше, но требует смысла
- структура должна держать внимание 10–60+ минут
- “вода” убивает удержание
- нужны открытые петли (open loops) и регулярные выплаты

Движок нужен, чтобы:
- видео было понятным и удерживающим
- обещания не превращались в кликбейт
- смысл и канон не расползались
- можно было штамповать ролики стабильно

---

## NON-GOALS

- не заменяет Genre engine
- не заменяет Editing & Montage engine
- не задаёт камеру/свет (это knowledge production)
Он задаёт **форматную механику longform**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Canon topic/scene/arc (what we are delivering)
- Genre + tone locks
- Target duration + platform constraints
- Evidence/refs pack (если эссе/разбор)
- Editing rhythm constraints (optional)

### PRODUCES
- LONGFORM BIBLE (LB) — canonical artifact
- OPEN LOOP SPEC (OLS)
- SEGMENT MAP (SM)
- RETENTION PLAN (RP)
- PAYOFF CADENCE MAP (PCM)
- ANTI-FILLER RULES (AFR)
- LONGFORM QC GATES (LQG)

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG.md
- 07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG.md
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 05_EXPRESSION_ENGINES (turning points, resolution)

### OUTPUT_TARGET
- Feeds:
  - script outline
  - chapter markers (timestamps)
  - edit beats and b-roll needs
  - thumbnail/title promise alignment

---

## CANON TERMS

### OPEN LOOP
Вопрос/обещание, которое удерживает:
- открываем в начале
- платим позже
- не обманываем

### RESET POINT
Короткий “сброс” внимания:
- смена темпа/визуала
- мини-саммари
- смена перспективы

### SECTION
Самостоятельный блок, который:
- имеет мини-цель
- имеет мини-payoff

### CLICKBAIT BETRAYAL
Обещали одно — дали другое.
Запрещено.

---

## CORE RULES (CANON)

### YT1 — Promise must be paid
Каждое обещание (title/thumbnail/opening) обязано получить выплату.

### YT2 — Sectioning is mandatory
Длинный ролик без секций = потеря удержания.
Секции должны быть:
- логически завершёнными
- с мини-payoff

### YT3 — Retention is built, not begged
“Подпишись” не заменяет смысл.
Retention строится:
- open loops
- stakes
- ясность
- регулярные выплаты

### YT4 — Reset cadence
Нужны reset points каждые N минут (зависит от темпа).

### YT5 — Anti-filler is law
Если кусок не:
- двигает идею вперёд
- отвечает на вопрос
- усиливает stakes
→ вырезать.

### YT6 — Clarity floor
Зритель должен понимать:
- о чём мы сейчас
- зачем это важно
- что будет дальше

### YT7 — Canon and tone locks survive
Никаких дешёвых поворотов, ломающих канон/жанр.

---

## REQUIRED ARTIFACT A: LONGFORM BIBLE (LB)

### LB SCHEMA (CANON)

Header:
- LB_ID:
- PROJECT_ID / WORLD_ID:
- CHANNEL/SERIES NAME (optional):
- VERSION:
- STATUS:
  - draft | canon | deprecated

Format:
- TARGET DURATION:
- PACE MODE:
  - calm | medium | fast
- SECTION LENGTH RANGE:
- RESET CADENCE (min):
- HOOK WINDOW (sec):
- SUMMARY POLICY:
  - micro summary per section | none
- CTA POLICY:
  - where allowed (never before hook)

Locks:
- GENRE LOCK:
- TONE LOCK:
- CLICKBAIT BETRAYAL BAN: true
- CLARITY FLOOR:
- VIOLENCE/HUMOR CAPS:

Rule:
- LB defines the operating system for longform.

---

## REQUIRED ARTIFACT B: OPEN LOOP SPEC (OLS)

### OLS SCHEMA (CANON)

- OLS_ID:
- LB_ID:

Loops list (repeat 1–5):
- LOOP QUESTION / PROMISE:
- OPENING TIME (mm:ss):
- PAYOFF TARGET (section or time window):
- PAYOFF TYPE:
  - answer | reveal | demonstration | twist | conclusion
- “NO CHEAT” CONDITION:
  - what counts as real payoff
- BACKUP PAYOFF:
  - if main payoff fails, what minimum we deliver

Rule:
- Every loop must have a payoff target and no-cheat condition.

---

## REQUIRED ARTIFACT C: SEGMENT MAP (SM)

### SM SCHEMA (CANON)

- SM_ID:
- LB_ID:

Segments (repeat):
- SEGMENT ID:
- TITLE (internal):
- PURPOSE:
- INPUT QUESTION:
- OUTPUT PAYOFF:
- KEY POINTS (max 3–5):
- REQUIRED EXAMPLES / SCENES:
- VISUAL SUPPORT NOTES:
- TRANSITION OUT (what carries us forward)

Rule:
- Each segment has an input question and output payoff.

---

## REQUIRED ARTIFACT D: RETENTION PLAN (RP)

### RP SCHEMA (CANON)

- RP_ID:
- LB_ID:

Mechanics:
- HOOK MECHANIC:
  - shock | promise | mystery | stakes | curiosity
- OPEN LOOP COUNT:
- “FORWARD REFERENCES” POLICY:
  - teasing without betrayal
- RESET POINTS:
  - where and how
- “VALUE DROPS”:
  - scheduled moments of high value (demo/reveal/story)
- “FATIGUE CONTROL”:
  - vary pace, cut repetition

Rule:
- RP must define at least:
  - hook
  - open loops
  - reset cadence
  - value drops

---

## REQUIRED ARTIFACT E: PAYOFF CADENCE MAP (PCM)

### PCM SCHEMA (CANON)

- PCM_ID:
- LB_ID:

Cadence:
- MICRO PAYOFFS:
  - every N minutes (or per section)
- MAJOR PAYOFFS:
  - 2–5 times per video (depends on length)
- FINAL PAYOFF:
  - must resolve main promise

Payoff types:
- answer
- reveal
- demonstration
- emotional catharsis
- summary conclusion

Rule:
- No long segment without payoff.

---

## REQUIRED ARTIFACT F: ANTI-FILLER RULES (AFR)

### AFR SCHEMA (CANON)

- AFR_ID:
- LB_ID:

Rules:
- BAN:
  - repeated restating
  - long disclaimers
  - “we’ll get to it” without delivering
  - excessive intro music
  - tangents without payoff
- CUT TEST:
  - if removed, does meaning change?
- DENSITY FLOOR:
  - each minute must deliver at least 1 new value unit:
    - fact, insight, beat change, example, payoff marker

Rule:
- Filler is treated as defect.

---

## REQUIRED ARTIFACT G: LONGFORM QC GATES (LQG)

### LQG SCHEMA (CANON)

- LQG_ID:
- LB_ID:

Gates:
1) Promise gate:
   - title/thumbnail promise is delivered
2) Hook gate:
   - hook within window
3) Loop gate:
   - OLS loops opened and paid (no-cheat)
4) Section gate:
   - SM has input question + output payoff per section
5) Retention gate:
   - RP resets and value drops implemented
6) Payoff cadence gate:
   - PCM satisfied
7) Anti-filler gate:
   - AFR passes cut test
8) Clarity gate:
   - viewer always knows where we are
9) Canon/tone gate:
   - locks respected

Rule:
- Fail 2+ gates → restructure script and re-edit.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- opening spends >30 sec without hook
- open loop never paid or paid weakly
- segments have no purpose/payoff
- “we’ll talk about later” repeated
- long tangents
- monotone pacing (no resets)
- conclusion doesn’t close main promise
- tone shifts for cheap jokes/drama

Fix options:
- rewrite opening to deliver promise fast
- add explicit payoff moments per section
- cut tangents and restatements
- add reset points (summary/visual shift/mini-turn)
- strengthen final conclusion to close loops
- re-lock tone and enforce betrayal ban

---

## PROCEDURE (HOW TO RUN)

1) Define main promise (title/thumbnail truth)
2) Draft LB (duration, cadence, locks)
3) Build OLS (1–5 open loops)
4) Build SM (sections with input question and payoff)
5) Build RP (resets + value drops)
6) Build PCM (payoff cadence)
7) Apply AFR (cut filler)
8) Produce script and edit plan
9) Run LQG gates, iterate, canonize

---

## QC CHECKLIST (MANDATORY)

- LB defines duration, sections, resets, hook window?
- OLS defines open loops and no-cheat payoffs?
- SM defines question → payoff per section?
- RP defines resets + value drops?
- PCM ensures regular payoffs?
- AFR cuts filler and enforces density floor?
- LQG gates applied to outline and final?

---

## VALIDATION RULES

- YTV1: Viewer gets hooked early and stays oriented.
- YTV2: Promises and open loops are honestly paid.
- YTV3: Sections deliver regular mini-payoffs and resets.
- YTV4: Filler is eliminated; density remains high.
- YTV5: Canon and tone remain stable.

---

OWNER: Universe Engine
LOCK: FIXED
