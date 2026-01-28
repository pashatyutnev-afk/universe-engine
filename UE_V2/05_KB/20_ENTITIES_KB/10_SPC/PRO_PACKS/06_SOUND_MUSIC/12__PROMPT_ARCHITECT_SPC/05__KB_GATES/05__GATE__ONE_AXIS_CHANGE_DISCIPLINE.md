# GATE — ONE-AXIS CHANGE DISCIPLINE (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/05__KB_GATES/05__GATE__ONE_AXIS_CHANGE_DISCIPLINE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: KB_GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001
OWNER: SYSTEM
ROLE: Gate for PROMPT_ARCHITECT: checks whether iteration changes follow the one-axis rule, keep deltas minimal, and maintain trace/log discipline. Outputs PASS/REWORK/FAIL with fix mapping and recheck plan.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created one-axis change discipline gate: axis declaration, minimal delta, baseline freeze, and variant/patch log checks."
- REASON: "Without iteration discipline, learning collapses and identity drifts."
- IMPACT: "Faster convergence and reproducible improvements."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.GATE.ONEAXIS.001

---

## 0) TARGET OUTPUT
TARGET_OUTPUT:
- Variant set (if produced)
- Patch prompt instructions (if produced)
- Variant log / patch log / trace notes (if present)

This gate checks iteration discipline, not musical quality.

---

## 1) TEST METHOD (DETERMINISTIC)
Run checks:

O1 — Baseline is frozen (explicit)
- Baseline prompt exists and is referenced as BASE_V0/BASELINE_ID.
- No silent edits to baseline.

O2 — Axis is declared
- Each variant/patch declares exactly one primary axis:
  - hook / vocals / repetition / style / texture / feel / mix intent
If axis not declared → REWORK.

O3 — One-axis rule enforced
- For each variant/patch:
  - only one block (or one axis-relevant block) changed
  - no simultaneous changes to style+structure+vocals together
Evidence:
- delta description exists OR line-level delta noted.

O4 — Delta size is minimal
Heuristic:
- ≤ 3 lines changed OR small delta description
If delta is large rewrite → FAIL (or REWORK if borderline).

O5 — Expected effect stated
- Each variant/patch includes:
  - “expected effect” (observable)
If missing → REWORK.

O6 — Result decision recorded
- Winner/keeper/loser OR PASS/REWORK/FAIL recorded after generation
If missing → REWORK.

O7 — Loop limits respected (when reworking)
- Rework loops have count and escalation rule (or mention)
If infinite/undefined → REWORK/FAIL depending on severity.

---

## 2) PASS / REWORK / FAIL CRITERIA
PASS:
- O1 PASS
- O2 PASS
- O3 PASS
- O4 PASS
- O5 PASS
- O6 PASS
- O7 PASS when rework loops exist

REWORK:
- missing one log field (axis, expected effect, decision) OR
- delta slightly too big but can be reduced

FAIL:
- baseline not frozen (silent edits)
- multiple axes changed in a single iteration
- large rewrite presented as “patch”
- no trace/log discipline across iterations (cannot reproduce)

---

## 3) OUTPUT RECORD (COPY)
GATE_RESULT_RECORD:
- GATE_UID: UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- RESULT: PASS/REWORK/FAIL
- FAILED_CHECKS:
  - <O#>
- EVIDENCE (short):
  - <snippet>
- FIX DIRECTIONS:
  - <action>
- RECHECK:
  - rerun this gate after fix

---

## 4) FIX MAPPING (WHAT TO DO IF FAILS)
If O1 fails:
- Fix: freeze baseline; label it explicitly and copy exact text.

If O2 fails:
- Fix: declare axis per variant/patch using canonical axis list.

If O3 fails:
- Fix: split into separate variants:
  - one variant per axis; do not mix.

If O4 fails:
- Fix: reduce delta to 1–3 lines; revert and reapply minimal patch.

If O5 fails:
- Fix: add one “expected effect” sentence per variant.

If O6 fails:
- Fix: record winner/keeper/loser or pass/rework/fail after results.

If O7 fails:
- Fix: set loop limit (default 3) and define escalation to DIAGNOSE.

Playbook mapping:
- Use PB-02 ONE-AXIS VARIANTS to structure variants.
- Use PB-04 PATCH MIN for minimal deltas.
- Use PB-03 DIAGNOSE for escalation.

---

## 5) EXAMPLES (PLACEHOLDER)
EXAMPLES:
- PASS example:
  - <to be filled>
- FAIL example:
  - <to be filled>
- BORDERLINE example:
  - <to be filled>

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- iteration discipline gate is skipped in pipelines that require learnability
- logs are fabricated (claiming axis/delta without evidence)
- gate outcome claimed without listing failed checks

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.ONE_AXIS.001 | WHY: variant generation method
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal patch method
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001 | WHY: escalation and loop limits
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.GATES.README.DRAFT.001 | WHY: gate map

--- END.
