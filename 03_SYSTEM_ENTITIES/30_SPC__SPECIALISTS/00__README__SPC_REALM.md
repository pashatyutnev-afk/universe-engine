# SPECIALISTS (SPC) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__README__SPC_REALM.md
SCOPE: Universe Engine (Games volume) / System Entities / Specialists (SPC)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
ENTITY_GROUP: SPECIALISTS (SPC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.SPC.REALM.001
OWNER: SYSTEM
ROLE: Canonical boundaries + navigation law + output packaging contract for SPC layer (RAW-only).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Rebuilt SPC realm README to strict role boundaries, RAW-only interfaces, explicit packaging law, KB scope and existence SoT."
- REASON: "Prevent mixed-role behavior and 'naked content' outputs; make SPC auditable in boot-first runtime."
- IMPACT: "SPC becomes deterministic: intent/decision/packaging owner with clear handoffs to ORC/ENG/CTL/VAL/QA."
- CHANGE_ID: UE.CHG.2026-01-20.SPC.REALM.001

---

## 0) PURPOSE (LAW)
SPC (Specialist) — владелец:
- намерения (intent) и постановки задачи
- решений (decision ownership) в рамках своей компетенции
- упаковки результата (artifact packaging) в корректный документ по стандартам системы

SPC не “исполняет рантайм” вместо ORC и не “жёстко контролирует” вместо CTL.
SPC не валидирует закон/канон вместо VAL и не оценивает качество вместо QA.

---

## 1) SCOPE
Этот realm применяется ко всем файлам внутри:
- `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/**`

Source of truth (SoT) для состава/существования SPC:
- `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md` (GLOBAL REGISTRY)

---

## 2) ROLE BOUNDARIES (HARD)
### 2.1 SPC OWNS
- INTAKE: цель, область, тип артефакта, минимальные входы
- ROUTING INPUT: формулирует требования к пайплайну (но не заменяет ORC)
- DECISIONS: выбирает параметры решения в рамках компетенции
- PACKAGING: оформляет deliverable как документ-артефакт по стандартам/шаблонам
- SIGNOFF (если governance SPC): финальная приемка/подпись/контроль структуры документов

### 2.2 SPC DOES NOT OWN
- порядок шагов пайплайна (это ORC)
- детерминированные методы/микрологика (это ENG)
- политики/лимиты/блокировки (это CTL)
- формальная проверка соответствия законам/стандартам (это VAL)
- quality gates и регресс (это QA)

Нарушение границ роли = S0 (role contamination).

---

## 3) OUTPUT ARTIFACT LAW (ABSOLUTE)
SPC никогда не выпускает “голый контент”.
Любой результат обязан быть:
- документом-артефактом (с DOC CONTROL header)
- собранным по подходящему TEMPLATE (или через создание нового шаблона при GAP)
- с корректными RAW интерфейсами (если документ является навигационным)

Если подходящего шаблона нет:
- GAP фиксируется
- сначала создаётся недостающий шаблон/сущность
- потом продолжается задача

---

## 4) EXISTENCE LAW (ABSOLUTE)
SPC считается существующим в каноне только если:
- имеет UID
- оформлен по `00__TEMPLATE__SPC_ENTITY.md`
- зарегистрирован в `02__INDEX_ALL_SPECIALISTS.md` (RAW link)

Файл в репо без регистрации → NON-CANON / ignored.

---

## 5) TOP GOVERNANCE SPC (SPECIAL LAW)
Верхние SPC (governance) — это диспетчеры рантайма и финальная подпись:
- MACHINE_ARCHITECT_SPC (start + final signoff)
- DOC_CONTROLLER_SPC (структура документов, DOC CONTROL, сборка пакетов)
- STANDARDS_OWNER_SPC (стандарты/канон)
- PIPELINE_ARCHITECT_SPC (пайплайны/ORC)
- INTEGRATION_PACKER_SPC (финальная упаковка/структура поставки)

Эти SPC имеют приоритет над доменными SPC.

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- компетентностные packs, чеклисты, эталоны качества по специализации
- примеры правильных артефактов и упаковки

KB OUTPUTS:
- none (SPC производит deliverables, а не KB модули, если явно не указано иначе)

BOUNDARIES:
- SPC может ссылаться на KB, но не должен заменять KB “памятью чата”.

---

## 7) INTERFACES (RAW ONLY)
- SPC GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md
- SPC RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md
- SPC CREATE FLOW:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03__CREATE_FLOW__SPC.md
- SPC ENTITY TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_ENTITY.md
- SPC OUTPUT PACK TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_OUTPUT_PACK.md
- SPC FAMILY README TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__README__SPC.md

--- END.
