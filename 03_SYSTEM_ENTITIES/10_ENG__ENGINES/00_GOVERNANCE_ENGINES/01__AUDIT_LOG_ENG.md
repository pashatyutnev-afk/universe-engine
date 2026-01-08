# AUDIT LOG ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.GOV.AUDIT_LOG.001
OWNER: SYSTEM
ROLE: Canon audit recorder (append-only). Creates the factual trail for every canon-impacting change event.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Audit Log Engine upgraded from scaffold to fully specified canonical recorder (formats, gates, modes, integrations)."
- REASON: "Governance family must be executable as a deterministic process, not just a description."
- IMPACT: "Every canon-impacting change becomes traceable, reproducible, and enforceable across layers."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.AUDIT.001

---

## 0) PURPOSE (LAW)

Audit Log Engine фиксирует **факт** изменения канона: что произошло, когда, кем, что затронуто, какой change-id, какая decision-id, какие артефакты созданы.

Audit Log:
- не обсуждает “правильно/неправильно” (это Authority/Decision)
- не применяет изменения (это Change Control)
- не проверяет консистентность (это Consistency)
- **только записывает факт** по строгому формату и запрещает “тихие” изменения.

Primary outcome:
- для каждого canon-impacting изменения существует AUDIT_RECORD.

Non-goals (hard):
- не является changelog смыслов (это `LOG__CHANGES.md`)
- не является release log (это DB release log, если используется)
- не хранит длинные диффы/тексты (только refs)

---

## 1) BOUNDARY (ANTI-DUPLICATION)

OWNED HERE:
- единый формат AUDIT_RECORD
- правило append-only (не редактировать прошлое)
- требования “без audit записи изменение считается незавершённым”
- минимальные ссылки/refs на Decision/Package/Verify

NOT OWNED HERE:
- approve/reject (Canon Authority)
- процедуры апрува/роли/кворум (Decision Approval)
- упаковка стадий изменения (Change Control)
- пост-валидация целостности (Consistency)
- версионирование (Versioning & Memory)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- DECISION_RECORD
- CHANGE_PACKAGE_RECORD
- CONSISTENCY_REPORT              # required for “CLOSE” audit events (see modes)

PRODUCES:
- AUDIT_RECORD

DEPENDS_ON:
- []                              # audit must be able to run standalone

OUTPUT_TARGET:
- 99_LOGS/LOG__AUDIT.md

---

## 3) CANON DEFINITIONS (STRICT)

### 3.1 Canon-impacting change
Любое изменение считается canon-impacting, если затрагивает хотя бы одно:
- любой файл с LOCK: FIXED
- любой canonical index / registry / law
- перемещение/переименование/удаление канонического файла
- изменения, которые меняют навигацию (raw-links) или existence rules
- изменения контрактов движков (mini-contract)

Если canon-impacting = YES, audit запись обязательна.

### 3.2 Append-only law
- прошлые AUDIT_RECORD не редактируются
- если нужна коррекция — создаётся новый AUDIT_RECORD с `ACTION: CORRECT` и ссылкой на RECORD_ID, который корректируется

---

## 4) OPERATION MODES (MANDATORY)

Audit Engine работает в трёх режимах.

### Mode A — APPLY AUDIT (change applied)
Когда: сразу после применения изменения (stage S3/S4 пайплайна).
Цель: зафиксировать факт “изменение применено”.

Required links:
- CHANGE_ID
- CHANGE_PACKAGE_ID
- DECISION_ID (для canon-impacting)
- AFFECTED list

### Mode B — CLOSE AUDIT (change closed)
Когда: после POST-VERIFY PASS и закрытия change package (stage S6).
Цель: зафиксировать факт “изменение закрыто корректно”.

Required links:
- CHANGE_ID
- CHANGE_PACKAGE_ID
- CONSISTENCY_REPORT_ID (must be PASS or PASS_WITH_WARN)
- VERSION_BUMP_PLAN ref (if used)

### Mode C — CORRECTION AUDIT (audit correction)
Когда: если нужно исправить неправильную audit запись.
Цель: не редактировать историю, а добавлять корректировку.

Required links:
- CORRECTS_RECORD_ID
- WHY
- corrected fields

Hard rule:
- закрывать изменения без Mode B записи запрещено.

---

## 5) HARD GATES (ENFORCEMENT)

- G1 CHANGE_NOTE must contain:
  DATE, TYPE, SUMMARY, REASON, IMPACT, CHANGE_ID

- G2 AFFECTED_FILES_LIST must be concrete:
  each item has ITEM + PATH, optional UID

- G3 Canon-impacting change requires DECISION_ID:
  missing DECISION_ID => FAIL

- G4 Mode B requires CONSISTENCY_REPORT PASS (or PASS_WITH_WARN):
  missing/FAIL => FAIL

- G5 Append-only:
  editing old record is forbidden; corrections are Mode C

- G6 RAW-only references:
  if record includes any link, it must be raw-link (no github ui links)

- G7 Identity coherence:
  CHANGE_ID must be the same across CHANGE_NOTE / DECISION_RECORD / CHANGE_PACKAGE_RECORD referenced by this audit

---

