# Twist & Reveal Engine
FILE: 08__TWIST_REVEAL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Designs twists and reveals as controlled narrative operations; maps truth-states, payoff effects, and foreshadow dependencies to ensure fairness, coherence, and meaningful state change

---

## PURPOSE

Twist/Reveal — это операция “смена истины”.
Движок нужен, чтобы:
- раскрытия были честными (seeded)
- твисты меняли смысл, а не “шок ради шока”
- новая правда не ломала логику мира/персонажей
- последствия фиксировались в continuity

---

## NON-GOALS

- не делает посевы (Foreshadowing engine) — он только требует их
- не управляет темпом (Pacing)
- не управляет драматической кривой (Dramatic Arc)
Он проектирует “истины” и их смену.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Foreshadow Map (FSM) or seed list
- Scene Specs (SS)
- Narrative Logic Spec (NLS)
- Story Structure Spec (SSS)
- Stakes & Tension Spec (STS) (optional but recommended)

### PRODUCES
- REVEAL/TWIST PLAN (RTP) — canonical artifact
- TRUTH STATE MAP (before/after truth)
- PAYOFF EFFECT statements
- FAIRNESS + COHERENCE report (flags)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/07__FORESHADOWING_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md (handoff requirement)

### OUTPUT_TARGET
- Feeds Scene Construction (04) and Continuity (09)
- Informs production for reveal staging (camera/editing/sound hooks)

---

## CANON TERMS

### REVEAL
Раскрытие истины, которая была скрыта.
Меняет понимание событий.

### TWIST
Резкая смена ожидаемого направления/значения.
Как правило:
- переворачивает цель
- меняет союзника/врага
- раскрывает скрытую причину
- меняет правила игры

### TRUTH STATE
Что “считается истинным” в системе на данный момент (для персонажей и/или зрителя).

### FAIR TWIST
Твист, который:
- был подготовлен (seeded)
- логически возможен в рамках законов
- не отменяет ставки задним числом

---

## TWIST/REVEAL TYPES (CANON SET)

- IDENTITY: “кто он на самом деле”
- MOTIVE: “зачем он это делал”
- RULE: “как работает закон/магия/технология”
- ALLY/ENEMY FLIP: “кто за кого”
- INFORMATION: “что мы не знали”
- CONTEXT SHIFT: “событие было другим по смыслу”
- POV TRICK: “мы видели ограниченно”
- COST REVEAL: “цена была скрыта”
- FALSE VICTORY: “победа была иллюзией” (опасно, требует trust policy)

Rule:
- Each RTP entry must declare TYPE.

---

## TWIST WEIGHT (IMPACT SCALE)

- MINOR: добавляет смысл, не ломает траекторию
- MAJOR: меняет направление/цели
- CORE: меняет основу истории/мира (редко)

Rule:
- CORE requires strict seeding + governance-level caution (risk flag).

---

## REQUIRED ARTIFACT: REVEAL/TWIST PLAN (RTP)

### RTP SCHEMA (CANON)

Global:
- RTP_ID:
- SCOPE:
  - episode | arc | season | book
- TWIST POLICY:
  - subtle | balanced | high-twist
- TRUST POLICY:
  - fakeouts: not allowed | rare | allowed (rare recommended)

Entries (repeat):
- RTP_ITEM_ID: RTP-0001
- TYPE:
- WEIGHT:
  - minor | major | core
- REVEAL SCENE:
  - SCENE_ID
- TRUTH BEFORE (viewer):
- TRUTH AFTER (viewer):
- TRUTH BEFORE (characters):
  - who believes what
- TRUTH AFTER (characters):
  - who knows now
- REQUIRED SEEDS:
  - list of SEED_ID (from FSM)
- PAYOFF EFFECT:
  - what changes (goal/stakes/relationship/law)
- CONSEQUENCES COMMITMENT:
  - what must remain true after (continuity lock)
- STAGING NOTES (optional):
  - how it lands (dialogue/object/action)
- PRODUCTION HOOKS (optional):
  - camera beat / silence beat / match cut / motif
- FLAGS:
  - unfair risk?
  - logic risk?
  - trust risk?
  - continuity risk?

---

## RULES (CANON)

### TR1 — No major reveal without seeds
MAJOR and CORE must reference at least 1–3 seeds.
If none → unfair.

### TR2 — Reveal must change state
После reveal/twist меняется:
- цель, или
- ставки, или
- понимание причины, или
- отношения, или
- правило мира
Если не меняется → это trivia, не reveal.

### TR3 — Logic compatibility is mandatory
Новая правда не может противоречить:
- NLS constraints
- world laws
- established character limits
Если противоречит → либо retcon (governance), либо rewrite.

### TR4 — Twist weight must match timing
CORE twist слишком рано ломает фундамент, слишком поздно выглядит “подмена”.
Нужно осознанное место в структуре (SSS turn map).

### TR5 — Fakeouts are expensive
False victory / “всё было сном” и подобное:
- ломает доверие
- требует компенсации (новая цена/правда)
Иначе запрещено.

### TR6 — Continuity lock required
Любой reveal обязан создавать continuity notes:
- кто теперь знает
- что стало истинным
- какие действия возможны/невозможны

---

## FAIRNESS + COHERENCE CHECKS

Flag if:
- seeds missing / too weak for weight
- reveal contradicts earlier facts
- reveal cancels stakes retroactively
- reveal has no consequences
- characters react unrealistically (handoff to character engines)

Fix options:
- add/strengthen seeds
- reduce weight
- add consequence/cost
- adjust earlier facts (retcon via governance)
- stage reveal differently (show, not tell)

---

## PROCEDURE (HOW TO RUN)

1) List planned reveal/twist moments (from SSS turns)
2) Assign type + weight
3) Define truth states before/after (viewer + characters)
4) Link required seeds (FSM)
5) Define payoff effect + consequences commitment
6) Run fairness/coherence checks
7) Output RTP and attach continuity locks

---

## VALIDATION RULES

- RTV1: RTP exists with explicit truth transitions.
- RTV2: Major/core items reference seeds.
- RTV3: Each item produces consequences commitments.
- RTV4: No contradictions with NLS/SSS; flagged items must be fixed or declared via governance.

---

OWNER: Universe Engine
LOCK: FIXED
