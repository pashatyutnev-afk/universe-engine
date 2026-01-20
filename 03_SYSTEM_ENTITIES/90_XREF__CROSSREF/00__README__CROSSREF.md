# CROSSREF (XREF) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md
SCOPE: Universe Engine (Games volume) / System Entities / Crossref (XREF)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
ENTITY_GROUP: CROSSREF (XREF)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.REALM.001
OWNER: SYSTEM
ROLE: Canonical boundaries + SoT navigation for cross-reference maps (RAW-only). Defines what XREF is and is not.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Rebuilt XREF realm README to DOC CONTROL, RAW-only interfaces, strict role boundaries, and SoT index definition."
- REASON: "Prevent broken routing due to missing/implicit mappings and mixed responsibilities."
- IMPACT: "Routing becomes deterministic: engines/pipelines/validators are discoverable via explicit maps."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.REALM.001

---

## 0) PURPOSE (LAW)
XREF слой — это карты соответствий, которые делают систему навигируемой и проверяемой:
- какие ENG используются в каких ORC шагах
- какие SPC получают результат какого ORC шага
- какая цепочка CTL → VAL → QA применяется к типу задачи/артефакта
- какие пайплайны считаются каноническими (pipeline maps)

XREF — это SoT для связей (links of meaning), а не хранилище контента.

---

## 1) SCOPE
Этот realm применяется ко всем файлам внутри:
- `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/**`

Source of truth (SoT) XREF слоя:
- `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md`

---

## 2) ROLE BOUNDARIES (HARD)
### 2.1 XREF OWNS
- карты соответствий между сущностями/слоями (maps)
- матрицы проверок (validation matrix)
- карты пайплайнов (pipeline maps)
- правила “куда идти дальше” (routing by map), но без принятия решений за SPC/ORC

### 2.2 XREF DOES NOT OWN
- порядок исполнения шагов (это ORC)
- методы/микрологика (это ENG)
- политики/лимиты (это CTL)
- формальная проверка соответствия законам (это VAL)
- оценка качества (это QA)
- доменные решения/упаковка результата (это SPC)

Нарушение границ = S0 (role contamination).

---

## 3) EXISTENCE LAW (ABSOLUTE)
XREF карта/матрица считается каноном только если:
- оформлена как документ с DOC CONTROL
- имеет UID
- зарегистрирована в `00__INDEX__CROSSREF.md` (SoT)

Файл в репо без регистрации → NON-CANON / ignored.

---

## 4) MINIMUM CANON MAP SET (REQUIRED)
В каноне должен существовать минимум:
- ENG → ORC map
- ORC → SPC map
- Validation matrix (CTL/VAL/QA placement)
- Pipeline map (что считать каноническими пайплайнами)

Если минимальный набор отсутствует → routing становится неполным.

---

## 5) HOW XREF IS USED (RUNTIME)
- При routing задачи: Top Governance SPC / ORC смотрит XREF карты, чтобы выбрать:
  - какой ORC пайплайн применить
  - какие ENG нужны внутри ORC
  - какие SPC упаковывают результат
  - где стоят CTL/VAL/QA гейты

Если карта отсутствует:
- фиксируется GAP
- предлагается создание недостающей XREF карты/записи
- после этого задача продолжается

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- методы построения карт
- примеры корректных матриц и пайплайнов

KB OUTPUTS:
- none (XREF не является KB модулем)

BOUNDARIES:
- XREF хранит только связи/карты, не хранит “знания домена” как KB SoT.

---

## 7) INTERFACES (RAW ONLY)
- XREF INDEX (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md
- MAP: ENG → ORC:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md
- MAP: ORC → SPC:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md
- MAP: VALIDATION MATRIX:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md
- MAP: PIPELINES:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md
- XREF TEMPLATE (INDEX):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_INDEX.md
- XREF TEMPLATE (RECORD):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_RECORD.md

--- END.
