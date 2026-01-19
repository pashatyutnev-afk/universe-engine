# 07__PIPELINE_REGISTRY

FILE: 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY (LAW)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.LAW.PIPELINES.REG.001
OWNER: SYSTEM
ROLE: Canonical registry of runtime pipelines (boot, task lifecycle, routing, validation, packaging). Defines step order, mandatory gates, handoffs, and required trace evidence.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Registry populated with canonical pipelines: BOOT, DEFAULT TASK LIFECYCLE, MISSING ENTITY CREATE, CHANGE MANAGEMENT, and domain pipeline slots."
- REASON: "Without an explicit pipeline registry, ORC/CTL/VAL/QA cannot deterministically enforce step order and evidence."
- IMPACT: "All runs become auditable: step order + gates + evidence are standardized."

---

## 0) PURPOSE (LAW)
Этот реестр фиксирует **канонические пайплайны** системы:
- порядок шагов (step order),
- handoffs между сущностями (SPC/ORC/ENG/CTL/VAL/QA),
- обязательные гейты (preflight, compliance, QA, doc control),
- требования к трассировке (что должно быть показано в выводе).

Пайплайн считается каноническим только если:
- имеет PIPELINE_ID,
- имеет шаги с OWNER ENTITY,
- имеет обязательные гейты и evidence.

---

## 1) DEFINITIONS
- **Pipeline** — последовательность шагов с handoffs и gates.
- **Step** — атомарный шаг пайплайна.
- **Owner Entity** — сущность, которая отвечает за шаг.
- **Gate** — проверка, без которой нельзя идти дальше.
- **Trace Evidence** — что должно быть предъявлено в `RESOURCES USED / DELIVERABLES / GATES`.

---

## 2) REGISTRY FORMAT (HOW TO READ)
Каждый пайплайн:

- PIPELINE_ID: уникальный ID
- NAME: коротко
- TYPE: BOOT / TASK / CREATE / CHANGE / DOMAIN
- SEVERITY: S0 (must-run) / S1 (default) / S2 (optional)
- ENTRY: какая команда/условие запускает
- EXIT: что считается завершением
- STEPS: список шагов по порядку
- REQUIRED GATES: минимальный набор гейтов
- TRACE MINIMUM: минимальный след в чате (что обязано быть отражено)

---

## 3) PIPELINES (REGISTRY)

# P-BOOT-001 — BOOT SEQUENCE (MANDATORY)
- PIPELINE_ID: P-BOOT-001
- NAME: Boot sequence
- TYPE: BOOT
- SEVERITY: S0
- ENTRY:
  - COMMAND: START_UNIVERSE_ENGINE
  - CONDITION: any task execution requested
- EXIT:
  - BOOT COMPLETE MARKER подтверждён (4 пункта)
- STEPS:
  1) Load System Law (read)
     - OWNER ENTITY: MACHINE_ARCHITECT_SPC
     - OUTPUT: Boot Trace: system law loaded list
  2) Load Standards for navigation + doc control (read)
     - OWNER ENTITY: STANDARDS_OWNER_SPC
     - OUTPUT: Boot Trace: standards loaded list
  3) Load Entity model + registries/templates indexes (read)
     - OWNER ENTITY: DOC_CONTROLLER_SPC
     - OUTPUT: Boot Trace: entity model loaded list
  4) Load Knowledge Base entrypoint (read)
     - OWNER ENTITY: KNOWLEDGE_INTEGRATOR_SPC (или MACHINE_ARCHITECT_SPC если нет отдельного SPC)
     - OUTPUT: Boot Trace: KB entrypoint loaded list
  5) Confirm BOOT COMPLETE MARKER (gate)
     - OWNER ENTITY: READINESS_CHECK_CTL
     - OUTPUT: Explicit marker confirmation for:
       - Naming + UID rules loaded
       - Doc Control + Index structure loaded
       - Entity model loaded
       - KB entrypoint loaded
- REQUIRED GATES:
  - READINESS_CHECK_CTL: BOOT markers present
