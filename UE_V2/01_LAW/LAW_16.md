# LAW_16

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW
UID: UE.V2.LAW.16.ROOT_INDEX_ACCESS_ONLY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: ROOT_INDEX используется только для выдачи RAW-доступа. Логика работы — только через START/NAV/IDX/PIPE.

---

## [M] INTENT
Исключить дублирование навигации и засорение контекста: ROOT_INDEX нужен только как "ключ" к RAW ссылкам.

---

## [M] RULES
1) ROOT_INDEX НЕ является точкой запуска.
2) ROOT_INDEX НЕ определяет маршруты работы, пайпы и выбор сущностей.
3) ROOT_INDEX используется только для:
   - доступа к RAW (возможность открыть документ)
   - обнаружения якорей (START, NAV_ROOT)
4) Любая логика запуска/переходов происходит только через:
   START → BOOT_SEQ → RUNTIME_MANIFEST → NAV_ROOT → IDX_* → PIPE_* → TARGET.
5) Использование ROOT_INDEX как "роутера" — нарушение (REWORK).

---

## [M] GATES
PASS если:
- задача запускается без использования ROOT_INDEX как логики
REWORK если:
- ROOT_INDEX используется для выбора пути/пайпа/сущностей
STOP если:
- нет доступа к START/NAV_ROOT через RAW
