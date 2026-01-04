# Narrative Continuity Engine
FILE: 09__NARRATIVE_CONTINUITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Maintains canonical continuity across scenes/episodes/arcs; tracks fact states, character knowledge states, resource/prop states, and resolves contradictions through explicit continuity ledger entries and governance-compatible fixes

---

## PURPOSE

Continuity — это “память истории”.
Движок гарантирует:
- факты не противоречат друг другу
- последствия сохраняются
- знание персонажей логично (кто что знает и когда узнал)
- предметы/ресурсы/травмы не “телепортируются”
- твисты/раскрытия фиксируются как новая истина

---

## NON-GOALS

- не создаёт события (Expression engines)
- не создаёт сцены (Scene Construction)
- не придумывает мир (World family)
Он фиксирует и охраняет уже созданные факты и изменения.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Scene Specs (SS) (especially BEFORE/AFTER + continuity notes)
- Narrative Logic Spec (NLS)
- Reveal/Twist Plan (RTP)
- World timeline anchors (optional)
- Character states (optional from character engines)

### PRODUCES
- CONTINUITY LEDGER (CL) — canonical artifact
- FACT REGISTRY (current truth)
- KNOWLEDGE REGISTRY (who knows what)
- CONTRADICTION REPORT (flags + fix strategy)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md (for retcons)
- 02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG.md

### OUTPUT_TARGET
- Feeds all downstream: character/world/production
- Acts as “canon gate” before publishing media specs

---

## CANON TERMS

### FACT
Утверждение, которое считается истинным в каноне (в рамках scope).

### STATEFUL FACT
Факт, который меняется:
- location of item
- injury state
- relationship status
- resource availability

### KNOWLEDGE STATE
Кто знает факт, и с какого момента.

### RETCON
Изменение ранее установленного факта.
Разрешено только через governance pipeline.

---

## REQUIRED ARTIFACT: CONTINUITY LEDGER (CL)

### CL SCHEMA (CANON)

Header:
- CL_ID:
- SCOPE:
  - episode | arc | season | book
- VERSION:
- STATUS:
  - active | locked
- LAST_UPDATED_SCENE_ID:

Sections:

### A) FACT REGISTRY (CURRENT)
Entry (repeat):
- FACT_ID: F-0001
- STATEMENT:
- TYPE:
  - world | character | item | resource | relationship | rule | event
- STATEFUL:
  - yes/no
- CURRENT STATE:
  - value (if stateful)
- INTRODUCED_IN:
  - SCENE_ID
- LAST_CHANGED_IN:
  - SCENE_ID (if changed)
- DEPENDENCIES:
  - other FACT_IDs (optional)
- NOTES:

### B) ITEM/RESOURCE TRACKING (STATEFUL)
Entry (repeat):
- ITEM_ID:
- OWNER/HOLDER:
- LOCATION:
- CONDITION:
- LAST_SEEN_SCENE:

### C) CHARACTER STATUS TRACKING (STATEFUL)
Entry (repeat):
- CHARACTER_ID:
- PHYSICAL STATE:
- EMOTIONAL STATE (optional tag):
- GOAL (current):
- INJURIES / LIMITS:
- RELATIONSHIP FLAGS:
- LAST_UPDATED_SCENE:

### D) KNOWLEDGE REGISTRY (WHO KNOWS WHAT)
Entry (repeat):
- KNOW_ID: K-0001
- FACT_ID (or STATEMENT):
- KNOWN_BY:
  - list (characters/factions)
- UNKNOWN_TO:
  - list
- LEARNED_IN:
  - SCENE_ID
- HOW_LEARNED:
  - seen | told | inferred | discovered
- LIES/MISINFO (optional):
  - who believes false version + since when

### E) CHANGE LOG (SEQUENCE)
Entry (repeat):
- CHANGE_ID: C-0001
- SCENE_ID:
- WHAT CHANGED:
  - fact/state/knowledge
- BEFORE:
- AFTER:
- REASON:
  - beat/turn/reveal reference
- IMPACT:
  - what this enables/blocks

### F) CONTRADICTIONS + FIXES
Entry (repeat):
- ISSUE_ID:
- TYPE:
  - logic | timeline | knowledge | prop | rule | relationship
- DESCRIPTION:
- DETECTED_IN:
  - SCENE_ID
- SEVERITY:
  - low | med | high
- FIX STRATEGY:
  - rewrite scene | adjust earlier fact | add bridge scene | retcon (governance)
- STATUS:
  - open | fixed | accepted-intentional

---

## CONTINUITY RULES (CANON)

### NC1 — Every scene must update continuity
Каждая каноническая сцена обязана:
- внести хотя бы 1 entry в change log
или явно “no-change interlude” (редко).

### NC2 — Knowledge cannot teleport
Персонаж не может знать факт без:
- learned_in + how_learned
Иначе — knowledge violation.

### NC3 — Stateful objects/resources are tracked
Если предмет важный — он в item tracking.
“Он где-то был” без следа — запрещено.

### NC4 — Consequences persist
Если stakes engine сказал “последствия обязательны”,
continuity обязана хранить их до устранения через сюжет.

### NC5 — Retcons require governance
Если надо поменять факт задним числом:
- фиксируется как contradiction
- создаётся fix strategy = retcon
- проводится через change control + audit log

### NC6 — Viewer truth vs Character truth may differ
Разрешено, но должно быть отмечено в knowledge registry
(особенно для RTP items).

---

## CONTRADICTION DETECTOR (HEURISTICS)

Flag if:
- fact statement conflicts with another fact
- timeline impossible ordering
- character acts on unknown info
- item appears without last seen
- rule changes without “change log” entry

Fix options:
- add bridging beat/scene
- revise beat causes
- update knowledge transfer
- track item properly
- retcon via governance (last resort)

---

## PROCEDURE (HOW TO RUN)

1) Initialize ledger for scope (episode/arc)
2) Ingest each Scene Spec in order
3) For each scene:
   - update change log
   - update fact registry (new facts / changed facts)
   - update item tracking
   - update character status
   - update knowledge registry
4) Run contradiction detector
5) Output contradictions + fix strategies
6) Lock ledger version when scope is “published”

---

## QC CHECKLIST (MANDATORY)

- does every scene produce continuity updates?
- any knowledge teleportation?
- are key props tracked end-to-end?
- do consequences persist across scenes?
- do RTP truth changes appear in ledger?
- any contradictions unresolved?

---

## VALIDATION RULES

- NCV1: CL exists and is versioned.
- NCV2: Knowledge registry entries exist for major reveals.
- NCV3: Key items/resources have last-seen trace.
- NCV4: Contradictions are either fixed, bridged, or escalated to governance.

---

OWNER: Universe Engine
LOCK: FIXED
