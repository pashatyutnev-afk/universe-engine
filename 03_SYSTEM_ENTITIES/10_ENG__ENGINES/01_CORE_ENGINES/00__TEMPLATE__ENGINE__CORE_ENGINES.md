# CORE ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__ENGINE__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CORE.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for any CORE engine file. Enforces canonical header schema, mini-contract law, boundaries, output schemas, and raw-only references to prevent drift.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "CORE engine template standardized: governance-style header schema, mini-contract law, section skeleton, and anti-duplication constraints."
- REASON: "Stop format drift and ensure CORE engines are uniform and machine-checkable."
- IMPACT: "Any CORE engine can be validated consistently and integrated safely."
- CHANGE_ID: UE.CHG.2026-01-08.CORE.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new CORE engine file.
2) Replace placeholders строго.
3) Fill MINI-CONTRACT (must be concrete).
4) Define scope boundaries and hard blockers.
5) Add raw-only references if the engine is meant to be navigated via index.

Rule:
- If required sections are missing → engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.CORE.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence describing what this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why this engine exists or why change was made>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.CORE.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

- Define what this engine solves (strict).
- Define what it guarantees (bullets).
- Define non-goals (explicit).

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- <list what it must not define to avoid collisions>

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; use clear artifact names>

PRODUCES:
- <1–7 outputs; use clear artifact names>

DEPENDS_ON:
- <engine paths (family/NN__ENGINE)> or []

OUTPUT_TARGET:
MANDATORY:
- <where the canonical outputs must be stored (paths)>

OPTIONAL:
- <assistive mirrors/records; must not override canon>

Rule:
- If MINI-CONTRACT is missing, vague, or inconsistent → INVALID.

---

## 3) DEFINITIONS (STRICT)

- Only define terms that this engine owns.
- Do not redefine governance authority/pipeline terms (reference them).

---

## 4) SCOPE & BOUNDARIES (ANTI-DUPLICATION)

IN SCOPE:
- <owned domains / responsibilities>

OUT OF SCOPE (HARD):
- <forbidden domains / responsibilities>

COLLISION RULE:
- If overlap exists, explicitly declare who owns the concept and how to resolve it.

---

## 5) CORE RULESET (THE LAW)

Write numbered rules using MUST/FORBIDDEN/ALLOWED language.

Example form:
- R1 (HARD): ...
- R2 (HARD): ...
- R3 (SOFT): ...

Include:
- strict sets (allowed values)
- invariants (must always hold)
- stop conditions (blockers)

---

## 6) REQUIRED ARTIFACTS / OUTPUT SCHEMAS (MINIMUM)

For each produced artifact define a minimal schema:

ARTIFACT: <NAME>
- MUST: <fields list>
- OPTIONAL: <fields list>
- STORAGE: <where it lives>
- VALIDATION: <how to detect missing/invalid>

Rule:
- If an artifact is required for canon operation and schema is absent → INVALID.

---

## 7) PIPELINE / ALGORITHM (DETERMINISTIC)

Describe deterministic steps in order:
1) ...
2) ...
3) ...

GATES (if applicable):
- G0 ...
- G1 ...

---

## 8) FAILURE MODES / S0 BLOCKERS

List absolute blockers (STOP conditions):
- S0-1: ...
- S0-2: ...
- S0-3: ...

Describe required fix actions briefly.

---

## 9) INTEGRATION (HOW THIS FITS THE SYSTEM)

- Who consumes outputs
- What this engine depends on and why
- When governance pipeline is required (Change Control)
- How this engine interacts with Core Identity / Core State / Core Lifecycle (if applicable)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)

If this engine is part of a canon index navigation map, list raw-only links:
- https://raw.githubusercontent.com/.../path/to/file.md

--- END.

---

## 2) TEMPLATE QUALITY CHECK (FAST)

Before using a new engine as ACTIVE:
- [ ] Header matches schema (no missing fields)
- [ ] STATUS/LOCK appear only in header
- [ ] MINI-CONTRACT is concrete and consistent
- [ ] Output schemas exist for produced artifacts
- [ ] S0 blockers declared
- [ ] References are raw-only where needed
