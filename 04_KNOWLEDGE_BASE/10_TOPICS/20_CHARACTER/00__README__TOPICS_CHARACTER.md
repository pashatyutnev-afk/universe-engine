# TOPICS — CHARACTER (README) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/00__README__TOPICS_CHARACTER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 20_CHARACTER
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.CHARACTER.001
OWNER: SYSTEM
ROLE: Orientation for CHARACTER topics scope: what belongs here, how entities use it, and a deterministic roadmap to populate the realm with high-signal character craft modules (no navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created CHARACTER topics realm README: scope boundaries, usage order, and roadmap for core character craft modules."
- REASON: "Entities need a consistent character craft library (motivation, trauma, values, behavior under pressure, arcs) without mixing narrative/world/visual."
- IMPACT: "Stronger characters, clearer motivations, less behavioral inconsistency."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.CHAR.README.001

---

## 0) PURPOSE (KB)
This realm contains CHARACTER craft knowledge:
- motivation and desire mechanics
- wounds/trauma and coping patterns
- values and moral compass (decision logic)
- behavior under pressure (consistent reactions)
- character arcs (change over time)
- relationships dynamics (as character system)

Goal:
- make character behavior predictable-by-design (not random),
  while still feeling human and dramatic.

---

## 1) WHAT BELONGS HERE / WHAT DOES NOT
### BELONGS (IN-SCOPE)
- motivation frameworks (goal / need / fear / cost)
- trauma/wound patterns and triggers
- value hierarchies and moral conflict design
- behavior under pressure (fight/flight/freeze/fawn patterns as craft)
- arc planning (belief change, identity shift)
- relationship dynamics (attachment, conflict loops)

### DOES NOT BELONG (OUT-OF-SCOPE)
- scene structure and pacing (belongs to 10_NARRATIVE)
- world building systems (belongs to 30_WORLD)
- cinematography/lighting/composition (belongs to 40_VISUAL)
- music/vocals (belongs to SOUND_MUSIC)
- governance laws and navigation maps (master index only)

---

## 2) NAVIGATION RULE (STRICT)
- This README is NOT navigation authority.
- KB navigation/existence authority is ONLY:
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- Do not add RAW registries here.

---

## 3) HOW ENTITIES USE CHARACTER TOPICS (DETERMINISTIC)
Order:
1) Load governance minimum set (no-fantasy, uid-only xref, trace).
2) Determine character scope for the task:
   - building a new character
   - diagnosing behavior inconsistency
   - designing arc or pressure behavior
3) Load minimal required modules:
   - constraints/gates first (if any)
   - then the specific topic module(s)
4) Apply checklists/gates (if relevant).
5) Output RUN_TRACE (UID-only sources + memory reuse).

---

## 4) FILL PLAN (ROADMAP: WHAT FILES WE MUST CREATE)
Roadmap list (not navigation authority).

### P1 — Core character craft
- CHARACTER__MOTIVATION_DESIRE_FOUNDATIONS
- CHARACTER__WOUND_TRAUMA_PATTERNS
- CHARACTER__VALUES_MORAL_COMPASS
- CHARACTER__BEHAVIOR_UNDER_PRESSURE
- CHARACTER__CHARACTER_ARC_MECHANICS

### P1 — Consistency & QA
- CHARACTER__CONSISTENCY_FAILS_FAST_FIXES
- CHARACTER__DECISION_LOGIC_CHECKLIST (PASS/REWORK/FAIL)
- CHARACTER__RELATIONSHIP_DYNAMICS_BASE

### P2 — Advanced depth
- CHARACTER__LIES_AND_DEFENSE_MECHANISMS
- CHARACTER__CONTRADICTION_DESIGN (human realism vs plot breaks)
- CHARACTER__VOICE_AND_SPEECH_SIGNATURES (as behavior, not acting)

### P3 — Tooling packs (optional later)
- CHARACTER__COMPETENCE_PACK__CHARACTER_ARCHITECT (if we standardize packs here)

---

## 5) STYLE RULES FOR CHARACTER MODULES
- Make behavior explainable:
  - trigger → interpretation → action → consequence
- Avoid “just vibes” advice unless you anchor it to observable behavior.
- Keep modules atomic (one craft function per file).
- Always state boundaries (what the module covers/excludes).

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- realm becomes a second navigation index (RAW registries)
- modules mix narrative/world/visual without split
- modules present invented facts as sourced truth
- outputs claim compliance without trace

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: governance rules apply to all KB usage
- XREF: UE.KB.REF.GLOSSARY.NARRATIVE_STRUCTURE.003 | WHY: shared structure terms; avoid confusion between arc/beat/scene
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing
- XREF: UE.KB.RULE.SCOPE_MODULE_LOAD.074 | WHY: minimal loading order

--- END.
