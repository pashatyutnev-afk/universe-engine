FILE: UE_V2/03_ENT/00_REG/00__PIPELINE_CONTRACT__REG.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: REG
UID: UE.V2.REG.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: KEY→RAW via INDEX_MANIFEST
CREATED: 2026-01-30
OWNER: SYS

---

# PIPELINE_CONTRACT — REG

PURPOSE:
Навигатор домена REG. Описывает, как рантайм:
- загружает REG без мусора,
- проверяет UID/коллизии,
- разрешает KEY→RAW,
- валидирует минимальные наборы.

RULE:
Этот контракт не хранит адреса. Все адреса берутся из REG.INDEX_MANIFEST.

---

## INPUTS
- TASK_TEXT
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: REQUESTED_KEYS (list)
- OPTIONAL: UID_CANDIDATES (list)

## OUTPUTS
- RESOLVED_RAW_MAP (KEY→RAW)
- UID_CHECK_REPORT
- REG_MIN_SET_STATUS (PASS|STOP|GAP)

---

## REQUIRED KEYS
MIN_SET:
- REG.INDEX_MANIFEST
- REG.PIPELINE_CONTRACT
- REG.ENTITY_IDS
- REG.PATH_MAP
- REG.UID_REGISTRY

---

## EXEC (STEP-RUN)

S0) LOAD INDEX_MANIFEST
- load REG.INDEX_MANIFEST
- build RESOLVED_RAW_MAP from TABLE

S1) MIN_SET LOAD
- load keys from MIN_SET using RESOLVED_RAW_MAP
- if any RAW missing → STOP

S2) UID CHECK (if UID_CANDIDATES provided)
- for each UID in UID_CANDIDATES:
  - check against REG.UID_REGISTRY record set (exact match)
  - return UID_CHECK_REPORT:
    - OK (free)
    - COLLISION (exists)
    - RESERVED (blocked)
    - INVALID (format)

S3) REQUESTED_KEYS (optional)
- if REQUESTED_KEYS provided:
  - resolve KEY→RAW via RESOLVED_RAW_MAP
  - if key missing → GAP

S4) DONE
- return PASS if MIN_SET loaded
- return GAP if requested keys missing
- return STOP if min set missing/raw missing

---

## OPERATIONAL API (mental model)
- REG.RESOLVE(KEY) -> RAW    (only via INDEX_MANIFEST)
- REG.CHECK_UID(UID) -> STATUS
- REG.RESERVE_UID(UID, NOTE) -> ENTRY (append-only, future commit by user)
