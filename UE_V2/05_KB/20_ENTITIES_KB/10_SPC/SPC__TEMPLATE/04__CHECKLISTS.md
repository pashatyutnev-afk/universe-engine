# 04__CHECKLISTS — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/04__CHECKLISTS.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (checklists)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.CHECKLISTS.001
OWNER: SYSTEM
ROLE: Canonical checklist template set (readiness/quality/compliance) for any SPC pack.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial checklist template set for SPC Pro Packs."
- REASON: "Provide repeatable verification steps mapped to gates."
- IMPACT: "All SPC packs must have at least readiness + quality checklists."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.CHECKLISTS.001

---

## PURPOSE (LAW)
Этот документ содержит **чеклисты**, которые прогоняются:
- перед запуском (готовность),
- после черновика (качество),
- перед финалом (комплаенс/границы).

Каждый чеклист обязан:
- иметь критерии,
- возвращать PASS/REWORK/FAIL,
- давать “что исправить”,
- ссылаться на гейты (UID-only) при наличии.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## CHECKLIST INDEX (README)
- CHK-01: PRE_RUN_READINESS
- CHK-02: OUTPUT_QUALITY
- CHK-03: SCOPE_AND_COMPLIANCE

> RULE: В реальном паке можно добавлять дополнительные чеклисты (например, EDGE_SCAN), но эти три — базовый минимум для шаблона.

---

# CHECKLIST CONTRACT (MUST USE THIS SHAPE)
## FIELDS
- CHECKLIST_ID
- INTENT
- INPUTS REQUIRED
- CHECK ITEMS
- RESULT LOGIC (PASS/REWORK/FAIL)
- FIX MENU (what to do on REWORK)
- VALIDATION LINKS (UID-only)

---

## CHK-01 — PRE_RUN_READINESS
- CHECKLIST_ID: CHK-01
- INTENT: Verify inputs and scope readiness before running any playbook.
- INPUTS REQUIRED:
  - PACK_UID, SPC_ENTITY_UID, TARGET_LEVEL
  - Declared PRIMARY_OUTPUTS
  - Declared COVERS/EXCLUDES
  - Required inputs present (per passport)

### CHECK ITEMS
1) Identity present:
   - PACK_UID set
   - SPC_ENTITY_UID set
   - TARGET_LEVEL set
2) Scope declared:
   - PRIMARY_OUTPUTS list not empty
   - COVERS/EXCLUDES explicit
3) Inputs present:
   - All REQUIRED_INPUTS available
4) Constraints known:
   - HARD LIMITS acknowledged
5) Validation route exists:
   - At least one gate/check UID bound (or placeholder in template)

### RESULT LOGIC
- PASS if all items satisfied.
- REWORK if missing optional items or minor formatting.
- FAIL if missing REQUIRED_INPUTS or scope undefined.

### FIX MENU (REWORK)
- If missing identity fields → fill header bindings.
- If missing scope lists → define outputs + covers/excludes.
- If missing inputs → request inputs; do not proceed.

### VALIDATION LINKS (UID-ONLY)
- RELATED_GATES:
  - <GATE_UID_INPUT_READINESS>
- RELATED_PLAYBOOKS:
  - PB-01, PB-02

---

## CHK-02 — OUTPUT_QUALITY
- CHECKLIST_ID: CHK-02
- INTENT: Verify output meets baseline quality before finalization.
- INPUTS REQUIRED:
  - Draft outputs for PRIMARY_OUTPUTS

### CHECK ITEMS
1) Clarity:
   - Output is readable and unambiguous
   - Key terms defined or consistent
2) Completeness:
   - All required sections present (per pack rules)
   - No missing placeholders that should be resolved at this stage
3) Consistency:
   - Internal contradictions absent
   - Format consistent across sections
4) Traceability:
   - Output references validations (gate/check UIDs) where applicable
5) Minimalism:
   - No extra scope creep content beyond COVERS

### RESULT LOGIC
- PASS if clarity + completeness + consistency are satisfied.
- REWORK if one of them is weak but fixable with one-axis patch.
- FAIL if output contradicts scope/limits or is unusable.

### FIX MENU (REWORK)
- Choose ONE axis:
  - clarity OR structure OR density OR consistency
- Apply PB-02 ONE_AXIS_PATCH_LOOP
- Re-run this checklist + the most relevant gate.

### VALIDATION LINKS (UID-ONLY)
- RELATED_GATES:
  - <GATE_UID_CLARITY>
  - <GATE_UID_CONSISTENCY>
- RELATED_PLAYBOOKS:
  - PB-01, PB-02, PB-04

---

## CHK-03 — SCOPE_AND_COMPLIANCE
- CHECKLIST_ID: CHK-03
- INTENT: Ensure output stays within boundaries and respects hard limits.
- INPUTS REQUIRED:
  - Final candidate output

### CHECK ITEMS
1) Scope boundary:
   - Nothing from EXCLUDES is produced
2) Hard limits:
   - No forbidden actions/claims appear
3) Correct routing:
   - If out-of-scope request found → escalation note prepared
4) Safety/compliance:
   - Any declared safety boundary is respected
5) Final validation:
   - Required gates passed or explicitly marked as pending (template stage)

### RESULT LOGIC
- PASS if no violations and routing is correct.
- REWORK if minor boundary issues can be removed cleanly.
- FAIL if hard limits violated or out-of-scope content central.

### FIX MENU (REWORK)
- Remove out-of-scope sections.
- Replace with escalation/routing output.
- Re-run CHK-01 (if scope changed) and CHK-02.

### VALIDATION LINKS (UID-ONLY)
- RELATED_GATES:
  - <GATE_UID_SCOPE_COMPLIANCE>
  - <GATE_UID_HARD_LIMITS>
- RELATED_PLAYBOOKS:
  - PB-05 (if used)

---
END
