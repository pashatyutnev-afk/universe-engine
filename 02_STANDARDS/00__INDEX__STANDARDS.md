# STANDARDS INDEX — MASTER REGISTRY (CANON)
FILE: 02_STANDARDS/00__INDEX__STANDARDS.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
INDEX_TYPE: MASTER_STANDARDS_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.IDX.STD.MASTER.000
OWNER: SYSTEM
ROLE: Canonical navigation law + registry for all standards/specs/protocols/templates/terms inside 02_STANDARDS (mandatory entrypoint)

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Создан канонический master-index слоя 02_STANDARDS + зафиксированы правила существования/навигации + план миграции на Doc Control/Naming"
- REASON: "Файл отсутствовал (404), слой не имел единого entrypoint"
- IMPACT: "Вся навигация и существование STANDARDS"

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для слоя `02_STANDARDS`.

Он фиксирует:
- полный состав стандартов/спек/протоколов/шаблонов/терминов
- строгий порядок навигации (by folder + number)
- канонические пути и raw-ссылки
- правило существования для STANDARDS

### EXISTENCE RULE (ABSOLUTE)
Если стандарта/спека/протокола нет в этом INDEX — он НЕ существует для слоя STANDARDS.  
Если файл есть в репо, но не зарегистрирован здесь — NON-CANON (ignored).

---

## 1) HOW TO USE (MANDATORY FLOW)
1) Сначала читаешь `00_CANON/ARCHITECTURE_OVERVIEW.md` (как устроена система).
2) Затем читаешь `00_CANON/SYSTEM_CANON.md` (что считается каноном в стандартах).
3) Потом выбираешь нужный раздел:
   - SPECIFICATIONS (SoT)
   - PROTOCOLS (операционные правила)
   - TECHNICAL (шаблоны/формы)
   - TERMS (глоссарий)
   - REQUIREMENTS_TZ
   - MARKING_STANDARDS (модули детализации)
4) Любой новый стандарт:
   - сначала добавляется в этот INDEX,
   - потом создаётся файл,
   - потом фиксируется через Canon Protocol + Versioning Policy.

---

## 2) ORDER OF AUTHORITY (WITHIN STANDARDS)
При конфликте внутри 02_STANDARDS приоритет такой:

1) SPECIFICATIONS (SoT) — `02_STANDARDS/01_SPECIFICATIONS/*`
2) MARKING MODULES (detailing) — `02_STANDARDS/06_MARKING_STANDARDS/*` (не SoT, только детализация)
3) PROTOCOLS — `02_STANDARDS/02_PROTOCOLS/*`
4) TECHNICAL TEMPLATES — `02_STANDARDS/03_TECHNICAL/*`
5) TERMS/DEFINITIONS — `02_STANDARDS/04_TERMS_DEFINITIONS/*`
6) REQUIREMENTS_TZ — `02_STANDARDS/05_REQUIREMENTS_TZ/*`

---

## ROOT FILES (STANDARDS LAYER)

00 — STANDARDS INDEX (THIS FILE)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__INDEX__STANDARDS.md

01 — DOC REGISTRY (Standards) (SoT)
CURRENT PATH:
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__DOC_REGISTRY.md
CANON NAMING TARGET (MIGRATION):
- `02_STANDARDS/01__DOC_REGISTRY.md`

02 — MASTER INDEX (Universe Engine) (Global Map)
CURRENT PATH:
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md
CANON NAMING TARGET (MIGRATION):
- `02_STANDARDS/02__MASTER_INDEX__UNIVERSE_ENGINE.md`

NOTE:
В текущем репо есть коллизия по префиксу `00__*` в одной папке.
По Naming/Constraints это должно быть устранено через переименование/перенос.
См. MIGRATION PLAN.

---

## 3) CANON MAP — STANDARDS TREE

### 00_CANON (Reference / Canon)
Folder: `02_STANDARDS/00_CANON/`

00 — Architecture Overview
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_CANON/ARCHITECTURE_OVERVIEW.md

01 — System Canon
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_CANON/SYSTEM_CANON.md

---

### 01_SPECIFICATIONS (SoT Specs)
Folder: `02_STANDARDS/01_SPECIFICATIONS/`
Rule: Здесь живут главные спеки (SoT), которые описывают “как должно быть”.

01 — UID & Marking Standard
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md

02 — Storage Map Standard
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

