FILE: UE_V2/03_ENT/00__PIPELINE_CONTRACT__ENT.md
SCOPE: UE_V2 / 03_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: ENT
UID: UE.V2.ENT.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для слоя 03_ENT.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.
Задачи:
- загрузить минимальный ENT core (MODEL + RULES)
- выбрать семейство (REG/TPL/SPC/ENG/ORC/CTL/VAL/QA/XREF)
- передать управление в семейный реалм через его INDEX_MANIFEST -> PIPELINE_CONTRACT

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (без исключений).
- Все обращения: TARGET_KEY -> resolve via ENT INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Никаких догадок: FAMILY_HINT обязателен (кроме режима CORE_AUDIT).
- Семейные PIPELINE_CONTRACT не дублировать тут: резолвить внутри семейного INDEX_MANIFEST.

## [M] REQUIRED_KEYS (must exist in ENT INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT

# ENT core
- ENT.MODEL
- ENT.RULES.SYSTEM_ENTITIES
- ENT.CONTRACT.ENT
- ENT.REGISTRY_CONTRACT
- ENT.TEMPLATE_SET
- ENT.ENTITY_MIN_PASS

# Family entrypoints (INDEX_MANIFEST only)
- ENT.FAM.REG.INDEX_MANIFEST
- ENT.FAM.TPL.INDEX_MANIFEST
- ENT.FAM.SPC.INDEX_MANIFEST
# optional placeholders may be DRAFT until created:
# - ENT.FAM.ENG.INDEX_MANIFEST
# - ENT.FAM.ORC.INDEX_MANIFEST
# - ENT.FAM.CTL.INDEX_MANIFEST
# - ENT.FAM.VAL.INDEX_MANIFEST
# - ENT.FAM.QA.INDEX_MANIFEST
# - ENT.FAM.XREF.INDEX_MANIFEST

## [M] FAMILY_SELECTOR (no guessing)
# RULE: FAMILY_HINT must be one of these tokens (except CORE_AUDIT).
- REG: ENT.FAM.REG.INDEX_MANIFEST
- TPL: ENT.FAM.TPL.INDEX_MANIFEST
- SPC: ENT.FAM.SPC.INDEX_MANIFEST
- ENG: ENT.FAM.ENG.INDEX_MANIFEST
- ORC: ENT.FAM.ORC.INDEX_MANIFEST
- CTL: ENT.FAM.CTL.INDEX_MANIFEST
- VAL: ENT.FAM.VAL.INDEX_MANIFEST
- QA:  ENT.FAM.QA.INDEX_MANIFEST
- XREF: ENT.FAM.XREF.INDEX_MANIFEST

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.INVALID_FAMILY_HINT
- UE.FAIL.FAMILY_INDEX_MISSING
- UE.FAIL.FAMILY_PIPELINE_MISSING
- UE.FAIL.GATE_FAIL

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT
- DOMAIN: ENT
- ARTIFACT_TYPES: [INDEX, PIPE, ENTITY, REGISTRY, TEMPLATE, OUTPUT_PACK, LOG]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL (how it runs)
1) Resolve ENT INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist (at least CORE keys + ready families)
3) Load ENT core minimal set
4) Choose FAMILY route:
   - CORE_AUDIT mode -> stop after core load
   - else FAMILY_HINT -> resolve family index key via FAMILY_SELECTOR
5) Open family INDEX_MANIFEST, then resolve KEY: PIPELINE_CONTRACT inside that family index
6) Handoff to family pipeline

## [M] STEP-RUN (canonical)
Each step block format:
- STEP: S<n>
  GOAL: <one line>
  INPUTS: [<tokens>]
  TARGETS: [<KEYS_ONLY>]
  ACTIONS:
    - <imperative action>
  OUTPUTS: [<tokens/artifacts>]
  CHECKS: [<gates>]
  FAIL: <FAIL_CODE_IF_ANY>
  NEXT: "го"

## [M] STEPS

- STEP: S0
  GOAL: Entry sanity and execution framing
  INPUTS: [TASK_TEXT, FAMILY_HINT?, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists, else FAIL
    - Decide EXEC_MODE using MODE_HINT or DEFAULT_MODE
    - If TASK_TEXT requests only audit/check -> set FAMILY_HINT = CORE_AUDIT
  OUTPUTS: [TASK_TOKEN, EXEC_MODE, FAMILY_HINT]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Load ENT navigation layer and validate readiness
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
    - Validate keys: INDEX_MANIFEST, PIPELINE_CONTRACT exist
    - Validate ENT core keys exist (MODEL/RULES/CONTRACTS/SET/GATE)
    - Validate ready family entrypoints exist (REG/TPL/SPC)
  OUTPUTS: [ENT_READY]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Load ENT core minimal set
  INPUTS: [TASK_TOKEN]
  TARGETS: [ENT.MODEL, ENT.RULES.SYSTEM_ENTITIES, ENT.CONTRACT.ENT, ENT.REGISTRY_CONTRACT, ENT.TEMPLATE_SET, ENT.ENTITY_MIN_PASS]
  ACTIONS:
    - Resolve and open each TARGET via ENT INDEX_MANIFEST
    - Confirm marker presence per doc (at least one [M] marker found)
  OUTPUTS: [ENT_CORE_SET, MARKERS_CONFIRMED]
  CHECKS: [CORE_LOADED]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Route to family or stop after audit
  INPUTS: [TASK_TOKEN, FAMILY_HINT]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - If FAMILY_HINT = CORE_AUDIT -> emit CORE_AUDIT_REPORT and stop with NEXT "го"
    - Else ensure FAMILY_HINT is one of FAMILY_SELECTOR tokens, else FAIL
    - Map FAMILY_HINT -> FAMILY_INDEX_KEY via FAMILY_SELECTOR
    - Open FAMILY INDEX_MANIFEST via FAMILY_INDEX_KEY
    - Inside family index, resolve KEY: PIPELINE_CONTRACT
    - Open family PIPELINE_CONTRACT
  OUTPUTS: [FAMILY_INDEX_KEY, FAMILY_PIPELINE_KEY, ROUTE_SUMMARY]
  CHECKS: [FAMILY_ROUTE_OK]
  FAIL: UE.FAIL.INVALID_FAMILY_HINT
  NEXT: "го"

- STEP: S4
  GOAL: Handoff summary and continue
  INPUTS: [ROUTE_SUMMARY, FAMILY_PIPELINE_KEY]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Return route summary (family, keys opened, gates)
    - Continue in family pipeline
  OUTPUTS: [ROUTE_SUMMARY]
  CHECKS: [TRACE_PRESENT]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"
