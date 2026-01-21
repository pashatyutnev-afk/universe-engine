# 91__KB_GATES — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/91__KB_GATES.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (gate set)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.GATES.001
OWNER: SYSTEM
ROLE: Canonical gate definitions template (pass/rework/fail) for SPC packs.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial gates template set for SPC Pro Packs."
- REASON: "Make output acceptance testable and deterministic."
- IMPACT: "All SPC packs must bind outputs to gates."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.GATES.001

---

## PURPOSE (LAW)
Гейты — это **тесты приёмки** результата.
Они не “советы”, а правила PASS/REWORK/FAIL.

> RULE: Гейт должен быть проверяемым: test method + signals + threshold + action.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## GATE CONTRACT (MUST USE THIS SHAPE)
### FIELDS
- GATE_UID
- NAME
- TARGET_OUTPUTS
- TEST_METHOD
- PASS_CRITERIA
- REWORK_CRITERIA
- FAIL_CRITERIA
- REWORK_ACTION (preferred playbook/axis)
- EXEMPLARS (case ids)
- RELATED_UIDS (checklists/playbooks/topics)

---

## GATES INDEX (README)
- GATE-01: INPUT_READINESS
- GATE-02: CLARITY_MINIMUM
- GATE-03: CONSISTENCY_NO_CONTRADICTIONS
- GATE-04: SCOPE_COMPLIANCE
- GATE-05: HARD_LIMITS_COMPLIANCE
- GATE-06: REPEATABILITY_MIN_TRACE (optional)

> Минимум для реального пака: GATE-01 + GATE-02 + GATE-04.

---

## GATE-01 — INPUT_READINESS
- GATE_UID: <GATE_UID_INPUT_READINESS>
- NAME: Input readiness is sufficient to run playbooks.
- TARGET_OUTPUTS: <N/A (pre-run)>
- TEST_METHOD:
  - Run CHK-01 PRE_RUN_READINESS.
- PASS_CRITERIA:
  - All required inputs present and normalized.
  - Scope (outputs + covers/excludes) is declared.
- REWORK_CRITERIA:
  - Minor missing optional inputs or minor formatting issues.
- FAIL_CRITERIA:
  - Missing required inputs OR undefined scope.
- REWORK_ACTION:
  - PB-01 step 1 (intake normalize) OR request inputs.
- EXEMPLARS:
  - CASE-G-001 (when available)
- RELATED_UIDS:
  - CHK-01, PB-01

---

## GATE-02 — CLARITY_MINIMUM
- GATE_UID: <GATE_UID_CLARITY>
- NAME: Output clarity meets minimum acceptance.
- TARGET_OUTPUTS:
  - <output_1>, <output_2>
- TEST_METHOD:
  - Run CHK-02 OUTPUT_QUALITY, focus on clarity items.
- PASS_CRITERIA:
  - No ambiguous instructions.
  - Key terms consistent.
  - Reader can execute without guessing.
- REWORK_CRITERIA:
  - Some ambiguity, fixable with one-axis (clarity/structure).
- FAIL_CRITERIA:
  - Output unusable / contradictory / missing core meaning.
- REWORK_ACTION:
  - PB-02 ONE_AXIS_PATCH_LOOP — AXIS: clarity.
- EXEMPLARS:
  - CASE-G-001 / CASE-B-001
- RELATED_UIDS:
  - CHK-02, PB-02, AX-01 (rubric)

---

## GATE-03 — CONSISTENCY_NO_CONTRADICTIONS
- GATE_UID: <GATE_UID_CONSISTENCY>
- NAME: No internal contradictions; format stable.
- TARGET_OUTPUTS:
  - <output_1>, <output_2>
- TEST_METHOD:
  - Scan for contradictions; ensure same terms mean same thing.
- PASS_CRITERIA:
  - No contradictions.
  - Format consistent.
- REWORK_CRITERIA:
  - Minor inconsistencies, fixable with one-axis (consistency).
- FAIL_CRITERIA:
  - Major contradictions affecting decisions/outcomes.
- REWORK_ACTION:
  - PB-02 — AXIS: consistency.
- EXEMPLARS:
  - CASE-BL-001 / CASE-B-001
- RELATED_UIDS:
  - CHK-02, PB-02, AX-03

---

## GATE-04 — SCOPE_COMPLIANCE
- GATE_UID: <GATE_UID_SCOPE_COMPLIANCE>
- NAME: Output remains within COVERS and avoids EXCLUDES.
- TARGET_OUTPUTS:
  - <output_1>, <output_2>
- TEST_METHOD:
  - Run CHK-03 SCOPE_AND_COMPLIANCE.
- PASS_CRITERIA:
  - No out-of-scope content.
  - No excluded actions/claims.
- REWORK_CRITERIA:
  - Minor scope creep removable without changing core.
- FAIL_CRITERIA:
  - Output primarily out-of-scope OR violates boundary rules.
- REWORK_ACTION:
  - Remove scope creep; if core is out-of-scope → PB-05 ESCALATION.
- EXEMPLARS:
  - CASE-B-001
- RELATED_UIDS:
  - CHK-03, PB-05, AX-04

---

## GATE-05 — HARD_LIMITS_COMPLIANCE
- GATE_UID: <GATE_UID_HARD_LIMITS>
- NAME: No hard limits are violated.
- TARGET_OUTPUTS:
  - All
- TEST_METHOD:
  - Check against HARD LIMITS from passport + forbidden actions.
- PASS_CRITERIA:
  - Zero hard limit violations.
- REWORK_CRITERIA:
  - If violation is localized and removable.
- FAIL_CRITERIA:
  - Central violation or repeated violations.
- REWORK_ACTION:
  - Remove violating content; if cannot → FAIL + escalate.
- EXEMPLARS:
  - CASE-B-001
- RELATED_UIDS:
  - 00__KB_PASSPORT, CHK-03

---

## GATE-06 — REPEATABILITY_MIN_TRACE (OPTIONAL)
- GATE_UID: <GATE_UID_REPEATABILITY>
- NAME: Output includes minimal trace so it can be reproduced.
- TARGET_OUTPUTS:
  - <output_1>, <output_2>
- TEST_METHOD:
  - Verify presence of: inputs summary + method used + gates passed.
- PASS_CRITERIA:
  - Trace present and sufficient.
- REWORK_CRITERIA:
  - Trace incomplete but easy to add.
- FAIL_CRITERIA:
  - No trace; output cannot be reproduced.
- REWORK_ACTION:
  - PB-04 finalize step: add minimal trace.
- EXEMPLARS:
  - CASE-G-001
- RELATED_UIDS:
  - PB-04, CHK-02, AX-05

---
END
