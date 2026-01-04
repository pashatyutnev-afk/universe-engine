# Emotional Resonance Engine
FILE: 03__EMOTIONAL_RESONANCE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Designs and locks emotional resonance by mapping triggers, stakes, attachment, contrast, repetition, and payoff timing; produces Resonance Maps, Emotional Anchors, Echo Patterns, and QC Gates that ensure scenes reliably land emotionally without breaking tone or collapsing into manipulation

---

## PURPOSE

Резонанс — это когда сцена не просто “понятна”, а **цепляет**.
Движок нужен, чтобы:
- эмоции были **управляемыми** (не рандом)
- сцены попадали в зрителя стабильнее
- “эхо” эмоций тянулось через арку (setup → payoff)
- не было дешёвой манипуляции, которая ломает доверие

---

## NON-GOALS

- не заменяет Tone & Mood (общая температура)
- не заменяет Dramatic Arc (структура)
- не заменяет Dialogue/Character engines (инструменты выражения)
Он отвечает за **проектирование эмоционального удара и его “эхо”**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Tone Bible + Mood Curve
- Character attachments (who matters)
- Stakes map (personal/social/existential)
- Key beats (turning points, climax, resolution)
- Symbolism/metaphor assets (if any)

### PRODUCES
- RESONANCE MAP (RM) — canonical artifact
- EMOTIONAL ANCHOR REGISTRY (EAR)
- ECHO PATTERN PLAN (EPP)
- PAYOFF TIMING RULES (PTR)
- ANTI-MANIPULATION POLICY (AMP)
- RESONANCE QC GATES (RQG)

### DEPENDS_ON
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 02_DOMAIN_CHARACTER_ENGINES (attachment + growth)
- 05_EXPRESSION_ENGINES/04__TURNING_POINT_ENG.md
- 05_EXPRESSION_ENGINES/05__CLIMAX_ENG.md
- 05_EXPRESSION_ENGINES/06__RESOLUTION_ENG.md

### OUTPUT_TARGET
- Feeds:
  - scene construction and dialogue emphasis
  - music placement and silence policy
  - shot selection and editing rhythm around payoff
  - symbolism/metaphor placement

---

## CANON TERMS

### EMOTIONAL ANCHOR
Якорь эмоции:
- объект/место/жест/фраза/музыка/символ, который возвращает чувство.

### ATTACHMENT
Привязанность зрителя:
- забота, узнавание, уважение, страх потерять, эмпатия.

### CONTRAST
Контраст, который усиливает эмоцию:
- тишина после шума, свет после мрака, нежность рядом с угрозой.

### ECHO
Эхо:
- повтор мотива/якоря в новых условиях, усиливающий смысл.

### PAYOFF
Вознаграждение эмоции:
- момент, когда накопление “выпускает ток”.

### EMOTIONAL HONESTY
Честность:
- эмоция соответствует причинам и последствиям.

---

## RESONANCE RULES (CANON)

### ER1 — Attachment precedes impact
Нельзя “убить персонажа” и ждать боли, если привязанности не было.

### ER2 — Emotion must be earned by stakes + consequence
Эмоция должна вытекать из:
- ставки
- выбора
- последствий
Не из музыки и крупного плана сами по себе.

### ER3 — Anchors must be reusable
Якоря обязаны быть такими, чтобы их можно было повторять (эхо).

### ER4 — Contrast is controlled
Контраст усиливает, но не превращает в тональный разрыв.

### ER5 — Payoff timing is a system
Payoff нельзя сливать слишком быстро или держать слишком долго без дыхания.

### ER6 — No cheap manipulation
Запрещено:
- подмена причин пустой трагедией
- шок ради шока без смысла
- “слезодав” без ставки и выбора

---

## REQUIRED ARTIFACT A: RESONANCE MAP (RM)

### RM SCHEMA (CANON)

Header:
- RM_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - episode | arc | season
- VERSION:
- STATUS:
  - draft | canon | deprecated

For each key beat/scene:
- SCENE_ID / BEAT_ID:
- TARGET EMOTION:
  - grief | awe | fear | relief | joy | rage | hope | shame | etc
- INTENSITY (0–10):
- ATTACHMENT DRIVER:
  - care | respect | identification | fear of loss | injustice
- STAKES TYPE:
  - personal | relational | social | existential
- TRIGGER:
  - what causes emotion (choice, loss, reveal)
- CONSTRAINTS:
  - tone limits, humor limits, violence feel
- REQUIRED CONSEQUENCE LINK:
  - what must change after this beat
- ANCHOR USED:
  - EAR_ID (optional)
- CONTRAST TOOL:
  - silence, light shift, tempo drop, etc
- PAYOFF RELATION:
  - setup | build | payoff | aftershock

Rule:
- Any intensity >=8 must reference attachment + stakes + consequence.

---

## REQUIRED ARTIFACT B: EMOTIONAL ANCHOR REGISTRY (EAR)

### EAR SCHEMA (CANON)

- EAR_ID:
- RM_ID:

