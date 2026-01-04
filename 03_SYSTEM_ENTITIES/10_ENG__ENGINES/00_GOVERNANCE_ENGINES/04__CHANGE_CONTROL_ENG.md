# Change Control Engine
FILE: 04__CHANGE_CONTROL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Canonical workflow that governs any change to ENG engines, families, index, dependencies, and canon metadata

---

## PURPOSE

Этот движок превращает любые изменения ENG в **управляемый, проверяемый и воспроизводимый процесс**.

Он отвечает за:
- как предлагать изменения (Change Request)
- как оценивать последствия (impact)
- как проверять на противоречия (consistency)
- как утверждать канон (approval)
- как фиксировать версию и память изменений (version + memory)
- как писать в журнал (audit)
- как ставить LOCK (canon lock)

---

## SCOPE (WHAT IT CONTROLS)

Изменениями считаются (все проходят через этот движок):
- правки любого файла в `03_SYSTEM_ENTITIES/10_ENG__ENGINES/**`
- добавление / удаление движков
- перенос движков между семействами
- изменение нумерации / именования
- любые правки `00__INDEX_ALL_ENGINES.md`
- любые изменения зависимостей / handoff правил
- изменение терминов, которые влияют на другие движки

---

## NON-GOALS (WHAT IT DOES NOT DO)

- не решает “истину канона” (это Canon Authority)
- не делает содержательную проверку качества (это Consistency Engine)
- не описывает сами зависимости (это Dependency Registry)
- не заменяет QA/VAL процессы (они отдельные реестры)

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- change proposal (описание правки)
- scope notes (какие файлы, какая цель)
- dependency impact notes (что заденем)
- consistency notes (проверки/конфликты)
- approval decision (canon authority)

### PRODUCES
- approved change packet (CHG packet)
- version bump decision
- required updates list (INDEX/deps/links)
- audit log entry request
- lock decision (fixed/unfixed)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

### OUTPUT_TARGET
- Applies to all ENG engine files + INDEX + README realm files
- Updates must result in: (a) valid canon registry, (b) consistent dependency graph, (c) audit record

---

## CHANGE CLASSIFICATION (CANON)

### PATCH (X.Y.Z+1)
- форматирование/опечатки/markdown-структура
- правка ссылок без изменения ролей
- уточнение формулировок без смены смысла
- добавление LOCK/OWNER/metadata выравнивание

### MINOR (X.Y+1.0)
- добавление новых секций/правил, backward-compatible
- расширение outputs/inputs без смены роли
- уточнение boundary + handoff
- добавление новых движков в конец семейства (без перестановок)

### MAJOR (X+1.0.0)
- изменение роли движка (ROLE)
- изменение mini-contract (CONSUMES/PRODUCES/DEPENDS_ON)
- смена уровня/класса семейства
- перенос между семействами
- изменение нумерации/структуры
- удаление движка или breaking change

---

## CANON CHANGE PACKET (CHG) — REQUIRED FORMAT

Каждое изменение должно иметь CHG пакет (в тексте PR/коммита или отдельным файлом):

- CHG_ID: CHG-ENG-0001
- DATE:
- CHANGE_TYPE: PATCH | MINOR | MAJOR
- TARGET_SCOPE: (families/engines)
- SUMMARY: one paragraph
- RATIONALE: why change is needed
- FILES_TOUCHED: explicit list
- INDEX_UPDATE: yes/no (what lines change)
- DEP_GRAPH_IMPACT: list of edges added/removed/changed
- CONTRACT_CHANGE: yes/no (what fields)
- RISKS: what could break
- VALIDATION_PLAN: what checks run
- APPROVALS: (canon authority signature)
- AUDIT_LOG: entry id / link
- LOCK_DECISION: FIXED | UNFIXED (and why)

---

## GOVERNANCE GATES (MANDATORY PIPELINE)

Каждая правка обязана пройти ворота:

### G1 — PROPOSE
- CHG пакет создан
- список файлов указан
- цель и тип изменения определены

### G2 — IMPACT (Dependency)
- описаны изменения графа зависимостей
- проверено: не создаём скрытых handoff
- проверено: нет новых циклов без обоснования

### G3 — CONSISTENCY (System)
- нет конфликтов ролей / дублей ответственности
- соблюдены naming/numbering правила
- README и INDEX соответствуют структуре

### G4 — APPROVE (Canon Authority)
- канон-решение принято: принять/отклонить/вернуть на доработку

### G5 — VERSION + MEMORY
- версия обновлена по правилам
- память изменений записана (что и почему)

### G6 — AUDIT LOG
- запись о правке внесена в audit
- указаны touched files, тип, итог

### G7 — LOCK
- если правка завершена и согласована → LOCK: FIXED
- если в работе/эксперимент → LOCK: UNFIXED (и почему)

---

## REQUIRED OUTPUT ARTIFACTS (DEFINITION OF DONE)

Правка считается завершённой только если:

1) ✅ CHG пакет заполнен  
2) ✅ INDEX обновлён (если затронут состав/порядок/ссылки)  
3) ✅ dependency edges обновлены (если менялись входы/выходы)  
4) ✅ mini-contract обновлён (если были изменения контрактов)  
5) ✅ consistency checks пройдены  
6) ✅ audit log entry сделан  
7) ✅ LOCK выставлен правильно

---

## VALIDATION CHECKLIST (QUICK)

- CC1: Нет второго `STATUS` внизу (используется `LOCK`)
- CC2: Заголовок и metadata построчно, единый формат
- CC3: Имя файла соответствует номеру в INDEX
- CC4: Все ссылки raw корректны (если менялись)
- CC5: `DEPENDS_ON` отражает реальную зависимость
- CC6: Handoff описан, если outputs используются downstream
- CC7: Нет дублирования ролей между движками без boundary
- CC8: Нет циклов в зависимостях без явно описанного разрыва через governance gate

---

## FAILURE MODES (WHAT CAN GO WRONG)

- Hidden coupling: движок зависит от чужого артефакта, но это не описано
- Role overlap: два движка “делают одно и то же”
- Index drift: файл существует, но отсутствует в INDEX / или номер не совпадает
- Level mismatch: CLASS/LEVEL в индексе не совпадает с README/движками
- Unlogged change: канон меняется без audit trail

---

## INTEGRATION NOTES (WHERE THIS FITS)

- INDEX является навигационным законом, но любые изменения INDEX идут через Change Control
- Dependency Registry даёт язык зависимостей и handoff
- Consistency Engine даёт “проверку целостности”
- Canon Authority решает “принимаем ли в канон”
- Versioning & Memory фиксирует версию и объясняет историю
- Audit Log фиксирует след правки

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
