# 🧷 GENRE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · GENRE CONTRACT · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__GENRE_ENG.md
- ENGINE_ID: L3-PROD-GENRE-ENGINE-001
- UID: UE.ENT.ENG.PROD.GENRE
- NAME: Genre Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (contract integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Genre is a promise. If you violate the promise, the audience exits.

---

## 1. PURPOSE

Genre Engine declares and enforces the **genre contract**:
- genre selection (bounded)
- expectations and allowed moves
- forbidden moves and taboos (platform/rating)
- required beats (genre obligations)
- optional beat palette (genre flavor)

It produces:
- **GENRE_PROFILE**
- genre obligations list
- forbidden moves list
- validation gates for downstream engines

This engine prevents “random genre drift”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Select primary genre + optional subgenre
- Define genre obligations (required beats)
- Define forbidden moves (what breaks contract)
- Define expectation map (what audience anticipates)
- Define tolerance ranges (violence/humor/horror/romance intensity)
- Define genre-specific pacing requirements
- Emit validation rules for blending/adaptation engines

### OUT-OF-SCOPE (FORBIDDEN)
- Plot decisions (event generation)
- Canon authority decisions
- Writing prose or scripts

---

## 3. GENRE MODEL

### 3.1 Output — GENRE_PROFILE (required fields)
- `gp_id`
- `primary_genre` (one)
- `subgenre` (optional one)
- `audience_target` (required)
- `tone_constraints` (required)
- `stakes_floor` (minimum stakes expectations)
- `obligations` (list of required beats)
- `optional_palette` (list of allowed beat types)
- `forbidden_moves` (list)
- `intensity_tolerances` (map)
- `pacing_rules` (map)
- `validation_gates` (hard rules)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Obligation Beat (required fields)
- `ob_id`
- `name`
- `must_occur_by` (time_ref: midpoint/climax_window/end)
- `proof_of_delivery` (what counts as delivered)
- `notes`

### 3.3 Forbidden Move (required fields)
- `fm_id`
- `name`
- `reason` (contract break / platform constraint / canon risk)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL
- `notes`

---

## 4. CONTROLLED GENRE SET (STANDARD)

Primary genres:
- SCI_FI
- FANTASY
- HORROR
- THRILLER
- MYSTERY
- DRAMA
- ACTION
- ADVENTURE
- ROMANCE
- COMEDY
- NOIR
- EPIC
- MYTHIC
- POST_APOC

Subgenres (examples):
- CYBERPUNK
- SPACE_OPERA
- HARD_SCI_FI
- DARK_FANTASY
- COSMIC_HORROR
- POLITICAL_THRILLER
- HEIST
- COMING_OF_AGE
- TRAGICOMEDY

---

## 5. HARD RULES (CONTRACT)

- Primary genre must be singular.
- Obligations must be bounded:
  - max 8 per arc (else becomes checklist overload).
- Forbidden moves must include severity.
- Tone constraints must align with Tone & Mood Engine output.
- Stakes must meet stakes_floor:
  - if below, engine emits PARTIAL/INVALID.

---

## 6. INPUT ARTIFACTS

### 6.1 INPUT — GENRE_REQUEST
**REQUIRED FIELDS**
- `g_req_id`
- `timestamp`
- `audience_target` (required)
- `platform_constraints_ref` (required)
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `format_target_ref` (optional: book/series/short/youtube/game)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 7. OUTPUT ARTIFACTS

### 7.1 OUTPUT — GENRE_PROFILE
(see model above)

### 7.2 OUTPUT — GENRE_VERDICT
- `g_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 8. CORE OPERATIONS

- OP_01: INGEST_PLATFORM_AND_TONE_CONSTRAINTS
- OP_02: SELECT_PRIMARY_GENRE_AND_SUBGENRE
- OP_03: DEFINE_EXPECTATION_MAP (contract)
- OP_04: DEFINE_OBLIGATIONS (required beats)
- OP_05: DEFINE_FORBIDDEN_MOVES (severity tagged)
- OP_06: DEFINE_INTENSITY_TOLERANCES_AND_PACING_RULES
- OP_07: BUILD_VALIDATION_GATES
- OP_08: EMIT_GENRE_PROFILE

---

## 9. GENRE VIOLATION DETECTION

Hard violations (INVALID):
- multiple primary genres
- obligations missing proof_of_delivery
- forbidden moves missing severity
- tone constraints contradict tone profile

Soft violations (PARTIAL):
- stakes below floor but can be raised
- obligations too many (fatigue)

Repair suggestions:
- reduce obligations
- clarify proofs
- align tone constraints
- adjust stakes plan

---

## 10. DEPENDENCIES

### REQUIRED
- Platform constraints
- Tone Profile

### OPTIONAL
- Mood curve
- Format target

### FORBIDDEN
- genre declared without obligations
- “genre = everything”
- ignoring platform constraints

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Genre contract undefined
- Tone mismatch unrepairable within platform constraints
- Stakes floor cannot be met given story constraints

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - choose single genre
  - rebuild obligations
  - adjust tone or platform targets

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into blending and adaptation engines

---

## 13. NON-GOALS
- Does not generate plot
- Does not write scripts
- Does not set canon

---

## 14. FINAL STATEMENT

Genre is expectation with teeth.
Declare it — then deliver it.

---

**STATUS:** Genre Engine v1.0  
**REALM:** ACTIVE
