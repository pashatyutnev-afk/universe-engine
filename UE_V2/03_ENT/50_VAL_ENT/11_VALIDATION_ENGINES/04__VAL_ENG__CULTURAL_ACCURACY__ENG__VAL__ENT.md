# 🌍 CULTURAL ACCURACY ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · VALIDATION ENGINE · CULTURAL CONTEXT · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__CULTURAL_ACCURACY_ENG.md
- ENGINE_ID: L4-VAL-CULTURAL-ACCURACY-ENGINE-004
- UID: UE.ENT.ENG.VAL.CULTURAL_ACCURACY
- NAME: Cultural Accuracy Engine
- CLASS: Validation Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (harm + incoherence)
- EDITABLE: true

### ABSOLUTE RULE
> Cultural mistakes break immersion and can create real-world harm. If risk is high — block.

---

## 1. PURPOSE

Cultural Accuracy Engine validates whether an artifact:
- respects declared locale/culture constraints
- avoids stereotypes and lazy generalizations
- keeps internal cultural consistency (names, customs, etiquette)
- flags sensitive content risks
- ensures representation is coherent with scope and time (if specified)
- produces a repair plan that is concrete and testable

This engine does not “police opinions”.  
It protects system quality and reduces harm risk by enforcing constraints.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Validate locale consistency (place, language, naming, currency, customs)
- Detect stereotypes and essentialist claims (e.g., “X people are…”)
- Detect cultural mismatch (rituals, etiquette, symbols used incorrectly)
- Validate names/terms for locale fit (if locale declared)
- Enforce sensitivity gates (religion, ethnicity, tragedy, violence context)
- Output repair plan with safer alternatives and specificity upgrades

### OUT-OF-SCOPE (FORBIDDEN)
- Historical accuracy verification (Historical Accuracy Engine)
- Scientific plausibility (Scientific Plausibility Engine)
- Truth claims about real groups beyond what is declared as fiction
- Governance decisions about what becomes canon

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — CULTURAL_VALIDATION_REQUEST
Required fields:
- `cv_req_id`
- `timestamp`
- `artifact_ref`
- `artifact_type`
- `artifact_payload`
- `locale_profile` (required)
- `sensitivity_policy_ref` (optional)
- `glossary_ref` (optional)
- `canon_refs` (optional)
- `trace_id` (optional)

Missing locale_profile → INVALID (CRITICAL) because checks cannot be grounded.

### 3.2 OUTPUT — VALIDATION_VERDICT
(uses realm README canonical schema)

---

## 4. LOCALE PROFILE (REQUIRED)

### 4.1 LOCALE_PROFILE (required fields)
- `locale_id`
- `region` (country/area/city or fictional analogue)
- `language_mode` (RU/EN/other)
- `time_period_ref` (optional)
- `culture_tags` (list)
- `taboos_constraints` (optional list)
- `representation_constraints` (optional)
- `canon_lock` (optional)

Hard rule:
- if locale_profile contradicts canon lock and no override record exists → INVALID (HIGH/CRITICAL).

---

## 5. CULTURAL CONSISTENCY GATES

### 5.1 INTERNAL CONSISTENCY
Checks:
- naming conventions consistent with locale (not random mixing)
- honorifics/etiquette consistent
- social norms and behaviors coherent with declared culture tags
- symbols and clothing coherent with locale/time (if time declared)

Violation:
- MEDIUM/HIGH depending on prominence.

### 5.2 SURFACE SIGNALS VS DEEP RULES
Surface signals (names, clothing, slang) must not contradict deep rules (values, etiquette) unless story intends conflict.

If conflict is not intentional → HIGH.

---

## 6. STEREOTYPE & ESSENTIALISM DETECTION

### 6.1 FORBIDDEN PATTERNS (HARD)
- essentialist group statements:
  - “All [group] are …”
  - “[group] are naturally …”
- caricature traits as identity replacement
- “one trait explains entire culture”
- mocking of protected cultural/religious symbols

If present in a non-critical context (not explicitly framed as character bias with narrative correction) → HIGH/CRITICAL.

