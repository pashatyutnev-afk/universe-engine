# FILE: UE_V2/05_KB/03__KB_OUTPUTS.md
SCOPE: UE_V2
LAYER: 05_KB
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.KB.OUTPUTS.001
OWNER: SYSTEM
TITLE: KB OUTPUTS (FOR RUNTIME)

## MARKERS
- [M] OUTPUT_TYPES
- [M] KB_EXTRACT_FORMAT
- [M] QUALITY_RULES

## [M] OUTPUT_TYPES
KB отдаёт:
- KB_EXTRACT: набор DEF/THR/MAP/CST под задачу
- KB_PROFILE: компактный профиль домена (например ORUM-B thresholds)
- KB_DIFF: список изменений (если обновляли)

## [M] KB_EXTRACT_FORMAT
Формат (в ответе/в документе):
- NEED: <что требуется>
- PULL: <ID1, ID2, ...>
- DEFINITIONS: <коротко>
- THRESHOLDS: <коротко>
- MAPPINGS: <коротко>
- CONSTRAINTS: <коротко>

## [M] QUALITY_RULES
- максимум 12 пунктов в одном extract
- каждый пункт ≤ 2 строки
- запрещено дублировать то, что уже есть в STD/Law
