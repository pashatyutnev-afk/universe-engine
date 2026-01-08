# AUDIT LOG ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.AUDIT_LOG.001>
OWNER: SYSTEM
ROLE: Mandatory audit recorder for any canon-impacting change (creates immutable change records)
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок — “чёрный ящик” канона: **любое изменение канона** должно оставлять **audit-след**.

What this engine is for:
- фиксировать любые canon-impacting изменения (индексы, правила, шаблоны, реестры, движки)
- создавать единый формат записи (audit record), который можно проверять и ссылать дальше
- обеспечивать прослеживаемость: WHAT/WHY/WHO/IMPACT/WHERE

Primary outcome:
- На каждую канон-правку существует audit record с обязательными полями.

Non-goals (hard):
- НЕ принимает решения “разрешить/запретить” (это Canon Authority / Change Control)
- НЕ правит файлы за пользователя (он только записывает факт)
- НЕ создаёт доменный контент (сюжет/персонажи/мир) и не делает production outputs

---

## 1) BOUNDARY (ANTI-DUPLICATION)

### 1.1 Owned area (this engine owns)
- единый формат audit записи
- правило “no silent change”
- минимальные требования к полям аудита
- политика неизменяемости записей (immutability intent)

### 1.2 Forbidden overlap (this engine must NOT do)
- не заменяет Change Control (планы/процессы) — только логирует
- не заменяет Canon Authority (approve/reject) — только логирует
- не заменяет Versioning & Memory (своды, история версий) — только логирует

### 1.3 Interface contract (what it touches)
- Reads: change intent/notes, affected files list, diffs summary, decision refs (optional)
- Requires: наличие обязательных полей audit записи
- Produces: audit record artifact
- Never: “тихо” меняет канон без фиксации записи

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: CHANGE_NOTE>              # краткая фиксация изменения (summary/reason/impact)
- <ARTIFACT: AFFECTED_FILES_LIST>      # список файлов/объектов затронутых правкой
- <ARTIFACT: DECISION_RECORD?>         # опционально: ссылка/UID решения (approve/reject)
- <ARTIFACT: DIFF_SUMMARY?>            # опционально: краткое описание диффа/патча

PRODUCES:
- <ARTIFACT: AUDIT_RECORD>             # обязательная запись аудита
- <ARTIFACT: AUDIT_INDEX_UPDATE?>      # опционально: указатель/свод по последним записям

DEPENDS_ON:
- []  # Audit Log должен быть минимально зависимым
# (если очень надо — допускается зависеть от Change Control, но это должно быть явным)

OUTPUT_TARGET:
- `99_LOGS/LOG__AUDIT.md`  # или другой канонический audit storage target, если у тебя иной

---

## 3) OPERATION MODEL (HOW IT WORKS)

### 3.1 Trigger (when to run)
Запускается всегда, когда:
- изменён любой канонический индекс/реестр
- добавлен/удалён/переименован канонический файл
- изменены STATUS/LOCK/VERSION/UID в каноническом документе
- добавлена/изменена зависимость движков/пайплайнов
- выполнен approve/reject канон-решения (фиксируем факт решения)

### 3.2 Inputs (minimal required)
Минимум для записи:
- DATE (или timestamp)
- CHANGE_TYPE
- AFFECTED (что изменили)
- SUMMARY
- REASON
- IMPACT
- AUTHOR/OWNER (кто сделал/инициировал)

### 3.3 Steps (deterministic pipeline)
1) Collect inputs (change note + affected files)
2) Validate minimum fields (см. Hard Gates)
3) Normalize identifiers:
   - для каждого affected объекта: PATH + (если есть) UID
4) Write audit record in standard format
5) (Optional) Update audit index/summary (если используется)

### 3.4 Output semantics
- PASS → создаётся AUDIT_RECORD
- FAIL → запись не создаётся, возвращается “BLOCK” как результат движка (через violation record у других движков; этот движок сам не владеет violation формой)

---

## 4) HARD GATES (ENFORCEMENT)

> Если любой HARD gate провален → audit запись НЕ считается валидной (движок возвращает FAIL).

- G1: Required fields present  
  CHECK: DATE/CHANGE_TYPE/AFFECTED/SUMMARY/REASON/IMPACT/AUTHOR присутствуют  
  FAIL: missing fields  
  FIX: заполнить обязательные поля