### 6.2 SAFE FICTION RULE
If content is fictional:
- cultural elements must still be coherent and respectful
- avoid mapping a real group directly into a villain caricature unless explicitly handled with nuance and constraints

---

## 7. SENSITIVITY GATES (RISK)

### 7.1 SENSITIVE TOPICS LIST (non-exhaustive)
- religion and sacred symbols
- ethnicity and identity
- colonialism / genocide / slavery references
- sexual violence references
- hate speech or dehumanization

If sensitive topic appears:
- require framing check: intent + context + mitigation
- require explicit warning policy if platform requires

Failure:
- CRITICAL if harm risk is high and mitigation absent.

---

## 8. CULTURAL DETAIL QUALITY (OPTIONAL BUT RECOMMENDED)

### 8.1 SPECIFICITY GATE
If a culture is used, it should be represented with:
- specific practices (not vague “exotic”)
- coherent material culture (food, greetings, spaces)
- consistent linguistic registers

Low specificity is not always a failure, but “fake specificity” (random words without meaning) is MEDIUM/HIGH.

---

## 9. SEVERITY & VERDICT RULES

- Harm risk (stereotype/essentialism/hate) → CRITICAL
- Locale contradictions in primary elements → HIGH
- Random mix of signals without intent → MEDIUM/HIGH
- Minor naming mismatch → LOW/MEDIUM
- Missing locale_profile → INVALID (CRITICAL)

Verdict:
- Any CRITICAL → INVALID
- Multiple HIGH → INVALID or PARTIAL if repairs are localized and clear
- Only MEDIUM/LOW → PARTIAL/VALID

---

## 10. OUTPUT: ISSUES + REPAIR PLAN

### 10.1 ISSUE ITEM (cultural)
- `issue_id`
- `type` = LOCALE_MISMATCH | STEREOTYPE_RISK | SENSITIVE_TOPIC_RISK | SYMBOL_MISUSE | NAMING_MISMATCH | INCONSISTENT_ETIQUETTE | FAKE_SPECIFICITY
- `location_ref`
- `description`
- `severity`
- `fix`

### 10.2 REPAIR ACTION TYPES
- `CLARIFY_LOCALE_PROFILE`
- `REWRITE_ESSENTIALIST_PHRASE_TO_CHARACTER_VIEW`
- `ADD_COUNTERBALANCE_CONTEXT`
- `REPLACE_SYMBOL_WITH_LOCALE_CORRECT_ONE`
- `UNIFY_NAMING_CONVENTION`
- `ADD_SENSITIVITY_MITIGATION`
- `REMOVE_HIGH_RISK_CONTENT`

Hard rule:
- repairs must be specific, not “be respectful”.

---

## 11. CORE OPERATIONS

- OP_01: INGEST_ARTIFACT_AND_LOCALE_PROFILE
- OP_02: EXTRACT_CULTURAL_MARKERS (names, symbols, customs)
- OP_03: RUN_LOCALE_CONSISTENCY_CHECKS
- OP_04: RUN_ETIQUETTE_AND_CUSTOMS_CHECKS
- OP_05: RUN_STEREOTYPE_ESSENTIALISM_CHECKS
- OP_06: RUN_SENSITIVE_TOPIC_RISK_CHECKS
- OP_07: RUN_SPECIFICITY_AND_FAKE_SPECIFICITY_CHECKS
- OP_08: BUILD_ISSUES_LIST
- OP_09: ASSIGN_SEVERITY_AND_VERDICT
- OP_10: BUILD_REPAIR_PLAN (ordered)
- OP_11: EMIT_VALIDATION_VERDICT

---

## 12. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- locale_profile missing or empty
- cannot identify cultural markers due to unstructured artifact
- sensitive topic detected but policy ref missing and artifact is for public output

Reaction:
- verdict INVALID (CRITICAL)
- request locale_profile or sensitivity policy

---

## 13. NON-GOALS
- Does not enforce a single “correct” culture if fictional
- Does not do historical correctness
- Does not validate scientific plausibility
- Does not decide canon

---

## 14. FINAL STATEMENT

Culture is a system, not a costume.
If you borrow it — you must keep it coherent and safe.

---

**STATUS:** Cultural Accuracy Engine v1.0  
**REALM:** ACTIVE
