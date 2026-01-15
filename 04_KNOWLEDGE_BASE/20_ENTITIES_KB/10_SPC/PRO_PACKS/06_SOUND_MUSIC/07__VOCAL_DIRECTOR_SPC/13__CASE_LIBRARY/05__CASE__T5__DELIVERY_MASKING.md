# SPC PRO PACK — CASE (T5) — DELIVERY MODE MASKING (GRIT/SHOUT HIDES P0) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/05__CASE__T5__DELIVERY_MASKING.md

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
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T5.DELIVERY_MASKING.001
OWNER: SYSTEM
ROLE: Case record for delivery-mode masking where grit/shout/overdrive reduces intelligibility of P0 targets. Maps symptom to type T5 and provides deterministic fix routes using one-axis discipline (PB-03 or PB-01 depending on root cause).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T5: delivery masking hides P0."
- REASON: "Aggressive textures often swallow consonant attacks; needs clarity-safe delivery constraints."
- IMPACT: "Keeps hook energy while protecting must-hear words."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T5.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T5.001
- type_code: T5
- severity: REWORK
- primary_gate_impacted: G3 (and sometimes G4)
- audible_symptom:
  - "Chorus sounds powerful but words disappear; P0 not recognized."
  - "Grit/shout texture smears consonants; attacks feel melted."
- typical_context:
  - "Nu-metal / rap-rock chorus lift, high intensity, distorted vocal character."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Root cause is delivery texture masking P0 attacks (not missing targets)."
  - "Clarity can often be restored by attack-only constraints without changing overall vibe."
- evidence_checks:
  - 1) Confirm P0 targets exist and are reasonable (otherwise treat as T3 first).
  - 2) Identify which P0 words fail under grit/shout (list 2–6).
  - 3) Check if reducing texture only on attacks would solve (attack-window fix).
  - 4) Check if the delivery profile itself is contradictory or vibe-only (if yes, profile repair is needed → G4).
  - 5) Confirm stacking is not the primary masker (if yes, treat as T6).

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-03 (default)
- tools_to_run:
  - T05 (attack protection notes) (recommended)
  - T06/T07 (only if profile contradiction is confirmed)
- one_axis: A1 (default) OR A4 (if profile contradiction)
- patch_scope:
  - If A1 (masking on attacks): "Add target→directive mapping: reduce grit ONLY on P0 attacks; land final consonants; pass tests."
  - If A4 (profile contradiction): "Rebuild/prune profile into <=6 executable principles + forbidden styles (PB-01)."
- do_not_change:
  - "Do not rewrite lyrics."
  - "Do not prescribe mix/master chains."
  - "Do not patch A1 and A4 in the same iteration (one-axis rule)."

---

## RERUN_GATES
RERUN_GATES:
- sequence (A1 path):
  - G3
- sequence (A4 path):
  - G4
  - (verify) G3
- verification:
  - "P0 recognized on first listen in hook; texture does not mask attacks."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Fixing masking by rewriting words."
  - "Fixing masking by plugin chains."
  - "Applying both PB-03 and PB-01 in one patch (violates one-axis)."
  - "Removing all aggression across the whole chorus (over-fix); prefer attack-window constraints."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If masking is tied to arc lever overload (too much intensity), consider T8 after basic attack protection is stable (one-axis)."
- escalation_needed: NO

--- END.
