# Core Identity Engine
FILE: 01__CORE_IDENTITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines canonical system identity profile (who/what the system is, its mission, scope, truth sources, and invariant principles) used by all ENG families and artifacts

---

## PURPOSE

Core Identity отвечает на вопросы:
- “Что это за система?”
- “Какая у неё миссия и границы?”
- “Что считается истиной?”
- “Какие принципы неизменны?”

Это “паспорт” Universe Engine для ENG слоя.

---

## NON-GOALS

- не управляет изменениями (governance)
- не описывает домены (story/character/world)
- не производит медиа
Он фиксирует базовую идентичность, которую все остальные обязаны уважать.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Index truth (00__INDEX_ALL_ENGINES.md)
- Governance law (00_GOVERNANCE_ENGINES/*)

### PRODUCES
- SYSTEM IDENTITY PROFILE (canonical fields + invariants)
- INVARIANT PRINCIPLES (non-negotiable rules)
- TRUTH SOURCES ORDER (truth hierarchy pointer)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

### OUTPUT_TARGET
- Every family README and every engine file should remain compatible with this identity profile

---

## SYSTEM IDENTITY PROFILE (CANON)

Identity profile — это набор полей, которые считаются “ядром”.

### IDENTITY FIELDS (MANDATORY)

- SYSTEM_NAME: Universe Engine
- SYSTEM_LAYER: ENG
- SYSTEM_PURPOSE:
  - “Build and maintain a canonical engine-based framework that turns knowledge into consistent worlds, narratives, and media artifacts.”
- SYSTEM_SCOPE:
  - What is included in ENG layer (engine families, indexes, rules)
  - What is excluded (ORC/SPC/CTL/VAL/QA are separate registries)
- SYSTEM_OWNER:
  - Universe Engine
- PRIMARY_REGISTRY:
  - `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__INDEX_ALL_ENGINES.md`
- GOVERNANCE_HOME:
  - `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/`
- TRUTH_HIERARCHY_POINTER:
  - `00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md`

---

## INVARIANT PRINCIPLES (NON-NEGOTIABLE)

### P1 — Single Registry Truth
INDEX defines existence and order.  
If not in INDEX → non-canon.

### P2 — Governance Pipeline
Canon changes must pass Change Control + Canon Authority + Audit + Versioning.

### P3 — Reproducibility
If an engine claims to output a spec, the spec must be reproducible (not “random inspiration”).

### P4 — Explicit Contracts
Every engine must have a mini-contract that states:
- consumes / produces / depends_on / output_target

### P5 — Clear Boundaries
Overlap is allowed only if:
- owner is assigned
- boundaries + handoff are explicit

### P6 — Layer Discipline
L1 rules do not leak into L2/L3 logic; L4 meta does not overwrite canon without approval.

---

## IDENTITY CONSISTENCY RULES

### IC1 — File Header Standard
All ENG files must contain standard header fields:
SCOPE, ENTITY_GROUP, FAMILY, CLASS, LEVEL, STATUS, VERSION, ROLE, OWNER.

### IC2 — Naming + Numbering
Files must follow:
- folder: `NN_<FAMILY>_ENGINES`
- engines: `NN__<NAME>_ENG.md`
- readme: `00__README__<FAMILY>_ENGINES.md`

### IC3 — Canon Path
Canonical path root:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/`

### IC4 — No Silent Canon
Any canon mutation must be traceable via:
CV + AL + RN (and optional CS for major).

---

## DEFAULT IDENTITY TAGS (OPTIONAL, FOR SEARCH)

- TAGS:
  - CANON
  - ENG_LAYER
  - ENGINE_SYSTEM
  - REGISTRY_DRIVEN
  - GOVERNANCE_GATED

---

## PROCEDURE (WHEN TO UPDATE IDENTITY)

Identity changes are rare and dangerous.

Allowed triggers:
- System renaming / major architecture shift
- Changing truth source order
- Introducing new entity groups in ENG layer

Required:
- Impact Report (I3)
- Decision level D3
- Canon verdict + audit + major version bump
- Migration notes for all families

---

## VALIDATION CHECKLIST

- CI1: Identity fields match actual repository paths.
- CI2: Truth hierarchy pointer exists and is stable.
- CI3: Invariant principles do not contradict governance engines.
- CI4: Any identity change is treated as MAJOR.

---

OWNER: Universe Engine
LOCK: FIXED
