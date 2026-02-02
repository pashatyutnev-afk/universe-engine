# 🗣️ LANGUAGE & LINGUISTICS ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · VALIDATION ENGINE · CLARITY + TERMINOLOGY · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__LANGUAGE_LINGUISTICS_ENG.md
- ENGINE_ID: L4-VAL-LANGUAGE-LINGUISTICS-ENGINE-003
- UID: UE.ENT.ENG.VAL.LANGUAGE_LINGUISTICS
- NAME: Language & Linguistics Engine
- CLASS: Validation Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (ambiguity)
- EDITABLE: true

### ABSOLUTE RULE
> If meaning is ambiguous, the system cannot execute safely.

---

## 1. PURPOSE

Language & Linguistics Engine validates **communicative correctness**:
- clarity of statements (no ambiguous meaning)
- terminology alignment with glossary and canon
- consistency of naming across files (same entity → same name)
- structural readability of specs (lists, enums, required fields)
- forbidden phrasing patterns that create interpretive holes
- language consistency policy (RU/EN rules if applicable)

It produces:
- `VALIDATION_VERDICT` with issues and repair plan
- terminology alignment report

This engine prevents “soft prose” from entering hard specs.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Detect ambiguity (pronouns without referent, vague quantifiers)
- Detect undefined terms (not in glossary)
- Detect term drift (same thing called different names)
- Detect naming inconsistencies (file name vs engine name vs index name)
- Enforce spec-style constraints (required fields as explicit lists)
- Enforce forbidden phrasing blacklist (subjective filler in specs)
- Validate language mode and consistency (if declared)

### OUT-OF-SCOPE (FORBIDDEN)
- Fact truth evaluation (Fact Consistency Engine)
- Cultural/historical/scientific correctness (other engines)
- Governance decisions (authority layer)
- Writing new content (only repairs)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — LANGUAGE_VALIDATION_REQUEST
Required fields:
- `lv_req_id`
- `timestamp`
- `artifact_ref`
- `artifact_type`
- `artifact_payload`
- `glossary_ref` (optional but recommended)
- `terminology_policy_ref` (optional)
- `style_policy_ref` (optional)
- `trace_id` (optional)

Missing required input → INVALID (CRITICAL).

### 3.2 OUTPUT — VALIDATION_VERDICT
(uses realm README canonical schema)

---

## 4. CLARITY GATES (HARD)

### 4.1 AMBIGUITY TYPES
- **Vague quantifiers:** “some”, “often”, “many”, “usually” (without bounds)
- **Undefined referents:** “it”, “they”, “this” without explicit antecedent
- **Undefined scope:** “system”, “project”, “world” used without scope tag
- **Soft modality:** “should”, “might”, “probably” in hard rules without being marked as modality
- **Non-testable statements:** “good”, “nice”, “proper” without criteria

Hard rule:
- hard rules must be testable.

### 4.2 REQUIRED TESTABILITY
Any rule statement must map to:
- a check
- a gate
- a field requirement
- or a deterministic decision rule

If not testable → issue HIGH.

---

## 5. TERMINOLOGY ALIGNMENT

### 5.1 TERMINOLOGY POLICY (default)
- Each entity has one canonical name in a given scope
- Glossary terms must be used exactly (or mapped explicitly)
- Acronyms must be defined once, then reused consistently
- Synonyms are forbidden in specs unless explicitly declared as alias mapping

### 5.2 TERM OBJECT (internal normalization)
- `term_text`
- `term_type` (entity/engine/artifact/layer/other)
- `scope_ref`
- `canonical_form`
- `aliases_allowed` (bool)
- `evidence_ref` (glossary/canon)

Undefined term (not in glossary and not defined locally):
- MEDIUM/HIGH depending on use frequency and criticality.

---

## 6. NAMING CONSISTENCY GATES

### 6.1 ENGINE NAMING CONSISTENCY (if artifact is engine spec)
The following must match semantically:
- file name
- ENGINE_FILE field
- ENGINE_ID name fragment (optional)
- NAME field
- index entry label (if available)

Mismatch:
- HIGH severity (because it breaks navigation and linking).

### 6.2 INDEX CONSISTENCY (if artifact is index)
- numbering in index matches file numbering
- family names consistent across sections
- link labels match target file names (at least stem)

Mismatch:
- HIGH/CRITICAL depending on reach.

