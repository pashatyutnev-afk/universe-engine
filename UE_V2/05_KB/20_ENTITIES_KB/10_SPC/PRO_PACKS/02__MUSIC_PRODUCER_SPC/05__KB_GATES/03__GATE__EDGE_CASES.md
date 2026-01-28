# 03__GATE__EDGE_CASES — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/05__KB_GATES/03__GATE__EDGE_CASES.md
SCOPE: KB — SPC Pro Pack — Music Producer — Gate (Edge Cases)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 05__KB_GATES
DOC_TYPE: GATE
GATE_TYPE: EDGE_CASES
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001
OWNER: SPC (Music Producer)
ROLE: Evaluate conflict handling, multi-variant discipline, and routing integrity under high-risk briefs.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Edge cases gate initialized for Music Producer SPC pack."
- REASON: "Prevent hidden failure modes when constraints conflict and variants are requested."
- IMPACT: "Defines explicit conflict strategy requirements."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.GATE.EDGE.001

---

## WHEN TO RUN
Run this gate only if any is true:
- conflicting constraints exist (density vs intelligibility, etc.)
- >=2 variants requested
- platform split (shorts + full) in one task
- role split is explicit (Prompt Architect / Mix Engineer)
- previous runs show drift or ping-pong repairs

---

## PREREQUISITE (MUST)
- Compliance checklist PASS:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001
- Consistency gate PASS or at least no hard contradictions:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---

## EDGE CHECKS (MUST)

### E1 Conflict visibility
[ ] Conflicts are explicitly flagged (C2 vs C3 style)
[ ] A resolution strategy is stated (decision-level, not engineering)

### E2 Conflict strategy quality
[ ] Strategy includes “what must not change”
[ ] Strategy includes “what may flex” (one lever / window concept)
[ ] Strategy includes acceptance tests tied to conflict (e.g., phone intelligibility + density retained)

### E3 Variants discipline (if variants exist)
[ ] Identity anchors are explicit
[ ] One lever change per variant
[ ] Variant acceptance exists
[ ] Variant rerun notes exist (at least consistency gate)

### E4 Routing integrity
[ ] Out-of-scope tasks are routed, not executed
[ ] Notes provide what downstream roles need (without takeover)
  - Prompt Architect gets structure + anchors + hook placement
  - Mix Engineer gets intent/tests (no numbers)

### E5 Failure containment
[ ] If a conflict cannot be resolved inside producer scope:
    - output contains STOP + request / escalate note
    - does not invent a solution

---

## DECISION RULES
- FAIL:
  - hidden conflict (not acknowledged) likely to break acceptance
  - variants drift anchors or multi-axis changes
  - routing integrity broken (scope takeover)
- REWORK:
  - conflict flagged but strategy weak / tests missing
  - variants missing acceptance or rerun notes
- PASS:
  - explicit conflicts + testable strategy + disciplined variants + proper routing

Axis recommendation:
- edge (conflict strategy)
- variants (anchors/levers)
- compliance (routing/scope)
- clarity (tests)

---

## OUTPUT (MANDATORY)
- GATE_UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001
- DECISION: <PASS|REWORK|FAIL>
- FAIL_REASONS:
  - <list E# items failed>
- AXIS_RECOMMENDATION (if REWORK):
  - <one axis>
- RERUN_SET (after patch):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---

## CALIBRATION ANCHOR
- EDGE exemplar:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001

---
END
