# Character Psychology Engine
FILE: 04__CHARACTER_PSYCHOLOGY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines character psychological mechanics (wounds, triggers, defense patterns, coping strategies, stress degradation); produces a Psychology Profile that makes behavior and dialogue consistent under pressure

---

## PURPOSE

Психология — это “как он устроен изнутри”:
- что его триггерит
- как он защищается
- как он деградирует под стрессом
- как он оправдывает и избегает боли
- почему его выборы повторяются

Движок нужен, чтобы персонаж был:
- живой
- последовательный
- узнаваемый в давлении

---

## NON-GOALS

- не заменяет терапию и клинические диагнозы
- не требует реальных псих. диагнозов (можно, но осторожно)
- не определяет мораль/ценности (это Moral & Value)
Он задаёт **поведенческую механику психики**, пригодную для письма.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Character Spec (CS)
- Motivation Map (MM)
- Value Framework (VF) (optional but helpful)
- Stakes/Tension (STS) (optional for pressure testing)

### PRODUCES
- PSYCHOLOGY PROFILE (PP) — canonical artifact
- TRIGGER LIST + RESPONSE PATTERNS
- DEFENSE MECHANISMS MAP
- STRESS LADDER (low->mid->high degradation)
- RECOVERY/REGULATION routines (how they stabilize)

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG.md
- 03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md

### OUTPUT_TARGET
- Feeds:
  - 03__CHARACTER_BEHAVIOR_ENG
  - 07__DIALOGUE_ENG
  - 09__GROWTH_TRAUMA_ENG
  - 10__CHARACTER_EVOLUTION_ENG
  - 02__NARRATIVE_CONTINUITY_ENG (state persistence)

---

## CANON TERMS

### WOUND
Глубокая рана/событие/дефицит, который формирует реакции.

### TRIGGER
Стимул, который активирует рану:
- фраза, ситуация, тип власти, запах, тема, потеря контроля

### DEFENSE MECHANISM
Способ защиты от боли/стыда/страха:
- отрицание, рационализация, контроль, юмор, агрессия, избегание

### COPING
Как они пытаются справляться:
- здорово или нездорово

### STRESS MODE
Поведение под нагрузкой, когда ресурсы падают.

---

## DEFENSE MECHANISMS (TOOLBOX)

Common set (writer-friendly):
- CONTROL: давить порядок и правила
- AVOIDANCE: уходить, тянуть, исчезать
- AGGRESSION: нападать, унижать, доминировать
- HUMOR: обесценивать через шутку
- INTELLECTUALIZE: уходить в анализ вместо чувства
- PEOPLE-PLEASE: угождать ради безопасности
- NUMBING: притуплять (работа, вещества, адреналин)
- PROJECTION: видеть в других то, что в себе не принять

Rule:
- choose 1–3 primary defenses.

---

## REQUIRED ARTIFACT: PSYCHOLOGY PROFILE (PP)

### PP SCHEMA (CANON)

Header:
- PP_ID:
- CHARACTER_ID:
- SCOPE:
- VERSION:
- STATUS:

Core Wound Model:
- CORE WOUND:
- ORIGIN (optional):
  - event/period
- CORE FEAR (psych-level):
- CORE SHAME (optional):
  - what they feel unworthy about
- CORE BELIEF (distorted belief):
  - e.g., "If I lose control, I die."

Trigger System:
- TRIGGER LIST (3–10):
  - trigger -> what it activates
- EARLY WARNING SIGNS:
  - micro-signs before blowup
- THRESHOLD:
  - what makes trigger “go critical”

Defense & Coping:
- PRIMARY DEFENSES (1–3):
- SECONDARY DEFENSES (0–3):
- HEALTHY COPING (list):
- UNHEALTHY COPING (list):
- REGULATION ROUTINE:
  - how they calm down when they can

Stress Ladder (degradation):
- LOW STRESS:
  - how they behave
- MID STRESS:
  - distortion patterns
- HIGH STRESS:
  - meltdown / shutdown / attack / escape
- AFTERMATH:
  - guilt, denial, repair attempts

Attachment & Loss Sensitivity:
- ATTACHMENT POINTS:
  - who/what anchors them
- LOSS SENSITIVITY:
  - what loss breaks them
- PROTECTIVE BEHAVIORS:
  - what they do to prevent loss (often unhealthy)

Relational Patterns:
- DEFAULT RELATIONSHIP MODE:
  - cling | avoid | control | test | submit | mirror
- TRUST STYLE:
  - fast | slow | never | transactional
- CONFLICT STYLE:
  - confront | withdraw | passive-aggressive | negotiate

Narrative Integration Hooks:
- WHAT THIS PSYCH MODEL ENABLES:
  - behaviors we can reliably write
- WHAT MUST NOT HAPPEN (unless evolved):
  - out-of-character psychological moves
- EVOLUTION PATH:
  - what can heal / what can worsen (handoff to growth/trauma engine)

---

## PSYCHOLOGY RULES (CANON)

### CP1 — Triggers must produce predictable pattern
Если trigger активирован, должно быть:
- предсказуемое изменение тактики/тона/решений

### CP2 — Defense has a cost
Защита всегда “платная”:
- портит отношения
- мешает цели
- усиливает shame
Если защита бесплатна → она не работает драматически.

### CP3 — Stress ladder must be consistent
Персонаж не может быть “спокоен” при high stress без причины.
Нужны:
- ресурсы (support)
- coping
- подготовка (growth)

### CP4 — Recovery must exist (or declared absent)
Если персонаж никогда не восстанавливается — он ломается слишком рано.
Либо declared: “no recovery access” (тогда это канон ограничение).

### CP5 — Avoid clinical labels unless required
Если используются клинические термины, нужно:
- осторожность
- consistency
Но базовый режим — writer-friendly model.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- stress reaction varies randomly across similar triggers
- defenses appear without cost
- coping contradicts declared habits
- character “heals instantly” after major wound event
- relational style flips with no bridge

Fix options:
- define stable stress ladder
- add defense cost
- add recovery routine or declare breakdown
- add bridging scenes for change
- align relational patterns with attachments

---

## PROCEDURE (HOW TO RUN)

1) Read CS + MM
2) Define wound -> fear -> distorted belief
3) List triggers and early warning signs
4) Choose 1–3 primary defenses and their costs
5) Build stress ladder (low/mid/high + aftermath)
6) Add coping + regulation routine
7) Define relational patterns
8) Output PP and lock for scope

---

## QC CHECKLIST (MANDATORY)

- wound/fear/belief exist?
- 3–10 triggers exist?
- primary defenses 1–3 exist and costs defined?
- stress ladder low/mid/high exists?
- coping + regulation routine exist (or declared absent)?
- relational patterns consistent?

---

## VALIDATION RULES

- CPV1: PP complete with wound, triggers, defenses, stress ladder.
- CPV2: Defenses have explicit costs.
- CPV3: Stress reactions are consistent across similar conditions.
- CPV4: Recovery/regulation is defined or explicitly denied.

---

OWNER: Universe Engine
LOCK: FIXED
