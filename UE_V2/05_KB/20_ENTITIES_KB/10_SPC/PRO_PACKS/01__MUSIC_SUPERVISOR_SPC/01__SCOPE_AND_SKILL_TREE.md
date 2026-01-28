# 01__SCOPE_AND_SKILL_TREE — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/01__SCOPE_AND_SKILL_TREE.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Scope & Skill Tree
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: SKILL_TREE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.SKILLTREE.001
OWNER: SPC (Music Supervisor)
ROLE: Canonical capability map (what this SPC can do) + proficiency levels + validation bindings.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Scope & skill tree initialized for Music Supervisor SPC pack."
- REASON: "Make outputs and decisions reproducible across tasks."
- IMPACT: "Defines outcomes O-IDs and maps them to playbooks/checklists/gates."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.SKILL.001

---

## PURPOSE (LAW)
Этот документ определяет:
- что входит в компетенцию Music Supervisor SPC,
- какие “умения” (outcomes) ожидаются,
- как растёт качество по уровням,
- какие проверки (CHK/GATE) подтверждают владение.

---

## SCOPE SUMMARY (MUST MATCH PASSPORT)
### IN-SCOPE (COVERS)
- supervision task shaping: goal/deliverables/constraints/acceptance
- style/mood/genre alignment at “direction” level
- structure/hook/pacing supervision guidance (без инженерных параметров)
- QA routing and repair discipline (one-axis)
- packaging notes for readiness (metadata, naming, variants — без правовых решений)

### OUT-OF-SCOPE (EXCLUDES)
- detailed mix/master engineering choices
- final prompt authoring (если у вас отдельная роль Prompt Architect)
- legal/licensing decisions (кроме “проверь/зафиксируй”)

---

## SKILL TREE STRUCTURE
- SKILL CLUSTERS:
  - S1: Intake & Brief Shaping
  - S2: Style/Intent Supervision
  - S3: Structure & Hook Supervision
  - S4: Quality Gates & Routing
  - S5: Packaging & Release Readiness
  - S6: Edge Handling & Robustness (optional)

Each skill has:
- OUTCOME_ID (stable)
- WHAT IT PRODUCES
- FAILURE MODES
- VALIDATION BINDINGS (UID-only)

---

## CLUSTER S1 — INTAKE & BRIEF SHAPING

### S1.1 — Normalize Task Brief
- OUTCOME_ID: MSUP.O1.NORM_BRIEF
- PRODUCES:
  - NORMALIZED_TASK_CARD (goal/deliverables/constraints/scope)
- COMMON FAILS:
  - ambiguous deliverables
  - hidden assumptions
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.READINESS.001 (R-02)
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001

### S1.2 — Scope Boundary Decision
- OUTCOME_ID: MSUP.O2.SCOPE_DECISION
- PRODUCES:
  - SCOPE_DECISION (IN/OUT) + routing note when OUT
- COMMON FAILS:
  - producing out-of-scope content
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001 (C-01/C-03)

---

## CLUSTER S2 — STYLE / INTENT SUPERVISION

### S2.1 — Intent Alignment
- OUTCOME_ID: MSUP.O3.INTENT_ALIGN
- PRODUCES:
  - intent bullets (tone/mood/energy/era references) at supervision level
- COMMON FAILS:
  - vague adjectives without operational meaning
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001 (Q-01/Q-03)

### S2.2 — Constraint Translation (platform/format)
- OUTCOME_ID: MSUP.O4.CONSTRAINT_TRANSLATE
- PRODUCES:
  - constraints translated into actionable checks (not engineering settings)
- COMMON FAILS:
  - constraint conflict not detected
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001 (C-04)

---

## CLUSTER S3 — STRUCTURE & HOOK SUPERVISION

### S3.1 — Structure Blueprint Supervision
- OUTCOME_ID: MSUP.O5.STRUCT_BLUEPRINT
- PRODUCES:
  - high-level structure plan (sections, dynamics, where hook appears)