## 6) OUTPUT FORM — AUDIT_RECORD (CANON)

### 6.1 Minimal record (required)
AUDIT_RECORD is a block with strict fields:

AUDIT_RECORD:
- RECORD_ID: UE.AUDIT.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- TIME: HH:MM                      # optional if you don't track time; keep field but allow "NA"
- MODE: APPLY|CLOSE|CORRECT
- ACTION: ADD|EDIT|MOVE|RENAME|DELETE|DEPRECATE|CORRECT
- AUTHOR: <string>
- CHANGE_ID: <UE.CHG...>
- CHANGE_TYPE: PATCH|MINOR|MAJOR|HARD-RESET|HOTFIX|DEPRECATION|RENAMING|MOVE|DELETE|ADD
- CANON_IMPACT: YES|NO
- SCOPE: <layers/families short>
- AFFECTED:
  - ITEM: DOC|INDEX|TEMPLATE|ENGINE|REGISTRY|MAP
    PATH: <repo path>
    UID: <optional uid>
- DECISION_ID: <required if CANON_IMPACT=YES>
- CHANGE_PACKAGE_ID: <required if CANON_IMPACT=YES>
- CONSISTENCY_REPORT_ID: <required if MODE=CLOSE>
- SUMMARY: <one line>
- NOTES: <optional>

### 6.2 Rules
- RECORD_ID must be unique.
- NNN increments per day.
- If TIME unknown: TIME: NA
- AFFECTED list must not be empty.

---

## 7) RELATIONSHIP TO OTHER GOVERNANCE ENGINES (INTEGRATION)

This engine is mandatory for:
- Change Control:
  - must call Mode A after apply
  - must call Mode B after close
- Canon Authority:
  - decision record must be referenced by audit when canon-impacting
- Versioning & Memory:
  - may consume audit record ids as part of memory package pointer
- Consistency:
  - must provide report id for Mode B

---

## 8) GOOD / BAD EXAMPLES

### 8.1 GOOD — APPLY + CLOSE
APPLY record:
AUDIT_RECORD:
- RECORD_ID: UE.AUDIT.2026-01-08.001
- DATE: 2026-01-08
- TIME: 14:20
- MODE: APPLY
- ACTION: EDIT
- AUTHOR: SYSTEM
- CHANGE_ID: UE.CHG.2026-01-08.GOV.104
- CHANGE_TYPE: MAJOR
- CANON_IMPACT: YES
- SCOPE: 03_SYSTEM_ENTITIES/ENG/00_GOVERNANCE_ENGINES
- AFFECTED:
  - ITEM: ENGINE
    PATH: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
    UID: UE.ENG.GOV.CHANGE_CONTROL.001
- DECISION_ID: UE.DEC.2026-01-08.002
- CHANGE_PACKAGE_ID: UE.PKG.2026-01-08.001
- SUMMARY: "Applied governance change package for Change Control engine."
- NOTES: "Applied via canonical pipeline."

CLOSE record:
AUDIT_RECORD:
- RECORD_ID: UE.AUDIT.2026-01-08.002
- DATE: 2026-01-08
- TIME: 15:10
- MODE: CLOSE
- ACTION: EDIT
- AUTHOR: SYSTEM
- CHANGE_ID: UE.CHG.2026-01-08.GOV.104
- CHANGE_TYPE: MAJOR
- CANON_IMPACT: YES
- SCOPE: 03_SYSTEM_ENTITIES/ENG/00_GOVERNANCE_ENGINES
- AFFECTED:
  - ITEM: ENGINE
    PATH: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
    UID: UE.ENG.GOV.CHANGE_CONTROL.001
- DECISION_ID: UE.DEC.2026-01-08.002
- CHANGE_PACKAGE_ID: UE.PKG.2026-01-08.001
- CONSISTENCY_REPORT_ID: UE.CNS.2026-01-08.001
- SUMMARY: "Closed change package after consistency PASS."
- NOTES: "Post-verify completed."

### 8.2 BAD — no decision
- CANON_IMPACT: YES but DECISION_ID missing → FAIL (G3)

### 8.3 BAD — editing old record
- Someone rewrites UE.AUDIT.2026-01-08.001 directly → forbidden (G5)
Fix:
- create MODE: CORRECT record.

---

## 9) FAILURE MODES & EDGE CASES

### 9.1 Emergency hotfix
Allowed to create APPLY audit first, but:
- must create DECISION_ID (emergency D4) and attach later
- must create CLOSE record after consistency verification
Otherwise change remains “open”.

### 9.2 Rename/move
AFFECTED must include:
- OLD_PATH and NEW_PATH info in NOTES
- two affected entries allowed (old path as MAP record + new path as DOC record)

### 9.3 Multiple files in one change
AFFECTED list includes all touched canonical items.

### 9.4 Partial rollback
If rollback happened:
- record ACTION: EDIT with NOTES explaining rollback
- create separate change-id if rollback is a separate canon-impacting change (recommended)

---

## 10) REFERENCES (RAW ONLY)

LOGS:
- RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md

GOVERNANCE engines:
- Change Control — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- Canon Authority — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- Consistency — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- Versioning & Memory — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

--- END.
