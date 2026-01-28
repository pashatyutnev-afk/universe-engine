# 02__PLAYBOOK__DIAGNOSE_AND_REWORK — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/03__METHOD_PLAYBOOKS/02__PLAYBOOK__DIAGNOSE_AND_REWORK.md
SCOPE: KB — SPC Pro Pack — Music Producer — Playbook (Diagnose & Rework)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: PLAYBOOK
PLAYBOOK_TYPE: DIAGNOSE_AND_REWORK
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
OWNER: SPC (Music Producer)
ROLE: One-axis repair workflow for failed checklists/gates and borderline outputs.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Diagnose & Rework playbook initialized for Music Producer SPC pack."
- REASON: "Stop chaotic edits and ping-pong fixes."
- IMPACT: "Enforces one-axis, patch log, and rerun set."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.PB.REWORK.001

---

## GOAL
Быстро и безопасно чинить output до PASS,
не ломая другие части и не выходя за scope.

---

## ENTRY TRIGGERS (WHEN TO USE)
Use this playbook when:
- any checklist FAIL/REWORK
- any gate FAIL/REWORK
- rubric average <7 or any dimension <6
- contradictions detected
- variants drift identity anchors
- repeated vagueness (“круто/мощно/как обычно”)

---

## HARD RULES
- ONE-AXIS ONLY per repair loop
- Patch must be minimal (smallest change that addresses failure)
- After patch → rerun minimum set
- If hard limit violated → FAIL (do not “repair into legality”)

---

## REPAIR AXES (CHOOSE ONE)
- clarity
- structure
- completeness
- consistency
- compliance
- variants
- edge

---

## DIAGNOSE STEP (FIND ROOT CAUSE)
### Step D1 — Identify failure source
Record:
- FAIL_SOURCE: <CHK|GATE|RUBRIC|HUMAN_REVIEW>
- FAIL_UID: <...>
- FAIL_SIGNAL: <short description>

### Step D2 — Map to axis
Use this mapping:
- vague, not testable → clarity
- section map/scanability broken → structure
- missing required block (acceptance/trace) → completeness
- conflicts/term drift → consistency
- out-of-scope, forbidden claims → compliance
- variants drift anchors → variants
- conflicting constraints not handled → edge

### Step D3 — Confirm “smallest fix”
Write:
- MIN_PATCH_INTENT (1 sentence)
- WHAT MUST NOT CHANGE (identity anchors / decisions already OK)

---

## PATCH STEP (ONE AXIS)
### Patch format (MANDATORY)
- AXIS_CHANGED: <one axis>
- BEFORE: (1–3 bullets)
- PATCH: (1–5 bullets, concrete edits)
- AFTER: (1–3 bullets)

Guidelines:
- clarity: rewrite acceptance as tests, add must-hear targets, reduce ambiguity
- structure: reorder sections, add timing table, add headings, improve scanability
- completeness: add missing required block(s) only
- consistency: unify terms, remove contradictions, reconcile rules
- compliance: remove forbidden parts, add routing note
- variants: define identity anchors + one lever change
- edge: add conflict flag + resolution strategy + gate routing

---

## RERUN (MINIMUM SET)
After each patch loop:
1) Rerun the failed item (same CHK/GATE)
2) Rerun CONSISTENCY gate
3) If structural/completeness patch → also rerun CORE_OUTPUT_QUALITY gate
4) If variants patch → rerun CONSISTENCY (+ EDGE if present)

Record results:
- RERUN:
  - <UID>: <PASS|REWORK|FAIL>
  - <UID>: <PASS|REWORK|FAIL>

---

## STOP CONDITIONS
STOP and escalate when:
- same failure repeats twice after patch
- ping-pong: fixing A breaks B repeatedly
- contradictions persist after 2 loops
- hard limit violation exists (engineering recipe/legal)
- missing inputs prevent resolution (readiness)

---

## PATCH LOG (MANDATORY)
Use this block every time:
- CHANGE_ID:
- AXIS_CHANGED:
- FAIL_SOURCE:
- FAIL_UID:
- BEFORE:
- PATCH:
- AFTER:
- RERUN:
- DECISION: <CONTINUE|STOP|READY>

---

## EXIT CONDITIONS
- READY when:
  - rerun set passes
  - no hard fail triggers
  - rubric thresholds likely met
- Otherwise:
  - loop again with a NEW axis only after finishing previous loop
  - or STOP if stop conditions hit

---

## REQUIRED UID REFERENCES
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001

---
END
