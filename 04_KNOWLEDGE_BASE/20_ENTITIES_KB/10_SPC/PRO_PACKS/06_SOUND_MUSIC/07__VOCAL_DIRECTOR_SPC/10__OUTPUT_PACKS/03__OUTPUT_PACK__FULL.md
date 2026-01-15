# SPC PRO PACK — OUTPUT PACK (FULL) — VOCAL_DIRECTOR (READY CONTRACT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/10__OUTPUT_PACKS/03__OUTPUT_PACK__FULL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: OUTPUT_PACK
PACK_TIER: FULL
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.OUTPUT.FULL.001
OWNER: SYSTEM
ROLE: Full READY output contract for VOCAL_DIRECTOR. Contains all stable artifact blocks in the canonical assembly order. Must pass Gates G1..G9. Scope-safe by design (no lyric rewrites; no mix/master chains).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created OUTPUT PACK FULL (READY contract) template for VOCAL_DIRECTOR."
- REASON: "Need a single canonical deliverable shape that fully encodes the workflow and is auditable."
- IMPACT: "Deterministic READY packs with minimal drift."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.OUTPUT.FULL.001

---

## 0) PURPOSE
FULL pack is the canonical READY contract:
- complete direction system for performance, clarity, breath, stacking, session, and compliance
- designed to be auditable and repeatable

---

## 1) REQUIRED GATES (FULL)
Must PASS:
- G1 INPUT READINESS
- G2 MUST-HEAR
- G3 INTELLIGIBILITY
- G4 DELIVERY COHERENCE
- G5 ARC/CONTRAST
- G6 BREATH/SINGABILITY
- G7 STACKING SAFE
- G8 TAKE PACK
- G9 SCOPE COMPLIANCE

---

## 2) REQUIRED BLOCKS (STABLE NAMES ONLY) — CANONICAL ORDER
FULL pack must include the following blocks in this exact order:

1)  MIN_INPUTS_CHECK
2)  HOOK_SECTION_LABEL
3)  MUST_HEAR_WORDS
4)  MUST_HEAR_PHRASES
5)  CLARITY_TARGETS
6)  INTELLIGIBILITY_GATES_CHECKLIST
7)  HARD_FAIL_TRIGGERS
8)  ATTACK_PROTECTION_NOTES
9)  MASKING_RISKS (optional but recommended)
10) VOCAL_STYLE_PROFILE
11) FORBIDDEN_STYLES
12) COHERENCE_CHECK
13) PERFORMANCE_ARC_MAP
14) CONTRAST_LEVERS
15) QC_ARC_CHECKS
16) MUST_HEAR_PROTECTION_RULES
17) BREATH_POLICY
18) BREATH_SPLIT_WARNINGS (optional)
19) DENSITY_SCAN
20) ESCALATION_TRIGGER (optional; required if any R2 exists)
21) ESCALATION_NOTES (optional; required if escalation trigger YES)
22) STACKING_DECISION / N_A_DECISION
23) STACKING_MAP_BY_SECTION (required if stacking_used=YES)
24) PROTECTED_ZONES (required if stacking_used=YES)
25) QC_RULES (required if stacking_used=YES)
26) SESSION_INTENT
27) TAKE_GOALS_BY_SECTION
28) RISK_LINES
29) REPEATABILITY_RULES
30) QC_HARD_FAILS
31) QC_SOFT_FAILS (optional)
32) COMP_NOTES
33) SCOPE_AUDIT
34) REPAIR_ROUTE (optional)

Rule:
- If a block is optional and not needed, omit it cleanly (do not add placeholders).
- If stacking_used=YES, stacking map + protected zones + QC rules are mandatory.

---

## 3) TEMPLATE (FILL-IN)
Below is the FULL template skeleton. Fill blocks as defined (stable names; no renaming).

### 1) MIN_INPUTS_CHECK
MIN_INPUTS_CHECK:
- LYRIC_DRAFT_PRESENT: YES/NO
- SECTION_STRUCTURE_PRESENT: YES/NO
- LANGUAGE_PRESENT: YES/NO
- HOOK_SECTION_IDENTIFIABLE: YES/NO

### 2) HOOK_SECTION_LABEL
HOOK_SECTION_LABEL:
- value: "<e.g., Chorus 1 (HOOK)>"
- why: "<1 line>"

### 3) MUST_HEAR_WORDS
MUST_HEAR_WORDS:
- P0: <comma list>
- P1: <comma list or N/A>
- P2: <comma list or N/A>

### 4) MUST_HEAR_PHRASES
MUST_HEAR_PHRASES:
- P0:
  - "<copy-exact phrase>"
- P1:
  - "<copy-exact phrase>" (optional)

### 5) CLARITY_TARGETS
CLARITY_TARGETS:
- Target A: "P0 understood on first listen in HOOK"
- Target B (optional): "No breath split inside P0 phrases"
- Target C (optional): "Hook clarity >= verse baseline"

### 6) INTELLIGIBILITY_GATES_CHECKLIST
INTELLIGIBILITY_GATES_CHECKLIST:
- Gate A (P0 first listen):
- Gate B (P1 second listen):
- Gate C (no breath split inside P0):
- Gate D (consonant attacks protected):
- Gate E (hook clarity >= verse):

### 7) HARD_FAIL_TRIGGERS
HARD_FAIL_TRIGGERS:
- HF-1:
- HF-2:
- HF-3:
- HF-4 (optional):
- HF-5 (optional):

### 8) ATTACK_PROTECTION_NOTES
ATTACK_PROTECTION_NOTES:
- target: "<P0 word>"
  - directives:
    - D?:
    - D? (optional):
  - do_not_do (optional):
    - "<forbidden delivery behavior>"
  - pass_test:
    - "<first-listen recognition test>"

