# GOVERNANCE ENGINES — REALM README (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: REALM_README
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.ENG.GOV.REALM.001
OWNER: SYSTEM
ROLE: Family law + boundaries + mandatory workflow for canon governance. Explains how governance engines work together (no existence authority).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "README made etalon: strict boundaries, shared vocabulary, mandatory governance pipeline, storage targets, and anti-duplication laws."
- REASON: "Stop scaffold drift. Governance family must be executable as a deterministic system."
- IMPACT: "Governance usage becomes unambiguous and consistent across the repo."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.REALM.003

---

## 0) PURPOSE (LAW)

Этот README описывает семейство `00_GOVERNANCE_ENGINES`:
- **что оно такое**
- **что оно контролирует**
- **как им пользоваться**
- **где хранятся записи**

IMPORTANT:
- README **не вводит** новые сущности в канон.
- Состав семейства (что существует) определяется только глобальными индексами/реестрами ENG.

---

## 1) FAMILY MISSION (ONE SENTENCE)

Governance Engines = система, которая превращает изменения канона в **управляемый, проверяемый и воспроизводимый** процесс.

---

## 2) WHAT THIS FAMILY OWNS (STRICT)

OWNED (в зоне ответственности):
- Canon change pipeline (пакет изменений + гейты + закрытие)
- Canon decision gate (ACCEPT/REJECT/CONDITIONAL)
- Approval procedure (quorum/veto/emergency)
- Audit (append-only след)
- Consistency (проверка целостности канона)
- Scope impact (blast-radius + required updates + migration law)
- Risk safety (blockers + mitigation)
- Dependency registry (no hidden deps)
- Rule hierarchy (resolution of conflicts)
- Versioning & memory (bump rules + memory packs + snapshots)

NOT OWNED (запрещено забирать сюда):
- создание контента домена (narrative/character/world)
- производство медиаконтента как результата (визуал/звук/монтаж как творчество)
- фактчекинг реальности/науки (это валидаторы/исследовательские движки)
- хранение сущностей проекта (это Projects/Databases)

---

## 3) NON-NEGOTIABLE META RULES (FAMILY)

### 3.1 RAW-ONLY LINK LAW
Внутри governance-доков любые переходы должны быть **raw-links**.
Никаких “кликабельных путей” как навигации в смысле SoT.

### 3.2 HEADER SINGLE-TRUTH LAW
STATUS/LOCK/VERSION/UID/OWNER/ROLE существуют **только в шапке**.
Запрещено дублировать эти поля внизу файла.

### 3.3 NO HIDDEN AUTHORITY LAW
Ни один документ семьи не может объявлять себя “единственной точкой истины о существовании” вне своего домена.
Existence определяется каноническими индексами/реестрами верхнего уровня.

---

## 4) SHARED ARTIFACT VOCABULARY (CANON)

Эти имена артефактов используются одинаково во всех governance engines.

### INPUT ARTIFACTS
- CHANGE_PROPOSAL
- CHANGE_NOTE
- TARGET_LIST
- AFFECTED_FILES_LIST
- DIFF_SUMMARY
- CHANGE_PACKAGE_RECORD
- DECISION_RECORD
- APPROVAL_RECORD
- CONSISTENCY_REPORT
- SCOPE_IMPACT_REPORT
- SAFETY_ASSESSMENT_REPORT
- DEPENDENCY_DECLARATIONS
- DEPENDENCY_RECORDS
- MIGRATION_MAP
- REQUIRED_UPDATES_LIST
- VERSION_DECISION_RECORD
- COMPATIBILITY_CONTRACT
- SNAPSHOT_RECORD
- MEMORY_PACK_RECORD

### OUTPUT ARTIFACTS
- AUDIT_RECORD
- DECISION_RECORD
- APPROVAL_RECORD
- CONSISTENCY_REPORT
- SCOPE_IMPACT_REPORT
- SAFETY_ASSESSMENT_REPORT
- DEPENDENCY_VALIDATION_REPORT
- VERSION_DECISION_RECORD
- MEMORY_PACK_RECORD
- SNAPSHOT_RECORD

Hard rule:
- если движок вводит новый термин — он должен быть согласован со словарём и добавлен через change pipeline.

---

## 5) MANDATORY GOVERNANCE PIPELINE (CANON FLOW)

Стандартный порядок для canon-impacting change:

1) **Change Control** — формирует change package и гейты
2) **Rule Hierarchy** — определяет приоритеты, фиксирует конфликт/резолв (если есть)
3) **Scope Impact** — required updates + migration map (если структурно)
4) **Risk Safety** — blockers + mitigation + safety decision
5) **Decision Approval** — процедура утверждения (quorum/veto)
6) **Canon Authority** — финальное решение (ACCEPT/REJECT/CONDITIONAL)
7) **Apply** — применение изменений строго в рамках пакета
8) **Audit Log** — запись APPLY + CLOSE (append-only)
9) **Consistency (POST-VERIFY)** — PASS как условие закрытия
10) **Versioning & Memory** — version decision + memory pack (+ snapshot при MAJOR)

### Close rule (hard)
Canon-impacting change считается “закрытым” только если есть:
- DECISION_RECORD
- AUDIT_RECORD (APPLY + CLOSE)
- CONSISTENCY_REPORT (POST-VERIFY PASS / PASS_WITH_WARN policy)
- MEMORY_PACK_RECORD

---

## 6) STORAGE TARGETS (WHERE RECORDS LIVE)

- AUDIT storage:
  `99_LOGS/LOG__AUDIT.md`

- CHANGES storage (packages / dependency edges / exception records):
  `99_LOGS/LOG__CHANGES.md`

Если нужно новое хранилище — это отдельное canon-impacting изменение.

---

## 7) QUALITY BAR (ETALON DEFINITION)

Governance engine считается “эталонным”, только если:
- полная шапка + UID не пустой
- mini-contract заполнен реальными артефактами
- определены modes + gates + severity/result mapping
- определены canonical output formats (records/reports)
- есть примеры good/bad + edge cases
- raw-only references
- нет дублирования authority/existence законов

---

## 8) REFERENCES (RAW ONLY)

ENG index (roster):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

Audit log storage:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md

Changes log storage:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md

--- END.
