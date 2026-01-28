# XREF — MAP: VALIDATION MATRIX (PIPELINES ↔ CTL/VAL/QA) (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP (XREF)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.VALIDATION_MATRIX.003
OWNER: SYSTEM
ROLE: Canon enforcement matrix defining which CTL/VAL/QA gates must run at each stage for each allowed pipeline. Resolves MATRIX_SELECTED ambiguity by defining minimum mandatory sets and optional extensions. Must align with PIPELINE_REGISTRY and MAP__PIPELINES.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Created deterministic validation matrix: minimum gates per pipeline stage + MATRIX_SELECTED resolution rules."
- REASON: "Pipeline steps were underspecified; MATRIX_SELECTED allowed silent skipping of gates."
- IMPACT: "No pipeline can run without an explicit minimum gate set; QA/VAL drift is prevented."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.VALMATRIX.003

---

## 0) PURPOSE (LAW)
Эта матрица убирает двусмысленность “MATRIX_SELECTED”.
Она фиксирует:
- минимальный обязательный набор гейтов (CTL/VAL/QA) для каждого пайплайна и стадии
- условия, когда добавляются дополнительные гейты
- правило, что “выбрать = не значит пропустить”

Если матрица расходится с `MAP__PIPELINES` или `PIPELINE_REGISTRY` → FAIL_CLASS: marker not confirmed.

---

## 1) REQUIRED REFERENCES (RAW)
MAP: PIPELINES  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

READINESS CHECK (CTL)  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 2) STAGES (CANON)
Стадии одинаковы для всех доменов:

S0 — RUN_START (boot/readiness)  
S1 — INTAKE (goal/inputs normalized)  
S2 — EXECUTE (ORC/ENG draft)  
S3 — CONTROL (CTL enforcement)  
S4 — VALIDATE (VAL checks)  
S5 — QA (acceptance/regression)  
S6 — PACKAGING (integration pack, release pack)  
S7 — SIGNOFF (doc controller + machine architect)

Примечание:
- CTL/VAL/QA могут применяться как “минимум” на отдельных стадиях.

---

## 3) MATRIX RECORD FORMAT (CANON)
Каждая строка матрицы задаёт:
- PIPELINE_ID
- STAGE
- REQUIRED_CTL (RAW list or NONE)
- REQUIRED_VAL (RAW list or NONE)
- REQUIRED_QA  (RAW list or NONE)
- CONDITIONS (when to add extra gates)
- OUTPUT_TRACE_REQUIRED (yes/no and what)

---

## 4) GLOBAL MINIMUM (APPLIES TO ALL PIPELINES)
### GM-01 — readiness must pass
For any pipeline, before S2 EXECUTE:
- REQUIRED_CTL must include READINESS_CHECK_CTL at S0.

If not passed → STOP.

---

## 5) MUSIC DOMAIN — PIPELINE MATRICES

### UE.PIPE.MUSIC.GROUP_TO_ALBUM.101
S0 RUN_START:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES (readiness trace)

S2 EXECUTE:
- CTL: NONE
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES (draft artifact pointer)

S3 CONTROL:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES (CTL verdict)

S7 SIGNOFF:
- CTL/VAL/QA: NONE (handled by governance chain outside matrix)
OUTPUT_TRACE_REQUIRED: YES (doc controller signoff note)

---

### UE.PIPE.MUSIC.ALBUM_TO_TRACK.102
S0 RUN_START:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S2 EXECUTE:
- CTL: NONE
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S3 CONTROL:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S4 VALIDATE:
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- CTL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES (VAL verdicts)

CONDITIONS (extra gates):
- If KB_CONSUMPTION is TRUE (corpus/poet used):
  - require CREDITS_RIGHTS_VAL at S4 OR require POET_PACK pipeline first (preferred).
  - require provenance block propagation in outputs.

---

### UE.PIPE.MUSIC.TRACK_TEST_GATE.103
S0 RUN_START:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S3 CONTROL (minimum):
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S4 VALIDATE (minimum):
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- CTL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S5 QA (minimum):
- QA: NONE (domain QA optional unless enforced by release route)
OUTPUT_TRACE_REQUIRED: YES (QA note if executed)

CONDITIONS (add):
- If user requests publish-ready or release pack planned:
  - add RELEASE_PACK_READY_VAL as precondition check at S4 (optional early)
- If “voice diversity” flagged:
  - add VOICE_DIVERSITY_AUDIT_QA at S5 (if available in current catalog)

---

### UE.PIPE.MUSIC.RELEASE_PACK.104
S0 RUN_START:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S6 PACKAGING:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md
- QA: NONE
OUTPUT_TRACE_REQUIRED: YES (CTL+VAL verdicts)

CONDITIONS (add):
- If KB_CONSUMPTION TRUE:
  - provenance block required in pack
  - KB_SCOPE_RAW must be present

---

### UE.PIPE.MUSIC.POET_PACK.105
S0 RUN_START:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES

S3 CONTROL:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
- VAL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES (CTL verdict)

S4 VALIDATE:
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
- CTL: NONE
- QA:  NONE
OUTPUT_TRACE_REQUIRED: YES (VAL verdict)

CONDITIONS (add):
- If FULL_TEXT_ALLOWED is required:
  - must be explicitly present in provenance markers

---

## 6) MATRIX_SELECTED RESOLUTION RULE (LAW)
Если в пайплайне/карте указан `MATRIX_SELECTED`, это означает:
- минимум берётся из этой матрицы для данного PIPELINE_ID
- дополнительные гейты добавляются только по CONDITIONS
- запрещено выбирать “пустой набор” вместо минимума

---

## 7) CHANGE POLICY (LOCK)
Любая правка пайплайна или гейтов обязана обновлять:
- PIPELINE_REGISTRY
- MAP__PIPELINES
- этот VALIDATION_MATRIX
в одном change pack (единый CHANGE_ID или связанный набор).

---

END.
