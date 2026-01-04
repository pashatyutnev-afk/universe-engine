# Short Content Engine
FILE: 06__SHORT_CONTENT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines reproducible rules for short-form vertical content (Shorts/Reels/TikTok) including hook/payoff cadence, one-idea constraint, loop design, on-screen text policy, pacing/editing expectations, and clarity gates; produces Short Bibles, Script Boards, Loop Specs, and QC Gates to preserve canon and maximize retention without genre drift or confusion

---

## PURPOSE

Short-form — это формат, где:
- внимание “дороже золота”
- первые секунды решают всё
- смысл должен быть упакован плотно
- петля (loop) усиливает просмотры
- монтаж и текст на экране — часть повествования

Движок нужен, чтобы:
- шорт был понятным, быстрым и “держал”
- влезали канонические смыслы без каши
- жанр/тон не ломались
- можно было штамповать шорты сериями

---

## NON-GOALS

- не заменяет Editing engine (но задаёт требования)
- не заменяет Genre engine
- не создаёт визуальные промпты (это knowledge production)
Он задаёт **форматную механику шортов**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Canon beat / micro-beat (1 ключевая идея)
- Genre + tone locks
- Platform constraints (duration, aspect, captions)
- Target retention goals
- Existing scene context (optional)

### PRODUCES
- SHORT BIBLE (ShB) — canonical artifact
- SHORT SCRIPT BOARD (SSB)
- HOOK/PAYOFF/LOOP SPEC (HPL)
- ONSCREEN TEXT POLICY (OTP)
- EDIT RHYTHM REQUIREMENTS (ERR)
- SERIES PACK RULES (SPR)
- SHORT QC GATES (ShQG)

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG.md
- 07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG.md
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 05_EXPRESSION_ENGINES (event/turning point)

### OUTPUT_TARGET
- Feeds:
  - short scripts
  - editing constraints
  - on-screen text/caption specs
  - production shot planning (knowledge production)

---

## CANON TERMS

### ONE-IDEA RULE
Один шорт = одна идея/вопрос/удар.

### HOOK WINDOW
Окно (секунды), где зритель решает смотреть или пролистать.

### PAYOFF WINDOW
Окно, где зритель получает “оплату” за внимание.

### LOOP
Концовка, которая естественно ведёт к началу (повтор просмотра).

### DENSITY BUDGET
Сколько новых понятий можно ввести:
- обычно 1–2 (максимум 3) за 30–60 секунд.

---

## CORE RULES (CANON)

### SC1 — One short = one beat
Никаких “мини-эпизодов” без структуры.
Шорт должен быть: hook → escalation → payoff → loop/close.

### SC2 — Hook is mandatory and measurable
Hook должен быть:
- в первые 1–3 секунды (жёстко)
- максимум до 5 секунд (край)
Иначе это не шорт.

### SC3 — Payoff must land before the end
Не оставляем payoff “за кадром”.
Даже если cliff — он должен быть “оплачен” микро-пэйоффом.

### SC4 — Clarity over lore
Лор — только если нужен для понимания.
Шорт не место для энциклопедий.

### SC5 — Text on screen is a tool, not decoration
Текст не должен:
- закрывать смысл кадра
- противоречить озвучке
- перегружать

### SC6 — Loop is a design choice
Loop либо есть по правилам, либо честное закрытие.
Случайный loop = раздражение.

### SC7 — No tone/genre drift for cheap virality
Виральность не должна ломать жанровый контракт и канон.

---

## REQUIRED ARTIFACT A: SHORT BIBLE (ShB)

### ShB SCHEMA (CANON)

Header:
- ShB_ID:
- PROJECT_ID / WORLD_ID:
- SERIES NAME (if any):
- VERSION:
- STATUS:
  - draft | canon | deprecated

Format:
- PLATFORM:
  - shorts | reels | tiktok | mixed
- ASPECT:
  - 9:16 (default)
- DURATION RANGE:
  - 10–20 | 20–35 | 35–60 | 60–90
- HOOK WINDOW (sec):
- PAYOFF WINDOW (sec):
- MAX CONCEPTS:
- CAPTION POLICY:
  - always | optional | never
- AUDIO MODE:
  - VO | dialogue | text-only (rare)

Style locks:
- GENRE LOCK:
- TONE LOCK:
- EDIT SPEED:
  - calm | medium | fast | hyper (capped)
- VISUAL CLARITY FLOOR:
- HUMOR/VIOLENCE CAPS:

Rule:
- ShB defines the “factory settings” for shorts.

---

## REQUIRED ARTIFACT B: SHORT SCRIPT BOARD (SSB)

### SSB SCHEMA (CANON)

- SSB_ID:
- ShB_ID:
- SHORT ID:
- ONE IDEA STATEMENT (one sentence):
- TARGET EMOTION:
- CTA (optional, if series):

Segments:
1) HOOK (0–X sec)
   - what is said/shown
2) SETUP (X–Y sec)
   - minimal context
3) TURN (Y–Z sec)
   - twist/reveal/escalation
4) PAYOFF (Z–end-2 sec)
   - answer/impact
5) LOOP/CLOSE (last 0–2 sec)
   - loop trigger or clean close

For each segment:
- VISUAL:
- AUDIO:
- TEXT ON SCREEN:
- MUST-UNDERSTAND:
- FORBIDDEN:

Rule:
- Every segment must specify “must-understand”.

