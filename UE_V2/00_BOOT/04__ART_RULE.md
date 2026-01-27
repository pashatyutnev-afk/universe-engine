# FILE: UE_V2/00_BOOT/04__ART_RULE.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: LAW (ARTIFACT-ONLY)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.ARTRULE.001
OWNER: SYSTEM

## MARKERS
- [M] RULE
- [M] WHAT_COUNTS_AS_ARTIFACT
- [M] GAP_IF_NO_TEMPLATE
- [M] MIN_ARTIFACT_FIELDS

## [M] RULE
Запрещён “голый контент”.
Любой результат обязан быть оформлен как артефакт-документ по стандарту.

## [M] WHAT_COUNTS_AS_ARTIFACT
Артефакт = файл (md/json/yaml) с:
- идентификатором (UID)
- назначением (DOC_TYPE / PURPOSE)
- входами/выходами (INPUTS/OUTPUTS или эквивалент)
- правилами/гейтами (RULES/GATES)
- маркерами [M] для проверки

## [M] GAP_IF_NO_TEMPLATE
Если нет подходящего шаблона:
- GAP: создать шаблон
- затем создать артефакт по новому шаблону

## [M] MIN_ARTIFACT_FIELDS
Минимум полей в шапке:
SCOPE, LAYER, DOC_TYPE, MODE, STATUS, VERSION, UID, OWNER
