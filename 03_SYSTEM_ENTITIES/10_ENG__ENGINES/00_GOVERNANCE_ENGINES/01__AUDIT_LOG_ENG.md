# Audit Log Engine
FILE: 01__AUDIT_LOG_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Canonical immutable change ledger for ENG; records what changed, why, scope, approvals, dependency impact, and lock decisions

---

## PURPOSE

Этот движок — **единый журнал памяти канона** для ENG.

Он нужен, чтобы:
- любая правка имела след
- можно было восстановить “почему система стала такой”
- можно было откатить/сравнить версии
- индекс/зависимости/контракты не менялись “втихую”

---

## SCOPE (WHAT MUST BE LOGGED)

В Audit Log обязаны попадать:

### A) Registry changes
- любые правки `00__INDEX_ALL_ENGINES.md`
- добавление/удаление движков
- переносы между семействами
- изменения нумерации/именования
- изменение ссылок raw (если влияет на навигацию)

### B) Contract / dependency changes
- любое изменение MINI-CONTRACT (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- любые изменения handoff правил
- любые изменения DEP_EDGES / cycles / overlap decisions

### C) Canon law changes
- изменения в governance движках (00/*)
- изменения в README realm files (термины/границы/законы)

### D) Lock decisions
- постановка или снятие `LOCK: FIXED/UNFIXED`
- waivers (временные допуски) по несоответствиям

---

## NON-GOALS

- audit log не является местом для длинных обсуждений
- audit log не заменяет change packet (CHG) — он его фиксирует
- audit log не утверждает канон (это Canon Authority)

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- approved change packets (CHG)
- version/memory notes (release notes)
- consistency reports (CR)
- dependency graph snapshots (DG) when applicable

### PRODUCES
- AUDIT ENTRY records (canonical ledger items)
- audit index pointers (IDs that other files can cite)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

### OUTPUT_TARGET
- Any canon change results in an Audit Entry
- Audit Entry IDs are referenced from CHG packets and (optionally) from touched files

---

## CANON ARTIFACT: AUDIT ENTRY (MANDATORY)

Каждая запись должна быть минимально достаточной, но полной по смыслу.

### AUDIT_ENTRY SCHEMA (CANON)

- AUDIT_ID: AL-ENG-0001
- DATE:
- CHANGE_TYPE: PATCH | MINOR | MAJOR
- SCOPE:
  - families:
  - engines:
- SUMMARY:
  - one paragraph: what changed
- RATIONALE:
  - one paragraph: why
- FILES_TOUCHED:
  - explicit list of canon paths
- INDEX_IMPACT:
  - yes/no + what lines/sections changed
- CONTRACT_IMPACT:
  - yes/no + which engines’ contracts changed
- DEP_GRAPH_IMPACT:
  - none | DG-ENG-XXXX reference + edge notes
- CONSISTENCY_REPORT:
  - CR-ENG-XXXX reference + verdict
- APPROVAL:
  - approved_by: (Canon Authority)
  - decision: APPROVE | REJECT | RETURN
- VERSION:
  - before:
  - after:
- LOCK_DECISION:
  - FIXED | UNFIXED
  - reason:
- WAIVERS (optional):
  - list of waivers with expiry/conditions
- NOTES (optional):
  - max 5 bullets

---

## AUDIT STORAGE STANDARD (WHERE IT LIVES)

Audit log должен быть доступен как “единый файл” или “единая папка”.

Например (канон-правило, выбрать один вариант и держать его всегда):
- OPTION A (single file): `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__AUDIT_LOG.md`
- OPTION B (entries folder): `.../00__AUDIT_LOG/AL-ENG-0001.md`

ВАЖНО:
- формат записи (schema) неизменен
- ссылки на AUDIT_ID должны быть стабильны

(Выбор конкретного storage-формата фиксируется в README Governance.)

---

## WHEN TO WRITE (TRIGGERS)

Запись делается **всегда**:

1) После прохождения governance gates G1–G7 (см. Change Control)
2) Перед постановкой `LOCK: FIXED` на набор изменений
3) После любого MAJOR изменения
4) После любой правки INDEX
5) После обнаружения и решения overlap/cycle (dependency decisions)

---

## PROCEDURE (HOW TO LOG A CHANGE)

1) Получить CHG пакет (из Change Control)
2) Привязать отчёты:
   - CR (Consistency Report), если был аудит
   - DG (Dependency Graph), если менялись связи/контракты
3) Заполнить AUDIT_ENTRY schema
4) Проверить минимальные поля (см. checklist)
5) Записать entry в audit storage
6) Сослаться на AUDIT_ID в:
   - CHG packet
   - (опционально) в touched files в блоке “LAST_AUDIT” (если у тебя такой стандарт появится)

---

## VALIDATION CHECKLIST (AUDIT ENTRY MUST PASS)

- AL1: есть AUDIT_ID и дата
- AL2: перечислены FILES_TOUCHED (явно)
- AL3: есть решение APPROVAL (кто и что решил)
- AL4: указана версия before/after
- AL5: указано LOCK_DECISION и причина
- AL6: если менялись зависимости — есть DG ссылка/edge notes
- AL7: если был аудит целостности — есть CR ссылка/вердикт

---

## SEVERITY / TRACEABILITY RULES

- PATCH может логироваться “коротко”, но schema всё равно обязателен
- MINOR и MAJOR должны включать dependency + consistency refs (если применимо)
- Любая WAIVER запись должна иметь условия и срок (expiry)

---

## INTEGRATION (HOW IT CONNECTS)

- Change Control (00/04):
  - audit запись — обязательный шаг перед lock (G6)
- Versioning & Memory (00/10):
  - audit фиксирует before/after версии
- Consistency (00/05):
  - audit хранит вердикт и CR ссылку
- Dependency Registry (00/06):
  - audit хранит DG ссылку и edge notes
- Canon Authority (00/02):
  - audit хранит финальное решение (approve/reject)

---

## FAILURE MODES (WHAT BREAKS SYSTEM TRUST)

- изменения без AUDIT_ID → “не существует” для канона
- файловые правки без FILES_TOUCHED → невозможно восстановить историю
- нет версии before/after → невозможно сравнивать состояния
- нет решения approval → канон становится “самопальным”

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
