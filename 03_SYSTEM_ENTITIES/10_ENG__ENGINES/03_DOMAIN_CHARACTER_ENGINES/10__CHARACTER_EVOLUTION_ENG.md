# Character Evolution Engine
FILE: 10__CHARACTER_EVOLUTION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Orchestrates character change across arcs/seasons; consolidates core, motivation, values, psychology, behavior, relationships, and growth/trauma into an Evolution Roadmap with continuity locks, guardrails against character substitution, and measurable proof-of-change moments

---

## PURPOSE

Эволюция персонажа — это контролируемая “траектория”.
Движок нужен, чтобы:
- изменения не были случайными
- персонаж не “подменялся”
- рост/падение имели доказательства в сценах
- continuity фиксировала ключевые повороты
- можно было вести сезон/сагу без развала личности

---

## NON-GOALS

- не пишет сюжет вместо Narrative engines
- не заменяет Growth & Trauma engine (там механика узлов и шрамов)
- не заменяет Continuity engine (там учет)
Этот движок делает **roadmap эволюции** и guardrails.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Character Spec (CS)
- Motivation Map (MM)
- Value Framework (VF)
- Psychology Profile (PP)
- Behavior Spec (BS)
- Relationship Map + Ledger (RM/RLSL)
- Growth/Trauma Tracker + Scar Registry (GTT/SR)
- Narrative Continuity Ledger (NCL)

### PRODUCES
- EVOLUTION ROADMAP (ER) — canonical artifact
- ARC STATES (baseline -> transitional -> new baseline)
- PROOF MOMENTS (scenes that prove change)
- CONTINUITY LOCKS (must-remember invariants)
- CHARACTER SUBSTITUTION GUARDRAILS (anti-OOC rules)

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/09__GROWTH_TRAUMA_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - Narrative structure (arc planning)
  - Scene construction (proof moments)
  - Dialogue/behavior adjustments
  - Canon authority + change control (if rewriting baseline)

---

## CANON TERMS

### BASELINE
Исходное состояние персонажа (до арки/сезона).

### TRANSITION STATE
Промежуточный режим:
- старые привычки ещё есть
- новые решения уже появляются

### NEW BASELINE
Новая стабильность после арки:
- новый выбор стал дефолтом

### PROOF MOMENT
Сцена, где персонаж делает **то, что раньше не мог/не делал**.

### SUBSTITUTION (OOC)
Подмена персонажа, когда автор делает его:
- удобным для сюжета
- умнее/глупее без причины
- “другим человеком” без мостов

---

## REQUIRED ARTIFACT: EVOLUTION ROADMAP (ER)

### ER SCHEMA (CANON)

Header:
- ER_ID:
- CHARACTER_ID:
- SCOPE:
  - arc/season/saga
- VERSION:
- STATUS:

Invariant Core (must persist unless explicitly rewritten):
- CORE INVARIANTS (3–10):
  - traits, values, fears, lines
- HARD LINES (from VF):
- SIGNATURE TACTICS (from BS):
- SIGNATURE VOICE MARKERS (from DS):
- CORE WOUND LINK (from PP):
- IMMUTABLE RELATIONSHIPS (optional):
  - if any are canon-locked

Baseline Snapshot:
- BASELINE GOALS (MM):
- BASELINE BEHAVIOR MODE (BS):
- BASELINE RELATIONSHIP STATE (RM/RLSL):
- BASELINE PSYCH STATE (PP):
- BASELINE COST TOKENS (if used):

Arc Plan (repeat per arc/season unit):
- ARC_ID:
- ARC THEME LINK (optional):
- START STATE:
  - baseline summary
- TARGET SHIFT:
  - what must change (capability/belief/value priority)
- CHANGE TYPE:
  - growth | hardening | corruption | redemption | breakdown
- PRIMARY DRIVER:
  - relationship | loss | failure | success | revelation | duty
- REQUIRED NODES:
  - link to GTT nodes + SR scars (if any)
- BRIDGE BEATS REQUIRED:
  - 1–7 beats/scenes
- PROOF MOMENTS (2–5):
  - scene candidates and what they prove
- RELAPSE WINDOWS:
  - where relapse is expected and why
- COST PAID:
  - what they lose/accept
- NEW BASELINE DEFINITION:
  - what becomes default after arc
- CONTINUITY LOCKS:
  - facts/state that must persist

Substitution Guardrails:
- OOC FORBIDDEN MOVES:
  - list of things they cannot do without bridge beats
- INTELLIGENCE CONSISTENCY:
  - where they are smart/dumb and why
- COMPETENCE BOUNDARIES:
  - what they can/can’t do
- EMOTION RULES:
  - how they show/hide emotion
- RECOVERY LIMITS:
  - how fast they can bounce back

Verification & Updates:
- ARC CHECKPOINTS:
  - mid-arc verification questions
- IF CHANGE FAILS:
  - fallback path (stagnation/partial change)
- REVISION POLICY:
  - changes to invariants require governance pipeline

---

## EVOLUTION RULES (CANON)

### CE1 — Invariants persist by default
Если не объявлено изменение инварианта,
он должен сохраняться во всех сценах.

### CE2 — Proof moments mandatory
Нельзя заявить “он изменился” без сцен-доказательств.

### CE3 — Bridge beats required for big flips
Большие повороты (values/lines/identity) требуют мостов.
Без мостов = подмена.

### CE4 — New baseline must be testable
Новая стабильность должна проявляться в:
- повторяемом выборе
- новой тактике
- изменённой речи
- изменённом отношении

### CE5 — Relapse is structured
Если есть рецидивы:
- у них есть триггеры
- у них есть длительность/окно
- у них есть recovery route

### CE6 — Continuity is enforced
Любой “поворот” фиксируется:
- в continuity ledger
- в ER locks
Иначе система развалится на серии 5–7.

---

## SUBSTITUTION DETECTOR (HEURISTICS)

Flag if:
- character solves problems with skills never established
- value priorities flip with no bridge beats
- voice changes completely without cause
- trauma disappears without healing conditions
- relationship trust jumps without ledger entry
- competence becomes “plot convenient”

Fix options:
- add bridge beats + training/support
- adjust ER to smaller shift
- add relapse window and slow change
- enforce invariants in scene revisions
- record continuity locks

---

## PROCEDURE (HOW TO RUN)

1) Collect CS/MM/VF/PP/BS/DS/RM/RLSL/GTT/SR
2) Define invariants (core must persist)
3) Write baseline snapshot
4) For each arc:
   - target shift
   - required nodes/bridge beats
   - proof moments
   - cost + new baseline
5) Add guardrails (OOC forbidden moves)
6) Define relapse windows and recovery route
7) Sync all locks to continuity
8) Lock ER, update per arc after proofs occur

---

## QC CHECKLIST (MANDATORY)

- invariants list exists?
- baseline snapshot complete?
- each arc has target shift + change type?
- bridge beats listed for major shifts?
- proof moments (2–5) exist per arc?
- new baseline definition testable?
- guardrails list exists?
- continuity locks specified?

---

## VALIDATION RULES

- CEV1: ER exists and references all required artifacts.
- CEV2: Proof moments exist and are tied to target shifts.
- CEV3: Invariants and guardrails prevent substitution.
- CEV4: Continuity locks are defined for all major changes.

---

OWNER: Universe Engine
LOCK: FIXED