- TRACE MINIMUM:
  - MODE
  - RESOURCES USED: RAW links opened + “MARKER FOUND”
  - DELIVERABLES: Boot Trace (4 groups)
  - GATES: BOOT COMPLETE MARKER = PASS or STOP marker not confirmed

---

# P-TASK-001 — DEFAULT TASK LIFECYCLE (CANON)
- PIPELINE_ID: P-TASK-001
- NAME: Default task lifecycle
- TYPE: TASK
- SEVERITY: S1 (default for all tasks)
- ENTRY:
  - BOOT complete
  - TASK present (user request)
- EXIT:
  - Signoff by DOC_CONTROLLER_SPC and MACHINE_ARCHITECT_SPC with required gates passed
- STEPS:
  1) INTAKE
     - OWNER ENTITY: MACHINE_ARCHITECT_SPC
     - OUTPUT: Task Spec (goal, scope, inputs, artifact type, stop risks)
  2) ROUTING
     - OWNER ENTITY: MACHINE_ARCHITECT_SPC (may delegate to top SPCs)
     - OUTPUT: Route Plan (which SPC/ORC/ENG/CTL/VAL/QA are used)
  3) EXECUTION (draft production)
     - OWNER ENTITY: ORC (selected orchestrator)
     - SUPPORT: ENG (selected engines)
     - OUTPUT: Draft Artifacts (not final)
  4) CONTROL (policy enforcement)
     - OWNER ENTITY: CTL (domain controller + readiness)
     - OUTPUT: Blockers or allowed actions list
  5) VALIDATION (compliance)
     - OWNER ENTITY: VAL (relevant validators)
     - OUTPUT: Violation records or PASS
  6) QA (acceptance gates)
     - OWNER ENTITY: QA (relevant QA)
     - OUTPUT: QA report, scoring, regression notes
  7) PACKAGING (final file set)
     - OWNER ENTITY: INTEGRATION_PACKER_SPC
     - OUTPUT: Final artifacts packaged as full docs
  8) DOC CONTROL + SIGNOFF
     - OWNER ENTITY: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC
     - OUTPUT: Final approval note + (если нужно) changelog entry
- REQUIRED GATES:
  - READINESS_CHECK_CTL (preflight)
  - relevant VAL checks
  - relevant QA gates
  - DOC_CONTROLLER_SPC structure compliance
  - MACHINE_ARCHITECT_SPC signoff
- TRACE MINIMUM:
  - MODE: REPO (USAGE-ONLY, NO-EDIT)
  - RESOURCES USED: RAW links for every entity/doc referenced + marker evidence
  - DELIVERABLES: Task Spec, Route Plan, Final Artifacts
  - GATES: list of gates with PASS/FAIL, and stop reason if stopped

---

# P-GAP-001 — MISSING ENTITY OR TEMPLATE (CREATE DUTY)
- PIPELINE_ID: P-GAP-001
- NAME: Missing entity/template protocol
- TYPE: CREATE
- SEVERITY: S0 (must-run when gap detected)
- ENTRY:
  - During routing/execution a required entity or template is missing
- EXIT:
  - Gap resolved by proposing creation pack (full file) and registration steps defined
- STEPS:
  1) Declare GAP
     - OWNER ENTITY: MACHINE_ARCHITECT_SPC
     - OUTPUT: GAP statement (what missing, why required, what blocks)
  2) Select TEMPLATE
     - OWNER ENTITY: DOC_CONTROLLER_SPC
     - OUTPUT: Template chosen (RAW link) + marker evidence
  3) Generate Minimal Entity Pack (full docs)
     - OWNER ENTITY: MACHINE_ARCHITECT_SPC + relevant domain SPC
     - OUTPUT: Full entity doc(s) per template (not partial)
  4) Define Registration Actions
     - OWNER ENTITY: DOC_CONTROLLER_SPC
     - OUTPUT: What registries/DB/logs must be updated (actions list)
  5) Resume Original Pipeline
     - OWNER ENTITY: MACHINE_ARCHITECT_SPC
- REQUIRED GATES:
  - READINESS_CHECK_CTL: “GAP resolved” marker present (template used, file produced)
