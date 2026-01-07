# DOC CONTROL — STANDARD
FILE: 02_STANDARDS/06_MARKING_STANDARDS/08__DOC_CONTROL.md

SCOPE: Universe Engine / Documentation Control
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единый контроль документации: обязательные поля, валидность ID, ссылки, отсутствие дублей, пригодность для канона.

SOURCE OF TRUTH:
- DOC_CONTROL чеклист, FAIL-коды, PASS/FAIL формат — здесь.

---

## 0) CORE LAW
- Док без обязательной шапки = FAIL.
- Невалидный ID = FAIL (S0).
- Два источника истины по одному правилу = FAIL (S0).
- PASS/FAIL фиксируется явно (в лог/в отчёт).

---

## 1) REQUIRED HEADER CHECK (S0)
Должно быть в шапке:
- FILE, SCOPE, LEVEL, STATUS, LOCK, VERSION, OWNER, ROLE

Отсутствие любого поля = S0: `MISSING_HEADER_FIELD`.

---

## 2) ID CHECK (S0)
Проверяем:
- ID существует
- ID соответствует формату (см. 01__ID_STANDARD)
- нет пробелов/кириллицы/запрещённых символов

FAIL CODE:
- `ID_INVALID` (S0)

---

## 3) LINK CHECK (S0/S1)
Проверяем:
- XREF/DEPENDS_ON содержат валидные ID
- DEPENDS_ON используется только для “нужно для сборки”
- нет запрещённых связей (REL_POLICY NEVER)

FAIL CODES:
- `LINK_ID_INVALID` (S0)
- `REL_POLICY_VIOLATION` (S0)
- `HIDDEN_DEPENDENCY` (S1) — если выявлено “использует, но не указано”

---

## 4) STRUCTURE CHECK (S1)
Проверяем:
- нет второй шапки STATUS/LOCK/VERSION в конце файла
- документ читаем (есть разделы, списки, переносы)
- нет заглушек “без изменений” в индексах/реестрах

FAIL CODES:
- `DUPLICATE_HEADER_FIELDS` (S1)
- `UNREADABLE_FORMAT` (S1)
- `PLACEHOLDER_REGISTRY` (S1)

---

## 5) STORAGE CHECK (S0)
Проверяем:
- файл лежит в правильной зоне по STORAGE_MAP
- канон не лежит в WORK

FAIL CODES:
- `STORAGE_MISPLACED` (S0)

---

## 6) OUTPUT FORMAT (canonical)
DOC_CONTROL:
  RESULT: "PASS|FAIL"
  FAILS:
    - CODE: "ID_INVALID"
      PRIORITY: "S0"
      NOTE: "ID содержит пробел"

END.