# 04__RELATION_TYPES_CANONICAL_DICTIONARY.md

SCOPE: Universe Engine (Games volume)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: DICTIONARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.DICT.REL_TYPES.004
OWNER: KB_GOVERNANCE
ROLE: Canonical dictionary of allowed REL relation types for KB semantic edges. Prevents invented relation names and graph drift.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Defined canonical REL type vocabulary for KB. Enforced UID-only targets and mandatory WHY."
- REASON: "REL blocks require a stable, shared vocabulary. Without it authors invent types and validation becomes impossible."
- IMPACT: "REL authoring becomes deterministic and reviewable. Graph audits become consistent."
- CHANGE_ID: UE.CHG.2026-01-20.KB.REL_TYPES.004

---

## 0) PURPOSE (LAW)
Этот словарь задаёт **единственный разрешённый** набор `REL_TYPE` для семантических связей в Knowledge Base.

Закон:
- Нельзя придумывать новые типы связей “по месту”.
- REL всегда описывает **семантическое отношение**.
- REL всегда связывает **UID → UID** (в REL запрещены URL/RAW/пути).
- Каждая связь должна иметь `WHY` (краткое объяснение).

---

## 1) KB SCOPE (REQUIRED)
KB INPUTS:
- KB документы, где требуется REL блок
- UID источника (FROM_UID) и UID цели (TO_UID)

KB OUTPUTS:
- Разрешённый список REL типов (vocabulary)
- Мини-правила направления связи (A -> B)

KB BOUNDARIES:
- Этот словарь не является XREF таблицей
- Этот словарь не задаёт NAV ссылки на документы
- Этот словарь не доказывает истинность фактов, только стандартизирует семантические связи

KB RAW REFERENCES (IF ANY):
- KB MASTER INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- KB REALM README:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md
- KB RULES:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 2) ABSOLUTE RULES FOR REL (CANON)
### 2.1 UID-only targets
REL запрещает:
- RAW URLs
- PATH/папки/имена файлов
- “человеческие” ссылки без UID

REL допускает:
- только `UE.*` UID в качестве TO_UID

### 2.2 Mandatory WHY
Каждая REL запись обязана иметь:
- `WHY: <короткое объяснение>`

### 2.3 No custom tokens
Если нужен новый тип связи:
- это изменение словаря через change-management
- до изменения словаря использовать нельзя

---

## 3) CANONICAL REL TYPES (ALLOWED SET)
Ниже перечислены **все** разрешённые `REL_TYPE`.

### 3.1 depends_on
Смысл: A требует B для корректного применения/валидности.
Направление: `A depends_on -> B`

### 3.2 governed_by
Смысл: A регулируется правилами/политикой/законом B.
Направление: `A governed_by -> B`

### 3.3 validated_by
Смысл: A проверяется/подтверждается чеклистом/валидатором B.
Направление: `A validated_by -> B`

### 3.4 constrained_by
Смысл: A ограничен лимитами/контролем/запретами B.
Направление: `A constrained_by -> B`

### 3.5 maps_to
Смысл: A сопоставляется B как карта соответствий (маппинг).
Направление: `A maps_to -> B`

### 3.6 supersedes
Смысл: A заменяет старый B (новая версия/новая сущность).
Направление: `A supersedes -> B`

### 3.7 deprecated_by
Смысл: A устарел и заменён B.
Направление: `A deprecated_by -> B`

---

## 4) REL RECORD FORMAT (STANDARD)
Рекомендуемый формат строки (читаемый и машино-дружелюбный):

- FROM_UID: <UE...>
  REL_TYPE: <depends_on|governed_by|validated_by|constrained_by|maps_to|supersedes|deprecated_by>
  TO_UID: <UE...>
  WHY: <one-line rationale>

Минимальный компактный вариант:
- `REL: <REL_TYPE> -> <TO_UID> | WHY: <...>`

---

## 5) ANTI-PATTERNS (FORBIDDEN)
Запрещено:
- `REL: depends_on -> https://...`
- `REL: related -> UE....` (несуществующий тип)
- `REL: depends_on -> file/path/name.md`
- REL без WHY

---

## 6) INTERFACES (RAW-ONLY, OPTIONAL)
NONE

---

## 7) COMPLIANCE CHECKLIST (REQUIRED)
### 7.1 Vocabulary integrity
- [ ] Используются только REL_TYPE из раздела 3
- [ ] Нет “самодельных” REL_TYPE

### 7.2 Encoding integrity
- [ ] TO_UID всегда UE.*
- [ ] Нет URL/RAW/пути в REL

### 7.3 Rationale integrity
- [ ] У каждой связи есть WHY

### 7.4 Registration
- [ ] Док зарегистрирован в KB MASTER INDEX (если используется рантаймом)

---

## 8) OPTIONAL CHANGE LOG
- 2026-01-20 — CREATE — v1.0.0

---
## END
