# FILE: UE_V2/06_PIPE/02__PIPE_GAP.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: PIPELINE
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.PIPE.GAP.001
OWNER: SYSTEM
TITLE: PIPE GAP

## MARKERS
- [M] GAP_TRIGGER
- [M] GAP_STEPS
- [M] GAP_OUTPUTS
- [M] RETURN_TO_PIPE

## [M] GAP_TRIGGER
GAP разрешён если:
- missing entity (SPC/ORC/CTL/VAL/QA/XREF)
- missing template
- missing KB definition/threshold/mapping
RAW missing НЕ лечится GAP (это STOP).

## [M] GAP_STEPS
1) IDENTIFY GAP
   - что отсутствует, зачем нужно, какой слой (ENT/TPL/KB)
2) PROPOSE CREATION
   - создать минимальный файл по контракту/шаблону (short, machine)
3) REGISTER
   - добавить в малый индекс соответствующей семьи (04_NAV)
4) RESUME
   - вернуться в исходный PIPE_* и продолжить

## [M] GAP_OUTPUTS
- GAP_NOTE (коротко)
- новый файл сущности/шаблона/KB-записи
- обновленный малый индекс

## [M] RETURN_TO_PIPE
Вернуться туда, где GAP возник:
- PIPE_DEFAULT / PIPE_AUD / PIPE_VIS / PIPE_LOR
