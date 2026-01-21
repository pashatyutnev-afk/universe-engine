# 01__SCOPE_AND_SKILL_TREE — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/01__SCOPE_AND_SKILL_TREE.md
SCOPE: KB — SPC Pro Pack — Music Producer — Scope & Skill Tree
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: SCOPE_AND_SKILL_TREE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.SCOPE.001
OWNER: SPC (Music Producer)
ROLE: Defines Music Producer SPC scope boundaries + capability tree used for routing, evaluation, and pack completeness.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Scope and skill tree initialized for Music Producer SPC pack."
- REASON: "Make producer competence measurable and separable from composer/mix/prompt roles."
- IMPACT: "Enables deterministic routing and rubric coverage."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.SCOPE.001

---

## SCOPE (BOUNDARIES)

### IN SCOPE (Producer SPC)
- arrangement blueprint (layers/instruments/roles per section)
- energy curve (density, dynamics, build/release)
- groove plan (drums/bass roles, swing/straight intent)
- hook support plan (spotlight, lead space, reinforcement)
- transitions (drops, fills, risers as intent — no plugins)
- contrast strategy (one-lever change discipline)
- variant discipline (identity anchors preserved)
- trace + validation routing (checklists → gates → one-axis repair)

### OUT OF SCOPE (Must Route)
- numeric mixing/mastering settings (LUFS/EQ/comp)
- plugin chains, engineering recipes
- legal certainty
- final prompt takeover (handoff only if Prompt Architect exists)
- vocal technique coaching (Vocal Director scope)

---

## INTERFACES (RUNTIME HANDOFFS)

### Inputs (minimum)
- TASK_GOAL
- PLATFORM_INTENT
- CONSTRAINTS
Optional:
- Composer anchors (motif/form/harmony)
- vocals required (yes/no)
- variants request (count)

### Outputs
- Mandatory: O1 PRODUCER_TASK_CARD, O2 ARRANGEMENT_EXEC_PLAN
- Optional: O3 LAYER_STACK_MAP, O4 TRANSITION_PLAN, O5 VARIANT_SET

### Downstream consumers
- Prompt Architect: arrangement/layer constraints + acceptance tests (handoff only)
- Mix Engineer: intent-level targets (clarity, separation intent — no numbers)
- Vocal Director: density/register intent (if vocals)

---

## SKILL TREE (CAPABILITY MAP)

### S1 — Intake normalization
- S1.1 Extract goal/platform/constraints
- S1.2 Identify missing inputs + ambiguity flags
- S1.3 Detect “hook-first” requirement

### S2 — Identity anchors & constraints
- S2.1 Pull anchors from Composer (if present)
- S2.2 Declare producer-level anchors:
  - core groove identity
  - main layer focus (lead vs bed)
  - hook spotlight rule
- S2.3 Define what may flex (one lever)

### S3 — Arrangement architecture
- S3.1 Section-by-section layer roles
- S3.2 Layer hierarchy (foreground/mid/bed)
- S3.3 Instrument role assignment (support vs lead)
- S3.4 Space plan (where lead breathes)

### S4 — Energy curve & density
- S4.1 Density map per section
- S4.2 Build/release mechanics (intent)
- S4.3 Peak/dip clarity (listener perception)

### S5 — Groove & rhythm system
- S5.1 Drum role map (kick/snare/hats intent)
- S5.2 Bass role (lock, counter, pump — intent)
- S5.3 Groove identity + micro-variation rules

### S6 — Hook support engineering (producer-level)
- S6.1 Hook spotlight window
- S6.2 Reinforcement vs clutter control
- S6.3 Call/response or hook framing (intent)

### S7 — Contrast & transitions
- S7.1 One-lever contrast definition
- S7.2 Transition map (fills, stops, drops — intent)
- S7.3 Reset mechanics for repeats

### S8 — Variant discipline
- S8.1 Variant lever selection (single axis)
- S8.2 Anchor preservation checks
- S8.3 Variant acceptance tests

### S9 — Consistency & compliance
- S9.1 Detect contradictions across sections/variants
- S9.2 Enforce scope (no engineering numbers, no prompt takeover)
- S9.3 Routing notes

### S10 — Validation & repair loop
- S10.1 Checklist order discipline
- S10.2 Gate outputs with one-axis recommendation
- S10.3 Minimal patch + rerun set (regression guard)

---

## COMPETENCE LEVELS (PACK EXPECTATION)
- Minimum runnable:
  - S1–S7 + S9–S10 functional
- Stable:
  - calibrated cases + clear anchors + repeatable variant discipline
- Scalable:
  - collision-aware routing + multi-format adaptation (shorts/full)

---

## COVERAGE TARGETS (PACK COMPLETENESS)
Required to mark pack “complete”:
- 4 calibrated cases: GOOD/BAD/BORDERLINE/EDGE
- rubric calibrated against cases
- regression guard axis→rerun mapping
- topic bindings with RAW links (NAV_RULE)

---
END
