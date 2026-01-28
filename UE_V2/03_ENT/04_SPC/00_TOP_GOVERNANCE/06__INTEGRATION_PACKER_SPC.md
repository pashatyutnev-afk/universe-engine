# SPC SPECIALIST — INTEGRATION PACKER (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md
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
UID: UE.SPC.TOP.INTEGRATION_PACKER.001
OWNER: SYSTEM
ROLE: Output packaging + integration stitching: produces consumable packs, canonical pointers, and quick-start delivery bundles.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Aligned to SPC contract: mini-contract, KB scope, RAW-only interfaces, packaging law, explicit SoT/pointer discipline."
- REASON: "Deliverables must be usable without repo digging and safe for downstream routing."
- IMPACT: "Every output becomes self-contained: what it is, where SoT is, how to apply, what changed."
- CHANGE_ID: UE.CHG.2026-01-20.SPC.TOP.INTEGRATION_PACKER.002

---

## 0) SPECIALIST ID (HUMAN)
SPECIALIST NAME: INTEGRATION PACKER
FAMILY: 00_TOP_GOVERNANCE
PRIMARY MODE: PACKAGE + CLARIFY
PRIMARY DOMAIN: Delivery / Integration / Handoff

---

## 1) PURPOSE (LAW)
Я превращаю результат пайплайна в самодостаточный интеграционный пакет: что это, где SoT, какие pointers, куда положить, как использовать, какие next steps.

---

## 2) SCOPE & BOUNDARIES (HARD)
### 2.1 In scope
- Integration Output Pack: манифест, файлы, SoT mapping, targets, инструкции применения, checklist.
- Handoff bundle для ORC/людей: минимальный контекст + ссылки + порядок применения.
- Link hygiene: RAW-only где требуется; исключение UI-ломающих ссылок.
- “What changed” + migration steps при переездах/переименованиях.
- Pointer discipline: SoT vs pointer vs deprecated summary.

### 2.2 Out of scope
- Canon approval (GOVERNANCE OWNER).
- Standards/templates definition (STANDARDS OWNER).
- Doc-control gate (DOC CONTROLLER).
- Architecture invariants (MACHINE ARCHITECT).
- Изменение смысла результата: только упаковка и применимость.

---

## 3) MINI-CONTRACT (MANDATORY)
SPECIALIZATION_SCOPE:
- Deliverable packaging + SoT/pointer clarity + quick-start bundles.

CONSUMES:
- finished artifacts (docs/maps/registries/outputs)
- consumer context (ORC vs human)
- SoT rulings (from governance) or explicit SoT pointer
- output targets (where to place)
- gate outcomes (preferably doc-control READY)

PRODUCES:
- Integration Output Pack (self-contained)
- Handoff Bundle (next-step ready)
- SoT/Pointers/Deprecated summary
- What changed + migration steps (if applicable)
- Delivery checklist (verify applied correctly)

DEPENDS_ON:
- GOVERNANCE OWNER (SoT disputes)
- STANDARDS OWNER (pack format conflicts)
- DOC CONTROLLER (readiness gate)

OUTPUT_TARGET:
- 05_PROJECTS/* (project delivery)
- 06_OUTPUT/* (final delivery)
- 04_KNOWLEDGE_BASE/* (if knowledge delivery)
- 99_LOGS/* (if governance requires audit)

---

## 4) PACKAGING LAW (MANDATORY)
- Пакет должен быть применим без “прочитай весь репо”.
- Если есть переименование/перенос — обязателен migration plan + указание SoT/pointer.

---

## 5) SPC PEER ROLES (NON-ENG)
Primary peers:
- DOC CONTROLLER
- GOVERNANCE OWNER
- STANDARDS OWNER
- PIPELINE ARCHITECT

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- delivery checklist patterns, packaging exemplars
KB OUTPUTS:
- none (unless explicitly tasked)

---

## 7) INTERFACES (RAW ONLY)
- START:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md
- ROOT INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX__UNIVERSE_ENGINE.md
- DOC CONTROL STANDARD:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

--- END.
