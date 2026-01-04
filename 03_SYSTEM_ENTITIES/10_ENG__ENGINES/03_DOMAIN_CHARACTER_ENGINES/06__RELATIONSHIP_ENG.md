# Relationship Engine
FILE: 06__RELATIONSHIP_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines and tracks relationships as stateful systems (bond, trust, power, attachment, conflict loops); produces Relationship Map and Relationship Ledger enabling consistent interpersonal dynamics across scenes/arcs with continuity locks

---

## PURPOSE

Отношения — это “почему они так влияют друг на друга”.
Движок нужен, чтобы:
- отношения были **состоянием**, а не “тегом”
- доверие/власть/близость менялись по событиям
- конфликтные циклы повторялись (и эволюционировали)
- любые сцены “между людьми” были заряжены смыслом

---

## NON-GOALS

- не пишет диалог (Dialogue engine)
- не описывает внутреннюю психику (Psychology engine)
- не заменяет сюжетные события
Он моделирует **взаимодействие двух и более персонажей** как систему.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Behavior Spec (BS) for each character
- Motivation Map (MM) for each character
- Value Framework (VF) for each character
- Psychology Profile (PP) (optional but helpful)
- Scene Specs (SS) (optional for per-scene tracking)
- Continuity Ledger (CL) (integration requirement)

### PRODUCES
- RELATIONSHIP MAP (RM) — canonical artifact
- RELATIONSHIP LEDGER (RLSL) — stateful tracking
- POWER/TRUST/INTIMACY axes per pair
- CONFLICT LOOP model
- “SCENE RELATIONSHIP BEATS” hooks

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md (state locks)

### OUTPUT_TARGET
- Feeds:
  - Dialogue engine (tone, subtext)
  - Scene construction (beats, tension)
  - Character evolution (relationship-driven change)
  - Continuity (relationship state changes)

---

## CANON TERMS

### BOND
Связь (привязанность) — почему они продолжают быть рядом.

### TRUST
Доверие — насколько один допускает другого к уязвимому.

### POWER
Власть — кто определяет рамки, решения, доступ к ресурсам.

### INTIMACY
Близость — эмоциональная/психологическая дистанция.

### CONFLICT LOOP
Повторяющийся цикл: триггер → реакция → эскалация → разрыв/ремонт.

### REPAIR
Как они чинят связь (если чинят).

---

## RELATIONSHIP AXES (STANDARD)

Для каждой пары A↔B фиксируем:

- TRUST (0–10)
- POWER BALANCE:
  - A> B | B> A | equal | unstable
- INTIMACY (0–10)
- SAFETY (0–10):
  - насколько рядом “безопасно”
- DEPENDENCY (0–10):
  - насколько один зависит от другого

Rule:
- нельзя менять эти оси без события/бейта (ledger entry).

---

## REQUIRED ARTIFACT A: RELATIONSHIP MAP (RM)

### RM SCHEMA (CANON)

Header:
- RM_ID:
- SCOPE:
- VERSION:
- STATUS:

Entities:
- CHARACTER_IDS:
- RELATIONSHIP PAIRS:
  - list of pairs

For each pair (repeat):
- PAIR_ID: R-0001 (A_ID__B_ID)
- RELATIONSHIP TYPE:
  - ally | rivals | lovers | family | mentor | enemies | fragile alliance | obsession
- BOND REASON:
  - why they stay connected
- PRIMARY TENSION:
  - what pulls them apart
- AXES INITIAL:
  - trust/power/intimacy/safety/dependency
- MUTUAL NEED:
  - what each needs from the other
- MUTUAL FEAR:
  - what each fears in the other
- CONTROL POINTS:
  - what each uses as leverage
- SUBTEXT THEME:
  - what this relationship is “about”
- CONFLICT LOOP:
  - trigger -> reaction -> escalation -> rupture/repair
- REPAIR STYLE:
  - apologize | bargain | punish | avoid | gift | confession
- BREAK CONDITION:
  - what would permanently sever them
- REDEMPTION CONDITION (optional):
  - what would truly heal them

---

## REQUIRED ARTIFACT B: RELATIONSHIP STATE LEDGER (RLSL)

### RLSL SCHEMA (CANON)

Header:
- RLSL_ID:
- SCOPE:
- VERSION:
- STATUS:
- LAST_UPDATED_SCENE_ID:

Entries (repeat):
- ENTRY_ID:
- PAIR_ID:
- SCENE_ID:
- EVENT/BEAT:
  - what happened
- AXES BEFORE:
  - trust/power/intimacy/safety/dependency
- AXES AFTER:
  - trust/power/intimacy/safety/dependency
- WHY IT CHANGED:
  - consequence of action/choice
- NEW RULE (optional):
  - “after this, they will never…”
- FLAGS:
  - betrayal | coercion | vulnerability | repair | escalation
- CONTINUITY LOCK:
  - what must be remembered going forward

Rule:
- RLSL entries must be mirrored to Narrative Continuity if relationship is canon-critical.

---

## RELATIONSHIP RULES (CANON)

### R1 — Relationships are stateful
Нельзя: “они друзья” без осей и динамики.

### R2 — Change requires an event
Любое изменение trust/power/intimacy требует:
- beat, или
- reveal, или
- sacrifice, или
- betrayal
И фиксируется в ledger.

### R3 — Conflict loop must repeat
Если отношений нет в повторяемом цикле — они плоские.
(можно deliberate “stable bond”, но declared explicitly)

### R4 — Power must be explicit
Даже в любви есть власть:
- ресурс
- знание
- статус
Если власть не описана — сцены теряют напряжение.

### R5 — Repair has a cost
Ремонт без цены делает связь игрушечной.
Цена может быть:
- признание
- уступка
- потеря контроля
- жертва

### R6 — No free betrayal
Предательство должно:
- менять оси резко
- иметь последствия в continuity
- влиять на future tactics (Behavior)

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- trust jumps without a beat
- power flips with no leverage change
- intimacy rises after harm with no repair
- conflict loop never appears on-screen
- relationship type contradicts actions repeatedly

Fix options:
- add explicit vulnerability/repair beat
- add leverage event (resource/knowledge shift)
- adjust axes and lock them
- write a rupture scene or reconciliation with cost
- revise relationship type tag

---

## PROCEDURE (HOW TO RUN)

1) For each key pair: define type, bond reason, primary tension
2) Set initial axes values
3) Define mutual need/fear + control points
4) Define conflict loop + repair style
5) Define break condition (what ends it)
6) Create ledger:
   - update axes per scene beats
7) Sync critical relationship changes to Continuity Ledger

---

## QC CHECKLIST (MANDATORY)

- each key pair has axes initial?
- bond reason and primary tension exist?
- conflict loop defined?
- repair style defined?
- break condition defined?
- ledger entries exist for major beats?
- continuity locks updated for canon relationships?

---

## VALIDATION RULES

- RV1: RM exists with axes + loop for each key pair.
- RV2: Relationship changes are recorded in RLSL.
- RV3: Power and leverage are explicit.
- RV4: Betrayals/repairs produce lasting continuity locks.

---

OWNER: Universe Engine
LOCK: FIXED
