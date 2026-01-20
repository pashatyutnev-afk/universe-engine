# XREF — RULES (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__RULES__XREF.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: RULES
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.RULES.001
OWNER: SYSTEM
ROLE: Laws and authoring rules for cross-reference artifacts.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Defined XREF laws: SoT discipline, map schemas, update rules, rename policy, gate requirements."
- REASON: "Prevent drift and make routing reproducible."
- IMPACT: "Any map can be validated, maintained, and used for deterministic routing."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.RULES.001

---

## 0) PURPOSE (LAW)
XREF — это слой “стыковки”, который делает систему исполнимой: видно, кто кого вызывает, кто за что отвечает, и какие гейты обязательны.

---

## 1) ABSOLUTE LAWS
### 1.1 SoT discipline
- Карта = SoT для соответствия. Если соответствие не в карте — его “не существует” для рантайма.
- Дубли соответствий запрещены (one mapping = one SoT).

### 1.2 Table-first
- Все карты должны быть табличными/строго-структурированными.
- Свободный текст допустим только как пояснение к схеме/полям.

### 1.3 Update rule
- Любое изменение карты:
  - bump VERSION,
  - change note,
  - сохранить совместимость полей (или объявить migration).

### 1.4 Rename policy (минимальный риск)
- Разрешён только косметический rename (например `to`→`TO`).
- Переезды/массовые rename требуют migration note + pointer plan (если система использует ссылки где-то ещё).

---

## 2) REQUIRED MAP SCHEMAS (MINIMUM)
### 2.1 ENG → ORC map
Minimum fields:
- ENG_ID
- ENG_NAME
- ENG_LAYER
- ORC_ID
- ORC_NAME
- CONTRACT (what ENG provides / what ORC expects)
- STATUS (ACTIVE/DEPRECATED)
- NOTES

### 2.2 ORC → SPC map
Minimum fields:
- ORC_ID
- ORC_NAME
- SPC_ID
- SPC_NAME
- OWNERSHIP (PRIMARY/SUPPORT)
- OUTPUT_ARTIFACT_TYPE
- STATUS
- NOTES

### 2.3 Validation matrix
Minimum fields:
- ARTIFACT_TYPE
- REQUIRED_CTL
- REQUIRED_VAL
- REQUIRED_QA
- REQUIRED_DOC_CONTROL (YES/NO)
- PASS_CRITERIA (short)
- NOTES

### 2.4 Pipelines map
Minimum fields:
- PIPELINE_ID
- PIPELINE_NAME
- PRIMARY_ORC
- PRIMARY_SPC
- ENG_SET (comma ids)
- GATES (CTL/VAL/QA)
- OUTPUT_TARGET
- STATUS
- NOTES

---

## 3) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- map patterns, field dictionaries, examples
KB OUTPUTS:
- none by default

---

## 4) INTERFACES (RAW ONLY)
- Runtime entrypoint:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md

--- END.
