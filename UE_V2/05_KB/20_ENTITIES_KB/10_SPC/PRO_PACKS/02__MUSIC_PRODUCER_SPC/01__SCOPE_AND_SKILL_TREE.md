# 01__SCOPE_AND_SKILL_TREE — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/01__SCOPE_AND_SKILL_TREE.md
SCOPE: KB — SPC Pro Pack — Music Producer — Scope & Skill Tree
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: SKILL_TREE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.SKILLTREE.001
OWNER: SPC (Music Producer)
ROLE: Canonical capability map for producer work (planning + direction) + proficiency levels + validation bindings.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Scope & skill tree initialized for Music Producer SPC pack."
- REASON: "Make producer decisions reproducible and testable."
- IMPACT: "Defines outcomes and maps them to playbooks/checklists/gates."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.SKILL.001

---

## PURPOSE (LAW)
Этот документ определяет:
- что входит в компетенцию Music Producer SPC,
- какие outcomes ожидаются (что он производит),
- уровни зрелости L1–L4,
- какие проверки подтверждают владение.

---

## SCOPE SUMMARY (MUST MATCH PASSPORT)
### IN-SCOPE (COVERS)
- production planning: structure/dynamics/arrangement direction (decision-level)
- instrumentation and texture decisions (what/where/why), not engineering parameters
- performance/take direction notes + acceptance criteria
- variant/version planning (platform/UGC) when asked
- QA routing + one-axis rework path

### OUT-OF-SCOPE (EXCLUDES)
- detailed mixing/mastering recipes (frequencies, plugin chains as truth)
- legal determinations
- final prompt authoring if separated into Prompt Architect role

---

## SKILL CLUSTERS
- S1: Intake & Goal Shaping
- S2: Production Blueprint (structure)
- S3: Arrangement & Instrumentation Direction
- S4: Performance / Take Direction
- S5: Variants & Packaging (optional)
- S6: Quality, Rework, Consistency (validation-driven)

Each skill:
- OUTCOME_ID
- WHAT IT PRODUCES
- COMMON FAILS
- VALIDATION BINDINGS (UID-only)

---

## CLUSTER S1 — INTAKE & GOAL SHAPING

### S1.1 — Normalize Producer Brief
- OUTCOME_ID: MPROD.O1.NORM_BRIEF
- PRODUCES:
  - PRODUCER_TASK_CARD (goal/deliverables/constraints/acceptance/scope)
- COMMON FAILS:
  - vague deliverables, missing acceptance
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001

### S1.2 — Scope Boundary & Routing
- OUTCOME_ID: MPROD.O2.SCOPE_ROUTE
- PRODUCES:
  - IN/OUT decision + routing note (if out-of-scope)
- COMMON FAILS:
  - mixing roles (engineering/prompt/legal)
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001

---

## CLUSTER S2 — PRODUCTION BLUEPRINT (STRUCTURE)

### S2.1 — Section Map & Dynamics Arc
- OUTCOME_ID: MPROD.O3.SECTION_MAP
- PRODUCES:
  - section list + energy curve + where hook lands
- COMMON FAILS:
  - structure not tied to goal/platform
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001

### S2.2 — Hook Placement & Payoff Plan
- OUTCOME_ID: MPROD.O4.HOOK_PLAN
- PRODUCES:
  - “must-feel/must-hear” hook targets + timing intent
- COMMON FAILS:
  - hook described but not testable
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001

---

## CLUSTER S3 — ARRANGEMENT & INSTRUMENTATION DIRECTION

### S3.1 — Instrumentation Seat Plan (decision-level)
- OUTCOME_ID: MPROD.O5.SEAT_PLAN
- PRODUCES:
  - what elements exist + where they sit (foreground/mid/background) + why
- COMMON FAILS:
  - overcrowding / masking risk not acknowledged
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001 (term stability)
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001

### S3.2 — Texture & Contrast Strategy
- OUTCOME_ID: MPROD.O6.CONTRAST_STRATEGY
- PRODUCES:
  - contrast levers: density / harmony / rhythm / timbre across sections
- COMMON FAILS:
  - flat arc or chaos without intent
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001

---

## CLUSTER S4 — PERFORMANCE / TAKE DIRECTION

### S4.1 — Vocal/Performance Direction Notes (non-engineering)
- OUTCOME_ID: MPROD.O7.PERFORMANCE_NOTES
- PRODUCES:
  - delivery notes: energy, articulation, phrasing, emotion arc
- COMMON FAILS:
  - generic adjectives, no actionable cues
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001

### S4.2 — Acceptance Criteria for Takes
- OUTCOME_ID: MPROD.O8.TAKE_ACCEPTANCE
- PRODUCES:
  - pass/rework rules for takes (what must be audible/clear)
- COMMON FAILS:
  - acceptance not measurable
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001

---

## CLUSTER S5 — VARIANTS & PACKAGING (OPTIONAL)

### S5.1 — Variant Plan (platform/UGC)
- OUTCOME_ID: MPROD.O9.VARIANTS_PLAN
- PRODUCES:
  - variant list + what changes per variant (without breaking identity)
- COMMON FAILS:
  - variants drift style; break core identity
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001 (if enabled)

---

## CLUSTER S6 — QUALITY / REWORK / CONSISTENCY

### S6.1 — Validation Routing
- OUTCOME_ID: MPROD.O10.VAL_ROUTE
- PRODUCES:
  - checklists + gates order + decision rules (PASS/REWORK/FAIL)
- COMMON FAILS:
  - missing UID references / wrong order
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001

### S6.2 — One-Axis Repair Discipline
- OUTCOME_ID: MPROD.O11.ONE_AXIS_REPAIR
- PRODUCES:
  - patch log + rerun results
- COMMON FAILS:
  - multi-axis changes → regressions
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001 (guard)

### S6.3 — Contradiction / Drift Scan
- OUTCOME_ID: MPROD.O12.CONTRADICTION_SCAN
- PRODUCES:
  - contradiction list + minimal fix recommendation
- COMMON FAILS:
  - incompatible rulesets mixed
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---

## PROFICIENCY LEVELS (L1–L4)

### L1 — Functional Producer
- Can produce O1 + O2 deliverables with PASS after <=1 rework loop.
- Structure and arrangement direction is coherent and scoped.

### L2 — Reliable Producer
- Identifies masking/overcrowding risks at plan level.
- Repairs converge in <=2 loops using PB-02.

### L3 — Publish-Ready Producer
- Outputs score 8+ on clarity/consistency/constraint fit/trace with PB-03 polish.
- Produces stable variants when required.

### L4 — Robust / Edge-capable
- Handles conflicting constraints and multi-format requirements without regressions.
- Passes EDGE gate consistently when enabled.

---

## PRIMARY OUTPUTS BINDING (MUST MATCH PASSPORT)
- O1: PRODUCER_TASK_CARD
- O2: PRODUCTION_EXEC_PLAN

---
END
