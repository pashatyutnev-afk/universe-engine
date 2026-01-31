# CTL — FINGERPRINT COLLISION THRESHOLDS (MUSIC) (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
FAMILY: 10_MUSIC_CONTROLLERS
LEVEL: L2
DOC_TYPE: CTL (CONTROLLER)
ENTITY_TYPE: CONTROLLER
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUSIC.FINGERPRINT_THRESHOLDS.001
OWNER: SYSTEM
ROLE: Defines collision thresholds and mandatory actions when new track candidates are too similar to existing catalog items. Provides deterministic severity bands and required remediation routes, without relying on any specific audio fingerprinting tool.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Introduced collision threshold bands (S0–S3) with deterministic actions, integrating with catalog memory and collision/repeat validators."
- REASON: "Catalog quality degrades when near-duplicates slip through; thresholds must be explicit."
- IMPACT: "Pipelines can block or redirect similar outputs consistently; QA/regression becomes enforceable."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.FPTH.001

---

## 0) PURPOSE (LAW)
Эта политика задаёт:
- как классифицировать “похожесть” трека на существующие треки каталога (collision),
- какие действия обязательны по каждому уровню (block / rework / tag / allow),
- как оформлять решение в виде trace.

Важно: политика не привязана к конкретному алгоритму отпечатка — она задаёт пороги как абстрактные “similarity score” в диапазоне 0.00–1.00.

---

## 1) ABSOLUTE RULES
### 1.1 Explicit similarity score required
Если пайплайн утверждает “похоже/не похоже”, должен быть явный SCORE (0.00–1.00) или иной численный эквивалент, приведённый к шкале 0–1.

Если нет численного значения → FAIL (marker not confirmed).

### 1.2 Deterministic banding
SCORE обязан быть отнесён к одному из бэндов (S0–S3) ниже.  
Иное — запрещено.

### 1.3 Mandatory action per band
Каждый бэнд имеет обязательное действие и return route.  
Нельзя “просто оставить как есть” при S0/S1.

---

## 2) APPLICABILITY
### 2.1 Artifact contexts
- MUSIC_TRACK_CARD (as catalog candidate)
- MUSIC_TRACK_RELEASE (as publish candidate)
- RELEASE_PACK variants (if generating multiple versions)

### 2.2 Invocation points (typical)
- ALBUM_TO_TRACK_ORC: после первичной генерации кандидата (pre-pack)
- TRACK_TEST_DOC_GATE_ORC: перед PASS на упаковку (если матрица требует)
- RELEASE_PACK_ORC: перед финальной публикацией вариантов

---

## 3) REQUIRED REFERENCES (RAW)
CATALOG MEMORY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

COLLISION BLOCKER (VAL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md

REPEAT GUARD (VAL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md

REGRESSION GUARD (QA)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md

---

## 4) THRESHOLD BANDS (CANON)
Assume similarity SCORE ∈ [0.00, 1.00], where 1.00 = identical.

### BAND S0 — HARD COLLISION (BLOCK)
- SCORE ≥ 0.92
Meaning:
- near-duplicate / same melody/hook/structure or obvious clone
Action (mandatory):
- BLOCK packaging/publishing
- require rework with “one-axis change” or new blueprint slot
Return:
- ALBUM_TO_TRACK_ORC (rework) or GROUP_TO_ALBUM_ORC (replan)

### BAND S1 — STRONG SIMILARITY (REWORK REQUIRED)
- 0.85 ≤ SCORE < 0.92
Meaning:
- very similar fingerprint; high risk of catalog duplication
Action (mandatory):
- REWORK required
- must specify “differentiation axis” (only one axis per patch run)
Return:
- ALBUM_TO_TRACK_ORC (patch prompt)

### BAND S2 — MODERATE SIMILARITY (ALLOW WITH TAG + DIFFERENTIATION NOTE)
- 0.70 ≤ SCORE < 0.85
Meaning:
- noticeable similarity but may be acceptable if positioned as variant
Action (mandatory):
- ALLOW only if:
  - tagged as VARIANT (or “close sibling”)
  - differentiation note exists in TRACK_CARD
Return:
- ALBUM_TO_TRACK_ORC (update card/notes) if missing tags/notes

### BAND S3 — LOW SIMILARITY (ALLOW)
- SCORE < 0.70
Meaning:
- acceptable uniqueness
Action:
- allow

---

## 5) REQUIRED EVIDENCE (MINIMUM TRACE)
Каждое решение по коллизии обязано фиксировать:

- FP_POLICY_ID: UE.CTL.MUSIC.FINGERPRINT_THRESHOLDS.001
- TARGET_TRACK_UID (or placeholder)
- COMPARATORS:
  - list of compared catalog items (UIDs or pointers)
- SCORE:
  - numeric score 0.00–1.00
- BAND:
  - S0 | S1 | S2 | S3
- ACTION:
  - BLOCK | REWORK | ALLOW_WITH_TAG | ALLOW
- REQUIRED_PATCH_AXIS (only for S0/S1):
  - one of: MELODY | HARMONY | RHYTHM | TEMPO | ARRANGEMENT | VOCAL_STYLE | LYRICS_APPROACH | SOUND_DESIGN
- RETURN_TO (if not ALLOW):
  - raw pointer route

Если missing SCORE/BAND/ACTION → FAIL (marker not confirmed)

---

## 6) DETERMINISTIC CHECKS
### CHECK A — score present and valid
- must be numeric
- 0.00 ≤ score ≤ 1.00
Else → FAIL (marker not confirmed)

### CHECK B — band assigned correctly
- band must match thresholds in section 4
Else → FAIL (policy violation)

### CHECK C — action matches band
- S0 must be BLOCK
- S1 must be REWORK
- S2 must be ALLOW_WITH_TAG
- S3 must be ALLOW
Else → FAIL (policy violation)

### CHECK D — remediation info for S0/S1
- REQUIRED_PATCH_AXIS must be present
- return route must be present
Else → FAIL (marker not confirmed)

---

## 7) DEFAULT RETURN ROUTES (RAW)
ALBUM_TO_TRACK_ORC (patch/rework)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

GROUP_TO_ALBUM_ORC (replan)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

---

## 8) CTL VERDICT FORMAT (REQUIRED)
- CTL_ID: UE.CTL.MUSIC.FINGERPRINT_THRESHOLDS.001
- TARGET_ARTIFACT_TYPE: (MUSIC_TRACK_CARD | MUSIC_TRACK_RELEASE | MUSIC_RELEASE_PACK | OTHER)
- TARGET_RAW: (raw link)
- VERDICT: PASS | FAIL
- FINDINGS:
  - bullet list
- REQUIRED_FIXES:
  - bullet list (empty if PASS)
- FAIL_CLASS:
  - RAW missing | marker not confirmed | input absent | policy violation
- RETURN_TO:
  - default return route raw

---

## 9) CHANGE POLICY (LOCK)
- Пороги менять только PATCH
- Если меняются обязательные поля trace — синхронизировать validators/QA and Validation Matrix.

---

END.
