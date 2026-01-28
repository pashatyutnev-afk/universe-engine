# 00__KB_PASSPORT — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/00__KB_PASSPORT.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (all SPC packs)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.PASSPORT.001
OWNER: SYSTEM
ROLE: Canonical passport template for any SPC Pro Pack (defines identity, scope, outputs, boundaries, dependencies)

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial template for SPC Pro Pack passport."
- REASON: "Standardize pack identity + scope + boundaries for deterministic authoring."
- IMPACT: "All SPC packs must conform to this passport structure."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.PASSPORT.001

---

## PURPOSE (LAW)
Этот документ — **паспорт компетентностного пака SPC**.
Он фиксирует: **кто владелец**, **что входит/не входит**, **какие выходы обязан производить**, **какие зависимости и ограничения**, **какие гейты применимы**.

---

## PACK IDENTITY
- PACK_UID: <PACK_UID>
- PACK_NAME: <HUMAN_READABLE_NAME>
- SPC_ENTITY_UID (OWNER): <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>
- STATUS: <DRAFT|ACTIVE|DEPRECATED>
- LOCK: <OPEN|FIXED>
- VERSION: <X.Y.Z>

### SHORT DESCRIPTION
<1–3 строки: что этот SPC пак реально “умеет делать” на практике.>

---

## KB SCOPE (MANDATORY)
### INPUTS (WHAT THIS PACK CONSUMES)
- REQUIRED_INPUTS:
  - <input_1>
  - <input_2>
- OPTIONAL_INPUTS:
  - <input_3>

### OUTPUTS (WHAT THIS PACK PRODUCES)
- PRIMARY_OUTPUTS:
  - <output_1>
  - <output_2>
- SECONDARY_OUTPUTS:
  - <output_3>

### BOUNDARIES (WHAT IS IN / OUT)
- COVERS:
  - <covers_1>
  - <covers_2>
- EXCLUDES:
  - <excludes_1>
  - <excludes_2>

### KB REFERENCES (RAW for navigation, UID-only for authority)
- RAW_REFERENCES (NAV ONLY):
  - <RAW_LINK_1>
  - <RAW_LINK_2>
- UID_REFERENCES (AUTHORITY):
  - <UID_1>
  - <UID_2>

---

## INTERFACES (RAW)
> Только для навигации. Авторитет связи — через UID в секции DEPENDENCIES / UID_REFERENCES.

- START / RULES:
  - <RAW_LINK_TO_RELEVANT_RULES_OR_START>
- RELATED TEMPLATES:
  - <RAW_LINK_TO_TEMPLATE_1>

---

## OPERATING CONTRACT
### WORK MODE
- DEFAULT_MODE: USAGE-ONLY (no edits outside pack scope)
- ONE-AXIS CHANGE DISCIPLINE: <ON|OFF> (если ON — правим только одну ось за итерацию)

### MINIMUM READY CHECK (PRE-RUN)
- Must have:
  - PACK_UID, SPC_ENTITY_UID, TARGET_LEVEL
  - Defined PRIMARY_OUTPUTS
  - Declared COVERS/EXCLUDES

---

## DEPENDENCIES (UID-ONLY)
### REQUIRED (BLOCKING)
- <UID_DEP_1> — <why needed>
- <UID_DEP_2> — <why needed>

### OPTIONAL (NON-BLOCKING)
- <UID_DEP_3> — <why useful>

### COMPATIBILITY NOTES
- <notes about required compatibility constraints>

---

## HARD LIMITS (ABSOLUTE)
> Это “нельзя никогда” в рамках компетенции данного SPC.

- <limit_1>
- <limit_2>
- <limit_3>

---

## NON-GOALS
> Это “не цель пака”, чтобы не раздувать scope.

- <non_goal_1>
- <non_goal_2>

---

## QUALITY TARGETS (OUTCOME-LEVEL)
- OUTPUT_CLARITY: <what “clear” means>
- CONSISTENCY: <what “consistent” means>
- SAFETY/COMPLIANCE: <what “safe” means>
- REPEATABILITY: <what “repeatable” means>

---

## APPLICABLE GATES (UID-ONLY)
> Какие гейты должны проверять результаты этого SPC.
- GATE_UIDS:
  - <GATE_UID_1>
  - <GATE_UID_2>

---

## CHANGE / VERSIONING RULES (PACK LOCAL)
- Any update requires:
  - VERSION bump
  - CHANGE_NOTE entry with unique CHANGE_ID
- If STATUS becomes DEPRECATED:
  - Provide replacement pointer (UID-only) + reason

---

## TEMPLATE USAGE INSTRUCTIONS
### How to instantiate a real pack
1) Copy this template into a real PRO_PACK folder.
2) Replace all `<...>` placeholders.
3) Bind to Topics via UID_REFERENCES (don’t paste “theory” into pack).
4) Add playbooks/checklists/gates/cases to make outputs testable.

### Completion signal
- A pack is “usable” only when:
  - PRIMARY_OUTPUTS are defined
  - COVERS/EXCLUDES are explicit
  - At least one GATE is bound
  - Dependencies are declared

---
END
