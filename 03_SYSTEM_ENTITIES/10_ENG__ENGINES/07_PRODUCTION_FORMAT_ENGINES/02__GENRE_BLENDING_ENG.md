# Genre Blending Engine
FILE: 02__GENRE_BLENDING_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Governs controlled blending of multiple genres via dominance hierarchy, contract reconciliation, scene-type routing, tone/pacing constraints, and payoff arbitration; produces Blending Specs, Conflict Resolution Rules, and QC Gates that prevent genre soup and maintain audience satisfaction

---

## PURPOSE

Genre blending — это не “всё сразу”.
Это инженерный микс, где:
- есть **PRIMARY GENRE** (контракт №1)
- есть **SECONDARY GENRE(S)** (усилители)
- есть правила: где что проявляется и что нельзя ломать

Движок нужен, чтобы:
- не было жанровой каши
- ожидания аудитории не рушились
- каждый жанр получал свою “выплату” (payoff)
- тон/ритм/визуал не дрейфовали

---

## NON-GOALS

- не выбирает жанр вместо Genre Engine
- не заменяет Tone & Mood Engine
- не заменяет Format Adaptation (платформенная адаптация)
Он фиксирует **механику совмещения контрактов**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Genre Bible(s) (GB) for each genre used
- Tone/Mood locks
- Target platform constraints
- Arc beats and resolution constraints
- Audience promises list

### PRODUCES
- BLENDING SPEC (BS) — canonical artifact
- DOMINANCE HIERARCHY (DH)
- CONTRACT RECONCILIATION TABLE (CRT)
- SCENE ROUTING MAP (SRM)
- PAYOFF ARBITRATION RULES (PAR)
- BLEND FAILSAFE RULES (BFR)
- BLEND QC GATES (BQG)

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG.md
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 05_EXPRESSION_ENGINES (turning points/climax/resolution)

### OUTPUT_TARGET
- Feeds:
  - beat design and scene lists
  - production style translation (camera/light/sound/edit)
  - marketing tags and audience expectation management

---

## CANON TERMS

### PRIMARY GENRE
Жанр-контракт, который нельзя ломать.

### SECONDARY GENRE
Жанр-усилитель, который добавляет специи и сцены, но не ломает основу.

### DOMINANCE HIERARCHY
Иерархия контроля:
- кто управляет тоном
- кто управляет stakes
- кто управляет ритмом
- кто управляет концовкой

### ROUTING
Маршрутизация сцен:
- какие сцены от какого жанра и где

### PAYOFF ARBITRATION
Арбитраж концовки:
- как удовлетворить обещания обоих жанров без предательства primary

---

## CORE RULES (CANON)

### GB1 — Primary contract is non-negotiable
Если primary жанр рушится — всё рушится.

### GB2 — Secondary must be bounded
Secondary ограничен:
- зоной сцен
- частотой
- “тональным потолком”

### GB3 — Every genre promise needs a payoff path
Если обещал mystery и horror:
- mystery требует объяснимости
- horror требует страха/стоимости
И оба должны получить payoff (или intentional subversion).

### GB4 — “Tone owner” must be defined
Если не определить, кто владеет тоном:
- получится хаос (шутки в трагедии, милота в хорроре).

### GB5 — Climax and resolution ownership is explicit
Кто контролирует финал:
- primary почти всегда владелец
- secondary может “окрасить”, но не перевернуть контракт

---

## REQUIRED ARTIFACT A: BLENDING SPEC (BS)

### BS SCHEMA (CANON)

Header:
- BS_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - season | arc | project
- VERSION:
- STATUS:
  - draft | canon | deprecated

Genres:
- PRIMARY GENRE:
- SECONDARY GENRES (1–2):
- BLEND TAGLINE (one sentence):
- BLEND MODE:
  - layered | alternating | fused | bait-switch (rare, governance required)

Owners:
- TONE OWNER:
- STAKES OWNER:
- PACING OWNER:
- RESOLUTION OWNER:

Constraints:
- MAX SECONDARY PRESENCE (%):
- HUMOR CAP:
- CONFUSION CAP:
- VIOLENCE CAP:
- ROMANCE CAP (if relevant):

Payoff plan:
- PRIMARY PAYOFF REQUIREMENTS:
- SECONDARY PAYOFF REQUIREMENTS:
- SUBVERSION FLAGS (if any):

Rule:
- Owners must be defined; otherwise blend is invalid.

---

## REQUIRED ARTIFACT B: DOMINANCE HIERARCHY (DH)

### DH SCHEMA (CANON)

- DH_ID:
- BS_ID:

Domains:
- TONE:
- PACING:
- STAKES:
- CLARITY:
- RESOLUTION:
- VISUAL LANGUAGE:
- SOUND LANGUAGE:

For each domain:
- OWNER GENRE:
- SECONDARY INFLUENCE (allowed/not allowed)
- RED LINES:
  - what can never happen

Rule:
- Tone + Resolution must always have an owner.

---

## REQUIRED ARTIFACT C: CONTRACT RECONCILIATION TABLE (CRT)

