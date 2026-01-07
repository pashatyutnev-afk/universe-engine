# CHAT PROTOCOL (UNIVERSE ENGINE) (CANON)
FILE: 02_STANDARDS/02_PROTOCOLS/CHAT_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.PROTOCOL.CHAT.201
OWNER: SYSTEM
ROLE: Operational protocol for chat-based work on Universe Engine: how chat produces canon-ready docs, how decisions are recorded, how to proceed by indices, and how to avoid duplicates.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован Chat Protocol: работа через master-index, UID-first ссылки, порядок переписывания, фиксация решений и change packages"
- REASON: "Чат — основной интерфейс редактирования системы, нужен единый рабочий закон"
- IMPACT: "All chat-based doc creation/editing flows"

---

## XREF (UID-first)
XREF: UE.LAW.CANON.PROTOCOL.004 | implements | chat work must follow canon protocol | 01_SYSTEM_LAW/04__CANON_PROTOCOL.md
XREF: UE.LAW.VERSIONING.003 | depends_on | SemVer change policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | doc header + change note format | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking rules | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.PROTOCOL.CHANGE_MGMT.200 | depends_on | standards change workflow | 02_STANDARDS/02_PROTOCOLS/CHANGE_MANAGEMENT_PROTOCOL.md

---

## 0) PURPOSE
Этот протокол задаёт “как работать через чат”, чтобы результат был:
- каноничным (или явно non-canon draft),
- согласованным (без дублей),
- навигируемым (через индексы),
- быстро применимым (copy/paste готовые файлы).

---

## 1) PRIME RULES (ABSOLUTE)
### 1.1 Work by index (always)
Любая работа начинается с master-index соответствующего слоя.
Если файла нет в master-index — он не существует для слоя.

### 1.2 UID-first always
Любые связи/ссылки/упоминания делаются UID-first:
- сначала UID
- потом путь (если надо)
- потом raw link (опционально)

### 1.3 No duplication
Один смысл → один SoT.
Если нужна детализация → module/template внутри контракта SoT.

### 1.4 Canon vs Draft separation
- Канон: `LOCK: FIXED`, зарегистрирован в master-index.
- Черновик: `LOCK: OPEN`, не регистрируется.

---

## 2) CHAT ROLES (WHO DOES WHAT)
### 2.1 User (Operator)
- задаёт цель/приоритет
- подтверждает порядок (“го дальше”)
- вставляет текущие файлы/скриншоты/контекст

### 2.2 Assistant (Builder)
- выдаёт готовые self-contained тексты файлов
- не дробит на “кусочки”
- соблюдает Doc Control header + UID + SemVer
- отслеживает коллизии имен/номеров и чинит через alias/migration

---

## 3) CANON WORKFLOW (CHAT FLOW)
### STEP A — Select target by index
Открываем master-index → берём следующий файл по списку.

### STEP B — Build / rewrite file
Ассистент выдаёт полный файл.
Поля:
- FILE path — точный
- UID — уникальный
- VERSION — SemVer
- CHANGE_NOTE — актуальный

### STEP C — Fix collisions
Если в папке конфликт `00__*` или `NN*`:
- создаём новый канонический файл с правильным номером
- старый превращаем в legacy alias pointer (non-canon)

### STEP D — Update registries
При изменении состава/путей:
- обновить master-index
- обновить doc registry

### STEP E — Proceed sequentially
Переходим к следующему файлу “по очереди”.

---

## 4) DECISION RECORDING (CHAT DECISIONS)
Любое решение, влияющее на канон, должно быть записано как минимум в `CHANGE_NOTE` изменённых файлов.

Если решение крупное:
- формируется mini change package (см. Change Management Protocol):
  - что меняем
  - почему
  - что ломается
  - миграция

---

## 5) LINKING RULES IN CHAT (HOW TO REFERENCE)
### 5.1 When referencing a doc
Формат:
- `UID: <...> | PATH: <...>`

Пример:
- `UID: UE.STD.SPEC.DOC_CONTROL.103 | PATH: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`

### 5.2 When referencing an entity/artifact
Формат:
- `ENTITY_UID: <...> | NOTE: <...>`

---

## 6) “GO” MODE (SEQUENTIAL REWRITE MODE)
Если пользователь говорит “го/го дальше/по очереди”:
- ассистент берёт следующий файл в индексе
- выдаёт его целиком
- в конце говорит: “следующий файл: <path>”

Без вопросов, без пауз.

---

## 7) ERROR HANDLING (WHEN SOMETHING DOESN’T MATCH)
Если обнаружены:
- отсутствующий файл
- битая raw-ссылка
- коллизия номера
- дубликат смысла

То чат обязан:
1) пометить проблему как S0/S1
2) предложить исправление через migration/alias
3) продолжить по очереди

---

## FINAL RULE (LOCK)
Этот протокол обязателен для chat-based работы над Universe Engine.
Любая правка протокола = изменение канона.
--- END.
