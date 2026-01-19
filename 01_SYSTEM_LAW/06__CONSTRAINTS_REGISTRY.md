# 06__CONSTRAINTS_REGISTRY

FILE: 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY (LAW)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.LAW.CONSTRAINTS.REG.001
OWNER: SYSTEM
ROLE: Canonical registry of runtime constraints and hard-stop rules. Used by CTL/VAL/QA to block unsafe or non-compliant execution.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Registry populated with hard constraints for RAW-only nav, snapshot refresh, boot-first, single-entrypoint routing, artifact-only output, and stop conditions."
- REASON: "Without a filled constraints registry, CTL/VAL cannot deterministically enforce system laws."
- IMPACT: "Runtime enforcement becomes explicit: each constraint has an ID, trigger, violation format, and required fix."

---

## 0) PURPOSE (LAW)
Этот реестр фиксирует **жёсткие ограничения** (constraints), которые:
- обязаны соблюдаться во всех рантайм-запусках,
- используются CTL/VAL/QA для блокировок и фиксации нарушений,
- определяют **единственные** стоп-условия рантайма.

---

## 1) DEFINITIONS
- **Constraint** — жёсткое правило “нельзя/обязан”.
- **Hard Stop** — условие, при котором выполнение прекращается.
- **Trigger** — что считается нарушением.
- **Required Fix** — что надо сделать, чтобы продолжить.

---

## 2) REGISTRY FORMAT (HOW TO READ)
Каждая запись:
- CONSTRAINT_ID: уникальный ID ограничения
- NAME: коротко
- CLASS: NAV / BOOT / ROUTING / OUTPUT / CHANGE / SAFETY
- SEVERITY: S0 (hard stop) / S1 (block) / S2 (warn)
- STATEMENT (LAW): формулировка
- TRIGGER: событие нарушения
- REQUIRED FIX: что исправить
- ENFORCEMENT:
  - CTL: чем блокируется
  - VAL: какое нарушение фиксируется
  - QA: какой гейт подтверждает
- EVIDENCE REQUIRED: что должно быть показано/указано в отчёте рантайма

---

## 3) CANONICAL CONSTRAINTS (REGISTRY)

### C-NAV-001 — RAW-only Navigation (ABSOLUTE)
- CONSTRAINT_ID: C-NAV-001
- NAME: RAW-only navigation
- CLASS: NAV
- SEVERITY: S0
- STATEMENT (LAW):
  - Использовать **только RAW ссылки**, которые присутствуют:
    - в ROOT LINK BASE (ROOT-INDEX), или
    - в сообщении пользователя.
  - Запрещено угадывать пути/файлы/URL вне базы.
- TRIGGER:
  - Попытка открыть/сослаться на ресурс, которого нет в ROOT-INDEX и не прислал пользователь.
- REQUIRED FIX:
  - STOP: RAW missing.
  - Запросить у пользователя RAW ссылку или обновлённый ROOT-INDEX.
- ENFORCEMENT:
  - CTL: READINESS_CHECK_CTL блокирует выполнение без подтверждённых RAW.
  - VAL: VAL_VIOLATION_RECORD “RAW_OUTSIDE_LINK_BASE”.
  - QA: QA_GATE “NAV_COMPLIANCE_PASS”.
- EVIDENCE REQUIRED:
  - В `RESOURCES USED` показать RAW ссылки + “MARKER FOUND”.

### C-NAV-002 — Link Base Snapshot / Manual Refresh Only
- CONSTRAINT_ID: C-NAV-002
- NAME: Snapshot-only link base
- CLASS: NAV
- SEVERITY: S0
- STATEMENT (LAW):
  - ROOT-INDEX — это **снимок**. Он **не обновляется автоматически**.
  - Любые новые ссылки считаются действительными только если:
    - пользователь прислал обновлённый ROOT-INDEX, или
    - пользователь прислал RAW ссылку в чат.
- TRIGGER:
  - Опора на “онлайн-репозиторий” как на обновляемую базу без явного refresh от пользователя.
- REQUIRED FIX:
  - STOP: marker not confirmed (если попытка продолжить без ссылок).
  - Продолжить только после получения обновлённого ROOT-INDEX/RAW ссылок.
- ENFORCEMENT:
  - CTL: блок “SNAPSHOT_REFRESH_REQUIRED”.
  - VAL: “SNAPSHOT_REFRESH_VIOLATION”.
  - QA: “SNAPSHOT_POLICY_PASS”.
- EVIDENCE REQUIRED:
  - В `RESOURCES USED` указать источник: ROOT-INDEX (version/date) или user-provided RAW.

### C-BOOT-001 — Boot-first Discipline
- CONSTRAINT_ID: C-BOOT-001
- NAME: Boot-first
- CLASS: BOOT
- SEVERITY: S0
- STATEMENT (LAW):
  - Нельзя выполнять задачу до завершения BOOT SEQUENCE.
- TRIGGER:
  - Любое действие “исполнения” до подтверждения BOOT COMPLETE MARKER.
