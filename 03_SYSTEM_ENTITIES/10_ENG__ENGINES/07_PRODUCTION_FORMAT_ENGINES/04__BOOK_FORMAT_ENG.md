# Book Format Engine
FILE: 04__BOOK_FORMAT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines reproducible rules for book outputs (chapter structure, POV policy, exposition control, description/action balance, pacing, hooks, and clarity); produces Book Bibles, Chapter Templates, POV Maps, Exposition Gates, and QC to keep canon, genre contract, and readability stable in text form

---

## PURPOSE

Книга — это формат, где:
- смысл несёт язык
- время растягивается и сжимается словами
- детали живут в голове читателя

Движок нужен, чтобы:
- текст был читаемый и кинематографичный
- не было “воды” и хаоса POV
- экспозиция была контролируемой
- ритм и жанр сохранялись
- можно было повторять стиль серии/цикла

---

## NON-GOALS

- не заменяет Story Structure Engine
- не заменяет Tone/Mood Engine
- не заменяет Sensory Detail Engine
Этот движок задаёт **форматные правила книги** как носителя.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Canon beats (events/turning points/climax/resolution)
- Genre Bible + blending spec (if used)
- Tone/Mood locks
- Character arcs and voice rules
- Sensory Profile (optional but recommended)

### PRODUCES
- BOOK BIBLE (BB) — canonical artifact
- CHAPTER TEMPLATE (CT)
- POV MAP (PM)
- EXPO POLICY & GATES (EPG)
- PACING MAP (BPM)
- “NO-FILLER” RULES (NFR)
- BOOK QC GATES (BQG)

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md
- 03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md
- 06_GENRE_STYLE_ENGINES (tone/atmosphere/sensory)

### OUTPUT_TARGET
- Feeds:
  - chapter outlines
  - prose drafting rules
  - series bible for consistent books

---

## CANON TERMS

### POV
Point of view:
- 1st / 3rd limited / omniscient (rare)

### EXPO
Exposition:
- объяснение мира/правил/предыстории

### SCENE vs SUMMARY
- scene: “проживаем” в моменте
- summary: “пересказ” для экономии времени

### HOOK
Крючок, чтобы читатель не отвалился:
- вопрос, угроза, обещание, необычная деталь

### MICRO-PAYOFF
Маленькая выплата:
- ответ на вопрос
- мини-развязка
- новая конкретика

---

## CORE RULES (CANON)

### BF1 — Clarity over cleverness
Книга может быть умной, но не должна быть непонятной.

### BF2 — POV must be stable and mapped
POV не прыгает хаотично.
POV смена = причина + правило.

### BF3 — Exposition is rationed
Экспозиция выдаётся:
- дозировано
- через действие/детали
- только когда нужно для понимания

### BF4 — Chapter has function
Каждая глава должна:
- менять состояние (world/character/stakes)
- иметь hook and/or payoff

### BF5 — No filler
Если абзац не:
- меняет
- раскрывает
- усиливает
→ выкинуть.

### BF6 — Show > tell, but not at cost of clarity
Показываем через сцену, но мостики для понимания разрешены.

---

## REQUIRED ARTIFACT A: BOOK BIBLE (BB)

### BB SCHEMA (CANON)

Header:
- BB_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - book | series_of_books
- VERSION:
- STATUS:
  - draft | canon | deprecated

Format rules:
- POV MODE:
  - 1st | 3rd limited | omni (rare)
- POV COUNT:
- TENSE:
  - past | present
- VOICE STYLE:
  - clean | lyrical | brutal | clinical | etc
- DESCRIPTION/ACTION RATIO:
  - e.g., 40/60
- DIALOGUE DENSITY:
  - low/med/high
- CHAPTER LENGTH RANGE:
  - words/pages
- SCENE vs SUMMARY BALANCE:
- CLIFFHANGER POLICY:
- INTERNAL MONOLOGUE POLICY:

Genre constraints:
- GENRE LOCK:
- HUMOR CAP:
- VIOLENCE FEEL:
- CLARITY FLOOR:

Rule:
- BB is the “book operating system”.

---

## REQUIRED ARTIFACT B: CHAPTER TEMPLATE (CT)

### CT SCHEMA (CANON)

- CT_ID:
- BB_ID:

Template:
1) ENTRY HOOK (0–300 words)
   - question/threat/oddity
2) ORIENTATION (where/when/who) minimal
3) SCENE BODY
   - action + choices
4) MICRO-PAYOFF (at least 1)
5) EXIT HOOK or RESOLUTION
   - depends on pacing map
6) STATE CHANGE LOG
   - what changed?

Rule:
- Every chapter must have “state change log”.

---

## REQUIRED ARTIFACT C: POV MAP (PM)

### PM SCHEMA (CANON)

- PM_ID:
- BB_ID:

