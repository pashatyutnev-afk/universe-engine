# VAL — CREDITS & RIGHTS (MUSIC RELEASE COMPLIANCE) (CANON)

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md
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
UID: UE.VAL.MUSIC.CREDITS_RIGHTS.001
OWNER: SYSTEM
ROLE: Hard validator for release-time rights clarity and credits completeness. Enforces KB provenance markers for any non-user lyrics/corpus usage and blocks publishing when rights are ambiguous. Produces deterministic violations.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt credits/rights validator: strict provenance checks, required credits fields, and publish-blocking severity for any ambiguity."
- REASON: "Rights ambiguity is the highest-risk failure mode; must be enforced at VAL level."
- IMPACT: "No release can pass without explicit rights provenance or original declaration."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.CREDITS.001

---

## 0) PURPOSE (LAW)
Этот валидатор проверяет два блока:
1) CREDITS — минимальный набор полей заполнен
2) RIGHTS — ясность прав на текст/источник (особенно для CORPUS)

Если есть сомнение → FAIL.

---

## 1) ABSOLUTE RULES
### 1.1 Source Lock is absolute
Все non-user lyrics/corpus обязаны иметь KB provenance.

KB SOURCE LOCK / NO FANTASY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

### 1.2 No “unknown status”
SOURCE_STATUS может быть только:
- PD_CONFIRMED
- LICENSE_CONFIRMED
Иначе → FAIL.

### 1.3 Release-time enforcement
Если документ помечен как PUBLISH_READY (или находится в release pack):
- любые нарушения прав/кредитов считаются блокирующими (S0/S1).

---

## 2) APPLICABILITY
- MUSIC_TRACK_RELEASE
- MUSIC_RELEASE_PACK

Invocation:
- RELEASE_PACK_ORC (final)
- DOC_CONTROLLER_SPC signoff chain

---

## 3) REQUIRED REFERENCES (RAW)
CREDITS & METADATA POLICY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

RELEASE PACK READY (VAL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md

---

## 4) REQUIRED FIELDS (MINIMUM)
### 4.1 CREDITS required
- MUSIC_BY
- LYRICS_BY (or N/A if INSTRUMENTAL)
- VOCALS (or N/A if INSTRUMENTAL)
Optional but recommended:
- MIX_MASTER
- ARTWORK

### 4.2 RIGHTS required
- LYRICS_MODE: ORIGINAL | CORPUS | INSTRUMENTAL

If LYRICS_MODE = ORIGINAL:
- RIGHTS_NOTE must state original text (user/system)

If LYRICS_MODE = CORPUS:
- KB_SOURCE_RAW
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE
- FULL_TEXT_ALLOWED (only if full text used)

If LYRICS_MODE = INSTRUMENTAL:
- RIGHTS optional

---

## 5) VALIDATION CHECKS
### CHECK A — credits present
If any required field missing/empty → VIOLATION: CREDITS_MISSING_FIELDS (S1)

### CHECK B — lyrics mode declared
If missing/invalid → VIOLATION: LYRICS_MODE_MISSING (S0)

### CHECK C — ORIGINAL requires rights note
If ORIGINAL and RIGHTS_NOTE missing → VIOLATION: ORIGINAL_RIGHTS_NOTE_MISSING (S1)

### CHECK D — CORPUS requires provenance
If CORPUS and any of required provenance fields missing → VIOLATION: CORPUS_PROVENANCE_MISSING (S0)

### CHECK E — SOURCE_STATUS strict enum
If CORPUS and SOURCE_STATUS not in allowed enum → VIOLATION: SOURCE_STATUS_INVALID (S0)

### CHECK F — full text requires explicit allowance
If full lyrics text included and FULL_TEXT_ALLOWED missing → VIOLATION: FULL_TEXT_NOT_ALLOWED (S0)

### CHECK G — no external source claims
If rights refer to an external source without KB_SOURCE_RAW → VIOLATION: NON_KB_SOURCE_REFERENCE (S0)

---

## 6) VIOLATION RECORD FORMAT (REQUIRED)
- VAL_ID: UE.VAL.MUSIC.CREDITS_RIGHTS.001
- TARGET_ARTIFACT_TYPE: (MUSIC_TRACK_RELEASE | MUSIC_RELEASE_PACK | OTHER)
- TARGET_RAW: (raw link)
- VIOLATION_CODE: (section 7)
- SEVERITY: S0 | S1 | S2 | S3
- EVIDENCE:
  - bullet list (missing fields / bad status)
- REQUIRED_FIX:
  - bullet list
- RETURN_TO:
  - release pack ORC raw

---

## 7) VIOLATION CODES (CANON)
- CREDITS_MISSING_FIELDS (S1)
- LYRICS_MODE_MISSING (S0)
- ORIGINAL_RIGHTS_NOTE_MISSING (S1)
- CORPUS_PROVENANCE_MISSING (S0)
- SOURCE_STATUS_INVALID (S0)
- FULL_TEXT_NOT_ALLOWED (S0)
- NON_KB_SOURCE_REFERENCE (S0)

---

## 8) VERDICT RULES
PASS:
- no S0/S1 violations

FAIL:
- any S0
- any S1 (when PUBLISH_READY=true or in release pack)

---

## 9) DEFAULT RETURN ROUTE (RAW)
RELEASE_PACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

---

## 10) CHANGE POLICY (LOCK)
- Keep aligned with KB Source Lock and Credits/Metadata CTL
- Any change to allowed statuses or fields → PATCH + sync related validators

---

END.
