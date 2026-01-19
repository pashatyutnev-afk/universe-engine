# SYSTEM LAW — CONSTRAINTS REGISTRY (CANON)

FILE: 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md  
SCOPE: Universe Engine  
LAYER: 01_SYSTEM_LAW  
DOC_TYPE: LAW  
LAW_TYPE: CONSTRAINTS  
LEVEL: L1  
STATUS: ACTIVE  
LOCK: FIXED  
VERSION: 1.0.1  
UID: UE.LAW.CONSTRAINTS.001  
OWNER: SYSTEM  
ROLE: Registry of system constraints (global prohibitions/requirements) with scope, owner, priority, and enforcement to keep canon deterministic and drift-free

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: PATCH
- SUMMARY: "Registry aligned with START runtime laws: added SYSTEM constraints (RAW-only, snapshot refresh, task entrypoint), added PRODUCTION artifact rule, added SUNO style constraint, and normalized formatting."
- REASON: "Make constraints auditable and consistent with the single-entrypoint runtime and output-as-artifact policy."
- IMPACT: "Violations become detectable by CTL/VAL/QA; runtime determinism is enforced."
- CHANGE_ID: UE.CHG.2026-01-19.LAW.CONSTRAINTS.002

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
- **CONSTRAINT**: A mandatory prohibition/requirement that limits allowable canon content or system behavior.
- **CLASS**: A category of constraint that defines its domain and typical owners.
- **SCOPE**: The exact domain where the constraint applies (system-wide, a layer, a project, a family, etc.).
- **OWNER**: The authority role responsible for keeping the constraint consistent and resolving ambiguity.
- **ENFORCEMENT**: How the constraint is checked (manual check, QA/VAL gate, CTL blocker, pipeline rule).
- **PRIORITY**: Severity/importance indicator (optional; only if used and only via standards enum).

---

## 2) CONSTRAINT CLASSES (MANDATORY)
Only these classes are allowed:
- **SYSTEM**: governance, navigation determinism, entrypoint rules, existence/audit discipline.
- **WORLD**: invariants of the universe/worldbuilding that must not be violated by canon content.
- **PRODUCTION**: production formats, output packaging, delivery rules.
- **SAFETY**: risk/safety boundaries for the system and outputs.
- **STYLE**: style principles and non-negotiable aesthetic/format principles.

Changing this class list requires canon protocol.

---

## 3) CONSTRAINT ID FORMAT (ABSOLUTE)
FORMAT: `UE.CNS.<CLASS>.<NNN>`

- `CLASS` must be one of: SYSTEM|WORLD|PRODUCTION|SAFETY|STYLE
- `NNN` is a 3-digit sequence (001..999) within the class
- IDs are stable and must never be reused

Examples:
- `UE.CNS.WORLD.001`
- `UE.CNS.SYSTEM.003`

---

## 4) PRIORITY ENUM SOURCE (MANDATORY)
If PRIORITY is used in a constraint record:
- allowed values and meaning must be sourced from Standards (never invented here)

Priority standard (RAW):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md

If priority is not needed, omit PRIORITY field.

---

## 5) CONSTRAINT RECORD FORMAT (REGISTRY) (ABSOLUTE)
Every constraint record MUST follow this format:

- ID: `UE.CNS...`
- CLASS: SYSTEM|WORLD|PRODUCTION|SAFETY|STYLE
- STATEMENT (LAW): the invariant requirement/prohibition (single clear statement)
- SCOPE: where it applies (system-wide or bounded)
- OWNER: authority role (or SYSTEM if global)
- PRIORITY: S0|S1|S2|S3 (optional)
- ENFORCEMENT: how it is checked (CTL/QA/VAL/ORC/manual)
- NOTES: clarifications, examples, edge cases (optional but recommended)

---

## 6) CONSTRAINT PRIORITY & CONFLICT (MANDATORY)

### 6.1 Conflict rule
If two constraints appear to conflict:
- resolve by **ORDER OF AUTHORITY** in `00__SYSTEM_LAW.md` first
- if still ambiguous, escalate to OWNER(s) and record clarification as a change (canon protocol)

### 6.2 Escalation path
Any SPC/ENG/ORC encountering ambiguity must escalate to governance owners (SYSTEM) and log the resolution.

---

# REGISTRY — CONSTRAINTS (CANON)

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
  - Barter, reputation, access rights, resource allocation, quotas, obligations, non-monetary credits may exist only if explicitly defined as **non-currency mechanisms** and do not function as money.
  - Any exception requires explicit canon protocol approval + recorded rationale.

---

## UE.CNS.SYSTEM.001
- ID: UE.CNS.SYSTEM.001
- CLASS: SYSTEM
- STATEMENT (LAW): RAW-only navigation and no guessing are mandatory for all runtime work.
- SCOPE: Runtime + any operation that references repository content (all layers).
- OWNER: SYSTEM
- PRIORITY: S0
- ENFORCEMENT: CTL (readiness) + VAL (compliance checks) + manual governance review.
- NOTES:
  - Allowed sources of RAW links are only:
    - ROOT LINK BASE snapshot (ROOT-INDEX), and/or
    - RAW links explicitly provided by the user in the chat.
  - If a needed RAW link is missing → STOP condition: `RAW missing`.

