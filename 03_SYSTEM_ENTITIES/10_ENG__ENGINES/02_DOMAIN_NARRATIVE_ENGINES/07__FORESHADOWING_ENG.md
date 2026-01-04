# Foreshadowing Engine
FILE: 07__FORESHADOWING_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Designs and validates foreshadowing (setups, seeds, hints) and maps them to future payoffs; prevents unfair reveals, random twists, and forgotten setups through an explicit foreshadow-payoff registry

---

## PURPOSE

Foreshadowing — это “честная магия истории”:
- зритель не должен чувствовать “взято из воздуха”
- подсказки должны существовать до раскрытия
- setups не должны забываться
- payoff должен быть заслуженным

---

## NON-GOALS

- не делает сами твисты (Twist & Reveal)
- не определяет структуру сезона (Story Structure)
- не определяет драматическую дугу (Dramatic Arc)
Он отвечает за **посевы** и их карту до payoff.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Story Structure Spec (SSS)
- Scene Specs (SS)
- Stakes & Tension Spec (STS) (optional, helpful)
- Planned reveals/twists list (from 08) if known

### PRODUCES
- FORESHADOW MAP (FSM) — canonical artifact
- SETUP/PAYOFF registry (seed -> payoff)
- FAIRNESS CHECK report (unfair reveal detector)
- FORGOTTEN SETUP FLAGS

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md

### OUTPUT_TARGET
- Feeds Twist & Reveal (08) and Continuity (09)
- Provides hooks to production (visual/audio motifs) when needed

---

## CANON TERMS

### SETUP (SEED)
Элемент, который вводится заранее и потом “возвращается” как payoff:
- объект
- правило мира
- привычка героя
- фраза/символ
- деталь окружения
- музыкальный мотив

### HINT
Слабый seed: не обязателен, но усиливает честность.

### PLANT
Явный seed: зритель “видит”, но не понимает до конца.

### SHADOW
Атмосферный seed: ощущение, предчувствие (тонкая штука).

### PAYOFF
Возврат setup, который:
- меняет смысл
- решает конфликт
- усиливает эмоцию
- раскрывает правду

---

## TYPES OF FORESHADOWING (TOOLBOX)

- OBJECT: предмет/артефакт
- RULE: правило/ограничение
- BEHAVIOR: паттерн поведения
- RELATION: динамика отношений
- INFORMATION: слух/факт/намёк
- SYMBOL: образ/метафора
- MOTIF: повторяющийся звук/цвет/ритм (production hook)
- CONTRAST: “слишком нормальное” как предвестник

Rule:
- each seed has a TYPE.

---

## REQUIRED ARTIFACT: FORESHADOW MAP (FSM)

### FSM SCHEMA (CANON)

Global:
- FSM_ID:
- SCOPE:
  - episode | arc | season | book
- POLICY:
  - subtle | balanced | heavy
- FAIRNESS TARGET:
  - strict | normal | loose (strict recommended)

Registry entries (repeat):
- SEED_ID: FS-0001
- TYPE:
- SETUP SCENE:
  - SCENE_ID
- SETUP FORM:
  - line | prop | action | environment | motif
- SETUP STRENGTH:
  - hint | plant | obvious
- WHAT IS PLANTED:
  - short statement
- PAYOFF TARGET:
  - SCENE_ID / segment
- PAYOFF TYPE:
  - reveal | twist | tool-use | emotional | irony | reversal
- PAYOFF EFFECT:
  - what changes when it hits
- REQUIRED CONTINUITY:
  - what must remain consistent until payoff
- OPTIONAL PRODUCTION HOOKS:
  - visual/audio motif tags
- STATUS:
  - planned | planted | paid | cut
- NOTES:

---

## FORESHADOW RULES (CANON)

### FS1 — Every major payoff must have at least one seed
Если payoff “крупный” (turn/reveal/climax tool),
он обязан иметь seed.
Иначе это unfair reveal.

### FS2 — Seed must be perceivable
Seed должен быть видим/слышим/логически присутствовать.
“Он где-то был, но мы не показывали” — запрещено (если не POV trick, и он declared).

### FS3 — Seeds must not overload
Слишком много seeds:
- зритель устаёт
- история становится загадкой ради загадки
Рекомендуемый лимит:
- episode: 3–7 активных seeds
- arc: 7–15
(можно иначе, но должно быть declared)

### FS4 — Setups must be tracked
Любой seed либо:
- paid,
- либо cut (и это фиксируется),
- либо intentionally unresolved (rare, and must be declared)

### FS5 — Seed strength must match payoff weight
Если payoff огромный, а seed был “микро” — риск unfair.
Либо усиливаем seed, либо уменьшаем payoff.

### FS6 — No retroactive foreshadow
Нельзя добавлять seed “задним числом” после payoff без явного retcon process (governance).

---

## UNFAIR REVEAL DETECTOR (HEURISTICS)

Flag unfair reveal if:
- payoff occurs with no registered seed
- seed exists but after payoff (temporal violation)
- seed too weak for payoff weight (mismatch)
- continuity breaks (seed contradicts later facts)

Fix options:
- add earlier seed
- strengthen seed (plant -> obvious)
- reduce payoff weight
- convert twist into reveal-with-setup

---

## PROCEDURE (HOW TO RUN)

1) Identify planned major payoffs (turns/reveals/tools)
2) For each payoff, design at least 1 seed
3) Place seeds into specific scenes (setup scene)
4) Choose seed strength (hint/plant/obvious)
5) Register entries into FSM
6) Run unfair reveal detector
7) Track status through writing (planned->planted->paid)

---

## QC CHECKLIST (MANDATORY)

- do all major payoffs have seeds?
- are setup scenes earlier than payoff scenes?
- is seed strength proportional to payoff?
- are active seeds within reasonable count?
- are continuity requirements stated?
- are cut seeds marked as cut (not forgotten)?

---

## VALIDATION RULES

- FSV1: FSM exists with seed registry entries.
- FSV2: No major payoff without a seed.
- FSV3: Temporal ordering holds (setup before payoff).
- FSV4: Seeds are tracked to a terminal state (paid/cut/declared unresolved).

---

OWNER: Universe Engine
LOCK: FIXED
