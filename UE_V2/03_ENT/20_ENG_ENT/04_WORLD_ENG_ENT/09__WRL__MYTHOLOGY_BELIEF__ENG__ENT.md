# MYTHOLOGY & BELIEF ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/09__MYTHOLOGY_BELIEF_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.WORLD.MYTH.BELIEF.001
OWNER: SYSTEM
ROLE: Defines mythologies and belief systems as world-state: cosmologies, doctrines, rituals, taboos, metaphysical claims (bounded by WORLD_LAWSET), and epoch-scoped belief evolution across civilizations.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Mythology & Belief Engine created: belief schema, ritual/doctrine catalogs, institution bindings, and epoch evolution mapping."
- REASON: "Worlds need coherent belief layers that shape civilizations and conflicts without breaking laws."
- IMPACT: "Belief becomes deterministic and auditable; culture drivers become reusable across epochs."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.MYTH.BELIEF.001

---

## 0) PURPOSE (LAW)
This engine owns **mythology & belief** as world-state:
- cosmology models (how believers think reality works)
- doctrines and sacred claims (bounded by world laws or explicitly marked as belief-claims)
- rituals, symbols, and taboos
- institutional forms (churches/orders/cults) as belief carriers (linked to civ/institutions)
- belief evolution across epochs (schisms, reforms, syncretism)

Hard rule:
- Belief can be false in-world; engine must label claims as CLAIM vs FACT relative to WORLD_LAWSET.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- redefine world laws (02)
- define civilization governance broadly (04) — consumes civ/institution outputs
- define geopolitics treaties (06)
- define conflict escalation mechanics (05)
- define narrative theme/meaning (narrative engine 10) — this is world belief, not author theme
- define production symbolism for shots (style/production families)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_LAWSET
- TIMELINE_EPOCH_MODEL
- CIVILIZATION_MODEL_SET
- INSTITUTION_MODEL_SET (optional but recommended)
- BELIEF_SEEDS (optional)

