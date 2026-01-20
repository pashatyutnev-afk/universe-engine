# 24__KB_RELATION_MODEL_STANDARD.md

SCOPE: Universe Engine (Games volume)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.REL_MODEL.024
OWNER: KB_GOVERNANCE
ROLE: Canonical standard for how KB relations are encoded and validated. Separates NAV (RAW) vs REL (UID-only) vs XREF (routing maps) to keep the graph deterministic.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Unified relation model: REL=UID-only + canonical REL_TYPE + mandatory WHY. Defined separation with NAV/XREF, deprecation pairing, and minimal formats."
- REASON: "Without a relation model, authors mix URLs/paths/semantics and break deterministic routing and validation."
- IMPACT: "KB relation graph becomes stable, auditable, and compatible with CTL/ORC consumption."
- CHANGE_ID: UE.CHG.2026-01-20.KB.REL_MODEL.024

---

## 0) PURPOSE (LAW)
Этот стандарт фиксирует **как правильно строить связи в KB**, чтобы:
- граф отношений был детерминированным,
- валидация REL/XREF была возможна,
- навигация не смешивалась с семантикой,
- депрекации и замены были однозначны.

---

## 1) KB SCOPE (REQUIRED)
KB INPUTS:
- KB документы, которые хотят ссылаться друг на друга
- UID источника (FROM_UID)
- UID цели (TO_UID)
- Требуемый тип связи (REL_TYPE)

KB OUTPUTS:
- Канонический формат REL записей
- Правила разделения NAV vs REL vs XREF
- Правила депрекаций (pairing)

KB BOUNDARIES:
- Этот стандарт не определяет, “что правда”, он определяет **как кодировать связи**
- Этот стандарт не заменяет master-index регистрацию
- Этот стандарт не является реестром файлов

KB RAW REFERENCES (IF ANY):
- KB MASTER INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- KB RULES:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 2) DEFINITIONS (CANON)
### 2.1 NAV (RAW)
Навигация: “куда перейти/что открыть”.
- Только RAW ссылки.

### 2.2 REL (UID-only)
Семантические связи: “что означает связь”.
- Только UID → UID.

### 2.3 XREF (Mapping)
Карта соответствий: “как маршрутизировать/сопоставлять”.
- Может содержать RAW (если XREF используется рантаймом как навигационный указатель).
- Не заменяет REL.

---

## 3) ABSOLUTE REL LAWS (BINDING)
### 3.1 REL targets are UID-only
В REL запрещены:
- RAW URLs
- PATH/имена файлов
- любые ссылки кроме UID

Разрешено:
- только `UE.*` UID в `TO_UID`.

### 3.2 REL uses canonical REL_TYPE only
REL_TYPE должен быть из канонического словаря:
- UE.KB.DICT.REL_TYPES.004

Если словаря пока нет — это GAP, нельзя придумывать типы.

### 3.3 Mandatory WHY
Каждая REL запись обязана включать:
- `WHY: <one-line rationale>`

### 3.4 No mixed blocks
Запрещено:
- писать URL в REL “чтобы было удобно открыть”
- писать UID в INTERFACES “чтобы было красиво”

---

## 4) REL RECORD FORMAT (STANDARD)
### 4.1 Canonical verbose format
- FROM_UID: <UE...>
  REL_TYPE: <depends_on|governed_by|validated_by|constrained_by|maps_to|supersedes|deprecated_by>
  TO_UID: <UE...>
  WHY: <...>

### 4.2 Canonical compact format (allowed)
- `REL: <REL_TYPE> -> <TO_UID> | WHY: <...>`

---

## 5) NAV & INTERFACES FORMAT (RAW-ONLY)
Если нужно “куда перейти”, это **INTERFACES**, не REL.

Рекомендуемый формат:
- NAME
- PURPOSE
- RAW

Пример:
- KB MASTER INDEX
  - PURPOSE: Canonical entrypoint for KB layer
  - RAW: <raw url>

---

## 6) XREF FORMAT (MINIMUM)
Этот стандарт не переписывает полный формат XREF, но задаёт минимум:

XREF record MUST contain:
- FROM (UID or stable ID)
- TO (target RAW pointer OR target UID depending on XREF type)
- PURPOSE (WHY mapping exists)
- STATUS/LOCK/VERSION (если это отдельный XREF артефакт)

Правило:
- Если XREF нужен рантайму как “указатель открыть документ” — TO должен быть RAW.
- Если XREF нужен как “семантическая карта” — лучше использовать REL (UID-only).

---

## 7) DEPRECATION & REPLACEMENT (PAIRING LAW)
Если вводится замена/депрекация:
- Новый документ/модуль A обязан иметь:
  - `REL: supersedes -> <OLD_UID> | WHY: ...`
- Старый документ/модуль B обязан иметь:
  - `REL: deprecated_by -> <NEW_UID> | WHY: ...`

Это исключает двусмысленность “кто кого заменил”.

---

## 8) GAP HANDLING (ALLOWED)
Если TO_UID ещё не существует:
- TO_UID: `GAP:<proposed_uid_or_name>`
- WHY: почему нужна сущность/док
- NEXT: что создать (doc/entity/template)

Запрещено:
- писать несуществующий UID как будто он существует без GAP.

---

## 9) ANTI-PATTERNS (FORBIDDEN)
- `REL: depends_on -> https://raw...`
- `REL: related -> UE....` (custom rel type)
- `REL: depends_on -> 04_KNOWLEDGE_BASE/...` (path in REL)
- REL без WHY
- INTERFACES без RAW (пусто или “путь” вместо URL)

---

## 10) COMPLIANCE CHECKLIST (REQUIRED)
### 10.1 REL encoding
- [ ] REL содержит только UID → UID
- [ ] REL не содержит URL/RAW/пути
- [ ] REL_TYPE только из словаря
- [ ] WHY присутствует в каждой связи

### 10.2 Separation
- [ ] NAV ссылки только в INTERFACES (RAW-only)
- [ ] XREF используется как mapping, не как “семантика”

### 10.3 Deprecation
- [ ] Если есть замена — есть пара supersedes/deprecated_by

### 10.4 Registration
- [ ] Док зарегистрирован в KB MASTER INDEX, если используется системой

---

## 11) OPTIONAL CHANGE LOG
- 2026-01-20 — CREATE — v1.0.0

---
## END
