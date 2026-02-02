FILE: UE_V2/03_ENT/90_XREF/00__PIPELINE_CONTRACT__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: XREF
UID: UE.V2.XREF.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: KEY→RAW via INDEX_MANIFEST
CREATED: 2026-01-30
OWNER: SYS

---

# PIPELINE_CONTRACT — XREF

PURPOSE:
XREF-слой связывает домены, роли, пайпы, проверки и дефолтные цепочки так, чтобы рантайм:
- не проходил мимо REG/XREF/KB/PIPE/NAV/LOG,
- выбирал цепочку детерминированно,
- мог резать задачу на стартовые точки и продолжать с места ошибки.

RULE:
Контракт не хранит RAW. Все адреса берутся из XREF.INDEX_MANIFEST.

---

## INPUTS
- ROUTE_TOKEN (domain, artifact_type, mode, pipe_selected, required_checks, exec_mode)
- OPTIONAL: START_POINT (id)
- OPTIONAL: REQUESTED_KEYS (list)
- OPTIONAL: OVERRIDES (map)

## OUTPUTS
- RESOLVED_RAW_MAP (KEY→RAW)
- DEFAULT_CHAIN_PLAN
- VALIDATION_PLAN
- ROLE_BINDINGS
- START_POINTS_SUGGESTION

---

## REQUIRED KEYS (MIN_SET)
- XREF.INDEX_MANIFEST
- XREF.PIPELINE_CONTRACT
- XREF.DEFAULT_CHAIN
- XREF.VALIDATION_MATRIX
- XREF.ROLE_MAP

---

## EXEC (STEP-RUN)

S0) LOAD INDEX_MANIFEST
- resolve KEY→RAW map

S1) LOAD MIN_SET
- load DEFAULT_CHAIN + VALIDATION_MATRIX + ROLE_MAP
- if any missing → STOP

S2) BUILD DEFAULT_CHAIN_PLAN
- select chain by ROUTE_TOKEN.DOMAIN if possible
- else use GLOBAL chain from XREF.DEFAULT_CHAIN
- apply OVERRIDES if given

S3) BUILD VALIDATION_PLAN
- map ROUTE_TOKEN.REQUIRED_CHECKS to checks in XREF.VALIDATION_MATRIX
- output ordered checklist (VAL then QA by default)
- missing check mapping → GAP

S4) ROLE_BINDINGS
- bind required roles (SPC/ORC/ENG/CTL/VAL/QA) from XREF.ROLE_MAP
- if role missing for domain → GAP (not STOP)

S5) START POINTS
- propose START points from ROUTE_TOKEN and DEFAULT_CHAIN (see START_POINTS section in DEFAULT_CHAIN doc)
- if START_POINT provided: validate it exists, else GAP

---

## STOP / GAP
STOP_IF:
- MIN_SET missing
GAP_IF:
- mapping absent for a required role/check/chain target
