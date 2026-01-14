# KB — ENTITY ↔ COMPETENCE PACK BINDING RULES (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/39__KB_ENTITY_COMPETENCE_PACK_BINDING_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.ENTITY_COMP_BIND.039
OWNER: SYSTEM
ROLE: Defines how entities must bind to Professional Competence Packs: required pack UIDs per entity, how packs are declared in entity docs, coverage validation rules, and update/deprecation behavior.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Established entity→competence pack binding rules and coverage validation."
- REASON: "Competence packs only improve quality if entities are deterministically bound to them and required to load them."
- IMPACT: "Entities become auditable: each has required competence packs; gaps are detectable; upgrades are controllable."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.039

---

## 0) PURPOSE (KB)
Define the contract:
- which competence packs an entity must use
- how to declare that in entity docs (UID-only)
- how to validate coverage and detect missing skills
- how to update bindings when packs are superseded/deprecated

---

## 1) ABSOLUTE RULES
R1 — Binding is mandatory for specialists
- Every SPC specialist must have at least one required competence pack bound.

R2 — UID-only binding
- Pack binding references packs by UID only.

R3 — ACTIVE-first
- Required packs should be ACTIVE when possible.
- DRAFT packs may be used only if no ACTIVE exists and must be declared.

R4 — Deprecation safe
- If a pack is deprecated, entity must bind to the replacement pack UID.

---

## 2) BINDING DECLARATION (ENTITY DOC BLOCK)
Entities must include a binding section:

ENTITY_COMPETENCE_PACKS:
- REQUIRED_PACK_UIDS:
  - <PACK_UID>
  - <PACK_UID>
- OPTIONAL_PACK_UIDS:
  - <PACK_UID>
- COVERAGE_TARGET:
  - MIN_CAPABILITIES: <number> (recommended)
  - MUST_COVER: <capability tags or names> (optional)
- UPDATE_POLICY:
  - ACTIVE_FIRST: YES
  - ALLOW_DRAFT_IF_NO_ACTIVE: YES/NO
  - DEPRECATED_ALLOWED: NO (pointer-only migration ok)

Rules:
- REQUIRED_PACK_UIDS must not be empty for SPC.
- Packs must be domain-consistent with the entity role.

---

## 3) COVERAGE VALIDATION (DETERMINISTIC)
Validate coverage as:
Step 1: For each REQUIRED_PACK_UID, confirm it exists and is registered in master index.
Step 2: Check pack status:
- ACTIVE: ok
- DRAFT: ok only if no ACTIVE equivalent exists (declare)
- DEPRECATED: fail unless it is pointer-only and replacement is used
Step 3: Ensure coverage target is satisfied:
- required minimum capabilities
- required skill tags (if used)
Step 4: If missing:
- trigger gap handling: create new pack or extend pack, then bind.

---

## 4) UPDATE / MIGRATION RULES
If a pack is replaced:
- new pack should supersede old (REL semantics)
- old pack should be deprecated_by new (pointer-first)
Entity update:
- replace old UID in REQUIRED_PACK_UIDS with new UID
- keep optional note for migration (if needed)

---

## 5) FAIL CONDITIONS
FAIL IF:
- entity has no REQUIRED_PACK_UIDS (for SPC)
- any REQUIRED pack UID is missing/unregistered
- entity binds to DEPRECATED pack as authority
- pack domain mismatch (e.g., vocal director bound to narrative-only pack)
- entity uses packs but does not emit trace

---

## 6) TRACE REQUIREMENT
When a run uses competence packs:
KB_SOURCES must include:
- XREF: <PACK_UID> | WHY: competence pack used for role methods and gates
MEMORY_REUSE: YES/NO

---

## 7) EXAMPLES
Example — SPC Vocal Director
ENTITY_COMPETENCE_PACKS:
- REQUIRED_PACK_UIDS:
  - UE.KB.PACK.MUSIC.VOCAL_DIRECTOR.001
- OPTIONAL_PACK_UIDS:
  - UE.KB.PACK.MUSIC.MIX_TRANSLATION.001

Example — ORC Release Orchestrator
- REQUIRED_PACK_UIDS:
  - UE.KB.PACK.PROD.RELEASE_ORCHESTRATION.001

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: defines competence pack standard content
- XREF: UE.KB.STD.ENTITY_KB_CONNECTOR.037 | WHY: connector defines how entities load KB scopes
- XREF: UE.KB.POL.ENTITY_ACCESS.031 | WHY: access rules for status-based module usage
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: deprecation/migration of packs

--- END.
