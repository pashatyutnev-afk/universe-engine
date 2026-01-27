# FILE: UE_V2/02_STD/09__GATES.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.GATES.001
OWNER: STANDARDS_OWNER
TITLE: GATES STANDARD (CTL/VAL/QA)

## MARKERS
- [M] INTENT
- [M] GATE_STATES
- [M] GATE_FORMAT
- [M] MIN_GATE_SET
- [M] GATES

## [M] INTENT
Единый язык гейтов для контроля, валидации и приёмки.

## [M] GATE_STATES
- PASS
- REWORK_REQUIRED
- FAIL
- STOP (только по рантайм-стопам: RAW missing / marker not confirmed / input absent)
- GAP (нужна новая сущность/шаблон/закон/стандарт)

## [M] GATE_FORMAT
Код гейта:
`G.<REALM>.<NAME> = <STATE> : <1-line reason>`
Пример:
`G.AUD.RI_LOW = FAIL : RI_t < 0.62`

## [M] MIN_GATE_SET
В каждом “выходе” минимум:
- G.TRACE (есть ли ресурсы и маркеры)
- G.DOC (формат документа)
- Доменные гейты (AUD/VIS/LOR) если это доменная задача

## [M] GATES
- G.GATE.NO_REASON = REWORK_REQUIRED если гейт без причины
- G.GATE.BAD_STATE = FAIL если состояние вне списка
