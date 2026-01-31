# 🧾 FACT CONSISTENCY ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · VALIDATION ENGINE · CLAIM CONSISTENCY · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__FACT_CONSISTENCY_ENG.md
- ENGINE_ID: L4-VAL-FACT-CONSISTENCY-ENGINE-002
- UID: UE.ENT.ENG.VAL.FACT_CONSISTENCY
- NAME: Fact Consistency Engine
- CLASS: Validation Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (truth alignment)
- EDITABLE: true

### ABSOLUTE RULE
> If two registered facts contradict and no precedence rule exists — the system is corrupted.

---

## 1. PURPOSE

Fact Consistency Engine validates **truth-structure** of artifacts:
- extracts factual claims
- checks contradictions against canon and registered facts
- checks internal contradictions inside the artifact
- enforces evidence requirements when the artifact type demands it
- assigns confidence and severity
- outputs a repair plan: which claims to fix, remove, or re-evidence

It does not “decide what is true” by opinion.  
It checks **consistency rules** and **canon precedence**.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Extract claims from text/spec
- Normalize claims into canonical claim objects
- Compare claims to:
  - Canon facts (if applicable)
  - Registered facts (if applicable)
  - Claims within the same artifact (internal)
- Detect contradiction classes:
  - direct contradiction
  - negation contradiction
  - impossible co-existence
  - timeline collision (if time included)
- Enforce evidence gates (when required)
- Emit verdict + repair plan + recheck gates

### OUT-OF-SCOPE (FORBIDDEN)
- Language quality editing (Language Engine)
- Cultural/historical/scientific plausibility (other validators)
- Governance decisions about what becomes canon (Governance layer)
- Inventing new facts to “patch holes”

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — FACT_VALIDATION_REQUEST
Required fields:
- `fv_req_id`
- `timestamp`
- `artifact_ref`
- `artifact_type`
- `artifact_payload`
- `canon_refs` (optional but recommended)
- `registered_fact_refs` (optional)
- `precedence_rules_ref` (optional)
- `evidence_policy_ref` (optional)
- `trace_id` (optional)

Missing required input → INVALID (CRITICAL).

### 3.2 OUTPUT — VALIDATION_VERDICT
(uses realm README canonical schema)

---

## 4. CLAIM MODEL (CANONICAL)

### 4.1 CLAIM (required fields)
- `claim_id`
- `claim_text` (original excerpt)
- `normalized_claim` (machine-normalized statement)
- `entity_refs` (what entities it talks about)
- `scope_ref` (system / project / world / episode etc.)
- `time_ref` (optional)
- `polarity` = AFFIRM | DENY
- `modality` = CERTAIN | PROBABLE | POSSIBLE | HYPOTHETICAL
- `source_location_ref` (section/line)
- `evidence_refs` (optional)
- `confidence` (0–1; engine estimate)
- `status` = NEW | MATCHES_CANON | CONTRADICTS_CANON | UNVERIFIED

Hard rule:
- claims must have `source_location_ref` to be actionable.

---

## 5. CANON & PRECEDENCE RULES

### 5.1 CANON PRIORITY (default)
If precedence rules are not provided, use:
1) System Canon (L1)  
2) Governance rules (L1)  
3) Registered entity passports (if exist)  
4) Project-specific facts (if within project scope)  
5) Unregistered claims (lowest)

Hard rule:
- lower layer cannot override higher layer without explicit approval record.

### 5.2 CONFLICT RESOLUTION OPTIONS (allowed outputs)
- fix claim to match canon
- downgrade modality (CERTAIN → POSSIBLE) if allowed by policy
- mark as hypothesis with explicit tag
- remove claim
- add evidence references (if conflict is evidential, not logical)

---

## 6. CONTRADICTION TYPES

### 6.1 DIRECT CONTRADICTION
- A: “X is true.”
- B: “X is false.”

### 6.2 ATTRIBUTE COLLISION
- A: “X has attribute A.”
- B: “X has attribute not-A.” (or mutually exclusive attribute)