---

## UE.CNS.SYSTEM.002
- ID: UE.CNS.SYSTEM.002
- CLASS: SYSTEM
- STATEMENT (LAW): The ROOT-INDEX link base is a snapshot and may be refreshed only manually by the user.
- SCOPE: Runtime navigation + routing + any link usage.
- OWNER: SYSTEM
- PRIORITY: S0
- ENFORCEMENT: CTL (readiness) + VAL (compliance) + audit log notes when refreshed.
- NOTES:
  - The system must treat the link set as fixed until the user provides an updated ROOT-INDEX or explicit new RAW links.
  - No “auto-update” assumptions are permitted.

---

## UE.CNS.SYSTEM.003
- ID: UE.CNS.SYSTEM.003
- CLASS: SYSTEM
- STATEMENT (LAW): Every task must start via START_UNIVERSE_ENGINE and enter through top governance dispatch; completion requires the verification chain.
- SCOPE: All tasks, all domains.
- OWNER: SYSTEM
- PRIORITY: S0
- ENFORCEMENT: CTL (readiness) + ORC (pipeline enforcement) + VAL/QA gates + DOC controller signoff.
- NOTES:
  - Mandatory entry dispatcher: `MACHINE_ARCHITECT_SPC`
  - Mandatory finish chain: `READINESS_CHECK_CTL` → relevant `VAL` → relevant `QA` → `DOC_CONTROLLER_SPC` → `MACHINE_ARCHITECT_SPC` signoff

---

## UE.CNS.PRODUCTION.001
- ID: UE.CNS.PRODUCTION.001
- CLASS: PRODUCTION
- STATEMENT (LAW): No “naked output” is allowed; any result must be packaged as an artifact-document under Doc Control rules and the correct template.
- SCOPE: Any outgoing result (content/solution/plan/track/cover/scene/entity passport).
- OWNER: DOC_CONTROLLER_SPC (or SYSTEM if global)
- PRIORITY: S0
- ENFORCEMENT: DOC control checks + QA gates + VAL compliance + packaging step by INTEGRATION_PACKER_SPC.
- NOTES:
  - If no suitable template/entity exists → GAP must be declared and creation proposed before proceeding.
  - For music: track outputs must map to the music artifact schema (e.g., TRACK CARD / PROMPT / RELEASE / OUTPUT_PACK).

---

## UE.CNS.STYLE.001
- ID: UE.CNS.STYLE.001
- CLASS: STYLE
- STATEMENT (LAW): For SUNO content, exclamation marks must not be used in prompts or track texts.
- SCOPE: Any SUNO prompt text and any track text intended for SUNO.
- OWNER: SYSTEM
- PRIORITY: S1
- ENFORCEMENT: CTL (prompt contract) + VAL (prompt fidelity) + QA (preflight checklist).
- NOTES:
  - Replace exclamation marks with punctuation such as period, dash, or ellipsis.
  - Do not start lines with command-style interjections using an exclamation prefix.

---

## (RESERVED) UE.CNS.WORLD.002
- ID: UE.CNS.WORLD.002
- CLASS: WORLD
- STATEMENT (LAW):
- SCOPE:
- OWNER: SYSTEM
- PRIORITY:
- ENFORCEMENT:
- NOTES:

---

## (RESERVED) UE.CNS.PRODUCTION.002
- ID: UE.CNS.PRODUCTION.002
- CLASS: PRODUCTION
- STATEMENT (LAW):
- SCOPE:
- OWNER:
- PRIORITY:
- ENFORCEMENT:
- NOTES:

---

## 7) BOUNDARIES (ANTI-OVERLAP)
- This law registers constraints; it does not replace canon facts or project content.
- Constraints do not create existence; existence is defined by canonical indexes.
- Conflict resolution is governed by ORDER OF AUTHORITY in `00__SYSTEM_LAW.md`.

---

## 8) ENFORCEMENT (MANDATORY)

### 8.1 Mandatory checks
- Every constraint uses the strict record format.
- Every constraint has a valid ID and class.
- Any use of PRIORITY follows the standards enum (no custom values).
- Constraints are not duplicated elsewhere as “shadow laws”.

### 8.2 Fail conditions
- Constraint introduced outside this registry and treated as authoritative.
- Invalid ID format or reused ID.
- Priority values not defined by standards.
- Constraint statement is ambiguous (multiple rules in one) without clarification.

### 8.3 Fix procedure
- Move/merge shadow constraints into this registry via canon protocol.
- Reissue IDs if collisions occur (never reuse).
- Clarify ambiguous constraints via change note + protocol.
- Add enforcement mapping (VAL/QA/CTL) if currently undefined.

---

## 9) INTERFACES (RAW ONLY)
- System Law index (SoT):  
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Core constitution:  
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- Canon protocol:  
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- START runtime entrypoint:  
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01__START_UNIVERSE_ENGINE.md
- Standards master index:  
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_STANDARDS%20%E2%80%94%20MASTER%20INDEX.md
- Priority enum standard:  
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md

---

## FINAL RULE (LOCK)
This registry is the only authoritative source of constraints.  
Any constraint violation must be treated as a system issue until corrected or explicitly approved via canon protocol.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
