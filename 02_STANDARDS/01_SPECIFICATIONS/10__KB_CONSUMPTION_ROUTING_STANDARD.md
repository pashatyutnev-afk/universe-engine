# KB CONSUMPTION ROUTING STANDARD (CANON)

FILE: 02_STANDARDS/01_SPECIFICATIONS/10__KB_CONSUMPTION_ROUTING_STANDARD.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 02_STANDARDS
DOC_TYPE: SPECIFICATION
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPEC.KB.ROUTING.011
OWNER: SYSTEM
ROLE: Standardizes how tasks/pipelines select KB scopes and how gates declare KB dependencies. Defines the minimum evidence trace contract for KB-consuming runs.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Spec: deterministic KB routing via scope maps + gate dependency maps + trace contract."
- REASON: "Ensure KB is consumed consistently across entities and pipelines."
- IMPACT: "Repeatable KB loading and audit-ready outputs."
- CHANGE_ID: UE.CHG.2026-01-20.SPEC.KB.ROUTING.010

---

## 0) SCOPE
Этот стандарт определяет:
- как выбирается KB scope для пайплайна,
- как gate связывается с KB,
- какой trace обязателен в результате.

---

## 1) REQUIRED CANON MAPS
Pipeline → scope:
- 04_KNOWLEDGE_BASE/40_RELATION_XREF/100__KB_PIPELINE_TO_KB_SCOPE_MAP.md

Gate → KB dependency:
- 04_KNOWLEDGE_BASE/40_RELATION_XREF/101__KB_GATE_TO_MODULE_MAP.md

Trace exemplar:
- 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/01__EXAMPLE__KB_CONSUMPTION_TRACE.md

---

## 2) DETERMINISTIC KB LOADING (STANDARD)

### Step A — Identify pipeline
Pipeline must be known (registry/map).

### Step B — Lookup required scopes
Use pipeline→scope map.
- If REQUIRED_INPUT says KB_SCOPE_RAW=YES → missing KB_SCOPE_RAW triggers STOP: input absent.

### Step C — Resolve scopes to modules
Use existing scope→module loading rules (KB side).
- If scope cannot be resolved → STOP: marker not confirmed.

### Step D — Execute gates
For each gate:
- lookup gate→KB dependency map
- load required scopes/modules (if not already loaded)
- apply gate checks

### Step E — Emit evidence trace
Output must contain:
- KB_SCOPE_USED (when required)
- KB_GATES_APPLIED (always when gates executed)
- KB_SOURCES_USED + provenance markers (when any non-user content used)

---

## 3) MINIMUM TRACE CONTRACT (STANDARD)
Output MUST include blocks:
- KB_SCOPE_USED
- KB_GATES_APPLIED
Conditional:
- KB_SOURCES_USED + provenance markers (only when external/non-user content exists)

---

END.
