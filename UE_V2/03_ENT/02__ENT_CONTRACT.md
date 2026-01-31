# FILE: UE_V2/03_ENT/02__ENT_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.CONTRACT.001
OWNER: STANDARDS_OWNER
TITLE: UNIVERSAL ENTITY CONTRACT

## MARKERS
- [M] INTENT
- [M] REQUIRED_FIELDS
- [M] REQUIRED_SECTIONS
- [M] IO_CONTRACT
- [M] LIMITS
- [M] GATES

## [M] INTENT
Единый минимальный контракт для любой сущности.

## [M] REQUIRED_FIELDS
- UID
- ROLE_TYPE: SPC|ORC|CTL|VAL|QA|XREF|REG|TPL|DOMAIN_PLUGIN
- OWNER
- STATUS: ACTIVE|DRAFT|DEPRECATED
- MODE: REPO (USAGE-ONLY, NO-EDIT)

## [M] REQUIRED_SECTIONS
- [M] PURPOSE (1–3 строки)
- [M] INPUTS (список)
- [M] OUTPUTS (список)
- [M] RULES (5–15 правил)
- [M] HANDOFFS (кому отдаёт/от кого принимает — без ссылок)
- [M] GATES (что проверяет/что может отклонить)

## [M] IO_CONTRACT
- INPUTS: тип данных, минимальные поля, допуски
- OUTPUTS: артефакт/отчёт/решение + формат
- Если нет шаблона OUTPUT → GAP: создать шаблон

## [M] LIMITS
- “Шапка” ≤ 12 строк (см. NOISE_BUDGET)
- PURPOSE ≤ 3 строки
- Никаких длинных описаний “для человека”

## [M] GATES
- G.ENT.REQ_FIELDS = FAIL если нет REQUIRED_FIELDS
- G.ENT.REQ_SECTIONS = FAIL если нет REQUIRED_SECTIONS
- G.ENT.NOISE = REWORK_REQUIRED если нарушены LIMITS
