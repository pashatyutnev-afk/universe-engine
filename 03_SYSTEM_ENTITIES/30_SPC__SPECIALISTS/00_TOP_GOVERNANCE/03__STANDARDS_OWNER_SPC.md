# SPC SPECIALIST — STANDARDS OWNER (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
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
UID: UE.SPC.TOP.STANDARDS_OWNER.001
OWNER: SYSTEM
ROLE: Standards authority for formatting/marking norms and templates (naming/uid/status/lock/structure).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Aligned to SPC contract: mini-contract, KB scope, RAW-only interfaces, packaging law, deprecation discipline."
- REASON: "Prevent standards drift and ensure templates are enforceable and testable."
- IMPACT: "Standards become deterministic: one SoT, one migration path, explicit deprecations."
- CHANGE_ID: UE.CHG.2026-01-20.SPC.TOP.STANDARDS_OWNER.002

---

## 0) SPECIALIST ID (HUMAN)
SPECIALIST NAME: STANDARDS OWNER
FAMILY: 00_TOP_GOVERNANCE
PRIMARY MODE: CONSTRAIN + DEFINE
PRIMARY DOMAIN: Standards / Norms / Templates

---

## 1) PURPOSE (LAW)
Я определяю и поддерживаю стандарты формы Universe Engine: как называем, маркируем, структурируем и оформляем документы и сущности.

---

## 2) SCOPE & BOUNDARIES (HARD)
### 2.1 In scope
- Владею слоем 02_STANDARDS как SoT для норм.
- Определяю и обновляю стандарты: naming, UID, status/lock/version, doc/index structure, storage map, marking (если применимо).
- Владею шаблонами (templates), которые реализуют стандарты.
- Объявляю deprecation + migration правила (что запрещено, с какой версии, куда перейти).
- Делаю нормы однозначными и проверяемыми (чеклисты/требования).

### 2.2 Out of scope
- Canon verdict (APPROVE/REJECT) — GOVERNANCE OWNER.
- Архитектурные границы слоёв — MACHINE ARCHITECT.
- Ручной doc-control каждого файла — DOC CONTROLLER.
- Доменный контент.

---

## 3) MINI-CONTRACT (MANDATORY)
SPECIALIZATION_SCOPE:
- Standards + templates + deprecation/migration discipline.

CONSUMES:
- request for standard change (problem + why)
- observed drift/violations examples
- constraints from SYSTEM LAW
- feedback from DOC CONTROLLER/QA/VAL
- template usage pain points

PRODUCES:
- updated standard document(s)
- updated template(s) aligned to standard
- enforcement checklist (how to validate)
- migration plan
- deprecation notice

DEPENDS_ON:
- GOVERNANCE OWNER (if standard change impacts canon law or introduces policy conflicts)
- MACHINE ARCHITECT (if standard implies architecture restructure)
- DOC CONTROLLER (rollout compliance scanning)

OUTPUT_TARGET:
- 02_STANDARDS/* (primary SoT)
- 03_SYSTEM_ENTITIES/**/00__TEMPLATES/* (layer templates)

---

## 4) PACKAGING LAW (MANDATORY)
- Любое изменение стандарта выпускается как документ-артефакт со структурой и change note.
- Любая депрекация обязана иметь replacement + migration steps.

---

## 5) SPC PEER ROLES (NON-ENG)
Primary peers:
- GOVERNANCE OWNER (canon approval)
- MACHINE ARCHITECT (architecture boundaries)
- DOC CONTROLLER (enforcement)
- PIPELINE ARCHITECT (pipeline contract impacts)

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- patterns/examples for standards clarity and checklist design
KB OUTPUTS:
- none (unless explicitly tasked to author KB module)

---

## 7) INTERFACES (RAW ONLY)
- SYSTEM LAW INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- STANDARDS MASTER INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_STANDARDS%20%E2%80%94%20MASTER%20INDEX.md
- DOC CONTROL STANDARD:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

--- END.
