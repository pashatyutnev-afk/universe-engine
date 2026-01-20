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
VERSION: 1.0.1
UID: UE.XREF.MAP.VALIDATION_MATRIX.001
OWNER: SYSTEM
ROLE: Defines required CTL/VAL/QA gates by artifact type and acceptance criteria.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Filled minimal validation matrix: core doc artifact classes + music factory artifact classes with deterministic gate sets."
- REASON: "Remove TBD ambiguity so pipelines can enforce gates without guessing."
- IMPACT: "Routing and acceptance become auditable. Every output can be checked against mandatory gates."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.MAP.VALMATRIX.002

---

## 0) PURPOSE (LAW)
Матрица говорит: для каждого класса артефакта какие CTL/VAL/QA обязательны и как выглядит PASS.

---

## 1) FIELD DICTIONARY
- ARTIFACT_TYPE
- REQUIRED_CTL (comma ids or names)
- REQUIRED_VAL (comma ids or names)
- REQUIRED_QA (comma ids or names)
- REQUIRED_DOC_CONTROL: YES | NO
- PASS_CRITERIA: short
- NOTES

---

## 2) MATRIX TABLE (CANON MINIMUM)

| ARTIFACT_TYPE | REQUIRED_CTL | REQUIRED_VAL | REQUIRED_QA | REQUIRED_DOC_CONTROL | PASS_CRITERIA | NOTES |
|---|---|---|---|---|---|---|
| RUNBOOK | READINESS_CHECK_CTL | ERROR_DETECTION_ENG, FACT_CONSISTENCY_ENG, LANGUAGE_LINGUISTICS_ENG | NATURALNESS_GATE_QA | YES | "BOOT markers required; stop conditions explicit; mandatory response format defined; no contradictions" | "Use for START / runtime entrypoints and any procedural runbooks" |
| MAP | READINESS_CHECK_CTL | ERROR_DETECTION_ENG, FACT_CONSISTENCY_ENG | NATURALNESS_GATE_QA | YES | "Schema complete; no broken references; no duplicate/conflicting rows; version bumped" | "Use for XREF maps, storage maps, selection maps" |
| SPEC | READINESS_CHECK_CTL | ERROR_DETECTION_ENG, FACT_CONSISTENCY_ENG, LANGUAGE_LINGUISTICS_ENG | NATURALNESS_GATE_QA | YES | "Required sections present; interfaces are RAW-only; boundaries explicit; no mixed roles inside ENG sections" | "Use for standards/specs/contracts" |
| PACKAGE | READINESS_CHECK_CTL | ERROR_DETECTION_ENG, FACT_CONSISTENCY_ENG | NATURALNESS_GATE_QA | YES | "Self-contained; pointers and targets explicit; naming/UID consistent; migration notes if rename" | "Use for output packs / release packs / integration packs" |
| MUSIC_TRACK_CARD | READINESS_CHECK_CTL, QUALITY_GATES_CTL, CATALOG_MEMORY_CTL | ERROR_DETECTION_ENG, PROMPT_FIDELITY_VAL, NAMING_COLLISION_VAL, CREDITS_RIGHTS_VAL | SCROLL_STOP_5S_QA, RECOGNITION_10S_QA, REGRESSION_GUARD_QA | YES | "Track metadata coherent; UID/title consistent; credits policy satisfied; QA gates PASS/WARN resolved per policy" | "Applies to 08_DATABASES track card artifacts" |
| MUSIC_TRACK_PROMPT | READINESS_CHECK_CTL, PROMPT_CONTRACT_CTL, DURATION_POLICY_CTL, NEGATIVE_SPEC_LIBRARY_CTL | PROMPT_FIDELITY_VAL, REPEAT_GUARD_VAL, PD_ONLY_VAL | HOOK_PANEL_QA, LOOP_15S_QA | YES | "Prompt pack follows contract; no contradictions; repeat-safe intent; PD policy satisfied; hook intent present" | "Applies to Suno/Udio prompt docs" |
| MUSIC_TRACK_RELEASE | READINESS_CHECK_CTL, QUALITY_GATES_CTL, FINGERPRINT_COLLISION_THRESHOLDS_CTL, CREDITS_METADATA_POLICY_CTL | COLLISION_BLOCKER_VAL, CREDITS_RIGHTS_VAL, REPEAT_GUARD_VAL, VOICE_DIVERSITY_VAL | MIX_TRANSLATION_QA, VOICE_DIVERSITY_AUDIT_QA, REGRESSION_GUARD_QA | YES | "Collision not BLOCK; rights/credits PASS; mix translates; voice diversity intent satisfied; release variant naming consistent" | "Applies to track release docs and final takes" |
| MUSIC_RELEASE_PACK | READINESS_CHECK_CTL, QUALITY_GATES_CTL, RELEASE_VARIANTS_CTL, CREDITS_METADATA_POLICY_CTL | COLLISION_BLOCKER_VAL, CREDITS_RIGHTS_VAL, NAMING_COLLISION_VAL | RELEASE_PACK_READY_QA, REGRESSION_GUARD_QA | YES | "All included artifacts have PASS; variants registered; credits complete; pack self-contained and navigable" | "Applies to brand/release pack outputs" |

---

## 3) NOTES (BOUNDARIES)
- Матрица перечисляет минимально-обязательные гейты.
- Если пайплайн требует дополнительные доменные проверки, они добавляются как новые строки или через расширение REQUIRED_* (PATCH).
- Нельзя оставлять TBD в обязательных полях. Если сущности не хватает, фиксируется GAP и создаётся сущность по шаблону.

---  
END.