- COMMON FAILS:
  - structure not mapped to deliverable goal
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001 (Q-02/Q-03)
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001

### S3.2 — Hook & Impact Guidance (non-engineering)
- OUTCOME_ID: MSUP.O6.HOOK_GUIDE
- PRODUCES:
  - hook target (“must-feel/must-hear”) + test cue
- COMMON FAILS:
  - hook described but not testable
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001 (Q-01/Q-05)

---

## CLUSTER S4 — QUALITY GATES & ROUTING

### S4.1 — Checklist/Gate Routing
- OUTCOME_ID: MSUP.O7.VALIDATION_ROUTE
- PRODUCES:
  - QUALITY_AND_ACCEPTANCE_ROUTE (which checks/gates, in what order)
- COMMON FAILS:
  - missing validation references
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.READINESS.001 (R-06)
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001

### S4.2 — One-Axis Repair Discipline
- OUTCOME_ID: MSUP.O8.ONE_AXIS_REPAIR
- PRODUCES:
  - PATCH_LOG with single axis
- COMMON FAILS:
  - multiple axes changed at once → regressions
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.DIAG_REWORK.001 (process)
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001 (guard)

### S4.3 — Contradiction Detection
- OUTCOME_ID: MSUP.O9.CONTRADICTION_SCAN
- PRODUCES:
  - CONTRADICTIONS_FOUND list + fix recommendation
- COMMON FAILS:
  - term drift, incompatible rulesets mixed
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001

---

## CLUSTER S5 — PACKAGING & READINESS

### S5.1 — Publish-Ready Packaging Notes
- OUTCOME_ID: MSUP.O10.PACKAGING_NOTES
- PRODUCES:
  - metadata/naming/variant notes (no legal decisions)
- COMMON FAILS:
  - missing trace / missing minimal packaging cues
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.QUALITY_POLISH.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001 (C-05)

### S5.2 — Minimum Trace
- OUTCOME_ID: MSUP.O11.MIN_TRACE
- PRODUCES:
  - TASK_ID + inputs summary + outputs list + validations list + next action
- COMMON FAILS:
  - cannot reproduce / no record of what was done
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001 (C-05)
  - Rubric D7

---

## CLUSTER S6 — EDGE HANDLING (OPTIONAL)

### S6.1 — Edge Condition Handling
- OUTCOME_ID: MSUP.O12.EDGE_HANDLING
- PRODUCES:
  - edge handling blocks + fallback/routing notes
- COMMON FAILS:
  - breaks scope, introduces contradictions
- VALIDATION:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.EDGE_CASES.001 (if enabled)
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001 (guard)

---

## PROFICIENCY LEVELS (L1–L4)

### L1 — Functional (baseline)
- Can execute PB-01 end-to-end.
- Produces O1/O2 outputs with PASS on CHK-QUALITY after 0–1 repair loops.
- Constraints and scope are respected.

### L2 — Reliable
- Detects contradictions early (O9).
- Uses PB-02 effectively (repairs converge in <=2 loops).
- Consistency gate passes without regressions.

### L3 — Publish-Ready Supervisor
- Produces ready outputs that reach rubric 8+ on D1/D4/D6/D7 with PB-03 polish.
- Handles multi-format packaging notes (O10) cleanly.

### L4 — Robust / Edge-capable
- Consistently handles edge conditions with enabled EDGE gate.
- Maintains low regression rate under iterative revisions.

---

## OUTCOME → VALIDATION MAP (QUICK)
- MSUP.O1, O2 → CHK-READINESS + CHK-COMPLIANCE
- MSUP.O7 → CHK-READINESS (R-06) + GATE-CORE
- MSUP.O9 → GATE-CONSISTENCY
- MSUP.O12 → GATE-EDGE (if enabled)

---

## PRIMARY OUTPUTS BINDING (MUST MATCH PASSPORT)
- O1: SUPERVISION_TASK_CARD
- O2: QUALITY_AND_ACCEPTANCE_ROUTE

---
END