PRODUCES:
- MYTHOLOGY_BELIEF_MODEL
- DOCTRINE_RITUAL_CATALOG
- BELIEF_INSTITUTION_BINDINGS
- BELIEF_EVOLUTION_MAP

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG, 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG, 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/MYTH_BELIEF/
OPTIONAL:
- KB/MYTH_BELIEF (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Belief System: structured set of claims, practices, and authority mechanisms.
- Cosmology: worldview model (origins, structure of reality, afterlife, metaphysical entities).
- Doctrine: normative claim (“must/should/forbidden”) plus justification.
- Ritual: repeatable practice with triggers and expected outcomes (social/psychological/metaphysical claim).
- Symbol: signifier linked to doctrine/identity.
- Claim Type:
  - FACT_COMPATIBLE: consistent with world laws
  - FACT_CONTRADICTING: contradicts world laws (belief-claim)
  - UNKNOWN: not decidable with current lawset
- Belief Carrier: institution or network that enforces/propagates beliefs.
- Evolution Event: schism/reform/syncretism/decline/violent suppression.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- belief system definitions and components
- claim classification vs world laws
- ritual/doctrine/symbol catalogs
- binding to civilizations/institutions
- epoch-scoped belief evolution

OUT OF SCOPE (HARD):
- world-law truth itself (02)
- civilization general norms unrelated to belief (04)
- narrative theme/meaning (02 narrative family)
- production symbolism for tone (06 style family)

COLLISION RULE:
- If a belief claim implies a new world law → route to governance + world law engine (exception protocol)
- If it’s author theme → theme & meaning engine (narrative), not here
- If it’s civ norm not rooted in belief system → civilization engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: each belief system lists claims and classifies them vs WORLD_LAWSET (FACT_COMPATIBLE / FACT_CONTRADICTING / UNKNOWN).
R2 (HARD) MUST: DOCTRINE_RITUAL_CATALOG defines testable rituals (triggers, steps, expected social outcomes).
R3 (HARD) MUST: BELIEF_INSTITUTION_BINDINGS link belief carriers to civ/institution entities.
R4 (HARD) MUST: BELIEF_EVOLUTION_MAP defines changes per epoch with causes and effects.
R5 (HARD) FORBIDDEN: treating belief claims as world facts without classification.
R6 (SOFT) SHOULD: include “control points” (where belief influences power/economy/conflict) via references.
R7 (HARD) MUST: outputs cannot contradict world laws as facts; contradictions must be labeled as belief-claims.
R8 (HARD) MUST: taboo lists must be enforceable by an institution or social mechanism.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: MYTHOLOGY_BELIEF_MODEL
- MUST:
  - belief_model_id
  - version
  - belief_systems[] (non-empty)
  - lawset_ref
  - timeline_ref
  - checks[] (non-empty)
- BELIEF SYSTEM (minimum):
  - belief_id
  - name
  - civ_refs[] (optional)
  - carrier_refs[] (institutions or networks)
  - cosmology_ref
  - doctrine_ritual_ref
  - symbols[] (optional)
  - claim_summary[] (non-empty)
  - epoch_states[] (optional but recommended)
  - notes
- CLAIM SUMMARY (minimum):
  - claim_id
  - statement (testable as claim text)
  - claim_type (FACT_COMPATIBLE|FACT_CONTRADICTING|UNKNOWN)
  - law_refs[] (optional; required if FACT_COMPATIBLE asserted)
  - enforcement_mechanism (how it is kept alive)
- VALIDATION:
  - each belief has at least one claim_summary
  - claim_type present for all claims
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/MYTH_BELIEF/MYTHOLOGY_BELIEF_MODEL.md

ARTIFACT: DOCTRINE_RITUAL_CATALOG
- MUST:
  - catalog_id
  - version
  - doctrines[] (non-empty)
  - rituals[] (non-empty)
  - taboos[] (optional)
  - symbols[] (optional)
- DOCTRINE (minimum):
  - doctrine_id
  - belief_id
  - rule_text (must/should/forbidden)
  - justification (belief claim link)
  - enforcement (institution/social)
  - violations (what counts)
  - consequences (what happens)
- RITUAL (minimum):
  - ritual_id
  - belief_id
  - trigger (when performed)
  - steps[] (non-empty)
  - expected_outcomes[] (non-empty; social/psychological; metaphysical only as CLAIM)
  - costs[] (time/resource/risk)
  - failure_modes[] (optional)
- TABOO (minimum):
  - taboo_id
  - belief_id
  - forbidden_action
  - detection_mechanism
  - consequence
- VALIDATION:
  - doctrines/rituals reference existing belief_id
  - expected_outcomes are explicit and testable (even if social)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/MYTH_BELIEF/DOCTRINE_RITUAL_CATALOG.md

ARTIFACT: BELIEF_INSTITUTION_BINDINGS
- MUST:
  - binding_id
  - version
  - bindings[] (non-empty)
  - checks[] (non-empty)
- BINDING (minimum):
  - belief_id
  - carrier_ref (institution_id or network id)
  - carrier_type (INSTITUTION|ORDER|CULT|MEMETIC_NETWORK)
  - authority_model (enum: PRIESTHOOD|COUNCIL|PROPHET|SCRIPTURE|AI_ORACLE|TRADITION|HYBRID)
  - enforcement_tools[] (non-empty)
  - recruitment_model (short)
  - notes
- VALIDATION:
  - each binding has enforcement_tools
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/MYTH_BELIEF/BELIEF_INSTITUTION_BINDINGS.md

ARTIFACT: BELIEF_EVOLUTION_MAP
- MUST:
  - evolution_id
  - version
  - events[] (non-empty)
  - checks[] (non-empty)
- EVENT (minimum):
  - event_id
  - belief_id
  - epoch_id
  - type (enum: SCHISM|REFORM|SYNCRETISM|DECLINE|REVIVAL|SUPPRESSION|INSTITUTIONAL_CAPTURE)
  - cause_refs[] (conflict/power/economy/civ)
  - changes[] (non-empty)
  - downstream_effects[] (optional)
  - notes
- CHANGE (minimum):
  - change_id
  - what_changed (doctrine/ritual/authority/symbol/taboo)
  - from (optional)
  - to
  - reason (testable)
- VALIDATION:
  - epoch_id exists in timeline
  - each event has at least one change
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/MYTH_BELIEF/BELIEF_EVOLUTION_MAP.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Validate inputs:
   - lawset + epochs + civs exist
2) Define belief systems:
   - stable ids, carriers, scope
3) Define cosmologies + claims:
   - classify each claim vs world laws
4) Define doctrines/rituals/taboos:
   - triggers, steps, outcomes, enforcement
5) Bind carriers:
   - institution authority model and tools
6) Define evolution:
   - epoch events with causes and changes
7) Run checks:
   - missing claim types, vague rituals, unbound enforcement
8) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: belief claims treated as world facts without claim_type classification.
- S0-2: taboo/doctrine has no enforcement mechanism.
- S0-3: evolution event references unknown epoch_id.
- S0-4: rituals have vague steps/outcomes (non-testable).
- S0-5: outputs imply new world law without governance routing note.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- world law (02), epochs (03), civ/institutions (04)

Downstream consumers:
- civilization engine (norms/taboos can reference belief, not replace it)
- conflict/power engine (ideological conflicts, legitimacy power source)
- geopolitics engine (treaty legitimacy, schisms crossing borders)
- narrative engines (can use belief system as constraints and motivators, not as author theme)

Governance:
- any belief-to-law promotion (claim becomes fact) must go through governance + world law engine.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