- TRACE MINIMUM:
  - MODE
  - RESOURCES USED: template RAW + registry RAW (if referenced)
  - DELIVERABLES: full entity file(s) + registration action list
  - GATES: GAP protocol PASS

---

# P-CHG-001 — CHANGE MANAGEMENT (LAW/STANDARD/TEMPLATE)
- PIPELINE_ID: P-CHG-001
- NAME: Change management protocol
- TYPE: CHANGE
- SEVERITY: S1 (required when editing law/standards)
- ENTRY:
  - Any proposed change to LAW / STANDARD / TEMPLATE documents
- EXIT:
  - CHANGE_NOTE and CHANGE_ID defined, version updated per policy
- STEPS:
  1) Change Proposal
     - OWNER ENTITY: STANDARDS_OWNER_SPC (or GOVERNANCE_OWNER_SPC for LAW)
     - OUTPUT: Proposed diff summary (what/why/impact)
  2) Doc Control Alignment
     - OWNER ENTITY: DOC_CONTROLLER_SPC
     - OUTPUT: Updated header blocks, UID consistency, file naming compliance
  3) Validation of Change Format
     - OWNER ENTITY: VAL (doc control validator if exists)
     - OUTPUT: PASS or violation record
  4) Approval
     - OWNER ENTITY: MACHINE_ARCHITECT_SPC
     - OUTPUT: Signoff marker
- REQUIRED GATES:
  - Presence of CHANGE_NOTE block
  - Presence of CHANGE_ID
  - Version updated
- TRACE MINIMUM:
  - DELIVERABLES include updated full file (not partial) or stop with reason

---

# P-DOMAIN-001 — DOMAIN PIPELINE SLOT (ABSTRACT)
- PIPELINE_ID: P-DOMAIN-001
- NAME: Domain pipeline slot
- TYPE: DOMAIN
- SEVERITY: S2 (optional until domain is invoked)
- ENTRY:
  - Task specifies a domain (e.g., MUSIC / NARRATIVE / WORLD / VISUAL)
- EXIT:
  - Domain artifacts produced and pass domain gates
- STEPS (abstract):
  1) Select Domain ORC
  2) Execute Domain ENG set
  3) Apply Domain CTL
  4) Run Domain VAL
  5) Run Domain QA
  6) Package domain artifacts
  7) Signoff
- REQUIRED GATES:
  - Domain readiness gate(s)
  - Domain QA acceptance
- TRACE MINIMUM:
  - Must list selected domain entities and their RAW links

NOTE:
- Конкретные доменные пайплайны должны быть зарегистрированы отдельными PIPELINE_ID (например P-MUSIC-001), и не могут ослаблять S0 ограничения из CONSTRAINTS_REGISTRY.

---

## 4) PIPELINE STEP CONTRACT (CANON)
Каждый шаг пайплайна обязан иметь:
- STEP_ID (внутри пайплайна)
- OWNER ENTITY
- INPUTS
- OUTPUTS
- HANDOFF TO (следующий owner)
- GATES (если применимо)
- EVIDENCE

Если шаг не может быть исполнен из-за RAW missing:
- STOP = RAW missing (без дополнительных причин)

---

## 5) TRACE REQUIREMENTS (MINIMUM FOR ANY RUN)
Любой рантайм-ответ обязан:
- MODE
- RESOURCES USED (USING RAW + MARKER FOUND)
- DELIVERABLES
- GATES

Дополнительно для пайплайнов:
- указать PIPELINE_ID
- указать текущий STEP и статус (PASS/FAIL/STOP)

---

## 6) APPENDIX: RECOMMENDED DOMAIN PIPELINES (TO REGISTER NEXT)
(это список кандидатов, не активные пайплайны)

- P-MUSIC-001: Group → Album → Track (factory route)
- P-MUSIC-002: Track test doc gate → iteration loop
- P-NARR-001: Scene pack build route
- P-WORLD-001: Location/entity workshop L0→L3 promotion route
- P-VIS-001: Visual scene prompt pack route
