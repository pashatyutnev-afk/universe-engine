# SPC PRO PACK — OUTPUT PACK (STD) — VOCAL_DIRECTOR (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/10__OUTPUT_PACKS/02__OUTPUT_PACK__STD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: OUTPUT_PACK
PACK_TIER: STD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.OUTPUT.STD.001
OWNER: SYSTEM
ROLE: Standard output contract for VOCAL_DIRECTOR: default working pack for iterative generation and testing. Includes intelligibility criteria, delivery profile, breath/density safety, and explicit stacking decision. Scope-safe by design.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created OUTPUT PACK STD template for VOCAL_DIRECTOR."
- REASON: "Need a stable default deliverable that supports repeatable testing without full production overhead."
- IMPACT: "Consistent mid-level quality; fewer regressions; faster routing."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.OUTPUT.STD.001

---

## 0) PURPOSE
STD pack is the default working contract:
- must-hear + intelligibility checks
- delivery profile constraints
- breath/density safety
- explicit stacking decision (YES/NO)
- scope compliance

---

## 1) REQUIRED GATES (STD)
Must PASS:
- G1 INPUT READINESS
- G2 MUST-HEAR
- G3 INTELLIGIBILITY
- G4 DELIVERY COHERENCE
- G6 BREATH/SINGABILITY
- G9 SCOPE COMPLIANCE

Should PASS:
- G5 ARC/CONTRAST
- G7 STACKING SAFE (if stacking_used=YES)
- G8 TAKE PACK (if recording plan needed)

---

## 2) REQUIRED BLOCKS (STABLE NAMES ONLY)
STD pack must include these blocks (in order):

1) MIN_INPUTS_CHECK
2) HOOK_SECTION_LABEL
3) MUST_HEAR_WORDS
4) MUST_HEAR_PHRASES
5) CLARITY_TARGETS
6) INTELLIGIBILITY_GATES_CHECKLIST
7) HARD_FAIL_TRIGGERS
8) ATTACK_PROTECTION_NOTES
9) VOCAL_STYLE_PROFILE
10) FORBIDDEN_STYLES
11) COHERENCE_CHECK (recommended; if omitted, must state contradictions_found=NO implicitly is NOT allowed → better include it)
12) MUST_HEAR_PROTECTION_RULES
13) BREATH_POLICY
14) DENSITY_SCAN
15) STACKING_DECISION (or N_A_DECISION)
16) SCOPE_AUDIT
17) ESCALATION_NOTES (only if needed)
18) REPAIR_ROUTE (optional)

Rule:
- If stacking_used=YES in STD tier, you should upgrade to FULL or at least include protected zones + QC rules (see FULL template). STD allows explicit NO stacking safely.

---

## 3) TEMPLATE (FILL-IN)
### MIN_INPUTS_CHECK
MIN_INPUTS_CHECK:
- LYRIC_DRAFT_PRESENT: YES/NO
- SECTION_STRUCTURE_PRESENT: YES/NO
- LANGUAGE_PRESENT: YES/NO
- HOOK_SECTION_IDENTIFIABLE: YES/NO

### HOOK_SECTION_LABEL
HOOK_SECTION_LABEL:
- value: "<e.g., Chorus 1 (HOOK)>"
- why: "<1 line>"

### MUST_HEAR_WORDS
MUST_HEAR_WORDS:
- P0: <comma list>
- P1: <comma list or N/A>
- P2: <comma list or N/A>

### MUST_HEAR_PHRASES
MUST_HEAR_PHRASES:
- P0:
  - "<copy-exact phrase>"
- P1:
  - "<copy-exact phrase>" (optional)

### CLARITY_TARGETS
CLARITY_TARGETS:
- Target A: "P0 understood on first listen in HOOK"
- Target B (optional): "No breath split inside P0 phrases"
- Target C (optional): "Hook clarity >= verse baseline"

### INTELLIGIBILITY_GATES_CHECKLIST
INTELLIGIBILITY_GATES_CHECKLIST:
- Gate A (P0 first listen):
- Gate B (P1 second listen):
- Gate C (no breath split inside P0):
- Gate D (consonant attacks protected):
- Gate E (hook clarity >= verse):

### HARD_FAIL_TRIGGERS
HARD_FAIL_TRIGGERS:
- HF-1:
- HF-2:
- HF-3:

### ATTACK_PROTECTION_NOTES
ATTACK_PROTECTION_NOTES:
- target: "<P0 word>"
  - directives:
    - D?:
  - pass_test:
    - "<first-listen recognition test>"

### VOCAL_STYLE_PROFILE
VOCAL_STYLE_PROFILE:
- delivery_principles:
  1)
  2)
  3)
  4)
  5) (optional)
  6) (optional)

### FORBIDDEN_STYLES
FORBIDDEN_STYLES:
- 1)
- 2)
- 3) (optional)
- 4) (optional)
- 5) (optional)

### COHERENCE_CHECK
COHERENCE_CHECK:
- contradictions_found: YES/NO
- executability_ok: YES/NO
- reasons:
  - 1)
  - 2) (optional)

### MUST_HEAR_PROTECTION_RULES
MUST_HEAR_PROTECTION_RULES:
- NEVER_SPLIT_PHRASES:
  - "<P0 phrase>"

### BREATH_POLICY
BREATH_POLICY:
- allowed:
  - "<allowed breath point>"
- forbidden:
  - "<forbidden split>"

### DENSITY_SCAN
DENSITY_SCAN:
- line_id: <Section>-L#
  - risk_level: R0 | R1 | R2
  - flags:
    - F_...
  - evidence:
  - fix_hints:
    - 1)

### STACKING_DECISION
STACKING_DECISION:
- stacking_used: YES/NO
- why:
  - 1)

(if NO, may use)
N_A_DECISION:
- stacking_used: NO
- why:
- alternative_lift_lever:

### SCOPE_AUDIT
SCOPE_AUDIT:
- lyric_rewrite_present (F1): NO
- structure_edit_present (F2): NO
- arrangement_ownership_present (F3): NO
- mix_chain_present (F4): NO
- guessing_present (F5): NO

### ESCALATION_NOTES (only if needed)
ESCALATION_NOTES:
- owner:
- section:
- problem:
- request (principles only):
  - 1)
- must_keep:
  - 1)
- forbidden (scope):
  - 1)
- success_criteria:
  - 1)
- next_check:
  - "<rerun gate>"

### REPAIR_ROUTE (optional)
REPAIR_ROUTE:
- <T-code> -> <PB>

---

## 4) VALIDATION RULES (STD)
- If G1 FAIL → stop.
- P0 must be present and protected by hard fail triggers.
- COHERENCE_CHECK must not report contradictions for PASS.
- Breath policy must include forbidden splits.
- Stacking must be explicit YES/NO.

---

## 5) UPGRADE RULE
Upgrade to FULL when:
- stacking_used=YES OR
- take pack / recording plan is required OR
- arc/contrast must be fully specified.

--- END.
