# SPC FAMILY REALM README — TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/<FAMILY_FOLDER>/00__README__<FAMILY_SHORTNAME>.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: <UE.SPC.REALM.<FAMILY>.001>
OWNER: <SYSTEM|<ROLE/NAME>>
ROLE: Family realm definition + boundaries + navigation rules for SPC family `<FAMILY_FOLDER>`

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <NEW|PATCH|MAJOR>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: <UE.CHG.<YYYY-MM-DD>.SPC.REALM.<FAMILY>.<NNN>>

---

## 0) PURPOSE (LAW)
Этот README задаёт **рамки семейства SPC**: `<FAMILY_FOLDER>`.

Он фиксирует:
- зачем существует семейство
- какие типы задач оно покрывает
- жёсткие границы (что НЕ делает)
- правила взаимодействия с ENG/ORC/VAL/QA
- строгую навигацию по специалистам этого семейства

---

## 1) EXISTENCE + NAV RULE (MANDATORY)
- Специалист существует для системы **только если** он:
  1) зарегистрирован в `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`
  2) и файл специалиста присутствует по каноническому пути
- Любые “левые” файлы в папке без регистрации в глобальном SPC INDEX — **NON-CANON / ignored**
- Навигация по системе SPC — **RAW-only** (ссылки в глобальном индексе)

---

## 2) FAMILY SCOPE
**FAMILY NAME:** `<FAMILY_NAME>`  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/<FAMILY_FOLDER>/`  
**WHO THIS FAMILY IS FOR:** `<1–2 строки: кому/для чего>`  

### 2.1 Covered domains (what we DO)
- <domain/task type 1>
- <domain/task type 2>
- <domain/task type 3>

### 2.2 Hard boundaries (what we DO NOT do)
- <explicit boundary 1>
- <explicit boundary 2>
- <explicit boundary 3>

---

## 3) OUTPUT PHILOSOPHY (DEFAULT)
**Default mindset:** `<Generate|Structure|Constrain|Validate|Package|Schedule>`  
**Quality priority:** `<Canon safety|Plausibility|Emotion|Clarity|Speed|Consistency>`  
**Default output format:** `<what family typically outputs>`

---

## 4) INTERFACES (SYSTEM LINKS)
### 4.1 ENG (Engines)
- Typical ENG families this SPC family supports:
  - `<ENG_FAMILY_XX> — why`
  - `<ENG_FAMILY_YY> — why`

### 4.2 ORC (Orchestrators)
- Typical ORC usage:
  - `<ORC_NAME> — when used`

### 4.3 VAL / QA (Gates)
- Required validations (typical):
  - `<VAL/QA gate 1>`
  - `<VAL/QA gate 2>`

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Naming + numbering
- Specialist files are numbered **strictly** and match the global SPC index order.
- Filename format (inside this family):
  `NN__<SPECIALIST_NAME>_SPC.md`
- README is always:
  `00__README__<FAMILY_SHORTNAME>.md`

### 5.2 STATUS / LOCK policy
Allowed STATUS:
- `STATUS: DRAFT`
- `STATUS: ACTIVE`
- `STATUS: DEPRECATED`
- `STATUS: ARCHIVED`

Allowed LOCK:
- `LOCK: OPEN`
- `LOCK: FIXED`

### 5.3 Anti-duplication
- Запрещены два спеца с одной и той же ролью под разными именами.
- Если роль спорная — сперва фиксируй границы в этом README, потом создавай спеца.

---

## 6) WHEN TO CREATE A NEW SPECIALIST (GATE)
Новый SPC создаётся **только если**:
- существует повторяющийся тип задач, который не закрывается текущими SPC без размывания границ
- движок (ENG) требует отдельного “режима мышления” / контрактов / чеклистов
- роль регулярно появляется как “временная заплатка” в пайплайнах

**Запрещено** создавать SPC “на всякий случай”.

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
> ВАЖНО: RAW ссылки на специалистов хранятся в глобальном SPC INDEX.  
> Здесь можно держать только человекочитаемый список (без RAW), если нужно.

01 — <SPECIALIST_NAME>  
02 — <SPECIALIST_NAME>  
03 — <SPECIALIST_NAME>  

---

## 8) CHANGE CONTROL
- Любое изменение состава семьи / порядка / смысловых границ:
  - фиксируется в CHANGE_NOTE
  - и синхронизируется с глобальным `02__INDEX_ALL_SPECIALISTS.md`

---

## FINAL RULE (LOCK)
Этот README задаёт **границы** семейства SPC `<FAMILY_FOLDER>`.  
Границы и порядок специалистов считаются законом семейства.

OWNER: <SYSTEM|...>  
LOCK: <OPEN|FIXED>

--- END.