- REQUIRED FIX:
  - STOP: marker not confirmed.
  - Выполнить boot load по порядку и подтвердить маркеры.
- ENFORCEMENT:
  - CTL: READINESS_CHECK_CTL требует BOOT markers.
  - VAL: “BOOT_NOT_COMPLETED”.
  - QA: “BOOT_COMPLETION_GATE”.
- EVIDENCE REQUIRED:
  - В `RESOURCES USED` перечислить 4 группы boot docs + “MARKER FOUND” по каждому.

### C-BOOT-002 — Boot Complete Marker Required
- CONSTRAINT_ID: C-BOOT-002
- NAME: Boot complete marker
- CLASS: BOOT
- SEVERITY: S0
- STATEMENT (LAW):
  - BOOT завершён только если явно подтверждено:
    - Naming + UID rules loaded
    - Doc Control + Index structure loaded
    - Entity model loaded
    - KB entrypoint loaded
- TRIGGER:
  - Отсутствует подтверждение хотя бы одного пункта.
- REQUIRED FIX:
  - STOP: marker not confirmed.
- ENFORCEMENT:
  - CTL: “BOOT_MARKER_MISSING”.
  - VAL: “BOOT_MARKER_NOT_CONFIRMED”.
  - QA: “BOOT_MARKER_AUDIT”.
- EVIDENCE REQUIRED:
  - Показать ссылки + найденные маркеры/разделы (название секции) в каждом документе.

### C-ROUTE-001 — Single Entry Point (START_UNIVERSE_ENGINE only)
- CONSTRAINT_ID: C-ROUTE-001
- NAME: Single entrypoint command
- CLASS: ROUTING
- SEVERITY: S0
- STATEMENT (LAW):
  - Любая задача запускается только командой `START_UNIVERSE_ENGINE`.
  - ROOT-INDEX не выполняет задач.
- TRIGGER:
  - Попытка трактовать ROOT-INDEX как выполнение работы, или выполнение без старта.
- REQUIRED FIX:
  - STOP: input absent.
  - Пользователь должен запустить `START_UNIVERSE_ENGINE` + дать TASK.
- ENFORCEMENT:
  - CTL: “ENTRYPOINT_REQUIRED”.
  - VAL: “ENTRYPOINT_BYPASS”.
  - QA: “ENTRYPOINT_COMPLIANCE”.
- EVIDENCE REQUIRED:
  - Зафиксированная команда + TASK.

### C-ROUTE-002 — Mandatory Dispatcher (Top Governance SPC)
- CONSTRAINT_ID: C-ROUTE-002
- NAME: Mandatory top dispatcher
- CLASS: ROUTING
- SEVERITY: S1
- STATEMENT (LAW):
  - Любая задача начинается у `MACHINE_ARCHITECT_SPC`.
- TRIGGER:
  - Попытка сразу “делать” без фиксации intake/routing.
- REQUIRED FIX:
  - Пройти INTAKE (goal/scope/inputs/artifact type) и ROUTING (назначение сущностей).
- ENFORCEMENT:
  - CTL: “DISPATCHER_INTAKE_REQUIRED”.
  - VAL: “NO_DISPATCHER_ROUTE”.
  - QA: “ROUTING_TRACE_PASS”.
- EVIDENCE REQUIRED:
  - В `DELIVERABLES` наличие Task Spec и Route Plan.

### C-ROUTE-003 — Mandatory Finish Chain (Verification)
- CONSTRAINT_ID: C-ROUTE-003
- NAME: Mandatory finish chain
- CLASS: ROUTING
- SEVERITY: S1
- STATEMENT (LAW):
  - Завершение только через цепочку:
    - READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff.
- TRIGGER:
  - Выдача результата без гейтов/валидации/док-контроля.
- REQUIRED FIX:
  - Прогнать result через гейты и приложить evidence.
- ENFORCEMENT:
  - CTL: “FINISH_CHAIN_REQUIRED”.
  - VAL: “UNVERIFIED_OUTPUT”.
  - QA: “ACCEPTANCE_GATE_PASS”.
- EVIDENCE REQUIRED:
  - Перечень пройденных гейтов + что именно проверено.

### C-OUT-001 — Output Must Be Artifact Doc (No Naked Content)
- CONSTRAINT_ID: C-OUT-001
- NAME: Artifact-only output
- CLASS: OUTPUT
- SEVERITY: S0
- STATEMENT (LAW):
  - Любой результат оформляется как артефакт-документ по стандартам/шаблонам.
- TRIGGER:
  - Ответ содержит “контент” без структуры артефакта (без DOC_CONTROL, без типа из registry).
- REQUIRED FIX:
  - Переформатировать в корректный артефакт (TRACK_CARD / PROMPT / OUTPUT_PACK / LAW_DOC / etc).
- ENFORCEMENT:
  - CTL: блок “ARTIFACT_SCHEMA_REQUIRED”.
  - VAL: “NAKED_CONTENT_OUTPUT”.
  - QA: “ARTIFACT_SCHEMA_PASS”.
