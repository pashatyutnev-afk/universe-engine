# SPC PRO PACK — TOOLS (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/00__README__TOOLS.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.TOOLS.README.DRAFT.001
OWNER: SYSTEM
ROLE: Map of tools (T01..T16) for VOCAL_DIRECTOR Pro Pack: what each tool produces (stable artifact blocks), which gate(s) it supports, and typical repair routing. Tools generate artifacts; gates validate them.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created TOOLS README for VOCAL_DIRECTOR: tool catalog + outputs + gate mapping."
- REASON: "Need deterministic artifact production map to avoid drift and missing blocks."
- IMPACT: "Faster runs, cleaner QA routing."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.TOOLS.README.001

---

## 0) PURPOSE
Tools are deterministic generators/assemblers of stable artifact blocks.

Rules:
- Tools DO NOT validate (gates validate).
- Tools DO NOT rewrite lyrics.
- Tools DO NOT prescribe mix/master plugin chains.

---

## 1) STABLE OUTPUT RULE
Each tool must output ONLY stable block names (no renaming).
Stable blocks are defined in:
- 10__OUTPUT_PACKS/00__README__OUTPUT_PACKS.md

---

## 2) TOOL CATALOG (T01..T16)
### T01 — INTAKE_NORMALIZER
Produces:
- MIN_INPUTS_CHECK, HOOK_SECTION_LABEL, GAP_REPORT, NEXT_STEP
Gate:
- G1

### T02 — MUST_HEAR_BUILDER
Produces:
- MUST_HEAR_WORDS, CLARITY_TARGETS
Gate:
- G2

### T03 — PHRASE_PROMOTION_HELPER
Produces:
- MUST_HEAR_PHRASES (copy-exact) + phrase notes
Gate:
- G2

### T04 — INTELLIGIBILITY_CHECKLIST_BUILDER
Produces:
- INTELLIGIBILITY_GATES_CHECKLIST, HARD_FAIL_TRIGGERS
Gate:
- G3

### T05 — CONSONANT_ATTACK_PROTECTOR
Produces:
- ATTACK_PROTECTION_NOTES (target→directives→pass_test)
Gate:
- G3

### T06 — DELIVERY_PROFILE_PRUNER
Produces:
- VOCAL_STYLE_PROFILE, FORBIDDEN_STYLES
Gate:
- G4

### T07 — CONTRADICTION_DETECTOR
Produces:
- COHERENCE_CHECK (+ contradiction list)
Gate:
- G4

### T08 — ARC_LEVER_SELECTOR
Produces:
- PERFORMANCE_ARC_MAP, CONTRAST_LEVERS, QC_ARC_CHECKS
Gate:
- G5

### T09 — BREATH_MAP_BUILDER
Produces:
- MUST_HEAR_PROTECTION_RULES, BREATH_POLICY
Gate:
- G6

### T10 — DENSITY_RISK_SCAN
Produces:
- DENSITY_SCAN (+ risk_level R0/R1/R2)
Gate:
- G6

### T11 — STACKING_SAFE_PLANNER
Produces:
- STACKING_DECISION / N_A_DECISION, STACKING_MAP_BY_SECTION, PROTECTED_ZONES, QC_RULES
Gate:
- G7

### T12 — TAKE_PACK_BUILDER
Produces:
- SESSION_INTENT, TAKE_GOALS_BY_SECTION, RISK_LINES, REPEATABILITY_RULES, QC_HARD_FAILS, COMP_NOTES (+ optional QC_SOFT_FAILS)
Gate:
- G8

### T13 — SCOPE_AUDIT_CHECKLIST
Produces:
- SCOPE_AUDIT (+ optional VIOLATIONS_FOUND, REMEDIATION)
Gate:
- G9

### T14 — ESCALATION_NOTE_FORMATTER
Produces:
- ESCALATION_NOTES (owner + evidence + request principles + must_keep + success_criteria + next_check)
Used in:
- T4/T7/T9 cases; supports G6/G9 remediation

### T15 — REPAIR_ROUTER (TYPE→PB)
Produces:
- REPAIR_ROUTE (type_code + chosen_axis + PB + rerun gates)
Used in:
- During-run triage (maps to PB-01..PB-08)

### T16 — THRESHOLD_GUIDE (PASS/REWORK/FAIL)
Produces:
- BORDERLINE_CLASSIFICATION (PASS/REWORK/FAIL rationale + rerun guidance)
Used in:
- Post-run review; stabilizes verdicts

---

## 3) ROUTING (TOOL ↔ PLAYBOOK)
- Targets problems → PB-02 (via T02/T03)
- Intelligibility/attacks → PB-03 (via T04/T05)
- Breath/density → PB-04 (via T09/T10)
- Profile coherence → PB-01 (via T06/T07)
- Arc/contrast → PB-05 (via T08)
- Take pack → PB-06 (via T12)
- Stacking safe → PB-07 (via T11)
- Compliance cleanup → PB-08 (via T13/T14)

---

## 4) NEXT FILES (ORDER)
Proceed in numeric order:
- 01__T01__INTAKE_NORMALIZER.md
- 02__T02__MUST_HEAR_BUILDER.md
- 03__T03__PHRASE_PROMOTION_HELPER.md
- 04__T04__INTELLIGIBILITY_CHECKLIST_BUILDER.md
- 05__T05__CONSONANT_ATTACK_PROTECTOR.md
- 06__T06__DELIVERY_PROFILE_PRUNER.md
- 07__T07__CONTRADICTION_DETECTOR.md
- 08__T08__ARC_LEVER_SELECTOR.md
- 09__T09__BREATH_MAP_BUILDER.md
- 10__T10__DENSITY_RISK_SCAN.md
- 11__T11__STACKING_SAFE_PLANNER.md
- 12__T12__TAKE_PACK_BUILDER.md
- 13__T13__SCOPE_AUDIT_CHECKLIST.md
- 14__T14__ESCALATION_NOTE_FORMATTER.md
- 15__T15__REPAIR_ROUTER.md
- 16__T16__THRESHOLD_GUIDE.md

--- END.
