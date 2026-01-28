# SPC PRO PACK — CHECKLIST (02) — DURING-RUN: GATE ORDER + ONE-AXIS (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/12__CHECKLISTS/02__CHECKLIST__DURING_RUN_GATE_ORDER_AND_ONE_AXIS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CHECKLIST
CHECKLIST_CLASS: DURING_RUN
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CHK.VOCAL_DIRECTOR.DURING_RUN.001
OWNER: SYSTEM
ROLE: During-run operational checklist: enforce fixed gate order (G1..G9), tool usage per step, and one-axis repair discipline (via T15 + PB). Prevents pipeline drift and scope violations.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created DURING-RUN checklist for VOCAL_DIRECTOR: gate order + one-axis repairs + stop triggers."
- REASON: "Most regressions happen when steps are skipped or multiple axes are patched together."
- IMPACT: "More deterministic runs; fewer loops."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CHK.VD.DUR.001

---

## 0) RULES (ABSOLUTE)
- Follow gate order: G1→G2→G3→G4→G5→G6→G7→G8→G9
- No lyric rewrites. No mix/master chains.
- One-axis patch only (use T15 routing + PB).
- If a gate FAILs, stop progression until fixed.

---

## 1) PIPELINE CHECKLIST (GATES + TOOLS)
G1 INPUT READINESS
[ ] Run T01 (intake) → evaluate G1
STOP if FAIL.

G2 MUST-HEAR
[ ] Run T02 (targets) + T03 (phrases) → evaluate G2
If FAIL: PB-02 → rerun G2.

G3 INTELLIGIBILITY
[ ] Run T04 (checklist) + T05 (attacks) → evaluate G3
If FAIL: classify type → route with T15:
    - T1/T5 → PB-03 (then rerun G3)
    - T2/T4 → PB-04 (rerun G6→G3)
    - T6 → PB-07 (rerun G7→G3)
    - T7 → Escalate T14 (rerun G3 after owner response)

G4 DELIVERY COHERENCE
[ ] Run T06 (profile) + (if needed) T07 (contradictions) → evaluate G4
If FAIL: PB-01 → rerun G4 (verify G3 if needed).

G5 ARC / CONTRAST
[ ] Run T08 (arc/levers) → evaluate G5
If FAIL: PB-05 → rerun G5 (verify G3 if needed).

G6 BREATH / SINGABILITY
[ ] Run T09 (breath map) + T10 (density scan) → evaluate G6
If R2/no safe breath: Escalate via T14 (no lyric rewrite)
If FAIL: PB-04 → rerun G6→G3.

G7 STACKING SAFE
[ ] Run T11 (stacking plan/decision) → evaluate G7
If FAIL: PB-07 → rerun G7→G3.

G8 TAKE PACK
[ ] Run T12 (take pack) → evaluate G8
If FAIL: PB-06 → rerun G8.

G9 SCOPE COMPLIANCE
[ ] Run T13 (scope audit) → evaluate G9
If FAIL:
    - remove forbidden content
    - convert ownership to escalation (T14)
    - apply PB-08 if needed
    - rerun G9

---

## 2) ONE-AXIS REPAIR DISCIPLINE
When something fails:
[ ] Identify failure type (T1..T9)
[ ] Choose ONE axis (A1..A7)
[ ] Apply exactly one PB for that axis
[ ] Rerun only required gates
[ ] Verify G3 after any change that might affect clarity

Priority order when multiple issues exist:
1) Scope violations (G9)
2) Targets (G2)
3) Intelligibility hard fails (G3/G6)
4) Density/unsingable (G6)
5) Stacking masking (G7)
6) Arc issues (G5)
7) Take pack (G8)

---

## 3) HARD STOP TRIGGERS
Stop immediately if:
[ ] G1 FAIL (missing inputs)
[ ] Any lyric rewrite appears (scope violation)
[ ] Any mix/master chain appears (scope violation)
[ ] Any hard fail trigger in intelligibility/breath is observed (HF-1/HF-2/HF-3)
[ ] Owner change required → escalate (T14) and pause until response

---

## 4) TRACE
TRACE:
- CHECKLIST: DURING_RUN
- UID: UE.KB.SPC.CHK.VOCAL_DIRECTOR.DURING_RUN.001
- ROUTING: T15 + PB-01..PB-08
- FINAL: G9 PASS

--- END.
