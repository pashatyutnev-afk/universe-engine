# Metaphor Engine
FILE: 05__METAPHOR_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Designs and governs metaphor systems by mapping abstract meanings to concrete carriers (scenes, objects, rituals, mechanics) with clarity levels, constraints, evolution rules, and QC gates; produces Metaphor Maps, Carrier Catalogs, Do/Don't lists, and Cross-Engine Compatibility rules to keep metaphors readable, intentional, and non-contradictory to tone/symbolism/canon

---

## PURPOSE

Метафора — это перенос:
- **ABSTRACT MEANING** → **CONCRETE CARRIER**
(идея становится предметом/действием/механикой/ситуацией)

Движок нужен, чтобы:
- метафоры были **осознанны и повторяемы**
- сохранялась читаемость (не “слишком умно”)
- метафоры не конфликтовали с символизмом
- метафоры не ломали причинность мира

---

## NON-GOALS

- не заменяет Theme & Meaning (что хотим сказать)
- не заменяет Symbolism (канонические знаки)
- не заменяет Visual Composition (как кадрировать)
Он отвечает за **конструкцию метафоры** как инженерного решения.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Theme/Meaning targets
- Tone/Mood locks
- Symbol Registry (if exists)
- World constraints (laws, tech, culture)
- Character arcs and conflict stakes

### PRODUCES
- METAPHOR MAP (MM) — canonical artifact
- CARRIER CATALOG (CCAT)
- CLARITY LEVEL POLICY (CLP)
- METAPHOR USAGE RULES (MUR)
- ANTI-CONFLICT GATES (MCG)
- “METAPHOR TO DEPARTMENT” translation (MDT)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG.md (collision prevention)
- 05_EXPRESSION_ENGINES family (events/conflict/payoffs)

### OUTPUT_TARGET
- Feeds:
  - scene writing and beat design
  - production prompts and shot lists
  - prop/set/motif decisions
  - dialogue subtext planning

---

## CANON TERMS

### ABSTRACT (SOURCE)
То, что хотим выразить:
- свобода, вина, распад, вера, власть, пустота

### CARRIER (TARGET)
То, во что переносим:
- объект, действие, ритуал, механизм, правило мира

### MAPPING
Связка “что значит” ↔ “что показывает”.

### CLARITY LEVEL
Насколько метафора “в лоб”:
- explicit / readable / subtle / cryptic

### METAPHOR COLLISION
Конфликт:
- метафора начинает выглядеть как символ другого значения
- или противоречит тону/миру

---

## METAPHOR RULES (CANON)

### M1 — Metaphor must not violate world laws
Метафора не может требовать невозможного для мира.

### M2 — Metaphor must be readable at chosen clarity level
Если выбрана “readable”, зритель должен понять без лекции.

### M3 — One carrier = one primary meaning (by default)
Если один объект значит “всё”, он значит “ничего”.
Мультизначность допустима, но ограниченно и явно.

### M4 — Metaphor must serve theme and arc
Если метафора не усиливает тему/выбор/последствие — убрать.

### M5 — Metaphors must not override symbols
Если есть зарегистрированный символ, метафора не должна его переопределять.
Если нужно — оформляется как evolution/override в governance.

### M6 — Metaphor repetition requires evolution
Повтор метафоры обязан:
- усиливать
- инвертировать
- менять контекст (эхо)

---

## REQUIRED ARTIFACT A: METAPHOR MAP (MM)

### MM SCHEMA (CANON)

Header:
- MM_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - episode | arc | season | world
- VERSION:
- STATUS:
  - draft | canon | deprecated

Mappings (repeat):
- METAPHOR_ID:
- ABSTRACT MEANING (source):
- CARRIER (target):
  - object | action | ritual | mechanic | environment
- PRIMARY MESSAGE:
  - what audience should feel/understand
- CLARITY LEVEL:
  - explicit | readable | subtle | cryptic
- CONTEXT LIMITS:
  - where it applies (faction/location/arc)
- FIRST USE:
- REUSE PLAN:
  - reinforce | invert | corrupt | absence
- CONSTRAINTS:
  - tone constraints, violence feel, humor policy
- COLLISION RISKS:
  - possible symbol overlap
- REQUIRED CONSEQUENCE LINK:
  - what changes after metaphor beat

Rule:
- Any canon metaphor must have a mapping entry.

---

## REQUIRED ARTIFACT B: CARRIER CATALOG (CCAT)

### CCAT SCHEMA (CANON)

- CCAT_ID:
- MM_ID:

Carriers (repeat):
- CARRIER ID:
- TYPE:
  - object/action/ritual/mechanic/environment
- VISUAL SIGNATURE:
- SOUND SIGNATURE:
- WHERE IT EXISTS IN WORLD:
- COST / LIMITATION:
  - why it’s not free/constant
