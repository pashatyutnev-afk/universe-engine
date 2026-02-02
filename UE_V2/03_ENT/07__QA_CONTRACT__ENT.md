# FILE: UE_V2/03_ENT/07__QA_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.QA.CONTRACT.001
OWNER: GOVERNANCE_OWNER
TITLE: QA CONTRACT (QUALITY)

## MARKERS
- [M] PURPOSE
- [M] ACCEPTANCE
- [M] REGRESSION
- [M] OUTPUTS
- [M] GATES

## [M] PURPOSE
QA даёт приёмку качества (скоринг, регресс) и финальный статус готовности.

## [M] ACCEPTANCE
QA проверяет:
- Комплектность (есть артефакт + отчёт + манифест если нужен)
- Доменные гейты (AUD/VIS/LOR) по минимуму
- “Не клоны” (если требуется семейное разнообразие)

## [M] REGRESSION
Если новое изменение ухудшило метрику/правило относительно базового таргета → REWORK_REQUIRED.

## [M] OUTPUTS
- QA Acceptance Output: PASS/REWORK/FAIL + причины
- Score (если применимо)

## [M] GATES
- G.QA.NO_PACK = REWORK_REQUIRED если нет упаковки там, где она обязательна
- G.QA.NO_REG = REWORK_REQUIRED если регресс не проверен в релизной ветке
