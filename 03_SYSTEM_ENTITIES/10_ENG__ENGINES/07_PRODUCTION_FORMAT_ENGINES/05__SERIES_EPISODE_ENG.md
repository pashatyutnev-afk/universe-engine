# Series & Episode Engine
FILE: 05__SERIES_EPISODE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines reproducible rules for serialized storytelling (episode structure, act breaks, cold opens, cliffhangers, season arcs, A/B/C plots, and payoff cadence); produces Series Bibles, Episode Templates, Beat Maps, and QC Gates that preserve genre contract, continuity, and viewer retention across episodic production

---

## PURPOSE

Сериал — это формат, где:
- история живёт на дистанции
- каждый эпизод должен “держать зрителя”
- есть макро-арка сезона и микро-арка серии
- клиффы и акты — производственный стандарт

Движок нужен, чтобы:
- эпизоды были цельными и “затягивали”
- арка сезона не расползалась
- A/B/C линии были управляемы
- ритм payoffs был регулярным
- производственная команда знала точные правила

---

## NON-GOALS

- не заменяет Story Structure Engine
- не заменяет Editing engine
- не режиссирует камеру
Он задаёт **форматный каркас сериала**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Canon beats and arc goals
- Genre Bible + blending spec (if any)
- Tone/Mood locks
- Character arcs + relationship arcs
- Platform constraints (episode length, ad breaks)

### PRODUCES
- SERIES BIBLE (SB) — canonical artifact
- SEASON ARC MAP (SAM)
- EPISODE TEMPLATE (ET)
- A/B/C PLOT RULES (ABCR)
- PAYOFF CADENCE MAP (PCM)
- CLIFFHANGER POLICY (CHP)
- SERIES QC GATES (SQG)

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md
- 05_EXPRESSION_ENGINES (turning points, climax, resolution)
- 06_GENRE_STYLE_ENGINES (tone/atmosphere)

### OUTPUT_TARGET
- Feeds:
  - episode outlines
  - writers room beat sheets
  - production shot lists (via knowledge production)
  - edit rhythm planning

---

## CANON TERMS

### COLD OPEN
Короткий старт серии до титров:
- hook + tone stamp + promise

### ACT BREAK
Точка перелома, где зритель “остается”.

### A/B/C PLOTS
- A: основной двигатель серии
- B: вторичная линия (персонажи/отношения/мир)
- C: микро-линия (комедия/деталь/подготовка payoff)

### CLIFFHANGER
Незакрытый вопрос/угроза/перелом в конце эпизода.

### PAYOFF CADENCE
Как часто зритель получает “оплату” (микро/мезо/макро).

---

## CORE RULES (CANON)

### SE1 — Every episode must have its own engine
Эпизод обязан иметь:
- проблему/цель
- изменение состояния к финалу

### SE2 — Season arc must progress
Каждый эпизод должен:
- или двигать сезонную арку
- или усиливать персонажей/мир так, чтобы это стало топливом арки

### SE3 — Cold open stamps the contract
Cold open закрепляет:
- жанр
- тон
- угрозу/вопрос

### SE4 — Act breaks are payoff machines
Акт = напряжение + мини-переворот.
Без сильных актов сериал “не держит”.

### SE5 — A/B/C must be bounded
B и C не должны:
- съедать A
- ломать тон
- нарушать ясность

### SE6 — Cliffhangers are a policy, not random
Клиффы применяются по правилам CHP.

### SE7 — Continuity is mandatory
Сериал прощает мало:
- continuity ошибки ломают доверие.

---

## REQUIRED ARTIFACT A: SERIES BIBLE (SB)

### SB SCHEMA (CANON)

Header:
- SB_ID:
- PROJECT_ID / WORLD_ID:
- SEASON COUNT (planned):
- EPISODE LENGTH (target):
- VERSION:
- STATUS:
  - draft | canon | deprecated

Rules:
- GENRE LOCK:
- TONE LOCK:
- FORMAT MODE:
  - procedural | serialized | hybrid
- POV POLICY:
  - whose story we follow
- MAIN PROMISES (3–7):
- CORE PAYOFFS (3–7):
- TABOOS:
- CLARITY FLOOR:
- VIOLENCE/HUMOR CAPS:

Operational:
- EPISODE ENGINE TYPES allowed:
  - heist, investigation, siege, trial, chase, ritual, etc.
- RECURRING STRUCTURE:
  - cold open, acts, tag
- “WHAT MAKES THIS SHOW THIS SHOW” (1 paragraph)

Rule:
- SB is the law book for the season(s).

---

## REQUIRED ARTIFACT B: SEASON ARC MAP (SAM)

### SAM SCHEMA (CANON)

- SAM_ID:
- SB_ID:

Season outline:
- SEASON GOAL:
- SEASON THREAT / QUESTION:
- MAJOR TURNING POINTS (3–6):
- MID-SEASON RESET (optional):
- CLIMAX TYPE:
- RESOLUTION TYPE:
- CHARACTER ARC MILESTONES (per key character):
- WORLD ARC MILESTONES (optional):

Per episode (repeat):
- EP#:
- EP ENGINE:
- EP PROMISE:
- EP PAYOFF:
- SEASON PROGRESS:
  - what moved forward
