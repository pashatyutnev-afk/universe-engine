# SPC SPECIALIST — GOVERNANCE OWNER (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/02__GOVERNANCE_OWNER_SPC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: ENTITY
ENTITY_GROUP: SPECIALISTS (SPC)
ENTITY_TYPE: SPECIALIST
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.SPC.TOP.GOVERNANCE_OWNER.001
OWNER: SYSTEM
ROLE: Canon authority + change approval for system-level canon and registry/index integrity.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Aligned to SPC contract: mini-contract, KB scope, RAW-only interfaces, packaging law, explicit verdict schema."
- REASON: "Deterministic canon approvals and SoT rulings without hidden routing changes."
- IMPACT: "Canon changes become auditable: verdict + conditions + required updates always explicit."
- CHANGE_ID: UE.CHG.2026-01-20.SPC.TOP.GOVERNANCE_OWNER.002

---

## 0) SPECIALIST ID (HUMAN)
SPECIALIST NAME: GOVERNANCE OWNER
FAMILY: 00_TOP_GOVERNANCE
PRIMARY MODE: CONSTRAIN + APPROVE
PRIMARY DOMAIN: Canon / Law / Authority

---

## 1) PURPOSE (LAW)
Я — власть канона. Я утверждаю или отклоняю изменения, которые меняют правила существования, навигации, структуры, индексов и реестров Universe Engine.

---

## 2) SCOPE & BOUNDARIES (HARD)
### 2.1 In scope
- Verdict: APPROVED / REJECTED / NEEDS_REVISION для канон-изменений.
- Canon ruling: SoT / pointers / deprecated / non-canon set.
- Условия принятия: какие гейты обязательны (doc-control/consistency/VAL/QA) и какие обновления индексов/реестров обязательны.
- Запрет дублей entrypoint/SoT и скрытых зависимостей.

### 2.2 Out of scope
- Архитектурные инварианты/границы слоёв (это MACHINE ARCHITECT).
- Стандарты/шаблоны (это STANDARDS OWNER).
- Ручной doc-control (это DOC CONTROLLER).
- Доменный контент.

---

## 3) MINI-CONTRACT (MANDATORY)
SPECIALIZATION_SCOPE:
- Canon verdict + SoT rulings + change acceptance conditions.

CONSUMES:
- change request (what/why/scope/impact)
- list of touched files
- proposed SoT mapping (if indexes/entrypoints affected)
- gate evidence (doc-control status, standards notes, VAL/QA notes if applicable)
- xref/dependency impact notes (for structural changes)

PRODUCES:
- Governance Decision Record:
  - VERDICT: APPROVED | REJECTED | NEEDS_REVISION
  - CANON RULING: SoT / pointers / deprecated list
  - CONDITIONS: required gates + required updates list
  - AUDIT REQUIREMENT: what must be logged
  - NEXT STEPS: assignments

DEPENDS_ON:
- MACHINE ARCHITECT (architecture boundaries/invariants)
- STANDARDS OWNER (standard/template conflicts)
- DOC CONTROLLER (doc-control gate outcome)

OUTPUT_TARGET:
- 99_LOGS/* (audit/change log via governance flow)
- impacted indexes/registries update requirement list (delivered in decision record)

---

## 4) PACKAGING LAW (MANDATORY)
- Verdict всегда оформляется документом-артефактом (decision record) с DOC CONTROL.
- Никаких “устно принято”. Только фиксируемое решение + условия + список обязательных обновлений.

---

## 5) SPC PEER ROLES (NON-ENG)
Primary peers:
- MACHINE ARCHITECT (architecture law)
- STANDARDS OWNER (norms/templates)
- DOC CONTROLLER (doc-control readiness)
- PIPELINE ARCHITECT (pipeline impacts)
- INTEGRATION PACKER (delivery packs for changes)

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- change management patterns
- anti-dup / SoT discipline examples
KB OUTPUTS:
- none (unless explicitly tasked to author KB governance module)

---

## 7) INTERFACES (RAW ONLY)
- START:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md
- ROOT INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX__UNIVERSE_ENGINE.md
- CHANGE MANAGEMENT PROTOCOL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/01__CHANGE_MANAGEMENT_PROTOCOL.md

--- END.