POV entries per chapter:
- CHAPTER ID:
- POV CHARACTER:
- WHY THIS POV:
  - what only they can show
- POV LIMITS:
  - what they cannot know
- VOICE NOTES:
  - lexicon, tempo, focus

POV shift rules:
- Allowed shift frequency:
- Forbidden shifts:
  - mid-scene unless emergency
- Transition style:
  - hard break | marker | scene cut

Rule:
- No POV chapter without “why this POV”.

---

## REQUIRED ARTIFACT D: EXPO POLICY & GATES (EPG)

### EPG SCHEMA (CANON)

- EPG_ID:
- BB_ID:

Expo types:
- NECESSARY EXPO:
  - required to follow scene
- FLAVOR EXPO:
  - optional, atmosphere
- LORE EXPO:
  - deep history (rare; gated)

Rules:
- MAX EXPO BLOCK LENGTH:
- EXPO INSERT TRIGGERS:
  - confusion points
- EXPO DELIVERY MODES:
  - dialogue, action, artifact, inner thought, footnote (optional)
- “EXPO TAX”:
  - every expo block must pay via:
    - new conflict, reveal, or concrete consequence

Gates:
1) Necessity gate:
2) Brevity gate:
3) Action adjacency gate:
4) Payoff gate:
5) Repetition gate:

Rule:
- Fail expo gates → rewrite into action/detail.

---

## REQUIRED ARTIFACT E: BOOK PACING MAP (BPM)

### BPM SCHEMA (CANON)

- BPM_ID:
- BB_ID:

Per act/section:
- TARGET TEMPO:
  - slow/medium/fast
- “PAYOFF CADENCE”:
  - micro-payoff every N pages
- “TENSION WAVES”:
  - rise/fall
- CLIFF POLICY:
  - where cliffs allowed
- REST CHAPTERS:
  - allowed minimal chapters for breath (capped)

Rule:
- Rest chapters exist but are capped and must still change state.

---

## REQUIRED ARTIFACT F: NO-FILLER RULES (NFR)

### NFR SCHEMA (CANON)

- NFR_ID:
- BB_ID:

Rules:
- Any paragraph must satisfy at least one:
  - state change
  - character reveal (action-based)
  - stakes escalation
  - world rule demonstrated
  - sensory signature (bounded)
- “Banned filler forms”:
  - repeated introspection loops
  - summary of nothing
  - long travel with no consequence
- “Cut test”:
  - if removed, would reader lose anything?

Rule:
- If cut test = no loss → cut.

---

## REQUIRED ARTIFACT G: BOOK QC GATES (BQG)

### BQG SCHEMA (CANON)

- BQG_ID:
- BB_ID:

Gates:
1) POV gate:
   - POV map followed; limits respected
2) Clarity gate:
   - reader can track who/where/why
3) Expo gate:
   - expo rationed and paid
4) Pacing gate:
   - tempo within BPM ranges
5) Genre gate:
   - promises/payoffs and taboos respected
6) No-filler gate:
   - NFR satisfied
7) Canon gate:
   - facts match world and continuity

Rule:
- Fail 2+ gates → chapter rewrite required.

---

## TEXT-TO-VISUAL COMPATIBILITY (OPTIONAL)

If book is later adapted:
- maintain a “scene handle”:
  - 1-line scene summary
  - key prop
  - key location
  - key emotional beat
This helps Format Adaptation and Knowledge Production engines.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- POV jumps mid-scene without rule
- long expo blocks with no payoff
- chapters that “nothing changes”
- tension flat for many pages (no micro-payoffs)
- repeated internal monologue loops
- genre drift (humor in grim, etc)

Fix options:
- enforce PM and cut mid-scene switches
- convert expo into action/dialogue + shorten
- add state change and micro-payoff
- tighten BPM cadence
- cut filler and replace with functional beats
- re-lock genre/tone per GB/BB

---

## PROCEDURE (HOW TO RUN)

1) Import canon beats + genre/tone locks
2) Draft BB (format rules)
3) Build CT (chapter template)
4) Build PM (POV plan)
5) Build EPG (expo rationing)
6) Build BPM (tempo and payoff cadence)
7) Apply NFR to drafts
8) Run BQG gates on each chapter
9) Canonize BB and enforce across book(s)

---

## QC CHECKLIST (MANDATORY)

- BB defines POV mode, voice, ratios, length ranges?
- CT exists and includes state change log?
- PM exists and explains each POV?
- EPG gates prevent expo dumps?
- BPM defines payoff cadence and tempo waves?
- NFR cut-test applied?
- BQG gates used on chapters?

---

## VALIDATION RULES

- BFV1: Book format is readable and reproducible.
- BFV2: POV and exposition are controlled and purposeful.
- BFV3: Pacing delivers regular micro-payoffs and tension waves.
- BFV4: No filler; every chapter changes state and preserves canon.

---

OWNER: Universe Engine
LOCK: FIXED
