# SPC PRO PACK — CASE (T4) — DENSITY / UNSINGABLE RISK (R2) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/04__CASE__T4__DENSITY_UNSINGABLE.md

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
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T4.DENSITY_UNSINGABLE.001
OWNER: SYSTEM
ROLE: Case record for density traps and unsingable risk (R2) where no safe breath points exist without breaking P0 phrases. Maps symptom to type T4 with fix route PB-04 plus mandatory escalation (T14) when R2 persists. Rerun gates G6→G3.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T4: density/unsingable risk (R2)."
- REASON: "Some lines cannot be performed clearly without changes outside VOCAL_DIRECTOR scope."
- IMPACT: "Forces explicit escalation instead of illegal lyric rewrites."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T4.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T4.001
- type_code: T4
- severity: FAIL
- primary_gate_impacted: G6 (and G3)
- audible_symptom:
  - "Line feels physically unperformable at target energy; forced breaths break meaning."
  - "Words compress into a blur; clarity collapses even with careful articulation."
- typical_context:
  - "Long clause chains, rapid syllables, heavy consonant clusters, hook at high intensity."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Root cause is density/phrase length causing no safe breath points."
  - "Any breath solution would split a P0 phrase or force intelligibility loss."
- evidence_checks:
  - 1) Run DENSITY_SCAN and confirm at least one line is R2.
  - 2) Confirm flags include F_NO_SAFE_BREATH_POINT and/or F_LONG_CLAUSE_CHAIN.
  - 3) Check whether P0 phrases are embedded in the dense chain (F_P0_EMBEDDED).
  - 4) Confirm that performance-safe fixes (chunking/breath before phrase) do not resolve it.
  - 5) Confirm you are NOT allowed to rewrite lyrics → escalation required.

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-04
- tools_to_run:
  - T10 (density scan) (mandatory)
  - T09 (breath map) (recommended)
  - T14 (escalation formatter) (mandatory if R2 persists)
- one_axis: A3
- patch_scope:
  - "Produce explicit breath policy + density scan + escalation trigger for unsingable lines."
- do_not_change:
  - "Do not rewrite lyrics or propose replacement text."
  - "Do not prescribe mix/master chains."
  - "Do not change targets unless they are wrong (then T3/PB-02 first)."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G6
  - G3
- verification:
  - "If R2 remains: escalation must exist; pack cannot be READY until owner response."
  - "After owner response: rerun G6→G3 again."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Solving density by rewriting lyrics inside VOCAL_DIRECTOR (forbidden)."
  - "Hiding density with distortion or mix chains (forbidden)."
  - "Ignoring R2 and proceeding to stacking/take pack."
  - "Vague escalation without line_ids and must_keep constraints."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If density is caused by delivery intensity lever, you may also treat as T8 after PB-04 clarifies breath constraints (one-axis rule still applies)."
- escalation_needed: YES
- if escalation_needed:
  - owner: Lyricist/Songwriter
  - next_check: "After owner response, rerun G6 → G3"

--- END.
