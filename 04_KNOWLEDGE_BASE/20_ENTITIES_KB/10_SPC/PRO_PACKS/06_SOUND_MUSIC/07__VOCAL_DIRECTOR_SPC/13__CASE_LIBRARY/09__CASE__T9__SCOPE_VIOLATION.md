# SPC PRO PACK — CASE (T9) — SCOPE VIOLATION (F1..F5) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/09__CASE__T9__SCOPE_VIOLATION.md

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
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T9.SCOPE_VIOLATION.001
OWNER: SYSTEM
ROLE: Case record for scope/ownership violations in VOCAL_DIRECTOR outputs. Maps symptom to type T9 with deterministic remediation using T13 audit and PB-08 one-axis compliance patch (A7). Rerun gate G9.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T9: scope violation (F1..F5)."
- REASON: "Forbidden content breaks auditability and entity boundaries; must be removed deterministically."
- IMPACT: "Restores scope-safe outputs and prevents repeated drift."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T9.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T9.001
- type_code: T9
- severity: FAIL
- primary_gate_impacted: G9
- audible_symptom:
  - "Not audible—this is a compliance failure: output contains forbidden actions."
  - "Example: replacement lyrics, plugin chains, ownership claims, or guessing."
- typical_context:
  - "Over-helpful fixes that drift into rewriting or production/mixing instructions."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Failure is compliance-level, not craft-level."
  - "Pack cannot be used until forbidden content is removed."
- evidence_checks:
  - 1) Run scope audit and classify violations as F1..F5.
  - 2) F1 (lyric rewrite) present? → automatic FAIL.
  - 3) F4 (mix/master chain) present? → automatic FAIL.
  - 4) F2/F3 ownership language present without escalation format? → fail/rework.
  - 5) F5 guessing present? → convert to GAP or stop.

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-08
- tools_to_run:
  - T13 (scope audit) (mandatory)
  - T14 (escalation formatter) (if converting ownership to escalation)
- one_axis: A7
- patch_scope:
  - "Remove forbidden content (F1/F4). Convert ownership to ESCALATION_NOTES. Ensure ONE-AXIS record."
- do_not_change:
  - "Do not introduce new solutions while cleaning."
  - "Do not rewrite lyrics."
  - "Do not add mixing chains."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G9
- verification:
  - "All forbidden classes NO: F1..F5 clean."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Leaving even small lyric replacements in the text."
  - "Leaving plugin chain hints ('add EQ/compressor') in the text."
  - "Proceeding to other gates before scope is clean."
  - "Fixing other axes while performing compliance cleanup."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If the run requires lyric change to resolve density, escalate via T14 instead of rewriting (T4/T2 overlap)."
- escalation_needed: POSSIBLE
- if escalation_needed:
  - owner: Lyricist/Songwriter or Arranger/Producer (depending on issue)
  - next_check: "After owner response, rerun affected gate(s) + G9"

--- END.