Anchors (repeat):
- ANCHOR:
  - object | gesture | phrase | motif | place | sound
- EMOTION LINKED:
- INTRO SCENE:
- REUSE RULE:
  - when to bring it back
- EVOLUTION RULE:
  - how it changes over time
- DO NOT:
  - misuse cases that cheapen it

Rule:
- At least 3 anchors per season/large arc (unless minimalism is intended).

---

## REQUIRED ARTIFACT C: ECHO PATTERN PLAN (EPP)

### EPP SCHEMA (CANON)

- EPP_ID:
- RM_ID:

Echo patterns (repeat):
- PATTERN TYPE:
  - repetition | inversion | absence | corrupted echo | delayed return
- ANCHOR ID:
- FIRST USE:
- RETURN USE:
- WHAT CHANGED:
  - context, ownership, meaning
- EFFECT:
  - amplify grief, turn hope into dread, etc

Rule:
- At least one inversion or absence pattern in a long arc.

---

## REQUIRED ARTIFACT D: PAYOFF TIMING RULES (PTR)

### PTR SCHEMA (CANON)

- PTR_ID:
- RM_ID:

Timing rules:
- MAX BUILD LENGTH WITHOUT RELEASE:
- MIN BREATH AFTER PEAK:
- AFTERSHOCK POLICY:
  - short quiet beat after high intensity
- EDITING GUIDANCE:
  - slower cuts at grief, tighter at fear, etc
- MUSIC GUIDANCE:
  - enter/exit rules (underscore vs none)
- SILENCE POLICY:
  - when silence is mandatory

Rule:
- Every peak (>=8) must have a breath window and an aftershock beat.

---

## REQUIRED ARTIFACT E: ANTI-MANIPULATION POLICY (AMP)

### AMP SCHEMA (CANON)

- AMP_ID:
- RM_ID:

Forbidden tactics:
- “sad music instead of stakes”
- “random death without attachment”
- “shock gore without consequence”
- “betrayal without setup”
- “miracle rescue without cost”

Required honesty checks:
- WHY THIS HURTS:
- WHAT IT COSTS:
- WHO CHOSE WHAT:
- WHAT CHANGES AFTER:

Rule:
- If honesty checks cannot be answered, beat is invalid.

---

## REQUIRED ARTIFACT F: RESONANCE QC GATES (RQG)

### RQG SCHEMA (CANON)

- RQG_ID:
- RM_ID:

Gates:
1) Attachment gate:
   - audience has reason to care
2) Stakes gate:
   - something meaningful is at risk
3) Choice gate:
   - someone chose, or failed to choose
4) Consequence gate:
   - post-state changes are real
5) Tone gate:
   - emotion fits tone contract
6) Manipulation gate:
   - no cheap tactics
7) Echo gate:
   - anchors and echoes are consistent

Rule:
- Fail 2+ gates → beat/scene must be rewritten.

---

## RESONANCE PATTERNS (STANDARD)

### Pattern 1: Loss with responsibility
- grief amplified by “it was my choice”

### Pattern 2: Hope with cost
- joy underlined by sacrifice (earned relief)

### Pattern 3: Awe with danger
- wonder mixed with threat (sacred + fear)

### Pattern 4: Injustice ignition
- anger + moral clarity (or gray shame)

### Pattern 5: Quiet intimacy
- low intensity, high attachment (silence and micro-gestures)

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- high-intensity moments have no attachment setup
- scenes try to “force” emotion via music/visuals only
- betrayals come from nowhere
- violence replaces stakes
- no aftershock beat after peak
- anchors are reused randomly or too often (cheapening)
- emotional tone contradicts the locked tone bible

Fix options:
- add attachment beats earlier
- add consequence links and post-state deltas
- convert shock into system shock or earned turning point
- add aftershock + breath windows via PTR
- define or reduce anchors and enforce reuse rules
- rewrite for choice and responsibility

---

## PROCEDURE (HOW TO RUN)

1) Import tone locks (TB) and arc beats
2) Map target emotions per beat (RM)
3) Define attachment drivers and stakes
4) Create anchors (EAR) and echo plan (EPP)
5) Define payoff timing rules (PTR)
6) Add anti-manipulation policy (AMP)
7) Run QC gates (RQG) on key scenes
8) Canonize RM/EAR and enforce reuse + honesty

---

## QC CHECKLIST (MANDATORY)

- RM exists for key beats?
- peaks reference attachment + stakes + consequence?
- EAR has reusable anchors with reuse rules?
- EPP defines echoes (incl. inversion/absence)?
- PTR enforces breath + aftershock?
- AMP forbids cheap tactics and enforces honesty questions?
- RQG gates defined and used?

---

## VALIDATION RULES

- ERV1: Emotional hits are earned via attachment, stakes, choice, and consequence.
- ERV2: Anchors and echoes create emotional continuity across arcs.
- ERV3: Payoff timing includes breath and aftershock, preserving credibility.
- ERV4: System avoids cheap manipulation and maintains tone contract.

---

OWNER: Universe Engine
LOCK: FIXED