- WHAT IT CAN’T MEAN:
  - anti-overload rule
- MAINTENANCE:
  - how to keep it consistent

Rule:
- Each carrier must include “what it can’t mean” to prevent semantic spam.

---

## REQUIRED ARTIFACT C: CLARITY LEVEL POLICY (CLP)

### CLP SCHEMA (CANON)

- CLP_ID:
- MM_ID:

Policy:
- DEFAULT CLARITY:
- WHEN EXPLICIT IS ALLOWED:
- WHEN CRYPTIC IS ALLOWED:
- “READABILITY FLOOR”:
  - minimum clarity for main storyline
- SUPPORT MECHANISMS:
  - how to help audience (echo, dialogue subtext, framing, music)

Rule:
- Main arcs must not rely on cryptic-only metaphors.

---

## REQUIRED ARTIFACT D: METAPHOR USAGE RULES (MUR)

### MUR SCHEMA (CANON)

- MUR_ID:
- MM_ID:

Rules:
- MAX METAPHORS PER SCENE (cap):
- MAX NEW METAPHORS PER EPISODE:
- NO-STACK ZONES:
  - where metaphors should be minimal (climax clarity zones)
- DIALOGUE SUBTEXT POLICY:
  - how much can be said vs shown
- VISUAL vs VERBAL BALANCE:

Rule:
- Over-metaphorization kills clarity. Caps are mandatory.

---

## REQUIRED ARTIFACT E: ANTI-CONFLICT GATES (MCG)

### MCG SCHEMA (CANON)

- MCG_ID:
- MM_ID:

Gates:
1) World-law gate:
   - carrier is possible in-world
2) Tone gate:
   - metaphor delivery fits tone locks
3) Symbol collision gate:
   - does not override registered symbol meaning
4) Clarity gate:
   - matches declared clarity level
5) Consequence gate:
   - beat changes something, not decorative
6) Overload gate:
   - caps respected, no stacking chaos

Rule:
- Fail 2+ gates → metaphor beat must be rewritten.

---

## REQUIRED ARTIFACT F: METAPHOR → DEPARTMENT TRANSLATION (MDT)

### MDT SCHEMA (CANON)

- MDT_ID:
- MM_ID:

Mapping:
- TO VISUAL:
  - framing emphasis, recurring visuals, color cues
- TO SOUND:
  - motif, silence, texture cues
- TO EDITING:
  - cut patterns for metaphor reveals
- TO PERFORMANCE:
  - gestures, pacing, micro-expression
- TO DIALOGUE:
  - subtext lines, taboo phrasing, echo lines

Rule:
- At least 1 directive for any “primary arc metaphor”.

---

## STANDARD METAPHOR PATTERNS

### Pattern 1: Mechanic metaphor
- world rule/mechanic embodies meaning (e.g., memory tax)

### Pattern 2: Ritual metaphor
- ritual repeats and evolves across arc (echo system)

### Pattern 3: Environmental metaphor
- weather/space/ruins embody internal state (bounded by realism)

### Pattern 4: Object burden
- object carries guilt/hope and changes hands

### Pattern 5: Absence metaphor
- missing thing becomes signal (empty chair, silent radio)

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- metaphors appear but have no map entry
- multiple metaphors stack in a climax and confuse stakes
- carrier means contradictory things across scenes
- metaphor requires impossible world behavior
- metaphor visually collides with existing symbol registry
- audience needs external explanation to understand a core beat

Fix options:
- map it in MM and declare clarity
- reduce metaphors per scene and move some to subplots
- enforce one primary meaning per carrier
- redesign carrier or scope it to a faction/location
- align metaphor with symbol evolution or remove collision
- add echoes/support mechanisms (dialogue subtext, framing, music)

---

## PROCEDURE (HOW TO RUN)

1) Import theme targets and tone locks
2) Draft MM mappings for key arcs/beats
3) Build CCAT for carriers (with costs and “can’t mean”)
4) Set clarity policy (CLP) and readability floor
5) Set usage caps (MUR)
6) Run anti-conflict gates (MCG) against world/symbol/tone
7) Translate to departments (MDT)
8) Canonize MM and enforce usage via QC

---

## QC CHECKLIST (MANDATORY)

- MM exists and has mappings for primary metaphors?
- carriers are cataloged with costs and anti-overload?
- clarity policy defines readability floor?
- usage caps prevent stacking overload?
- gates prevent symbol collision and world-law violations?
- translation exists for visuals/audio/edit/performance/dialogue?

---

## VALIDATION RULES

- MV1: Metaphors are mapped, scoped, and readable at declared clarity levels.
- MV2: Carriers are consistent and do not become “everything”.
- MV3: Metaphors do not override symbols or world laws.
- MV4: Metaphor system supports theme and arc via echoes and payoff.

---

OWNER: Universe Engine
LOCK: FIXED
