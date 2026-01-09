# SYSTEM LAW — CONSTRAINTS REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: CONSTRAINTS
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.CONSTRAINTS.001
OWNER: SYSTEM
ROLE: Registry of system constraints (global prohibitions/requirements) with scope, owner, priority, and enforcement to keep canon deterministic and drift-free

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable constraints registry: constraint classes, strict ID format, priority source rule, record format, conflict resolution, and enforcement."
- REASON: "System needs a single authoritative place for invariant constraints to prevent canon drift and hidden rule injection."
- IMPACT: "All layers (ENG/SPC/ORC/PRJ/KB) must comply with registered constraints; violations become detectable and auditable."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.CONSTRAINTS.001

---

## 0) PURPOSE (LAW)
This registry is the single source of truth for system-level constraints.

It defines:
- the allowed constraint classes
- a strict constraint ID format
- the canonical record format
- conflict resolution rules
- enforcement expectations (who checks and how)

Constraints here are invariants: they restrict what may be authored or produced anywhere in the system.

---

## 1) DEFINITIONS (STRICT)
- CONSTRAINT: A mandatory prohibition/requirement that limits allowable canon content or system behavior.
- CLASS: A category of constraint that defines its domain and typical owners.
- SCOPE: The exact domain where the constraint applies (system-wide, a layer, a project, a family, etc.).
- OWNER: The authority role responsible for keeping the constraint consistent and resolving ambiguity.
- ENFORCEMENT: How the constraint is checked (manual check, QA/VAL gate, CTL blocker, pipeline rule).
- PRIORITY: Severity/importance indicator (only if used and only via standards enum).

---

## 2) CONSTRAINT CLASSES (MANDATORY)
Only these classes are allowed:

- SYSTEM: constraints about governance, navigation determinism, existence rules, audit discipline.
- WORLD: invariants of the universe/worldbuilding that must not be violated by canon content.
- PRODUCTION: constraints about production formats, output packaging, delivery rules.
- SAFETY: constraints about risk/safety boundaries for the system and outputs.
- STYLE: constraints about style principles and non-negotiable aesthetic/format principles.

Changing this class list requires canon protocol.

---

## 3) CONSTRAINT ID FORMAT (ABSOLUTE)
- FORMAT: `UE.CNS.<CLASS>.<NNN>`
- `CLASS` must be one of: SYSTEM|WORLD|PRODUCTION|SAFETY|STYLE
- `NNN` is a 3-digit sequence (001..999) within the class
- IDs are stable and must never be reused

Examples:
- `UE.CNS.WORLD.001`
- `UE.CNS.SYSTEM.003`

---

## 4) PRIORITY ENUM SOURCE (MANDATORY)
If PRIORITY is used in a constraint record:
- The allowed values and meaning must be sourced from Standards (never invented here).

Priority standard (RAW):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md

If priority is not needed, omit PRIORITY field.

---

## 5) CONSTRAINT RECORD FORMAT (REGISTRY) (ABSOLUTE)
Every constraint record MUST follow this format:

- ID: `UE.CNS.<CLASS>.<NNN>`
- CLASS: SYSTEM|WORLD|PRODUCTION|SAFETY|STYLE
- STATEMENT (LAW): the invariant requirement/prohibition (single clear statement)
- SCOPE: where it applies (system-wide or bounded)
- OWNER: authority role (or SYSTEM if global)
- PRIORITY: S0|S1|S2|S3 (optional; only if used)
- ENFORCEMENT: how it is checked (CTL/QA/VAL/ORC/manual)
- NOTES: clarifications, examples, edge cases (optional but recommended)

---

## 6) CONSTRAINT PRIORITY & CONFLICT (MANDATORY)
### 6.1 Conflict rule
If two constraints appear to conflict:
- Resolve by ORDER OF AUTHORITY in `00__SYSTEM_LAW.md` first.
- If still ambiguous, escalate to OWNER(s) and record clarification as a change (canon protocol).

### 6.2 Escalation path
- SPC/ENG/ORC encountering ambiguity must escalate to governance owners (SYSTEM) and log the resolution.

---

# REGISTRY — CONSTRAINTS (CANON)

---

## UE.CNS.WORLD.001
- ID: UE.CNS.WORLD.001
- CLASS: WORLD
- STATEMENT (LAW): Great civilizations in the universe do not use currency (no money-based economy).
- SCOPE: All worldbuilding canon (projects, KB guidance, engines outputs, specialist outputs).
- OWNER: SYSTEM
- PRIORITY: S1
- ENFORCEMENT: VAL (world consistency) + CTL (canon readiness) + manual governance review on canon changes.
- NOTES:
  - This prohibits introducing “currency as a universal medium of exchange” for great civilizations.
  - Barter, reputation, access rights, resource allocation, quotas, obligations, non-monetary credits may exist only if they are explicitly defined as non-currency mechanisms and do not function as money.
  - Any exception requires explicit canon protocol approval + recorded rationale.

---

## (RESERVED) UE.CNS.WORLD.002
- ID: UE.CNS.WORLD.002
- CLASS: WORLD
- STATEMENT (LAW): <TBD>
- SCOPE: <TBD>
- OWNER: SYSTEM
- PRIORITY: <optional>
- ENFORCEMENT: <TBD>
- NOTES: <TBD>

---

## (RESERVED) UE.CNS.SYSTEM.001
- ID: UE.CNS.SYSTEM.001
- CLASS: SYSTEM
- STATEMENT (LAW): <TBD>
- SCOPE: <TBD>
- OWNER: SYSTEM
- PRIORITY: <optional>
- ENFORCEMENT: <TBD>
- NOTES: <TBD>

---

## 7) BOUNDARIES (ANTI-OVERLAP)
- This law registers constraints; it does not replace canon facts or project content.
- Constraints do not create existence; existence is defined by canonical indexes.
- CONFLICT RESOLUTION: resolved by ORDER OF AUTHORITY in `00__SYSTEM_LAW.md`.

---

## 8) ENFORCEMENT (MANDATORY)
### 8.1 MANDATORY CHECKS
- Every constraint uses the strict record format.
- Every constraint has a valid ID and class.
- Any use of PRIORITY follows the standards enum (no custom values).
- Constraints are not duplicated elsewhere as “shadow laws”.

### 8.2 FAIL CONDITIONS
- Constraint introduced outside this registry and treated as authoritative.
- Invalid ID format or reused ID.
- Priority values not defined by standards.
- Constraint statement is ambiguous (multiple rules in one) without clarification.

### 8.3 FIX PROCEDURE
- Move/merge shadow constraints into this registry via canon protocol.
- Reissue IDs if collisions occur (never reuse).
- Clarify ambiguous constraints via change note + protocol.
- Add enforcement mapping (VAL/QA/CTL) if currently undefined.

---

## 9) INTERFACES (RAW ONLY)
- System Law index (SoT):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Core constitution:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- Canon protocol:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- Standards master index:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

---

## FINAL RULE (LOCK)
This registry is the only authoritative source of constraints.  
Any constraint violation must be treated as a system issue until corrected or explicitly approved via canon protocol.

OWNER: SYSTEM
LOCK: FIXED

--- END.
