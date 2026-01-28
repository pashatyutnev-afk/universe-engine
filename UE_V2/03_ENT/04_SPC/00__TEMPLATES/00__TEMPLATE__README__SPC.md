# SPC FAMILY — README TEMPLATE (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__README__SPC.md
SCOPE: Universe Engine (Games volume) / System Entities / Specialists (SPC)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: SPC_FAMILY_README
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.TPL.SPC.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical README template for a SPC family folder (purpose, included SPCs, boundaries, KB scope, RAW-only interfaces).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Normalized family README: strict boundaries + included list + KB scope + RAW-only interfaces."
- REASON: "Prevent family drift and mixed-role instructions."
- IMPACT: "Families become easy to navigate and safe to use."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.SPC.FAMREADME.001

---

## 0) FAMILY PURPOSE (REQUIRED)
- зачем семья существует
- какие типы задач обслуживает
- какие типы deliverables упаковывает

## 1) INCLUDED SPECIALISTS (REQUIRED)
- 01 — <name> — RAW: <...>
- 02 — <name> — RAW: <...>

## 2) ROLE BOUNDARIES (MANDATORY)
SPC OWNS:
- intent/decisions/packaging

SPC DOES NOT:
- pipeline order (ORC)
- deterministic methods (ENG)
- policies/limits (CTL)
- compliance validation (VAL)
- quality gates (QA)

## 3) DEFAULT OUTPUTS (OPTIONAL)
- common artifact types this family produces

## 4) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- what this family typically uses

KB OUTPUTS:
- none (unless explicitly producing KB modules)

## 5) INTERFACES (RAW ONLY)
- SPC REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__README__SPC_REALM.md
- SPC GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md
- SPC RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md

--- END.
