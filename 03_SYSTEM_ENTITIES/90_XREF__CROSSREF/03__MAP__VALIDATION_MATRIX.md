# XREF MAP — VALIDATION MATRIX (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: VALIDATION_MATRIX
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.VALIDATION_MATRIX.001
OWNER: SYSTEM
ROLE: Deterministic gate requirements per ARTIFACT_TYPE. Defines required CTL/VAL/QA sets and canonical order. Used by ORC to enforce compliance without guessing.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized minimal working validation matrix for music artifact types (track card/prompt/release, release pack, spec/package)."
- REASON: "Make gate selection deterministic across ORC pipelines; remove ad-hoc checks and ambiguity."
- IMPACT: "Every pipeline can resolve required CTL/VAL/QA per artifact type and produce auditable verdicts."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.VALMATRIX.001

---

## 0) PURPOSE (LAW)
Эта матрица говорит ORC: какие гейты обязательны для каждого типа артефакта.
ORC обязан:
- определить ARTIFACT_TYPE,
- взять REQUIRED_CTL/VAL/QA,
- применить в каноническом порядке,
- зафиксировать verdicts и violations.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Только RAW ссылки.

### 1.2 Canonical order (default)
READINESS_CHECK_CTL → REQUIRED_CTL → REQUIRED_VAL → REQUIRED_QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.3 No implicit gates
Если гейт не указан в строке типа артефакта — он не обязателен.
Сделать его обязательным можно только через PATCH этой матрицы.

---

## 2) REQUIRED CORE CTL (GLOBAL)
READINESS_CHECK_CTL (mandatory for any pipeline step that outputs artifacts)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 3) MATRIX RECORD SCHEMA (CANON)
Каждая строка обязана иметь:
- ARTIFACT_TYPE
- REQUIRED_CTL_RAW (0..n)
- REQUIRED_VAL_RAW (0..n)
- REQUIRED_QA_RAW (0..n)
- PASS_CRITERIA (short)
- RETURN_TO_ORC_DEFAULT (raw)
- NOTES

---

# 4) VALIDATION MATRIX — MUSIC (MINIMUM WORKING SET)

## 4.1 ARTIFACT_TYPE: MUSIC_TRACK_CARD
REQUIRED_CTL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md
REQUIRED_VAL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md
REQUIRED_QA_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md
PASS_CRITERIA: Card is complete, consistent, non-colliding, and passes quality gates.
RETURN_TO_ORC_DEFAULT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
NOTES: Card gates focus on metadata integrity and catalog differentiation.

---

## 4.2 ARTIFACT_TYPE: MUSIC_TRACK_PROMPT
REQUIRED_CTL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md
REQUIRED_VAL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md
REQUIRED_QA_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md
PASS_CRITERIA: Prompt meets contract, avoids repetition, and passes quick attention/recognition gates.
RETURN_TO_ORC_DEFAULT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
NOTES: UA/UGC-specific CTL/QA are optional unless added here by PATCH.

---

## 4.3 ARTIFACT_TYPE: MUSIC_TRACK_RELEASE
REQUIRED_CTL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md
REQUIRED_VAL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
REQUIRED_QA_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md
PASS_CRITERIA: Release metadata/credits are consistent and rights-safe; collision risk is controlled.
RETURN_TO_ORC_DEFAULT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
NOTES: If release is part of a pack, pack-level validators still apply separately.

---

## 4.4 ARTIFACT_TYPE: MUSIC_RELEASE_PACK
REQUIRED_CTL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
REQUIRED_VAL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md
REQUIRED_QA_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md
PASS_CRITERIA: Pack is self-contained, link-complete, rights-safe, and collision-safe; passes differentiation and regression gates.
RETURN_TO_ORC_DEFAULT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
NOTES: Pack requires working RAW pointers to all included artifacts.

---

## 4.5 ARTIFACT_TYPE: SPEC
REQUIRED_CTL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md
REQUIRED_VAL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md
REQUIRED_QA_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md
PASS_CRITERIA: Spec is complete, consistent, and does not break downstream pipelines.
RETURN_TO_ORC_DEFAULT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
NOTES: SPEC is validated for structural readiness more than content quality.

---

## 4.6 ARTIFACT_TYPE: PACKAGE
REQUIRED_CTL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md
REQUIRED_VAL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md
REQUIRED_QA_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md
PASS_CRITERIA: Package is self-contained, manifest-complete, and pointer-safe; does not regress structure.
RETURN_TO_ORC_DEFAULT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
NOTES: PACKAGE here is structural; domain-specific packs may add stricter rows via PATCH.

---

## 4.7 ARTIFACT_TYPE: POET_PACK_SPEC
REQUIRED_CTL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
REQUIRED_VAL_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
REQUIRED_QA_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md
PASS_CRITERIA: Poet pack complies with PD policy and is structurally reusable.
RETURN_TO_ORC_DEFAULT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md
NOTES: PD-only enforcement is mandatory for this type.

---

## 5) EXTENSION POLICY (STRICT)
- Добавление нового ARTIFACT_TYPE = новая строка + PATCH.
- Усиление обязательности гейтов = PATCH (не “по умолчанию”).
- Если для строки нет существующего CTL/VAL/QA файла по RAW → STOP: marker not confirmed (must create missing entity first).

---

END.