### 9) MASKING_RISKS (optional)
MASKING_RISKS:
- target: "<P0 word>"
  - risks:
    - RISK_T?:

### 10) VOCAL_STYLE_PROFILE
VOCAL_STYLE_PROFILE:
- delivery_principles:
  1)
  2)
  3)
  4)
  5) (optional)
  6) (optional)

### 11) FORBIDDEN_STYLES
FORBIDDEN_STYLES:
- 1)
- 2)
- 3) (optional)
- 4) (optional)
- 5) (optional)

### 12) COHERENCE_CHECK
COHERENCE_CHECK:
- contradictions_found: YES/NO
- executability_ok: YES/NO
- reasons:
  - 1)
  - 2) (optional)

### 13) PERFORMANCE_ARC_MAP
PERFORMANCE_ARC_MAP:
- Verse:
- Chorus:
- Bridge (optional):
- Final Chorus (optional):

### 14) CONTRAST_LEVERS
CONTRAST_LEVERS:
- lever: L?
  - verse_setting:
  - chorus_setting:
- lever: L? (optional)
  - verse_setting:
  - chorus_setting:
- lever: L? (optional)
  - verse_setting:
  - chorus_setting:

### 15) QC_ARC_CHECKS
QC_ARC_CHECKS:
- chorus_lift_present:
- lever_count_ok (<=3):
- intelligibility_preserved:
- bridge_contrast_present:

### 16) MUST_HEAR_PROTECTION_RULES
MUST_HEAR_PROTECTION_RULES:
- NEVER_SPLIT_PHRASES:
  - "<P0 phrase>"

### 17) BREATH_POLICY
BREATH_POLICY:
- allowed:
  - "<allowed breath point>"
- forbidden:
  - "<forbidden split>"

### 18) BREATH_SPLIT_WARNINGS (optional)
BREATH_SPLIT_WARNINGS:
- high_risk_splits:
  - "<split that must not happen>"

### 19) DENSITY_SCAN
DENSITY_SCAN:
- line_id: <Section>-L#
  - risk_level: R0 | R1 | R2
  - contains_P0: YES/NO
  - flags:
    - F_...
  - evidence:
  - fix_hints:
    - 1)

### 20) ESCALATION_TRIGGER (optional; required if any R2)
ESCALATION_TRIGGER:
- YES/NO
- why:
- if YES:
  - owner:
  - lines:

### 21) ESCALATION_NOTES (optional; required if escalation YES)
ESCALATION_NOTES:
- owner:
- section:
- line_ids: (optional list)
- problem:
- evidence:
  - 1)
- request (principles only):
  - 1)
- must_keep:
  - 1)
- forbidden (scope):
  - 1)
- success_criteria:
  - 1)
- next_check:
  - "<gate/tool to rerun>"

### 22) STACKING_DECISION / N_A_DECISION
STACKING_DECISION:
- stacking_used: YES/NO
- why:
  - 1)

N_A_DECISION (if stacking_used=NO):
- stacking_used: NO
- why:
- alternative_lift_lever:

### 23) STACKING_MAP_BY_SECTION (required if YES)
STACKING_MAP_BY_SECTION:
- Verse:
- Chorus:
- Final Chorus (optional):
- Bridge (optional):

### 24) PROTECTED_ZONES (required if YES)
PROTECTED_ZONES:
- P0 phrases:
  - "<phrase>"
- avoid stacking over consonant attacks on:
  - <P0 list>

### 25) QC_RULES (required if YES)
QC_RULES:
- QC-S1:
- QC-S2:
- QC-S3:
- FAIL_TRIGGERS:
  - 1)
  - 2)

### 26) SESSION_INTENT
SESSION_INTENT:
- identity:
- priorities:
- forbidden:

### 27) TAKE_GOALS_BY_SECTION
TAKE_GOALS_BY_SECTION:
- Verse:
  - goal:
  - goal:
- Chorus:
  - goal:
  - goal:
- Bridge (optional):
  - goal:
  - goal:
- Final Chorus (optional):
  - goal:
  - goal:

### 28) RISK_LINES
RISK_LINES:
- <Section>-L#:
  - excerpt:
  - risk:

### 29) REPEATABILITY_RULES
REPEATABILITY_RULES:
- 1)
- 2)
- 3)
- 4) (optional)

### 30) QC_HARD_FAILS
QC_HARD_FAILS:
- HF-1:
- HF-2:
- HF-3:
- HF-4 (optional):

### 31) QC_SOFT_FAILS (optional)
QC_SOFT_FAILS:
- SF-1:
- SF-2:

### 32) COMP_NOTES
COMP_NOTES:
- 1)
- 2)
- 3)

### 33) SCOPE_AUDIT
SCOPE_AUDIT:
- lyric_rewrite_present (F1): NO
- structure_edit_present (F2): NO
- arrangement_ownership_present (F3): NO
- mix_chain_present (F4): NO
- guessing_present (F5): NO

### 34) REPAIR_ROUTE (optional)
REPAIR_ROUTE:
- <T-code> -> <PB>

---

## 4) VALIDATION RULES (FULL)
- Any NO in MIN_INPUTS_CHECK → stop (do not assemble further).
- Any hard fail in G3/G6 triggers → treat as FAIL until repaired.
- If stacking_used=YES and missing protected zones/QC → FAIL.
- Scope audit must remain clean (F1/F4 always NO).

---

## 5) NEXT STEP
After FULL is assembled:
- run gates G1..G9 verdicts
- if any REWORK/FAIL, route via T15 to PB fixes (one-axis)

--- END.
