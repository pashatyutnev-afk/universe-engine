# SPC PRO PACK — CASE LIBRARY (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/00__README__CASE_LIBRARY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: README
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE_LIBRARY.README.DRAFT.001
OWNER: SYSTEM
ROLE: Defines the Case Library for VOCAL_DIRECTOR: deterministic “symptom → type (T1..T9) → playbook → rerun gates” records. Used to speed up triage and enforce consistent repairs.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created CASE_LIBRARY README for VOCAL_DIRECTOR: case format + rules + routing + file roadmap."
- REASON: "Need reusable, auditable examples for common failure patterns to reduce ad-hoc fixes."
- IMPACT: "Faster repair decisions and less regression."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.CASE.README.001

---

## 0) PURPOSE
Case Library is a deterministic collection of real-world failure patterns and repairs.

Each case:
- describes a symptom pattern (what you hear/observe)
- assigns a failure type (T1..T9)
- prescribes a primary playbook (PB-01..PB-08) and rerun gates
- captures “what not to do” to avoid scope violations

Case Library supports:
- Tool T15 (Repair Router)
- Tool T16 (Threshold Guide)

---

## 1) SCOPE RULE (ABSOLUTE)
Cases MUST NOT include:
- lyric rewrites / replacement words or lines
- mix/master plugin chains or DAW recipes

Cases MAY include:
- performer-level directives
- breath/stacking placement rules
- escalation notes (principles only, T14 format)

---

## 2) TYPE CODES (REFERENCE)
Use the failure types from Tool T15:

T1 — consonant loss/swallow (P0 attacks not landing)
T2 — breath split inside P0 phrase
T3 — must-hear targets wrong/bloated/missing
T4 — density/unsingable risk (forced breath inside P0)
T5 — delivery mode masking (girt/shout masks P0)
T6 — stacking masking (layers reduce P0 clarity)
T7 — arrangement seat conflict (requires escalation)
T8 — arc lever overload / flat arc
T9 — scope violation (lyric rewrite / mix chain / ownership)

---

## 3) CASE FILE FORMAT (MANDATORY)
Every case file must follow this schema:

CASE_HEADER:
- CASE_ID:
- type_code: T?
- severity: REWORK | FAIL
- primary_gate_impacted: G?
- audible_symptom (1–2 lines):
- typical_context (1 line):

DIAGNOSIS:
- why_this_type (1–3 bullets):
- evidence_checks (what to verify):
  - 1)
  - 2)

FIX_ROUTE:
- primary_playbook: PB-0?
- tools_to_run:
  - T?? (optional)
- one_axis: A?
- patch_scope (what to change):
- do_not_change (protected blocks):

RERUN_GATES:
- sequence:
  - G?
  - G? (optional)
- verification:
  - "Verify G3" (if relevant)

NEGATIVE_SPEC (WHAT TO AVOID):
- avoid:
  - 1)
  - 2)

NOTES (OPTIONAL):
- edge_cases:
- escalation_needed: YES/NO
- if escalation_needed:
  - owner:
  - next_check:

---

## 4) NAMING / ORDER RULE
Case files should be numbered and grouped by type:

- 01__CASE__T1__CONSONANT_LOSS.md
- 02__CASE__T2__BREATH_SPLIT_P0.md
- 03__CASE__T3__TARGET_BLOAT_OR_MISSING.md
- 04__CASE__T4__DENSITY_UNSINGABLE.md
- 05__CASE__T5__DELIVERY_MASKING.md
- 06__CASE__T6__STACKING_MASKING.md
- 07__CASE__T7__ARRANGEMENT_SEAT_CONFLICT.md
- 08__CASE__T8__ARC_OVERLOAD_OR_FLAT.md
- 09__CASE__T9__SCOPE_VIOLATION.md

---

## 5) HOW TO USE (OPERATIONAL)
1) Observe symptom → pick closest case
2) Confirm evidence checks
3) Apply primary playbook (one-axis)
4) Rerun gates listed
5) If still failing, route via T15 (do not stack fixes)

---

## 6) NEXT FILES (ORDER)
Proceed in numeric order (one file per type):
- 01__CASE__T1__CONSONANT_LOSS.md
- 02__CASE__T2__BREATH_SPLIT_P0.md
- 03__CASE__T3__TARGET_BLOAT_OR_MISSING.md
- 04__CASE__T4__DENSITY_UNSINGABLE.md
- 05__CASE__T5__DELIVERY_MASKING.md
- 06__CASE__T6__STACKING_MASKING.md
- 07__CASE__T7__ARRANGEMENT_SEAT_CONFLICT.md
- 08__CASE__T8__ARC_OVERLOAD_OR_FLAT.md
- 09__CASE__T9__SCOPE_VIOLATION.md

--- END.