### 6.3 CO-EXISTENCE IMPOSSIBILITY
- two claims cannot be true together under declared rules (e.g., “no currency exists” + “they pay with currency”)

### 6.4 TIMELINE COLLISION (when time_ref exists)
- same entity cannot be in two exclusive states at the same time

### 6.5 SCOPE COLLISION
- claim intended for Project scope but asserted as System Canon

Hard rule:
- scope collision is HIGH severity by default.

---

## 7. EVIDENCE GATES (WHEN REQUIRED)

### 7.1 EVIDENCE POLICY (optional ref)
If evidence policy is present, apply:
- claims of type FACT must include evidence refs
- claims of type OPINION must be labeled as such
- claims of type HYPOTHESIS must be explicitly marked

### 7.2 MINIMUM EVIDENCE RULES (default)
- Canon claims: must reference canon file/section
- Project claims: must reference project source
- External claims: must reference knowledge base or sources (if policy requires)

Missing required evidence:
- MEDIUM/HIGH depending on artifact type
- CRITICAL if artifact is used for decision/approval

---

## 8. SEVERITY & VERDICT RULES

### 8.1 SEVERITY ASSIGNMENT (default)
- Contradicts System Canon → CRITICAL
- Contradicts Governance rule → CRITICAL/HIGH
- Internal contradiction on core fields → HIGH
- Unverified factual claim with required evidence missing → HIGH
- Unverified factual claim without evidence requirement → MEDIUM
- Minor ambiguity but no contradiction → LOW/MEDIUM

### 8.2 VERDICT RULES
- Any CRITICAL issue → INVALID
- Multiple HIGH issues → INVALID or PARTIAL depending on fixability
- Only MEDIUM/LOW → PARTIAL or VALID

Hard rule:
- VALID requires zero unresolved contradictions.

---

## 9. OUTPUT STRUCTURE: ISSUE + REPAIR

### 9.1 ISSUE ITEM (fact)
- `issue_id`
- `type` = CONTRADICTION | UNVERIFIED | SCOPE_COLLISION | TIMELINE_COLLISION | EVIDENCE_MISSING
- `claim_ids_involved` (list)
- `description`
- `severity`
- `fix_options` (ordered list)

### 9.2 REPAIR ACTION (canonical)
- `action_id`
- `action_type` = EDIT_CLAIM | REMOVE_CLAIM | DOWNGRADE_MODALITY | ADD_EVIDENCE | CHANGE_SCOPE_TAG
- `target_claim_id`
- `instruction`
- `recheck_gates` (list)

---

## 10. CORE OPERATIONS

- OP_01: INGEST_ARTIFACT_AND_CONTEXT (canon/refs/policy)
- OP_02: EXTRACT_CLAIMS (parse → claim objects)
- OP_03: NORMALIZE_CLAIMS (entities/scope/polarity/modality)
- OP_04: RUN_INTERNAL_CONSISTENCY_CHECKS
- OP_05: RUN_CANON_CONSISTENCY_CHECKS
- OP_06: RUN_REGISTERED_FACT_CONSISTENCY_CHECKS
- OP_07: RUN_SCOPE_AND_TIMELINE_CHECKS
- OP_08: APPLY_EVIDENCE_GATES (if required)
- OP_09: BUILD_ISSUES_LIST
- OP_10: ASSIGN_SEVERITY_AND_VERDICT
- OP_11: BUILD_REPAIR_PLAN (ordered)
- OP_12: EMIT_VALIDATION_VERDICT

---

## 11. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- cannot extract claims (artifact too unstructured)
- missing artifact payload
- canon references required but not provided and artifact claims “canon truth”

Reaction:
- verdict INVALID (CRITICAL)
- request structured claims list or provide canon refs

---

## 12. NON-GOALS
- Does not prove external reality
- Does not do scientific plausibility (separate engine)
- Does not do historical or cultural correctness
- Does not rewrite narrative (only fixes claims)

---

## 13. FINAL STATEMENT

The system survives by consistency.
A single unhandled contradiction is a crack in reality.

---

**STATUS:** Fact Consistency Engine v1.0  
**REALM:** ACTIVE