03 — Doc Control Standard
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

04 — REL Policy + XREF Standard
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

05 — Scene Stack 4Track Standard
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md

05A — Template: Scene Pack
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md

05B — Template: Track Event
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md

06 — Naturalness Gates Standard
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md

06A — Template: NAT Profile
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/06A__TEMPLATE__NAT_PROFILE.md

07 — Doc Registry Standard
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md

LEGACY / TO-NORMALIZE (non-SoT until normalized):
- Entity Model Spec
  🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/ENTITY_MODEL_SPEC.md
- Index Structure Spec
  🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/INDEX_STRUCTURE_SPEC.md

---

### 02_PROTOCOLS (Operational Protocols)
Folder: `02_STANDARDS/02_PROTOCOLS/`

00 — Change Management Protocol
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/CHANGE_MANAGEMENT_PROTOCOL.md

01 — Chat Protocol
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/CHAT_PROTOCOL.md

NOTE (MIGRATION):
Имена файлов протоколов должны быть нормализованы под `NN__...md`.

---

### 03_TECHNICAL (Templates / Technical Forms)
Folder: `02_STANDARDS/03_TECHNICAL/`

00 — Entity Passport Template
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/03_TECHNICAL/ENTITY_PASSPORT_TEMPLATE.md

01 — Index Template
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/03_TECHNICAL/INDEX_TEMPLATE.md

NOTE (MIGRATION):
Имена файлов templates должны быть нормализованы под `NN__...md` (или явное исключение).

---

### 04_TERMS_DEFINITIONS (Language / Glossary)
Folder: `02_STANDARDS/04_TERMS_DEFINITIONS/`

00 — Glossary
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/04_TERMS_DEFINITIONS/GLOSSARY.md

---

### 05_REQUIREMENTS_TZ (Requirements / TZ)
Folder: `02_STANDARDS/05_REQUIREMENTS_TZ/`

00 — Requirements Index
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/05_REQUIREMENTS_TZ/00__INDEX.md

---

### 06_MARKING_STANDARDS (Modules: Marking System)
Folder: `02_STANDARDS/06_MARKING_STANDARDS/`
Rule: Здесь живут модули маркировки. Они НЕ дублируют спеки, а являются детализацией/модульными правилами.

01 — ID Standard (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md

02 — Storage Map (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md

03 — Status / Lock / Version (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/03__STATUS_LOCK_VERSION.md

04 — Priority S0–S3 (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md

05 — REL Policy + XREF (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md

06 — Scene Stack 4Track (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/06__SCENE_STACK_4TRACK.md

07 — Naturalness Gates (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/07__NATURALNESS_GATES.md

08 — Doc Control (Module)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/08__DOC_CONTROL.md

---

## 4) NO-DUPLICATION RULE (STANDARDS)
- Один смысл → один SoT документ (в 01_SPECIFICATIONS).
- Если нужно “детальнее” — делаем MODULE (06_MARKING_STANDARDS) и в SPEC даём ссылку, не копию.
- Дубли стандартов с одинаковым смыслом запрещены.

---

## 5) MIGRATION PLAN (REQUIRED TO COMPLY WITH SYSTEM LAW)
S0 (обязательно):
1) Устранить коллизию префиксов `00__*` в `02_STANDARDS/`:
   - переименовать `00__DOC_REGISTRY.md` → `01__DOC_REGISTRY.md`
   - переименовать `00__MASTER_INDEX__UNIVERSE_ENGINE.md` → `02__MASTER_INDEX__UNIVERSE_ENGINE.md`

2) Нормализовать SemVer и Doc Control шапки:
   - `VERSION: 1.0` → `1.0.0`
   - добавить `UID` всем каноническим документам
   - убрать любые дубли OWNER/LOCK/VERSION внизу

3) Нормализовать Naming в папках без `NN__` (02_PROTOCOLS, 03_TECHNICAL, 04_TERMS_DEFINITIONS):
   - привести к `NN__NAME.md` или зафиксировать исключение в Naming Rules

S1 (желательно):
4) Сверить ссылки в `00__MASTER_INDEX__UNIVERSE_ENGINE.md` (там встречаются устаревшие имена SoT-путей) и привести к фактическим путям.

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке `02_STANDARDS`.
Любая правка INDEX считается изменением канона и проходит Canon Protocol.
--- END.
