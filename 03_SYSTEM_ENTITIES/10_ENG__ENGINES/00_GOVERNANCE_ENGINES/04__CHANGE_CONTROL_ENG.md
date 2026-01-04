# Change Control Engine
FILE: 04__CHANGE_CONTROL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Controls all canon changes: proposals, review gates, approvals, and safe application rules

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- Change proposal (draft or formal)
- Diffs / suggested edits / new file requests
- Registry/index impact notes
- Risk notes (if any)
- Canon Authority verdicts / decision IDs (if exist)

PRODUCES:
- Approved or rejected change decision
- Required edit list (targets + exact actions)
- Versioning instructions (what to bump, where)
- Audit log entry payload (what must be recorded)
- Canon-safe merge checklist

DEPENDS_ON:
- 01__AUDIT_LOG_ENG
- 02__CANON_AUTHORITY_ENG
- 03__RULE_HIERARCHY_ENG
- 10__VERSIONING_MEMORY_ENG

OUTPUT_TARGET:
- Governance-controlled updates to ENG layer files, READMEs, registries, and engine docs

---

## 0) PURPOSE (LAW)
Change Control Engine гарантирует, что:
- канон меняется **только управляемо**
- правки **не ломают** реестры, зависимости, границы
- любое изменение оставляет **след** (audit + versioning)

### ABSOLUTE LAW
> Любая правка, влияющая на канон, обязана пройти Change Control.  
> “Тихие правки” запрещены.

---

## 1) WHAT COUNTS AS CANON CHANGE (SCOPE)
Canon change = любое действие, которое меняет хотя бы один пункт:

### A) Registry / Index / Order
- добавление/удаление движков
- смена номера
- смена порядка
- смена семейства
- смена путей / канонических ссылок

### B) Rules / Laws / Realm
- изменение правил слоя/семейства/движка
- изменение правил нумерации/именования
- изменение “existence rule”, “lock standard”, “mini-contract law”

### C) Contracts / Dependencies
- изменение CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET
- добавление новой зависимости
- изменение governance dependency registry

### D) Boundaries / Ownership
- перенос ответственности между движками
- сужение/расширение scope у движка/семейства
- устранение дублирования (anti-duplication)

### E) Status / Lock
- смена STATUS
- смена LOCK (OPEN ↔ FIXED)

---

## 2) CHANGE STATES (STATUS MODEL)
Статус относится к **изменению**, а не к файлу.

- `DRAFT` — идея/черновик, не готово к review
- `PROPOSED` — оформлено по шаблону, готово к проверке
- `REVIEW` — идет проверка влияний (scope/deps/conflicts)
- `APPROVED` — принято в канон (можно применять)
- `REJECTED` — отклонено (с причиной)
- `APPLIED` — внесено в файлы + обновлены реестры + аудит
- `ROLLED_BACK` — откат (если сломали канон)

### HARD RULE
> Нельзя “APPLIED” без “APPROVED”.

---

## 3) CHANGE LEVELS (SEVERITY)
- `MINOR` — правка текста без изменения смысла/правил/контрактов
- `MAJOR` — меняет правила, порядок, зависимости или границы
- `CRITICAL` — трогает existence/registry/order/lock law или ломает совместимость слоёв

### RULE
> MAJOR и CRITICAL всегда требуют Canon Authority решения (явного).

---

## 4) REQUIRED PIPELINE (MANDATORY)
Любая каноническая правка проходит шаги:

1) **Proposal** (описать изменение по шаблону)
2) **Impact Scan** (scope + registry + deps + boundaries)
3) **Conflict Check** (Rule Hierarchy: кто владелец области)
4) **Decision** (Canon Authority: approve/reject)
5) **Apply** (внести изменения: файлы + ссылки + порядок)
6) **Registry Sync** (index/registry обязаны совпасть)
7) **Audit Log** (зафиксировать факт)
8) **Versioning** (если затронуто: bump и запись в memory)

---

## 5) IMPACT SCAN CHECKLIST (MANDATORY)
Перед approve ответить “да/нет”:

### 5.1 Scope
- [ ] Тронут ли слой ENG?
- [ ] Тронуто ли семейство?
- [ ] Тронут ли конкретный движок?

### 5.2 Registry
- [ ] Нужно ли менять INDEX?
- [ ] Нужен ли новый движок в реестре?
- [ ] Меняется ли порядок/номер?

### 5.3 Dependencies
- [ ] Меняются ли DEPENDS_ON?
- [ ] Нужно ли обновить dependency registry?

### 5.4 Boundaries
- [ ] Есть ли дублирование владения?
- [ ] Меняются ли critical boundaries?

### 5.5 Lock/Status
- [ ] Нужно ли менять LOCK/STATUS?

---

## 6) CHANGE PROPOSAL TEMPLATE (COPY-PASTE)
Используй этот блок как стандарт.

CHANGE_ID: CHG-XXXX
STATUS: DRAFT|PROPOSED|REVIEW|APPROVED|REJECTED|APPLIED|ROLLED_BACK
SEVERITY: MINOR|MAJOR|CRITICAL

TITLE: <коротко, что меняем>
OWNER: <кто ведёт изменение>

SCOPE:
- LAYER: ENG
- FAMILY: <если применимо>
- ENGINE: <если применимо>

MOTIVATION:
- почему это нужно (1–5 строк)

PROPOSAL (WHAT CHANGES):
- конкретные изменения пунктами

AFFECTED FILES:
- path/to/file.md
- path/to/index.md

REGISTRY IMPACT:
- добавляем/удаляем/меняем порядок/нет

DEPENDENCY IMPACT:
- новые deps / удалённые deps / нет

BOUNDARY IMPACT:
- кто владелец области до/после

RISK NOTES:
- что может сломаться

ROLLBACK PLAN:
- как откатить, если плохо

CANON AUTHORITY REQUIRED:
- YES/NO (если MAJOR/CRITICAL → YES)

APPROVAL:
- decision_id: <если есть>
- date: <если есть>

APPLY CHECKLIST:
- [ ] Files updated
- [ ] Index synced
- [ ] Dependency registry synced
- [ ] Audit log written
- [ ] Version bumped (if needed)

---

## 7) RULES FOR APPLY (SAFE MERGE LAW)
### 7.1 No orphan changes
Если меняешь файл движка — проверь:
- registry entry существует
- ссылки валидны
- нумерация совпадает

### 7.2 No silent deps
Любая новая зависимость:
- добавляется в DEPENDS_ON
- отражается в dependency registry

### 7.3 No duplicate ownership
Если правка создаёт пересечение областей:
- сначала boundary fix
- потом остальное

### 7.4 No broken locks
LOCK: FIXED нельзя менять без MAJOR/CRITICAL процесса.

---

## 8) WHAT TO DO WHEN FOUND A BROKEN CANON
Если обнаружено:
- файл есть, но нет в INDEX
- номер не совпадает
- README/engine конфликтуют
- deps скрыты

Тогда:
1) создать change proposal (SEVERITY минимум MAJOR)
2) указать конфликт и владельца по Rule Hierarchy
3) провести Canon Authority решение
4) привести всё к канону
5) записать в audit

---

## 9) FINAL RULE (LOCK)
> Change Control — шлюз канона.  
> Всё, что меняет канон, проходит через этот шлюз и оставляет след.

OWNER: Universe Engine  
LOCK: FIXED
