# TOPICS — NARRATIVE (README) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/00__README__TOPICS_NARRATIVE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 10_NARRATIVE
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.NARRATIVE.001
OWNER: SYSTEM
ROLE: Orientation for NARRATIVE topics scope: what belongs here, how entities use it, and a deterministic roadmap to populate the realm with high-signal narrative craft modules (no navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created NARRATIVE topics realm README: scope boundaries, usage order, and roadmap for core narrative craft modules."
- REASON: "Entities need a clean narrative craft library that improves story quality without mixing domains or turning into a second index."
- IMPACT: "More consistent scene construction, stronger tension/stakes, fewer story logic drift errors."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.NARR.README.001

---

## 0) PURPOSE (KB)
This realm contains NARRATIVE craft knowledge:
- scene construction and causality
- tension/stakes management
- dramatic arc and turning points
- foreshadowing and payoff discipline
- dialogue purpose (structure-level, not acting coaching)
- continuity of narrative logic (not visual continuity)

Goal:
- make story outputs consistently intelligible, tense, and meaningful.

---

## 1) WHAT BELONGS HERE / WHAT DOES NOT
### BELONGS (IN-SCOPE)
- scene mechanics: goal→conflict→turn→new state
- causality: cause→effect chains, payoff discipline
- tension tools: uncertainty, time pressure, stakes escalation
- structure tools: acts, midpoint, turning points, climaxes (as craft)
- foreshadowing: setup/payoff patterns
- dialogue as action (purpose, subtext as technique)

### DOES NOT BELONG (OUT-OF-SCOPE)
- character psychology deep dives (belongs to 20_CHARACTER)
- world systems, geopolitics, economy (belongs to 30_WORLD)
- visual composition/camera (belongs to 40_VISUAL)
- music/arrangement (belongs to SOUND_MUSIC)
- governance laws and navigation maps (master index only)

---

## 2) NAVIGATION RULE (STRICT)
- This README is NOT navigation authority.
- KB navigation/existence authority is ONLY the KB master index:
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- Do not add RAW registries here.

---

## 3) HOW ENTITIES USE NARRATIVE TOPICS (DETERMINISTIC)
Order:
1) Load governance minimum set (no-fantasy, uid-only xref, trace).
2) Determine if the task is narrative (scene/episode/story structure).
3) Load minimal narrative modules needed:
   - constraints/gates first (if any)
   - then the specific topic module(s)
4) Apply checklists/gates (if relevant).
5) Output RUN_TRACE (UID-only sources + memory reuse).

---

## 4) FILL PLAN (ROADMAP: WHAT FILES WE MUST CREATE)
Roadmap list (not navigation authority).

### P1 — Core scene craft
- NARRATIVE__SCENE_CRAFT_FOUNDATIONS
- NARRATIVE__CAUSE_EFFECT_CHAINING
- NARRATIVE__TURNING_POINTS_AND_STATE_CHANGE
- NARRATIVE__TENSION_STAKES_ESCALATION
- NARRATIVE__PAYOFF_SETUP_DISCIPLINE

### P1 — Continuity & clarity
- NARRATIVE__CONTINUITY_LOGIC (facts, motivations, constraints)
- NARRATIVE__CLARITY_COMMON_FAILS (symptom→cause→fix)
- NARRATIVE__SCENE_QA_CHECKLIST (pass/rework/fail)

### P2 — Structure tools
- NARRATIVE__DRAMATIC_ARC_MAP
- NARRATIVE__MIDPOINT_FUNCTIONS
- NARRATIVE__CLIFFHANGER_PATTERNS (as craft, not “clickbait”)

### P2 — Dialogue as action
- NARRATIVE__DIALOGUE_PURPOSE_AND_SUBTEXT
- NARRATIVE__INFORMATION_REVEAL_PACING

### P3 — Advanced craft
- NARRATIVE__THEME_INTEGRATION_METHOD
- NARRATIVE__FORESHADOWING_MESH_PATTERNS
- NARRATIVE__TWIST_FAIRNESS_RULES

---

## 5) STYLE RULES FOR NARRATIVE MODULES
- Atomic modules: one purpose per file.
- Prefer operational guidance:
  - inputs
  - steps
  - failure modes
  - measurable-ish checklists/gates where possible
- Avoid “taste-only” advice unless paired with observable checks.
- Keep cross-domain boundaries strict.

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- realm becomes a second navigation index (RAW registries)
- modules mix character/world/visual without split
- modules present invented facts as sourced truth
- outputs claim compliance without trace

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: governance rules apply to all KB usage
- XREF: UE.KB.REF.GLOSSARY.NARRATIVE_STRUCTURE.003 | WHY: controlled vocabulary for narrative structure terms
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing
- XREF: UE.KB.RULE.SCOPE_MODULE_LOAD.074 | WHY: minimal loading order

--- END.