---

## REQUIRED ARTIFACT C: HOOK / PAYOFF / LOOP SPEC (HPL)

### HPL SCHEMA (CANON)

- HPL_ID:
- SSB_ID:

Hook types:
- question
- threat
- contradiction
- extreme specificity
- “you won’t believe” (use cautiously; avoid cheapness)

Hook rules:
- HOOK MUST:
  - show the conflict or the promise
- HOOK MUST NOT:
  - be generic greeting
  - be long intro

Payoff types:
- answer
- reveal
- win/loss
- cost
- punchline
- “holy moment”

Loop modes:
- hard loop:
  - last frame matches first
- semantic loop:
  - last line reframes first
- curiosity loop:
  - last line creates new question but pays current one

Loop constraints:
- no loop that feels like “clickbait betrayal”
- loop must not violate canon clarity

Rule:
- If loop used → it must be explicitly declared and designed.

---

## REQUIRED ARTIFACT D: ONSCREEN TEXT POLICY (OTP)

### OTP SCHEMA (CANON)

- OTP_ID:
- ShB_ID:

Text roles allowed:
- clarity (names, key fact)
- emphasis (1–3 words)
- structure (STEP 1/2)
- caption (full)

Rules:
- MAX WORDS ON SCREEN (per shot):
- MAX LINES:
- SAFE ZONES:
  - keep UI areas clear
- CONTRADICTION BAN:
  - text cannot contradict audio
- SPEED MATCH:
  - text speed must match edit pace
- READABILITY FLOOR:
  - large enough, high contrast (implementation detail)

Rule:
- If text is not serving clarity/emphasis/structure → remove.

---

## REQUIRED ARTIFACT E: EDIT RHYTHM REQUIREMENTS (ERR)

### ERR SCHEMA (CANON)

- ERR_ID:
- ShB_ID:

Editing targets:
- AVERAGE SHOT LENGTH:
- MAX DEAD AIR (sec):
- CUT POLICY:
  - cut on motion / on word / on beat
- “RESET FRAMES”:
  - occasional stable frames to reduce fatigue (if fast mode)
- B-ROLL POLICY:
- JUMP CUT POLICY:
- SOUND PUNCTUATION:
  - hits/whooshes only if aligned with tone

Rule:
- ERR gives the editor constraints without micromanaging.

---

## REQUIRED ARTIFACT F: SERIES PACK RULES (SPR)

### SPR SCHEMA (CANON)

- SPR_ID:
- ShB_ID:

Series rules:
- EPISODE COUNT (pack):
- CONSISTENT OPENING STAMP:
- CONSISTENT END STAMP:
- “RUNNING QUESTION”:
- PAYOFF DISTRIBUTION:
  - micro per short + macro per pack
- CROSS-SHORT CONTINUITY:
  - props/terms/visual stamps

Rule:
- Series pack must have macro-payoff within the pack.

---

## REQUIRED ARTIFACT G: SHORT QC GATES (ShQG)

### ShQG SCHEMA (CANON)

- ShQG_ID:
- ShB_ID:

Gates:
1) One-idea gate:
   - only one idea/beat
2) Hook gate:
   - hook lands within window
3) Clarity gate:
   - must-understand achieved
4) Payoff gate:
   - payoff delivered (or paid cliff)
5) Density gate:
   - concepts within budget
6) Text policy gate:
   - OTP followed; no clutter
7) Edit rhythm gate:
   - ERR satisfied; no dead air
8) Genre/tone gate:
   - locks respected; no cheap drift
9) Canon gate:
   - no contradictions with world/continuity

Rule:
- Fail 2+ gates → rewrite board or re-edit.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- hook starts after 5 sec
- intro greetings and “subscribe” before hook
- 3+ concepts introduced quickly with no anchors
- payoff missing or only “to be continued”
- text overload (too many words)
- dead air and slow build
- tone whiplash vs genre lock
- canon terms used without definition

Fix options:
- rewrite hook as conflict/promise
- reduce concepts, rename terms to simpler
- add micro-payoff before cliff
- trim dead air; enforce ERR
- cut text; keep only clarity words
- add one anchor line for canon concept
- align with tone owner rules

---

## PROCEDURE (HOW TO RUN)

1) Choose one idea (ONE-IDEA statement)
2) Draft SSB (hook → setup → turn → payoff → loop/close)
3) Define HPL (hook type + payoff mode + loop mode)
4) Apply OTP (text minimal, readable, non-contradicting)
5) Define ERR (edit speed and punctuation)
6) If series: define SPR (pack macro-payoff)
7) Produce short
8) Run ShQG gates and iterate
9) Canonize final short board + publish rules

---

## QC CHECKLIST (MANDATORY)

- ShB defines windows, budgets, locks?
- SSB has one idea and must-understand per segment?
- HPL defines loop mode (or none) explicitly?
- OTP prevents text clutter and contradictions?
- ERR defines edit cadence and dead-air cap?
- SPR defines pack macro-payoff (if series)?
- ShQG gates applied?

---

## VALIDATION RULES

- SCV1: Hook lands early and clearly.
- SCV2: One idea, high clarity, controlled density.
- SCV3: Payoff delivered (or cliff paid with micro-payoff).
- SCV4: Text and edit rules preserve readability and tone.
- SCV5: Output preserves canon and genre contract.

---

OWNER: Universe Engine
LOCK: FIXED
