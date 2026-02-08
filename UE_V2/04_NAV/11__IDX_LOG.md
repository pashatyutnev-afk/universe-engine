# 11__IDX_LOG

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / INDEX
UID: UE.V2.NAV.IDX_LOG.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Вход в LOG слой (трейс, токены, решения, изменения). Без LOG пайплайн не считается выполненным.

---

## [M] INTENT
Сделать фиксацию прогонов и решений стандартной: чтобы ничего не "плыло" и не терялось.

---

## [M] LINKS (PATH)

LOG ядро:
- UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md
- UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

LOG артефакты:
- UE_V2/14_LOG/01__RUN_LOG.md
- UE_V2/14_LOG/02__CHANGE_LOG.md
- UE_V2/14_LOG/03__TOKEN_ARCHIVE.md
- UE_V2/14_LOG/04__DECISION_LOG.md
- UE_V2/14_LOG/05__START_POINT_LOG.md

---

## [M] RULES
1) Каждый STEP обязан оставить запись в RUN_LOG (кратко).
2) Каждый выбор вариантов обязан оставить DECISION_LOG запись.
3) Токены старых шагов выносятся в TOKEN_ARCHIVE, а не держатся в контексте.
4) Любое изменение правил/словарей/карт фиксируется в CHANGE_LOG.
5) Любая BOOT/START инициализация фиксируется в START_POINT_LOG.

---

## [M] GATES
PASS если:
- доступен RUN_LOG
- доступен DECISION_LOG
GAP если:
- отсутствует CHANGE_LOG или TOKEN_ARCHIVE
STOP если:
- отсутствуют LOG ядро (PIPELINE_CONTRACT/INDEX_MANIFEST) или RUN_LOG
