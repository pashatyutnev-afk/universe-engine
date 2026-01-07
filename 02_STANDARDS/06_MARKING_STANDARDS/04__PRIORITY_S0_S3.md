# PRIORITY STANDARD — S0..S3
FILE: 02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md

SCOPE: Universe Engine / Operations
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единый стандарт приоритетов ошибок/задач/исправлений.

SOURCE OF TRUTH:
- S0–S3 значения описаны здесь.

---

## 1) LEVELS
- S0 — крит: ломает канон/маркировку/сборку/хранилище
- S1 — высокий: ломает качество результата, но система живёт
- S2 — средний: улучшение/дыра без срочности
- S3 — низкий: косметика

---

## 2) S0 — STOP CONDITIONS (must fix)
S0 всегда:
- нарушение ID_STANDARD (01__ID_STANDARD)
- нарушение STORAGE_MAP для канона (02__STORAGE_MAP)
- конфликт двух “истин” (две SoT по одному правилу)
- сломана сборка PACK (невозможна связка по XREF/DEPENDS)
- DOC_CONTROL FAIL по обязательным полям

---

## 3) FAIL→FIX RULE
Любая ошибка фиксируется как FIX с PRIORITY.
FAIL ≠ STOP, кроме S0.

---
END.
