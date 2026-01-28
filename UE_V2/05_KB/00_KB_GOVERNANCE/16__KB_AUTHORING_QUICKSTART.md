# 16__KB_AUTHORING_QUICKSTART.md

SCOPE: Universe Engine (Games volume)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: GUIDE (AUTHORING)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GUIDE.AUTHORING.016
OWNER: KB_GOVERNANCE
ROLE: Quickstart for creating KB documents that are immediately navigable, link-safe (RAW-only), and relationship-stable (UID-only).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Unified KB authoring rules: NAV=RAW, REL=UID-only, XREF=mapping. Added mandatory KB SCOPE + compliance checklist."
- REASON: "Stop inconsistent formats and prevent broken navigation/graphs."
- IMPACT: "New KB docs become deterministic and auditable from first commit."
- CHANGE_ID: UE.CHG.2026-01-20.KB.AUTHORING.016

---

## 0) PURPOSE (LAW)
Этот гайд задаёт **минимально-достаточный** способ писать документы Knowledge Base так, чтобы:
- навигация была **только по RAW ссылкам**,
- семантические связи были **только по UID** (без URL),
- кросс-ссылки (XREF) были **маппингом/роутингом**, а не контентом,
- каждый KB-док сразу проходил контроль и мог быть зарегистрирован в master-index.

---

## 1) DEFINITIONS (CANON)
### 1.1 NAV (Navigation)
Ссылки для перехода/открытия документов.
- Формат: **RAW URL**.
- Источник допустимых RAW: только ROOT LINK BASE и/или RAW ссылки пользователя.

### 1.2 REL (Semantic Relations)
Семантические связи в графе знаний: “зависит”, “уточняет”, “проверяется”, “использует”.
- Формат: **UID → UID**.
- В REL **запрещены URL** любого вида.

### 1.3 XREF (Cross-Reference / Mapping)
Таблицы соответствий: сущность ↔ документ, документ ↔ стандарт, стандарт ↔ гейт.
- XREF — это **карта маршрутизации/соответствий**, не замена REL и не NAV.

---

## 2) ABSOLUTE KB AUTHORING LAWS
### 2.1 RAW-only for NAV
- В разделе навигации/интерфейсов использовать только **RAW** ссылки.
- Запрещено писать “пути” и “угаданные URL”.

### 2.2 UID-only for REL
- Любые смысловые связи фиксируются как **UID ↔ UID**.
- В REL запрещены RAW/URL.

### 2.3 Separation rule (NAV vs REL vs XREF)
- NAV отвечает на “**куда открыть**”.
- REL отвечает на “**как связано по смыслу**”.
- XREF отвечает на “**как маршрутизировать/проверять/сопоставлять**”.

### 2.4 Mandatory KB SCOPE block
Каждый KB-док **обязан** содержать KB SCOPE: inputs/outputs/boundaries + RAW references (если есть).

### 2.5 No orphan docs
KB-док считается “каноном” только после регистрации в master-index слоя KB.

---

## 3) WHERE THIS GUIDE APPLIES
Используй этот гайд для:
- KB статей (концепты, определения, правила),
- KB процедур (runbooks внутри KB),
- KB справочников (словари, модели связей),
- KB карт (XREF таблицы),
- KB пакетов интеграции (restore packs, compliance reports).

---

## 4) MINIMAL KB DOCUMENT TEMPLATE (COPY-PASTE)
Ниже — минимальный “скелет”, который должен быть в каждом KB-доке.

### 4.1 HEADER (REQUIRED)
- SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE
- CHANGE_NOTE (минимум: DATE, TYPE, SUMMARY, REASON, IMPACT, CHANGE_ID)

### 4.2 SECTIONS (REQUIRED)
1) PURPOSE (LAW)  
2) KB SCOPE (REQUIRED)  
3) CONTENT (CANON)  
4) INTERFACES (RAW-only)  
5) RELATIONS (UID-only)  
6) XREF (optional but recommended)  
7) COMPLIANCE CHECKLIST (REQUIRED)  
8) CHANGE LOG (optional)

---

## 5) KB SCOPE (REQUIRED)
**KB SCOPE** — это контракт “что документ принимает и что выдаёт”.