- CLIFF TYPE (if any):
- CONTINUITY SENSITIVE ITEMS:

Rule:
- Every episode must log “season progress”.

---

## REQUIRED ARTIFACT C: EPISODE TEMPLATE (ET)

### ET SCHEMA (CANON)

- ET_ID:
- SB_ID:
- EP LENGTH:

Template blocks:
0) COLD OPEN (1–5 min)
   - hook + tone stamp + promise
1) ACT 1 — Setup + problem definition
2) ACT 2 — escalation + complication
3) ACT 3 — turning point + cost
4) ACT 4 — climax + immediate resolution
5) TAG/END — cliff, aftertaste, or closure

Optional variations:
- 3-act template
- ad-break aligned template

Rule:
- Template choice must match platform and runtime.

---

## REQUIRED ARTIFACT D: A/B/C PLOT RULES (ABCR)

### ABCR SCHEMA (CANON)

- ABCR_ID:
- SB_ID:

Rules:
- A PLOT:
  - must carry episode engine and stakes
- B PLOT:
  - must support A (character cost, world info) or seed future payoff
- C PLOT:
  - must be micro and must not change tone violently

Caps:
- MAX B SCREEN TIME (%):
- MAX C SCREEN TIME (%):
- MAX SIMULTANEOUS THREADS:
- THREAD RESOLUTION REQUIREMENTS:
  - A must resolve at least partially every ep
  - B must pay within N episodes
  - C must pay within same episode

Rule:
- If B/C violates caps → cut or merge.

---

## REQUIRED ARTIFACT E: PAYOFF CADENCE MAP (PCM)

### PCM SCHEMA (CANON)

- PCM_ID:
- SB_ID:

Cadence:
- MICRO PAYOFFS:
  - every N minutes
- ACT PAYOFFS:
  - per act break
- EPISODE PAYOFF:
  - end of episode
- SEASON PAYOFFS:
  - at major milestones

Payoff types:
- reveal
- victory
- cost
- reversal
- catharsis
- dread spike

Rule:
- If cadence is too slow → viewer drops; must be adjusted.

---

## REQUIRED ARTIFACT F: CLIFFHANGER POLICY (CHP)

### CHP SCHEMA (CANON)

- CHP_ID:
- SB_ID:

Cliff types allowed:
- threat escalation
- new question/reveal
- moral choice
- point-of-no-return
- betrayal/turn

Cliff constraints:
- MAX CLIFFS IN A ROW:
- “NO CHEAP CLIFF” rule:
  - cannot be solved instantly next ep without cost
- “CLIFF PAYOFF WINDOW”:
  - must pay within N episodes

When to use cliff:
- end of ep before arc milestone
- after big reveal
- before season midpoint or finale

Rule:
- Cliff must be earned and paid.

---

## REQUIRED ARTIFACT G: SERIES QC GATES (SQG)

### SQG SCHEMA (CANON)

- SQG_ID:
- SB_ID:

Gates:
1) Episode engine gate:
   - ep has goal/problem and state change
2) Season progress gate:
   - SAM progress logged and real
3) Cold open gate:
   - stamps genre/tone and hooks
4) Act break gate:
   - each act has escalation and payoff
5) A/B/C gate:
   - caps respected; B/C support or seed payoff
6) Payoff cadence gate:
   - PCM satisfied
7) Cliff policy gate:
   - CHP followed; no cheap cliff
8) Continuity gate:
   - no contradictions

Rule:
- Fail 2+ gates → episode outline rewrite required.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- episodes feel “samey” (no unique episode engine)
- B plot eats A plot
- too many threads, none paid
- cold opens are weak or irrelevant
- act breaks don’t flip anything
- cliff is cheap (resolved instantly)
- season arc stalls for many eps
- continuity errors accumulate

Fix options:
- assign explicit EP ENGINE per episode
- cap threads and merge B/C into A support
- add act reversals and costs
- strengthen cold open promise and hook
- enforce payoff windows and cliff policy
- restructure SAM milestones
- run continuity checklist and lock props/facts

---

## PROCEDURE (HOW TO RUN)

1) Draft SB (genre, tone, format mode, taboos)
2) Build SAM (season milestones + episode logs)
3) Choose ET template (acts + runtime)
4) Define ABCR caps and payoff windows
5) Define PCM cadence (micro/act/episode/season)
6) Define CHP (cliff types + rules)
7) Produce episode outlines using ET + ABCR + PCM
8) Run SQG gates on every episode
9) Canonize SB and maintain via governance

---

## QC CHECKLIST (MANDATORY)

- SB exists and locks genre/tone/format mode?
- SAM exists and each episode logs progress?
- ET used (acts + cold open + tag)?
- ABCR caps respected?
- PCM cadence ensured?
- CHP cliff rules followed?
- SQG gates applied?
- Continuity checklist maintained?

---

## VALIDATION RULES

- SEV1: Each episode has an engine and changes state.
- SEV2: Season arc progresses with paid milestones.
- SEV3: Acts, hooks, and payoffs follow consistent cadence.
- SEV4: A/B/C plots are bounded and serve the contract.
- SEV5: Cliffhangers are earned and paid.

---

OWNER: Universe Engine
LOCK: FIXED
