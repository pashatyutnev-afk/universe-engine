# Consistency Engine
FILE: 05__CONSISTENCY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Enforces canon consistency across ENG layer (naming, numbering, paths, links, contracts, registries, deps)

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- ENG layer indexes + registries
- Family READMEs (realm files)
- Engine files (all families)
- Dependency registry entries
- Change proposals (optional)

PRODUCES:
- Consistency report (violations list + severity)
- Required fix actions (targets + exact changes)
- Canon sync checklist (index ↔ filesystem ↔ links)
- Approval gating notes for Change Control
- Suggested refactors for anti-duplication

DEPENDS_ON:
- 03__RULE_HIERARCHY_ENG
- 04__CHANGE_CONTROL_ENG
- 06__DEPENDENCY_REGISTRY_ENG
- 10__VERSIONING_MEMORY_ENG

OUTPUT_TARGET:
- Fix directives applied to ENG docs, indexes, READMEs, and registries

---

## 0) PURPOSE (LAW)
Consistency Engine гарантирует, что ENG-слой:
- **не расходится** между индексом, путями, именами и файлами
- остаётся **навигируемым** и **машиночитаемым**
- не содержит **скрытых зависимостей** и **дубликатов владения**

### ABSOLUTE LAW
> Если индекс/правила говорят одно, а файлы/ссылки другое — канон считается нарушенным.

---

## 1) CONSISTENCY AXES (WHAT MUST MATCH)
Проверка ведётся по осям:

### A) Index ↔ Filesystem
- все движки из INDEX должны существовать как файлы
- все файлы движков должны быть зарегистрированы в INDEX

### B) Numbering ↔ Filenames ↔ Index
- номер в INDEX == номер в имени файла
- номера внутри семейства идут подряд (01..NN без дыр, если не разрешено)

### C) Paths
- канонический путь соответствует стандарту:
  `03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY>/<FILE>`

### D) Links
- у каждой FAMILY есть README realm link
- у каждого движка есть raw-link
- ссылки не битые и указывают на правильный файл

### E) Mini-contract
- каждый движок содержит mini-contract
- поля не пустые (кроме DEPENDS_ON допускает [])

### F) Dependencies
- DEPENDS_ON совпадает с dependency registry
- нет скрытых deps
- циклы только с явным объяснением

### G) Status/Lock
- в файле только один STATUS
- LOCK указан и соблюдается правилами (FIXED/OPEN)

---

## 2) VIOLATION SEVERITY (GATES)
Каждое нарушение имеет уровень:

- `S1_CRITICAL` — ломает канон (index mismatch, неверный номер, отсутствует файл, неверный путь, скрытая зависимость)
- `S2_MAJOR` — мешает навигации/поддержке (битые ссылки, дырки в нумерации без правила, конфликт ownership)
- `S3_MINOR` — косметика/формат (пробелы, пунктуация, стиль заголовков), не меняет смысла

### HARD RULE
> S1_CRITICAL блокирует любые изменения канона до фикса.

---

## 3) CANON CHECKS (MANDATORY TESTS)
### 3.1 Index Coverage Check
- [ ] Все перечисленные в INDEX raw-links открываются
- [ ] Каждая запись в INDEX соответствует существующему файлу в репо
- [ ] Нет “лишних” engine файлов вне INDEX

### 3.2 Family Realm Check
- [ ] В каждой FAMILY есть `00__README__<FAMILY>_ENGINES.md`
- [ ] README содержит STATUS + LOCK
- [ ] README определяет границы семейства (что входит/не входит)

### 3.3 Numbering Check
- [ ] Внутри FAMILY движки начинаются с 01
- [ ] Номера уникальны
- [ ] Номер в названии файла совпадает с номером в INDEX
- [ ] Дырки допускаются только если прямо описано правило “reserved numbers”

### 3.4 Canon Path Check
- [ ] Путь в raw-link соответствует стандарту
- [ ] Нет “съехавших” папок/имен

### 3.5 Mini-contract Check
- [ ] Есть блок MINI-CONTRACT
- [ ] CONSUMES/PRODUCES/OUTPUT_TARGET заполнены
- [ ] DEPENDS_ON указан (или [])
- [ ] Нет “забытых” зависимостей в тексте без DEPENDS_ON

### 3.6 Dependency Sync Check
- [ ] DEPENDS_ON == dependency registry
- [ ] Любой новый DEPENDS_ON отражён в registry
- [ ] Циклы отмечены + причина

### 3.7 Status/Lock Check
- [ ] В файле только один STATUS
- [ ] LOCK один и в конце (или в стандартном месте)
- [ ] FIXED нельзя править без Change Control (MAJOR/CRITICAL)

---

## 4) QUICK FIX RULES (FAST PATCHES)
### 4.1 Allowed without canon change (S3 only)
Можно править без Canon Authority, если:
- исправление опечаток
- форматирование
- корректировка пробелов/переносов
- уточнение текста без изменения правил/контрактов

### 4.2 Not allowed as “quick fix”
Запрещено как “быстрая правка”:
- менять номера/порядок
- добавлять движок
- менять DEPENDS_ON
- менять границы владения
- менять LOCK (особенно FIXED)

---

## 5) CONSISTENCY REPORT TEMPLATE (COPY-PASTE)
REPORT_ID: CNS-XXXX
DATE: YYYY-MM-DD
SCOPE: ENG

SUMMARY:
- total_violations: N
- S1_CRITICAL: N
- S2_MAJOR: N
- S3_MINOR: N

VIOLATIONS:
- ID: CNS-XXXX-01
  SEVERITY: S1_CRITICAL|S2_MAJOR|S3_MINOR
  TYPE: INDEX_MISMATCH|MISSING_FILE|BROKEN_LINK|NUMBERING|PATH|MINI_CONTRACT|DEP_SYNC|LOCK_STATUS|OWNERSHIP
  TARGET: path/to/file.md
  DETAILS: <что сломано>
  REQUIRED_FIX:
    - <точные действия>
  OWNER_HINT:
    - <какой движок/семейство отвечает по rule hierarchy>

---

## 6) ANTI-DUPLICATION ENFORCEMENT
Если найден дубликат владения (две области отвечают за одно и то же):
1) определить владельца по Rule Hierarchy
2) перенести/развести ответственность
3) обновить README границы
4) обновить INDEX при необходимости
5) записать в audit + versioning

---

## 7) MINIMUM “CANON OK” BAR
ENG слой считается “OK”, когда:

- нет S1_CRITICAL
- все raw-links валидны
- INDEX ↔ файлы совпадают
- у всех движков есть mini-contract
- dependency registry синхронизирован

---

## 8) FINAL RULE (LOCK)
> Consistency Engine — системный детектор рассинхрона.  
> Он не “советует”, а фиксирует: что канонично, а что нет.

OWNER: Universe Engine  
LOCK: FIXED