### 5.1 KB INPUTS
- Какие данные/контекст нужны, чтобы применить документ.
- Пример: “UID целевой сущности”, “ссылка на стандарт”, “задача пользователя”.

### 5.2 KB OUTPUTS
- Что документ даёт системе.
- Пример: “набор правил”, “словарь типов связей”, “чеклист контроля”.

### 5.3 KB BOUNDARIES (WHAT THIS DOC IS NOT)
- Чётко зафиксировать, что документ **не делает**.
- Пример: “не задаёт NAV ссылки”, “не заменяет стандарты”, “не является реестром”.

### 5.4 KB RAW REFERENCES (IF ANY)
- Сюда допускаются только RAW ссылки, которые реально разрешены link-base’ом пользователя.
- Если ссылок нет — оставить “NONE”.

---

## 6) INTERFACES (RAW-ONLY, NO PATH)
В INTERFACES указываются **точки входа/выхода**, куда можно перейти, чтобы:
- прочитать закон/стандарт,
- открыть реестр,
- открыть связанную сущность,
- открыть канонический индекс слоя.

Формат:
- NAME
- PURPOSE
- RAW

Пример:
- KB MASTER INDEX
  - PURPOSE: Canonical entrypoint for KB layer
  - RAW: (allowed only if provided)

---

## 7) RELATIONS (UID-ONLY)
Рекомендуемый формат (таблично или списком):

- FROM_UID: <this_doc_uid>
- REL: <relation_type>
- TO_UID: <target_uid>
- WHY: <one-line reason>

Правила:
- TO_UID должен существовать в каноне или быть явно помечен как GAP (см. ниже).
- REL_TYPE должен быть из разрешённого словаря типов (если словарь существует в KB).

### 7.1 GAP NOTATION (ALLOWED)
Если нужной сущности/дока ещё нет:
- TO_UID: GAP:<proposed_uid_or_name>
- WHY: почему нужен
- NEXT: что создать (entity/doc/template)

---

## 8) XREF (OPTIONAL, RECOMMENDED)
XREF — таблицы соответствий для рулинга и маршрутизации.
Примеры XREF таблиц:
- Document UID → Responsible SPC
- Doc Type → Required gates (CTL/VAL/QA)
- KB Topic → Registry entry

---

## 9) COMPLIANCE CHECKLIST (REQUIRED)
Перед регистрацией в master-index проверь:

### 9.1 Format
- [ ] Header заполнен полностью (VERSION/UID/OWNER/ROLE есть)
- [ ] Есть CHANGE_NOTE с CHANGE_ID
- [ ] Есть PURPOSE (LAW)
- [ ] Есть KB SCOPE (inputs/outputs/boundaries + RAW references)

### 9.2 Navigation & Links
- [ ] В INTERFACES используются только RAW ссылки
- [ ] Нет “путей” вместо RAW
- [ ] Нет “угадывания” ссылок

### 9.3 Relations
- [ ] В RELATIONS нет URL/RAW
- [ ] Все REL — только UID → UID
- [ ] Неизвестные сущности отмечены как GAP, не как “будто существуют”

### 9.4 Registration
- [ ] Док зарегистрирован в `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md` (master-index)
- [ ] Если есть sub-index темы — добавлена запись и туда

---

## 10) REGISTRATION RULE (LAW)
Док считается каноном слоя KB только после регистрации в master-index KB.

### 10.1 Where to register (RAW)
KB MASTER INDEX (RAW):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

KB REALM README (RAW):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

KB RULES (RAW):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 11) QUICK EXAMPLE (MINI)
KB SCOPE:
- INPUTS: UID of target entity + task
- OUTPUTS: relation model rules for consistent graph building
- BOUNDARIES: does not define new entities; only authoring guidance
- RAW REFERENCES: KB master index (if allowed)

INTERFACES:
- KB MASTER INDEX → RAW

RELATIONS (UID-only):
- FROM_UID: UE.KB.GUIDE.AUTHORING.016
- REL: supports
- TO_UID: UE.KB.IDX.MASTER.001
- WHY: Authoring guide must be discoverable from KB index

---

## 12) OPTIONAL: CHANGE LOG
- 2026-01-20 — CREATE — v1.0.0 — initial release

--- 
## END
