# VAL — COLLISION BLOCKER (CATALOG UNIQUENESS) (CANON)

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 50_VAL__VALIDATORS
FAMILY: 10_MUSIC_VALIDATORS
LEVEL: L2
DOC_TYPE: VAL (VALIDATOR)
ENTITY_TYPE: VALIDATOR
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUSIC.COLLISION_BLOCKER.001
OWNER: SYSTEM
ROLE: Validates catalog uniqueness based on explicit similarity score + banding from fingerprint thresholds policy. Blocks near-duplicates (S0/S1) deterministically, enforces evidence fields, and routes fixes to the correct ORC step.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt collision blocker: consumes FP policy score/band/action trace and hard-fails on S0/S1; requires comparator list and patch axis."
- REASON: "Catalog quality collapses when collisions are handled informally."
- IMPACT: "Near-duplicates cannot pass release gates; remediation becomes standardized."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.COLLISION.001

---

## 0) PURPOSE (LAW)
Этот валидатор проверяет, что кандидат трека не является коллизией каталога:
- использует численный SCORE и BAND
- применяет обязательное действие по BAND
- блокирует релиз при S0/S1
- разрешает S2 только при корректной маркировке “variant”
- пропускает S3

---

## 1) ABSOLUTE RULES
### 1.1 Requires FP trace
Без FP trace (score/band/action/comparators) валидатор не может работать.
Если FP trace отсутствует → FAIL_CLASS: input absent.

### 1.2 Hard fail on S0/S1
S0/S1 → FAIL (нельзя пропустить).

### 1.3 Deterministic evidence
Список сравнений (comparators) обязателен — хотя бы 1 элемент.
Пусто → FAIL.

---

## 2) APPLICABILITY
### 2.1 Artifact contexts
- MUSIC_TRACK_CARD (candidate)
- MUSIC_TRACK_RELEASE (publish candidate)
- MUSIC_RELEASE_PACK (variants set)

### 2.2 Invocation points
- TRACK_TEST_DOC_GATE_ORC (pre-release)
- RELEASE_PACK_ORC (final)

---

## 3) REQUIRED REFERENCES (RAW)
FINGERPRINT COLLISION THRESHOLDS (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

CATALOG MEMORY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

Return routes (ORC):
ALBUM_TO_TRACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

GROUP_TO_ALBUM_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

---

## 4) REQUIRED INPUT SHAPE (FP TRACE)
В целевом артефакте должен присутствовать блок FP trace:

- SCORE: 0.00–1.00
- BAND: S0 | S1 | S2 | S3
- ACTION: BLOCK | REWORK | ALLOW_WITH_TAG | ALLOW
- COMPARATORS:
  - list of compared catalog item UIDs/pointers (>=1)
- REQUIRED_PATCH_AXIS: (required for S0/S1)

Если отсутствует любой обязательный элемент → VIOLATION.

---

## 5) VALIDATION CHECKS
### CHECK A — score valid
- numeric
- in range [0.00, 1.00]
Else → VIOLATION: SCORE_INVALID (S0)

### CHECK B — band/action consistency
Must match policy:
- S0 → BLOCK
- S1 → REWORK
- S2 → ALLOW_WITH_TAG
- S3 → ALLOW
Else → VIOLATION: BAND_ACTION_MISMATCH (S0)

### CHECK C — comparators present
- COMPARATORS length >= 1
Else → VIOLATION: COMPARATORS_MISSING (S0)

### CHECK D — hard fail S0/S1
If BAND in {S0,S1} → VIOLATION: COLLISION_TOO_HIGH (S0)

### CHECK E — S2 must be tagged variant
If BAND = S2:
- artifact must contain VARIANT tag (or equivalent marker) + DIFFERENTIATION_NOTE
Else → VIOLATION: VARIANT_TAG_MISSING (S1)

### CHECK F — patch axis required for S0/S1
If BAND in {S0,S1}:
- REQUIRED_PATCH_AXIS must be present
Else → VIOLATION: PATCH_AXIS_MISSING (S1)

---

## 6) VIOLATION RECORD FORMAT (REQUIRED)
- VAL_ID: UE.VAL.MUSIC.COLLISION_BLOCKER.001
- TARGET_ARTIFACT_TYPE: (MUSIC_TRACK_CARD | MUSIC_TRACK_RELEASE | MUSIC_RELEASE_PACK | OTHER)
- TARGET_RAW: (raw link)
- VIOLATION_CODE: (section 7)
- SEVERITY: S0 | S1 | S2 | S3
- EVIDENCE:
  - bullets (score/band/action/comparators)
- REQUIRED_FIX:
  - bullets
- RETURN_TO:
  - raw link route (section 8)

---

## 7) VIOLATION CODES (CANON)
- FP_TRACE_MISSING (S0)
- SCORE_INVALID (S0)
- BAND_ACTION_MISMATCH (S0)
- COMPARATORS_MISSING (S0)
- COLLISION_TOO_HIGH (S0)
- VARIANT_TAG_MISSING (S1)
- PATCH_AXIS_MISSING (S1)

---

## 8) DEFAULT RETURN ROUTES (RAW)
If S0 with SCORE >= 0.92:
- return to GROUP_TO_ALBUM_ORC (replan) OR ALBUM_TO_TRACK_ORC (major rework)

If S1 (0.85–0.92):
- return to ALBUM_TO_TRACK_ORC (patch prompt one-axis)

Default:
ALBUM_TO_TRACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 9) VERDICT RULES
PASS:
- no violations

FAIL:
- any S0 or S1 violation

---

## 10) CHANGE POLICY (LOCK)
- Alignment with FP thresholds policy is mandatory
- If thresholds or required trace fields change, update this VAL via PATCH

---

END.
