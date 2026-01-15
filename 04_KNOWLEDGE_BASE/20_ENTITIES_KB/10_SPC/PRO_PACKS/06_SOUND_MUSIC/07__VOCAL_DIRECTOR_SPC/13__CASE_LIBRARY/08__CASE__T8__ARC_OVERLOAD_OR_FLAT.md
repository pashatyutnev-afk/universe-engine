# SPC PRO PACK — CASE (T8) — ARC OVERLOAD / FLAT ARC (LEVER PRUNE) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/08__CASE__T8__ARC_OVERLOAD_OR_FLAT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T8.ARC_OVERLOAD_OR_FLAT.001
OWNER: SYSTEM
ROLE: Case record for arc issues: either flat performance (no hook lift) or lever overload (>3 levers) causing chaotic delivery and regressions. Maps symptom to type T8 with deterministic fix route PB-05 and rerun gate G5 (verify G3).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T8: arc overload or flat arc."
- REASON: "Arc drift reduces hook impact and can indirectly destroy intelligibility under stress."
- IMPACT: "Restores controlled lift with <=3 levers."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T8.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T8.001
- type_code: T8
- severity: REWORK
- primary_gate_impacted: G5
- audible_symptom:
  - "Verse and chorus feel the same (flat), hook doesn't lift."
  - "Or: too many performance changes; delivery becomes chaotic and words blur."
- typical_context:
  - "Over-specified direction; multiple conflicting constraints; chorus lift attempted via too many levers."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Root cause is arc/contrast definition: missing lift or lever overload."
  - "Fix is lever selection/prune, not targets or lyrics."
- evidence_checks:
  - 1) Check if PERFORMANCE_ARC_MAP exists (if missing → flat by default).
  - 2) Count contrast levers: if >3 → overload confirmed.
  - 3) Verify levers are explicit and not contradictory.
  - 4) Check if intelligibility drops only in chorus due to intensity lever (if yes, verify G3 after fix).
  - 5) Confirm breath splits are not the root cause (if yes, T2/T4 first).

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-05
- tools_to_run:
  - T08 (arc/lever selector) (recommended)
- one_axis: A2
- patch_scope:
  - "Create/repair arc map + prune levers to <=3; add QC checks (lift present + intelligibility preserved)."
- do_not_change:
  - "Do not rewrite lyrics."
  - "Do not change must-hear targets in the same patch."
  - "Do not prescribe mix/master chains."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G5
- verification:
  - "Hook lift is present and controlled."
  - "Levers <=3."
  - "Verify G3 if intensity changes materially."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Adding more levers to fix a flat arc (often makes chaos)."
  - "Vague levers ('more emotion') without executable settings."
  - "Changing multiple axes in one patch (targets + arc + breath)."
  - "Fixing arc by lyric rewrite (forbidden)."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If fixing arc requires changing delivery profile character, treat that separately as A4 (PB-01) in a separate iteration."
- escalation_needed: NO

--- END.