- EVIDENCE REQUIRED:
  - Указать ARTIFACT_TYPE + соответствие MIN_SCHEMA.

### C-OUT-002 — Template First (If No Template → GAP)
- CONSTRAINT_ID: C-OUT-002
- NAME: Template gating
- CLASS: OUTPUT
- SEVERITY: S1
- STATEMENT (LAW):
  - Если нет подходящего шаблона/сущности — сначала GAP → предложение создания → полный файл по TEMPLATE.
- TRIGGER:
  - “Придумали формат” без фиксации GAP и без шаблона.
- REQUIRED FIX:
  - Сгенерировать сущность/шаблон по template realm, затем продолжить.
- ENFORCEMENT:
  - CTL: “MISSING_TEMPLATE_GAP_REQUIRED”.
  - VAL: “TEMPLATE_BYPASS”.
  - QA: “TEMPLATE_COMPLIANCE”.
- EVIDENCE REQUIRED:
  - GAP statement + ссылка на template used.

### C-CHG-001 — Change Control Required for Law/Standards
- CONSTRAINT_ID: C-CHG-001
- NAME: Change management for laws/standards
- CLASS: CHANGE
- SEVERITY: S1
- STATEMENT (LAW):
  - Любое изменение LAW/STANDARD/TEMPLATE должно иметь CHANGE_NOTE + CHANGE_ID.
- TRIGGER:
  - Изменён документ без CHANGE_NOTE/CHANGE_ID.
- REQUIRED FIX:
  - Добавить CHANGE_NOTE и CHANGE_ID по правилам versioning.
- ENFORCEMENT:
  - CTL: “CHANGE_NOTE_REQUIRED”.
  - VAL: “MISSING_CHANGE_ID”.
  - QA: “CHANGELOG_AUDIT_PASS”.
- EVIDENCE REQUIRED:
  - CHANGE_NOTE блок.

### C-STOP-001 — Stop Conditions Are Limited
- CONSTRAINT_ID: C-STOP-001
- NAME: Only defined stop conditions
- CLASS: SAFETY
- SEVERITY: S0
- STATEMENT (LAW):
  - Стоп возможен только по:
    - RAW missing
    - marker not confirmed
    - input absent
- TRIGGER:
  - “Остановился потому что так решил” или любые другие причины.
- REQUIRED FIX:
  - Переформулировать в один из трёх стоп-кодов или продолжить.
- ENFORCEMENT:
  - CTL: “STOP_REASON_INVALID”.
  - VAL: “INVALID_STOP_REASON”.
  - QA: “RUN_TRACE_INTEGRITY”.
- EVIDENCE REQUIRED:
  - Явный стоп-код.

### C-CHAT-001 — Mandatory Runtime Output Format
- CONSTRAINT_ID: C-CHAT-001
- NAME: Mandatory chat contract
- CLASS: OUTPUT
- SEVERITY: S1
- STATEMENT (LAW):
  - Каждый рантайм-ответ обязан быть строго:
    - MODE
    - RESOURCES USED (USING RAW + MARKER FOUND)
    - DELIVERABLES
    - GATES
- TRIGGER:
  - Ответ без этого формата.
- REQUIRED FIX:
  - Переформатировать ответ.
- ENFORCEMENT:
  - CTL: “CHAT_CONTRACT_REQUIRED”.
  - VAL: “CHAT_OUTPUT_CONTRACT_VIOLATION”.
  - QA: “TRACE_FORMAT_PASS”.
- EVIDENCE REQUIRED:
  - Структура 4 секции.

---

## 4) STANDARD VIOLATION CODES (CANON)
(используются VAL/QA как коды причин)

- RAW_MISSING
- MARKER_NOT_CONFIRMED
- INPUT_ABSENT
- RAW_OUTSIDE_LINK_BASE
- SNAPSHOT_REFRESH_VIOLATION
- BOOT_NOT_COMPLETED
- BOOT_MARKER_NOT_CONFIRMED
- ENTRYPOINT_BYPASS
- NAKED_CONTENT_OUTPUT
- TEMPLATE_BYPASS
- MISSING_CHANGE_ID
- INVALID_STOP_REASON
- CHAT_OUTPUT_CONTRACT_VIOLATION

---

## 5) ENFORCEMENT NOTES
- Этот реестр **не заменяет** START_UNIVERSE_ENGINE, а даёт CTL/VAL/QA “таблицу блокировок”.
- При появлении новой подсистемы (например, MUSIC) допускается добавление доменных constraints (CLASS=DOMAIN),
  но они не могут ослабить S0 constraints.

---

## 6) APPENDIX: RESERVED DOMAIN CONSTRAINTS (FUTURE)
(добавлять только через change management)

- C-MUSIC-001 Voice diversity minimum
- C-MUSIC-002 Anti-repetition threshold
- C-MUSIC-003 Credits/rights compliance
