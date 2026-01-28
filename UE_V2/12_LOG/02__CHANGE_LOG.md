# 02__CHANGE_LOG

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LOG / CHANGE
UID: UE.V2.LOG.CHANGE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единый журнал изменений правил/стандартов/карт/реестров/пайпов.

---

## [M] INTENT
Фиксировать любые изменения в "законах и механике" системы так, чтобы можно было восстановить: что меняли, почему, что сломали, что починили.

---

## [M] RULES
1) Любое изменение в следующих зонах обязано фиксироваться здесь:
   - 00_BOOT (протоколы, router, manifest, commands)
   - 01_LAW (законы)
   - 02_STD (стандарты)
   - 03_ENT/00_REG (реестры совместимости)
   - 08_XREF (карты связности)
   - 04_NAV (индексы)
   - 06_PIPE (пайпы, контрольные узлы)
   - 05_KB (границы, источники, scope)
2) Один change = одна запись с CHANGE_ID.
3) Запрещено менять смысл правил без CHANGE_LOG записи.
4) Переезды/переименования фиксируются как:
   - WHAT: old_path -> new_path
   - WHY: причина
   - IMPACT: какие ссылки/пайпы затронуты
   - ACTION: обновить REG_PATH_MAP / IDX / ссылки
5) Если изменение критичное — добавить rollback plan.

---

## [M] ENTRY_TEMPLATE
CHANGE_ENTRY:
- CHANGE_ID:
- DATE:
- AUTHOR:
- TYPE: (ADD|EDIT|RENAME|MOVE|DELETE|DEPRECATE)
- SCOPE: (BOOT|LAW|STD|REG|XREF|NAV|PIPE|KB|LOG)
- WHAT:
- WHY:
- IMPACT:
- ACTIONS:
- ROLLBACK (optional):
- STATUS: (APPLIED|PENDING|ROLLED_BACK)

---

## [M] CHANGELOG (APPEND ONLY)
| CHANGE_ID | DATE | TYPE | SCOPE | WHAT | WHY | IMPACT | STATUS |
|---|---|---|---|---|---|---|---|

---

## [M] GATES
PASS если:
- изменение отражено записью
REWORK если:
- изменения в правилах сделаны без CHANGE_LOG
STOP если:
- обнаружен конфликт изменений без возможности восстановить порядок