### CRT SCHEMA (CANON)

- CRT_ID:
- BS_ID:

Rows (repeat):
- PROMISE (genre A):
- PROMISE (genre B):
- CONFLICT?
  - yes/no
- RESOLUTION STRATEGY:
  - prioritize primary
  - split by act
  - satisfy via alternate payoff
  - intentional subversion (requires plan)
- NOTES:

Common conflicts:
- Mystery clarity vs Surreal ambiguity
- Comedy relief vs Horror dread
- Romance warmth vs Noir cynicism
- Epic scale vs Intimate realism

Rule:
- Any “conflict = yes” requires a strategy.

---

## REQUIRED ARTIFACT D: SCENE ROUTING MAP (SRM)

### SRM SCHEMA (CANON)

- SRM_ID:
- BS_ID:

For each act/episode:
- ZONE:
  - act1/act2/act3 or ep1/ep2
- PRIMARY SCENE TYPES REQUIRED:
- SECONDARY SCENE TYPES ALLOWED:
- “NO-GO SCENES”:
- TRANSITION RULES:
  - how we shift (music/lighting/editing) without tonal whiplash

Rule:
- Secondary scenes must have zones; no free roaming.

---

## REQUIRED ARTIFACT E: PAYOFF ARBITRATION RULES (PAR)

### PAR SCHEMA (CANON)

- PAR_ID:
- BS_ID:

Rules:
- PRIMARY PAYOFF PRIORITY:
- SECONDARY PAYOFF MINIMUM:
- ENDING TYPE LOCK:
- “DUAL PAYOFF TEMPLATE”:
  - how both payoffs can land (sequence)
- “PAYOFF TRADEOFFS”:
  - what can be sacrificed and what cannot
- DEUS-EX BAN POLICY:
  - how to avoid cheating

Rule:
- If secondary payoff breaks primary ending lock → not allowed.

---

## REQUIRED ARTIFACT F: BLEND FAILSAFE RULES (BFR)

### BFR SCHEMA (CANON)

- BFR_ID:
- BS_ID:

Failsafes:
- If tone drift detected → revert to tone owner rules
- If pacing chaos → enforce pacing owner constraints
- If audience confusion > cap → add clarity beats
- If secondary dominates → cut secondary scenes or reduce frequency
- If payoff imbalance → insert payoff micro-beat earlier

Rule:
- Failsafes are the emergency brakes of production.

---

## REQUIRED ARTIFACT G: BLEND QC GATES (BQG)

### BQG SCHEMA (CANON)

- BQG_ID:
- BS_ID:

Gates:
1) Primary contract gate:
   - primary promises intact
2) Ownership gate:
   - tone/pacing/stakes/resolution owners followed
3) Secondary cap gate:
   - secondary presence within limits
4) Transition gate:
   - no tonal whiplash transitions
5) Payoff gate:
   - both genres get payoff per PAR
6) Taboo gate:
   - no forbidden drifts from either GB
7) Clarity gate:
   - confusion within cap, especially near climax

Rule:
- Fail 2+ gates → rewrite blend plan or cut scenes.

---

## STANDARD BLEND MODES (REFERENCE)

### Layered
Primary everywhere, secondary as spice in defined zones.

### Alternating
Episode/act alternates dominant vibe; requires strong transitions + SRM.

### Fused
Genres deeply fused; highest risk; needs strict DH + CRT.

### Bait-switch
Starts as one genre, becomes another.
Requires governance approval + explicit audience strategy.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- tone owner undefined
- resolution owner undefined
- secondary presence exceeds cap
- transitions feel like “different show”
- promises from one genre have no payoff
- required scenes for primary missing
- ending contradicts primary genre contract

Fix options:
- set owners and red lines (DH)
- route secondary scenes into safe zones (SRM)
- reduce secondary frequency and hard-cap it (BS)
- add transition rules (music/lighting/editing)
- adjust payoff sequence (PAR) to satisfy both
- if bait-switch: push through governance and mark explicitly

---

## PROCEDURE (HOW TO RUN)

1) Import GB for each genre (primary + secondary)
2) Draft BS with owners, caps, and blend mode
3) Build DH (who owns what)
4) Build CRT (resolve conflicts)
5) Build SRM (where secondary is allowed)
6) Build PAR (dual payoff and ending lock)
7) Define BFR failsafes
8) Run BQG gates on outlines and finished outputs
9) Canonize BS; log any future blend changes via governance

---

## QC CHECKLIST (MANDATORY)

- BS defines owners + caps + payoff requirements?
- DH defines tone and resolution owners?
- CRT resolves promise conflicts?
- SRM bounds secondary to zones?
- PAR ensures dual payoff without breaking primary?
- BFR provides emergency brakes?
- BQG gates used during production?

---

## VALIDATION RULES

- GBV1: Primary genre contract is preserved.
- GBV2: Secondary genre is bounded and intentional.
- GBV3: Promises from all genres have payoff paths.
- GBV4: Transitions and ending remain coherent and satisfying.

---

OWNER: Universe Engine
LOCK: FIXED
