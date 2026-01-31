# VAL — RELEASE PACK READY (MUSIC) (CANON)

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md
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
UID: UE.VAL.MUSIC.RELEASE_PACK_READY.001
OWNER: SYSTEM
ROLE: Validates that a MUSIC_RELEASE_PACK is complete, structured, and publish-ready: required files/sections exist, metadata and credits are present, rights/provenance are clear, and variants are declared. Produces deterministic violation records and blocks final packaging when incomplete.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt release pack readiness validator: checks minimum structure, metadata/credits compliance, rights provenance, and variant declarations."
- REASON: "Release packs were passing without consistent structure and publish-ready fields."
- IMPACT: "Packaging becomes reliable; downstream distribution processes become deterministic."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.RELPACK.001

---

## 0) PURPOSE (LAW)
Этот валидатор отвечает на один вопрос:
Готов ли релиз-пак к публикации без ручных догадок?

Проверяется:
- структура и обязательные элементы пакета
- метаданные и кредиты
- права на текст/источники (если corpus)
- описание вариантов (shorts/alt/clean/etc)

---

## 1) ABSOLUTE RULES
### 1.1 Target must be explicit
Должен быть явный TARGET_RAW на конкретный `MUSIC_RELEASE_PACK` документ/папку/паспорт.

Если отсутствует → FAIL_CLASS: input absent.

### 1.2 No silent pass
Если отсутствует обязательный элемент — всегда FAIL с REQUIRED_FIX.

### 1.3 Deterministic evidence
Каждое нарушение должно ссылаться на конкретный отсутствующий блок/файл/маркер.

---

## 2) APPLICABILITY
- MUSIC_RELEASE_PACK (primary)

Invocation:
- RELEASE_PACK_ORC (before final signoff)
- DOC_CONTROLLER_SPC signoff chain (as required validator)

---

## 3) REQUIRED REFERENCES (RAW)
MUSIC RELEASE PACK STANDARD  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/10_MUSIC_SYSTEM/05__MUSIC_RELEASE_PACK_STANDARD.md

RELEASE PACK ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

CREDITS & METADATA POLICY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

CREDITS & RIGHTS (VAL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

---

## 4) MINIMUM PACK CONTENT (CANON)
Validator expects the pack to contain, at minimum:

### 4.1 PACK PASSPORT / INDEX
- PACK_UID (or placeholder)
- TRACK_UID
- PACK_INTENT (single / EP / album track / shorts variants)
- FILE LIST (or pointers)

### 4.2 METADATA BLOCK
- as required by CREDITS_METADATA_POLICY_CTL (minimum fields)

### 4.3 CREDITS BLOCK
- as required by CREDITS_METADATA_POLICY_CTL

### 4.4 RIGHTS / PROVENANCE
- required if lyrics/corpus used (SOURCE_STATUS, KB_SOURCE_RAW, etc)

### 4.5 VARIANTS (if any)
If pack intent includes variants:
- VARIANT_LIST with names and purpose (e.g., SHORTS_15S, CLEAN, ALT_HOOK)
- For each variant: duration target and hook timing intent (if applicable)

---

## 5) VALIDATION CHECKS (DETERMINISTIC)
### CHECK A — pack standard alignment marker
Pack must declare it follows release pack standard (explicit reference or marker).
If missing → VIOLATION: STANDARD_REF_MISSING (S1)

### CHECK B — pack passport/index present
If missing → VIOLATION: PACK_PASSPORT_MISSING (S0)

### CHECK C — metadata present
If missing required metadata fields → VIOLATION: METADATA_INCOMPLETE (S0)

### CHECK D — credits present
If missing/empty → VIOLATION: CREDITS_INCOMPLETE (S0)

### CHECK E — rights/provenance compliance
If CORPUS used and provenance missing or SOURCE_STATUS not confirmed → VIOLATION: RIGHTS_NOT_CLEAR (S0)

### CHECK F — variants declared when needed
If pack intent includes variants but no variant list → VIOLATION: VARIANTS_MISSING (S1)

### CHECK G — variant fields completeness
For each variant (if present):
- name present
- purpose present
- (recommended) duration target present
If missing → VIOLATION: VARIANT_FIELDS_INCOMPLETE (S2)

---

## 6) VIOLATION RECORD FORMAT (REQUIRED)
- VAL_ID: UE.VAL.MUSIC.RELEASE_PACK_READY.001
- TARGET_ARTIFACT_TYPE: MUSIC_RELEASE_PACK
- TARGET_RAW: (raw link)
- VIOLATION_CODE: (section 7)
- SEVERITY: S0 | S1 | S2 | S3
- EVIDENCE:
  - bullet list (missing blocks/fields)
- REQUIRED_FIX:
  - bullet list
- RETURN_TO:
  - RELEASE_PACK_ORC raw

---

## 7) VIOLATION CODES (CANON)
- STANDARD_REF_MISSING (S1)
- PACK_PASSPORT_MISSING (S0)
- METADATA_INCOMPLETE (S0)
- CREDITS_INCOMPLETE (S0)
- RIGHTS_NOT_CLEAR (S0)
- VARIANTS_MISSING (S1)
- VARIANT_FIELDS_INCOMPLETE (S2)

---

## 8) VERDICT RULES
PASS:
- no S0/S1 violations
- S2 only allowed if pack intent is not “publish now” (otherwise treat as S1 by ORC)

FAIL:
- any S0
- any S1
- or S2 when pack is marked PUBLISH_READY=true

---

## 9) DEFAULT RETURN ROUTE (RAW)
RELEASE_PACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

---

## 10) CHANGE POLICY (LOCK)
- If release pack standard changes, update this validator via PATCH.
- Keep in sync with CREDITS_METADATA_POLICY_CTL and CREDITS_RIGHTS_VAL.

---

END.
