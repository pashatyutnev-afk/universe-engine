# Character Core Engine
FILE: 01__CHARACTER_CORE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines canonical character identity and invariant core; produces Character Spec payload that anchors all downstream character engines (motivation, values, psychology, behavior, dialogue, evolution)

---

## PURPOSE

Character Core — это “кто он” как система:
- идентичность и архетип
- базовые ценности и табу
- главные привязанности (что болит)
- внутренний конфликт
- пределы (что он не сделает)
- то, что должно оставаться узнаваемым

Без ядра:
- персонаж “плывёт” по сценам
- мотивации противоречат
- диалоги становятся случайными
- эволюция выглядит как подмена

---

## NON-GOALS

- не расписывает динамику желаний (это Motivation & Desire engine)
- не делает глубокую психику (это Character Psychology engine)
- не строит поведение по ситуациям (Behavior engine)
Он делает фундаментальную “конституцию” персонажа.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Story premise / role in structure (from narrative engines)
- World constraints (culture/laws/tech level) if known
- Theme axis/questions (optional, from Theme engine)

### PRODUCES
- CHARACTER SPEC (CS) — canonical payload
- CORE INVARIANTS (what must remain stable)
- LIMITS + TABOOS set
- INTERNAL CONFLICT statement
- ROLE IN STORY + FUNCTION tags

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md (role placement)
- 02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md (theme alignment optional)
- 04_DOMAIN_WORLD_ENGINES constraints (optional)

### OUTPUT_TARGET
- Feeds:
  - 03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md
  - 03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG.md
  - 03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG.md
  - 03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md
  - 03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md
  - 03_DOMAIN_CHARACTER_ENGINES/10__CHARACTER_EVOLUTION_ENG.md

---

## CANON TERMS

### CORE INVARIANT
Признак, который должен сохраняться:
- способ реагировать
- ключевая ценность
- ключевая рана/привязанность
- стиль решений

### LIMIT / TABOO
Граница: “он так не поступит” (или поступит только с огромной ценой).

### INTERNAL CONFLICT
Две силы внутри персонажа, которые нельзя полностью примирить без изменения.

### STORY FUNCTION
Функция в системе истории:
- protagonist | antagonist | mentor | foil | catalyst | witness | trickster | guardian

---

## REQUIRED ARTIFACT: CHARACTER SPEC (CS)

### CS SCHEMA (CANON PAYLOAD)

Header:
- CHARACTER_ID:
- NAME:
- STATUS:
  - draft | active | locked
- VERSION:
- SCOPE_TAGS:
  - episode/arc/season/book refs (optional)

Identity:
- ARCHETYPE (optional):
- STORY FUNCTION:
- PUBLIC FACE (how others see):
- PRIVATE SELF (truth inside):
- CORE WOUND (what hurt them):
- CORE NEED (what they truly need):
- CORE WANT (what they think they want):

Values & Limits:
- CORE VALUES (3–7):
- TABOOS / LIMITS (1–5):
- LINE THEY WON'T CROSS (default):
- PRICE IF THEY CROSS IT (if ever):

Attachments:
- PRIMARY ATTACHMENT:
  - person/idea/place
- SECONDARY ATTACHMENTS:
- FEAR OF LOSS:
  - what loss breaks them

Competence & Tools:
- SKILLS / ADVANTAGES:
- FLAWS / WEAKNESSES:
- RESOURCE ACCESS:
- SIGNATURE TOOL/OBJECT (optional):
- BODY LIMITS (optional):

Internal Mechanics:
- INTERNAL CONFLICT (one sentence):
- DEFAULT COPING STRATEGY:
  - fight | flight | freeze | fawn | negotiate | joke | control
- TRIGGER LIST (optional):
- COMFORT ZONE (where stable):
- STRESS MODE (how degrade):

Role Constraints:
- WHAT MUST NEVER CHANGE (invariants list):
- WHAT IS ALLOWED TO CHANGE (evolution channels):
- THEME LINK (optional):
  - which theme question they embody

Continuity Locks:
- CANON FACTS:
  - facts that must remain true
- KNOWLEDGE STATE (initial):
  - what they know at baseline
- RELATIONSHIP FLAGS (initial):
  - key relationships baseline

Validation:
- CHECKS PASSED:
- RISKS/FLAGS:
- NEXT HANDOFF:
  - Motivation / Values / Psychology etc.

---

## CHARACTER CORE RULES (CANON)

### CC1 — Want vs Need separation
WANT — поверхностная цель.
NEED — внутренний дефицит.
Если нет NEED → персонаж часто плоский.

### CC2 — Internal conflict is mandatory
Без внутреннего конфликта персонаж либо “идеал”, либо “функция”.

### CC3 — Limits exist
Если у персонажа нет границ — он становится “универсальным инструментом сюжета”.

### CC4 — Invariants are explicit
Минимум 2–5 инвариантов должны быть записаны.

### CC5 — Change channels are declared
Чтобы эволюция не выглядела подменой, заранее фиксируем:
- что может меняться
- что почти не меняется

---

## PROCEDURE (HOW TO RUN)

1) Assign story function + role placement
2) Define want/need/wound
3) Write internal conflict
4) Define values + limits + attachments
5) Define competence, flaws, stress mode
6) Declare invariants + allowed change channels
7) Set continuity locks (facts/knowledge/relationships)
8) Run QC checklist
9) Output CS

---

## QC CHECKLIST (MANDATORY)

- is function in story declared?
- want/need/wound present and distinct?
- internal conflict written as tension between two forces?
- values 3–7 and at least 1 taboo/limit?
- invariants list exists?
- allowed-to-change list exists?
- continuity locks (facts/knowledge/relationships) present?

---

## VALIDATION RULES

- CHV1: CS schema complete (no missing mandatory fields).
- CHV2: Want/Need/Wound and Internal Conflict exist.
- CHV3: Values + Limits are explicit.
- CHV4: Invariants + Change Channels declared.

---

OWNER: Universe Engine
LOCK: FIXED
