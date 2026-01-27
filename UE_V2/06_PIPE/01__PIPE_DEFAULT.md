# FILE: UE_V2/06_PIPE/01__PIPE_DEFAULT.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: PIPELINE
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.PIPE.DEFAULT.001
OWNER: SYSTEM
TITLE: PIPE DEFAULT

## MARKERS
- [M] INTENT
- [M] INPUTS_MIN
- [M] STEPS
- [M] OUTPUTS
- [M] ROUTING

## [M] INTENT
Единый конвейер: принять задачу → выбрать минимум сущностей → сделать артефакт → пройти гейты.

## [M] INPUTS_MIN
- TASK (text)
- TARGET ARTIFACT TYPE (doc/track/visual/lore/release)
- LINKS (optional raw links)
Если чего-то нет → STOP (input absent).

## [M] STEPS
1) INTAKE (SPC: MACHINE_ARCHITECT)
   - определить артефакт и домен (AUD/VIS/LOR/REL/STD)
2) ROUTE (SPC: PIPELINE_ARCHITECT)
   - выбрать один из: PIPE_AUD / PIPE_VIS / PIPE_LOR / PIPE_GAP
3) EXECUTE (ORC + relevant ENG)
   - собрать черновик артефакта
4) CONTROL (CTL_READINESS + CTL_NOISE)
   - входы/формат/шум
5) VALIDATE (VAL_DOC + domain VAL)
   - соответствие стандартам и метрикам
6) QA (QA_ACCEPT + optional QA_PACK)
   - оценка/регресс/маркировка REWORK
7) PACK (SPC: INTEGRATION_PACKER)
   - финальная упаковка и имена
8) SIGNOFF (DOC_CONTROLLER → MACHINE_ARCHITECT)
   - финальное утверждение/выпуск

## [M] OUTPUTS
- готовый артефакт (doc)
- отчет (acceptance output)
- решение: PASS / REWORK_REQUIRED / STOP / GAP_CREATED

## [M] ROUTING
- если нет сущности/шаблона/определения → PIPE_GAP
- если домен аудио → PIPE_AUD
- визуал → PIPE_VIS
- лор → PIPE_LOR