---

## 7. SPEC LANGUAGE MODE

### 7.1 LANGUAGE MODE (optional)
Artifacts may declare:
- `LANGUAGE_MODE: RU | EN | MIXED_CONTROLLED`

Default rule if not declared:
- allow mixed, but forbid mixing within a single hard rule sentence.

If language mode is RU:
- core terms may be EN if they are canonical (e.g., ENGINE_ID), but prose should remain RU.

Violation:
- LOW/MEDIUM unless it causes ambiguity.

---

## 8. FORBIDDEN PHRASING BLACKLIST (SPECS)

Forbidden in hard rules unless paired with criteria:
- “proper”, “nice”, “good”, “clean”, “better”
- “etc.” (in required lists)
- “and so on”
- “as needed”
- “in general”
- “probably/likely” (unless modality is explicit and bounded)

Hard rule:
- required lists cannot contain “etc.” → INVALID (HIGH).

---

## 9. READABILITY + STRUCTURE CHECKS

### 9.1 STRUCTURE GATES (specs)
- required fields must be a bullet list
- enums must list allowed values explicitly
- rejection rules must be explicit
- operations list must be explicit (OP_01…)
- failure conditions must be explicit

Violation:
- MEDIUM/HIGH depending on downstream risk.

### 9.2 REDUNDANCY & DRIFT
- repeated sections with conflicting wording must be flagged
- duplicated definitions must be merged or made canonical

---

## 10. SEVERITY & VERDICT RULES

- Ambiguous hard rule → HIGH
- Undefined critical term in required field list → HIGH
- Naming mismatch breaking navigation → HIGH/CRITICAL
- “etc.” in required list → HIGH
- Non-testable rule phrasing → HIGH
- Minor style inconsistency → LOW/MEDIUM

Verdict:
- Any CRITICAL → INVALID
- Multiple HIGH in core rules → INVALID
- Some HIGH but repairable local → PARTIAL
- Only MEDIUM/LOW → VALID/PARTIAL based on policy

---

## 11. OUTPUT: ISSUES + REPAIR PLAN

### 11.1 ISSUE ITEM (language)
- `issue_id`
- `type` = AMBIGUITY | UNDEFINED_TERM | TERM_DRIFT | NAMING_MISMATCH | NON_TESTABLE_RULE | FORBIDDEN_PHRASING | STRUCTURE_VIOLATION
- `location_ref`
- `description`
- `severity`
- `fix`

### 11.2 REPAIR ACTION (canonical)
- `action_type` = DEFINE_TERM | REPHRASE_RULE_TESTABLE | UNIFY_NAME | REMOVE_FORBIDDEN_PHRASE | FIX_ENUM_LIST | FIX_REQUIRED_FIELDS_LIST
- `instruction`
- `recheck_gates`

---

## 12. CORE OPERATIONS

- OP_01: INGEST_ARTIFACT_AND_POLICIES
- OP_02: DETECT_LANGUAGE_MODE (if declared)
- OP_03: EXTRACT_TERMS_AND_NAMES
- OP_04: RUN_CLARITY_AMBIGUITY_CHECKS
- OP_05: RUN_TERMINOLOGY_GLOSSARY_CHECKS
- OP_06: RUN_TERM_DRIFT_CHECKS
- OP_07: RUN_NAMING_CONSISTENCY_CHECKS
- OP_08: RUN_FORBIDDEN_PHRASING_CHECKS
- OP_09: RUN_STRUCTURE_READABILITY_CHECKS
- OP_10: BUILD_ISSUES_LIST
- OP_11: ASSIGN_SEVERITY_AND_VERDICT
- OP_12: BUILD_REPAIR_PLAN
- OP_13: EMIT_VALIDATION_VERDICT

---

## 13. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- artifact too unstructured to locate rule boundaries
- missing payload
- glossary required by policy but not provided

Reaction:
- verdict INVALID (CRITICAL)
- request structured artifact or provide glossary ref

---

## 14. NON-GOALS
- Does not judge factual truth
- Does not enforce cultural correctness
- Does not rewrite style for aesthetics (only clarity/spec compliance)

---

## 15. FINAL STATEMENT

Clear language is executable language.
Ambiguity is a hidden bug.

---

**STATUS:** Language & Linguistics Engine v1.0  
**REALM:** ACTIVE
