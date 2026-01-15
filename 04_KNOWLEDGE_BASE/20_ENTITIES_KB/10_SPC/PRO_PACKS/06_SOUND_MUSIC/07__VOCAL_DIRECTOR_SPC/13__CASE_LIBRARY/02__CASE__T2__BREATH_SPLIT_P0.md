# SPC PRO PACK — CASE (T2) — BREATH SPLIT INSIDE P0 PHRASE (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/02__CASE__T2__BREATH_SPLIT_P0.md

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
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T2.BREATH_SPLIT_P0.001
OWNER: SYSTEM
ROLE: Case record for breath splits occurring inside MUST-HEAR P0 phrases. Maps symptom to type T2 and deterministic fix route (PB-04) with rerun gates G6→G3. Includes escalation note path when density makes splits unavoidable.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T2: breath split inside P0 phrase."
- REASON: "Breath splits inside must-hear phrases are hard fails and a primary intelligibility killer."
- IMPACT: "Forces explicit breath policy and phrase protection."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T2.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T2.001
- type_code: T2
- severity: FAIL
- primary_gate_impacted: G6 (and G3)
- audible_symptom:
  - "Key phrase breaks mid-meaning; hook feels chopped."
  - "Listener hears two halves instead of one phrase; recognition drops."
- typical_context:
  - "Fast syllable density, long clause chains, weak breath planning."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Failure is breath placement inside P0 phrase boundary."
  - "Even if consonants are clear, phrase meaning collapses when split."
- evidence_checks:
  - 1) Identify P0 phrase(s) being split (copy-exact).
  - 2) Locate split point (word boundary) and mark as forbidden.
  - 3) Check if split is required by density (no safe breath points).
  - 4) If no safe breath point exists → treat as density trap and evaluate escalation (T4 overlap).
  - 5) Verify that stacking is not the primary cause (if masking, treat as T6).

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-04
- tools_to_run:
  - T09 (breath map) (recommended)
  - T10 (density scan) (recommended)
  - T14 (escalation formatter) (only if R2/no safe breath)
- one_axis: A3
- patch_scope:
  - "Define NEVER_SPLIT_PHRASES + explicit allowed/forbidden breath points + density scan with line_ids."
- do_not_change:
  - "Do not rewrite lyrics."
  - "Do not prescribe mix/master chains."
  - "Do not change must-hear targets unless they are wrong (then T3/PB-02)."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G6
  - G3
- verification:
  - "HF-2 cleared: no breath split inside any P0 phrase."
  - "P0 understood on first listen remains true."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Allowing breath 'anywhere' without forbidden splits."
  - "Vague breath guidance without explicit P0 phrase protection."
  - "Fixing by rewriting words/lyrics (forbidden)."
  - "Fixing by plugin chains (forbidden)."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If density makes P0 phrase unsingable (R2, no safe breath), escalate to Lyricist/Songwriter with T14; do not rewrite here."
- escalation_needed: POSSIBLE
- if escalation_needed:
  - owner: Lyricist/Songwriter
  - next_check: "After owner response, rerun G6 → G3"

--- END.
