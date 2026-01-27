# FILE: UE_V2/03_ENT/07__XREF_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.XREF.CONTRACT.001
OWNER: PIPELINE_ARCHITECT
TITLE: XREF CONTRACT (CROSS-REFERENCE)

## MARKERS
- [M] PURPOSE
- [M] MAP_TYPES
- [M] ROUTING_SUPPORT
- [M] OUTPUTS
- [M] GATES

## [M] PURPOSE
XREF хранит карты соответствий между законами, стандартами, метриками и пайплайнами.

## [M] MAP_TYPES
- LAW ↔ METRICS (например LAW-09 ↔ RI)
- PIPE ↔ ENT (кто участвует в каком пайплайне)
- DOMAIN ↔ VALIDATORS/QA (какие проверки обязательны)

## [M] ROUTING_SUPPORT
XREF не содержит “контент”. Только связи и правила выбора.

## [M] OUTPUTS
- Matrices / Maps (короткие)
- Routing hints (минимальные)

## [M] GATES
- G.XREF.BLOAT = REWORK_REQUIRED если XREF превращается в энциклопедию