- G2: AFFECTED list is concrete  
  CHECK: каждый affected элемент имеет PATH и тип (DOC/INDEX/TEMPLATE/ENGINE/REGISTRY)  
  FAIL: “что-то поменялось” без конкретики  
  FIX: перечислить файлы/объекты

- G3: Canon-impact declared  
  CHECK: IMPACT явно говорит: canon-impacting или non-canon  
  FAIL: непонятно, трогали ли канон  
  FIX: указать impact и scope

- G4: No silent change linkability  
  CHECK: запись содержит стабильные ссылки-идентификаторы (PATH + optional UID)  
  FAIL: невозможно сослаться на запись  
  FIX: добавить идентификаторы

- G5: Immutability intent  
  CHECK: запись помечена как “append-only” по смыслу (не переписывать старые записи, только добавлять новые)  
  FAIL: попытка “переписать прошлое”  
  FIX: создать новую запись с correction_note вместо изменения старой

---

## 5) OUTPUT ARTIFACTS (STANDARD FORMS)

### 5.1 AUDIT RECORD — Canon Format (REQUIRED)
RECORD_FORMAT (Markdown, append-only):

- RECORD_ID: <incremental or uid-like token>
- DATE: YYYY-MM-DD (or ISO timestamp)
- CHANGE_TYPE: <PATCH|MINOR|MAJOR|HARD-RESET|HOTFIX|DEPRECATION|RENAMING|MOVE|DELETE|ADD>
- AUTHOR: <name/role>
- SCOPE: <which layer/family>
- AFFECTED:
  - ITEM: <DOC|INDEX|TEMPLATE|ENGINE|REGISTRY|MAP>
    PATH: <repo path>
    UID: <optional>
- SUMMARY: <one-liner>
- REASON: <why>
- IMPACT: <what changes for users/system>
- DECISION_REF: <optional UID or pointer to decision record>
- NOTES: <optional>

### 5.2 AUDIT INDEX UPDATE (OPTIONAL)
Если ты ведёшь оглавление audit записей — обновлять “свод” можно отдельным артефактом, но это не обязательно для v1.

---

## 6) EXAMPLES (GOOD / BAD)

### 6.1 Good example
Scenario:
- Поменяли шаблон движка governance и подняли версию.

Audit record (пример):
- RECORD_ID: UE.AUDIT.2026-01-08.001
- DATE: 2026-01-08
- CHANGE_TYPE: PATCH
- AUTHOR: SYSTEM
- SCOPE: 03_SYSTEM_ENTITIES / 00_GOVERNANCE_ENGINES
- AFFECTED:
  - ITEM: TEMPLATE
    PATH: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md
    UID: <UE.TPL.ENG.GOV.ENGINE.001>
- SUMMARY: “Refined hard gates + normalized audit record format”
- REASON: “Needed deterministic governance enforcement”
- IMPACT: “All governance engines now share identical audit semantics”
- DECISION_REF: <optional>
- NOTES: “No behavior change beyond documentation contract tightening”

Why passes:
- есть конкретный affected + поля заполнены + impact понятен

### 6.2 Bad example
Scenario:
- “Почистил кучу файлов и индексы” без списка.

FAIL reasons:
- нет AFFECTED списка → G2 fail
- нет impact → G3 fail

Fix:
- перечислить файлы, типы, summary/reason/impact

---

## 7) FAILURE MODES & EDGE CASES

- Partial update: индекс обновлён, но файл отсутствует  
  → Audit record можно создать, но IMPACT должен явно говорить “broken state detected”; дальше Change Control решает.

- Rename/move: файл переехал  
  → AFFECTED должен содержать OLD_PATH и NEW_PATH (в NOTES или отдельными item)

- Delete: файл удалён  
  → AFFECTED содержит PATH + CHANGE_TYPE: DELETE + REASON (почему)

- Correction: нашли ошибку в прошлой записи  
  → НЕ правим старую запись. Создаём новую с CHANGE_TYPE: HOTFIX + NOTES: “Correction for RECORD_ID …”

---

## 8) REL / XREF (UID-FIRST)

REL:
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.###> | WHY: audit logs change control actions
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CANON_AUTHORITY.###> | WHY: audit logs approval decisions
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.VERSIONING_MEMORY.###> | WHY: audit provides ground truth for memory/version summaries

XREF:
- XREF_UID: <UE.ENG.GOV.DEPENDENCY_REGISTRY.###> | WHY: dependency changes require audit records

RULE:
- RAW links держим в INDEX/REGISTRY.
- Здесь — UID-first, чтобы не плодить “второй индекс”.

--- END.
