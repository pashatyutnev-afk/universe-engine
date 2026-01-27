# FILE: UE_V2/06_PIPE/06__CTL_READINESS.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: CONTROLLER
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.CTL.READY.001
OWNER: SYSTEM
TITLE: CTL READINESS

## MARKERS
- [M] INTENT
- [M] CHECKS
- [M] FAIL_CODES
- [M] OUTPUT

## [M] INTENT
Пропускать в работу только “готовые” таски, не тратить токены на мусор.

## [M] CHECKS
R0 INPUTS:
- TASK present?
- artifact type resolvable?
R1 MARKERS:
- документ-артефакт содержит MARKERS?
R2 KB:
- нужны ли DEF/THR/MAP? если отсутствуют → GAP (не STOP)
R3 LINKS:
- если заявлен RAW-only маршрут: ссылки присутствуют?
  - если нет RAW → STOP (RAW missing)

## [M] FAIL_CODES
- STOP.INPUT_ABSENT
- STOP.RAW_MISSING
- STOP.MARKER_NOT_CONFIRMED
- GAP.KB_MISSING
- GAP.TPL_MISSING
- GAP.ENTITY_MISSING

## [M] OUTPUT
- decision: PASS / STOP / GAP
- minimal note: what failed
