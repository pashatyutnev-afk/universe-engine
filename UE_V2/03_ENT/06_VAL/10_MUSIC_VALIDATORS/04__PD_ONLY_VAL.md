# VAL — PD ONLY (POETRY SOURCE COMPLIANCE) (CANON)

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
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
UID: UE.VAL.MUSIC.PD_ONLY.001
OWNER: SYSTEM
ROLE: Enforce PD-only (or explicitly licensed) corpus usage by validating KB provenance markers and policy compliance. Produces deterministic violation records; blocks packaging/usage when source status is not confirmed.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt PD_ONLY_VAL as strict provenance validator: checks KB pointers, PD/license status markers, excerpt limits flags, and forbids unknown/guessed sources."
- REASON: "CTL sets policy; VAL must hard-fail any ambiguous provenance to prevent rights risk."
- IMPACT: "Poet packs and prompts cannot pass gates unless provenance is explicit and compliant."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.PDONLY.001

---

## 0) PURPOSE (LAW)
Этот валидатор проверяет, что любой corpus text (не user original) соответствует политике PD-only:
- источник существует в KB (RAW pointer),
- статус источника подтверждён (PD_CONFIRMED или LICENSE_CONFIRMED),
- выдержки оформлены с provenance блоком,
- отсутствуют “серые” источники и догадки.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Только RAW.

### 1.2 No guessing
Нельзя выводить, что текст PD “по ощущениям”.
Если нет явного маркера статуса в provenance → FAIL.

### 1.3 Validator enforces policy, not replaces it
Этот VAL предполагает, что CTL `POET_PD_POLICY_CTL` уже применён.
Если CTL trace отсутствует (когда он обязателен по матрице) → FAIL как нарушение пайплайна.

### 1.4 Stop conditions (validator context)
В рамках валидации фиксируем нарушения и возвращаем FAIL.
Если не можем открыть RAW pointer (источник/док) → трактуем как RAW missing (fatal).

---

## 2) REQUIRED REFERENCES (RAW)
POET PD POLICY (CTL)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

KB SOURCE LOCK (NO FANTASY)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

Primary consumer ORC (poet pack)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

---

## 3) APPLICABILITY
### 3.1 Artifact types (minimum)
- POET_PACK_SPEC
- MUSIC_TRACK_PROMPT (если содержит corpus text)

### 3.2 Trigger rule
Если артефакт содержит corpus text:
- должен существовать provenance блок (см. 4)
- иначе нарушение.

---

## 4) REQUIRED INPUT SHAPE (WHAT VAL EXPECTS)
Для каждого corpus item должен существовать provenance блок:

- KB_SOURCE_RAW: (raw link to KB item/module)
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE: short note, no guessing
- FULL_TEXT_ALLOWED: optional marker (only if full text is used)

Если артефакт хранит список corpus items:
- каждый item обязан ссылаться на provenance.

---

## 5) VALIDATION CHECKS (DETERMINISTIC)

### CHECK A — KB pointer exists and opens
For each KB_SOURCE_RAW:
- RAW opens successfully
If any fails → VIOLATION: RAW_MISSING

### CHECK B — SOURCE_STATUS is explicit and allowed
SOURCE_STATUS must be exactly:
- PD_CONFIRMED
or
- LICENSE_CONFIRMED
Anything else (missing/unknown/freeform) → VIOLATION: STATUS_NOT_CONFIRMED

### CHECK C — Policy CTL trace present when required
If artifact type requires `POET_PD_POLICY_CTL` (by matrix / by pipeline contract):
- validate presence of CTL verdict trace in artifact (or attached trace)
If absent → VIOLATION: CTL_NOT_APPLIED

### CHECK D — Excerpt limits compliance marker
If excerpt text length exceeds policy default and FULL_TEXT_ALLOWED not present:
- VIOLATION: EXCERPT_LIMIT_VIOLATION

Validator rule:
- VAL does not compute exact chars universally; it requires the artifact to declare whether it is FULL_TEXT and to include FULL_TEXT_ALLOWED marker when needed.
If full text used without FULL_TEXT_ALLOWED → VIOLATION.

### CHECK E — No “non-KB external source”
If provenance references anything without KB_SOURCE_RAW:
- VIOLATION: NON_KB_SOURCE_REFERENCE

---

## 6) VIOLATION RECORD FORMAT (REQUIRED)
Каждое нарушение фиксируется как запись:

- VAL_ID: UE.VAL.MUSIC.PD_ONLY.001
- TARGET_ARTIFACT_TYPE: (POET_PACK_SPEC | MUSIC_TRACK_PROMPT | OTHER)
- TARGET_RAW: (raw link)
- VIOLATION_CODE: (one of section 7)
- SEVERITY: S0 | S1 | S2 | S3
- EVIDENCE:
  - short bullet list (include the specific missing marker / pointer)
- REQUIRED_FIX:
  - short bullet list
- RETURN_TO:
  - default ORC to repair (poet pack or album_to_track)

---

## 7) VIOLATION CODES (CANON)
- RAW_MISSING (S0)
  - A required KB_SOURCE_RAW cannot be opened.
- STATUS_NOT_CONFIRMED (S0)
  - SOURCE_STATUS missing or not one of allowed statuses.
- CTL_NOT_APPLIED (S1)
  - Required PD policy CTL trace is missing.
- EXCERPT_LIMIT_VIOLATION (S1)
  - Full text used without FULL_TEXT_ALLOWED marker.
- NON_KB_SOURCE_REFERENCE (S0)
  - Corpus text references an external/untracked source without KB pointer.

---

## 8) VERDICT RULES
### PASS
Только если:
- no violations recorded

### FAIL
Если есть хотя бы одно нарушение S0 или S1.

---

## 9) DEFAULT RETURN ROUTES (RAW)
Poet pack repairs:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

Track prompt repairs:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 10) CHANGE POLICY (LOCK)
Изменения кодов/жёсткости:
- только PATCH
- при изменении обязательности CTL/VAL для типов артефактов — обновить Validation Matrix.

---

END.
