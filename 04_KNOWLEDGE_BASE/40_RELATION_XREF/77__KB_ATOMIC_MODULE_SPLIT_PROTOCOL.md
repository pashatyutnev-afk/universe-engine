# KB — ATOMIC MODULE SPLIT PROTOCOL (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/77__KB_ATOMIC_MODULE_SPLIT_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PROC.ATOMIC_SPLIT.077
OWNER: SYSTEM
ROLE: Deterministic protocol for splitting large KB modules into atomic sub-modules: triggers, split strategy, relation wiring (REL/XREF), deprecation/alias handling, and master-index updates.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created protocol for splitting KB modules into atomic units with safe relation wiring and index updates."
- REASON: "Large monolithic modules reduce clarity, increase contradictions, and make entities load too much. Atomicity is required for deterministic operation."
- IMPACT: "Smaller reusable modules, cleaner scope boundaries, easier audits and upgrades."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PROC.077

---

## 0) PURPOSE (KB)
Provide a deterministic method to split modules when they become too large or mixed:
- identify split triggers
- plan new sub-modules
- wire relations safely
- update master index
- preserve backward compatibility via pointers

---

## 1) SPLIT TRIGGERS (WHEN TO SPLIT)
Split if any is true:
- module mixes multiple domains (scope boundary violation)
- module has multiple unrelated purposes
- entities must load too many sections to get one method
- contradictions increase due to bloated scope
- module exceeds “operational scan” size (cannot be used quickly)

---

## 2) SPLIT STRATEGY (DETERMINISTIC)
Step A: Identify sub-topics / sub-functions:
- list 3–10 atomic functions the module currently contains

Step B: Assign each function a target module type:
- STANDARD / POLICY / TOPIC / CHECKLIST / TEMPLATE / PACK

Step C: Decide ownership:
- primary domain for each new module
- scope boundary for each new module

Step D: Create new atomic modules:
- each gets its own UID
- each is registered in master index

Step E: Wire relations:
- parent module XREFs children (UID-only)
- if semantics matter, add REL edges (depends_on, supersedes, etc.)

---

## 3) WIRING RULES (REL/XREF)
- Use XREF for pointer links:
  - parent → child modules (see also / decomposition)
- Use REL when semantics matter:
  - depends_on for prerequisites
  - governed_by for policy control
  - validated_by for checklist/gate dependencies

Do not:
- put URLs/PATH in XREF
- create circular dependencies unless explicitly justified

---

## 4) DEPRECATION / COMPATIBILITY HANDLING
### Case 1: Safe split with same “parent purpose”
- Keep the original module as a thin “hub” TOPIC:
  - summary + boundaries
  - XREF list to new modules
  - remove duplicated content

### Case 2: Replace the original canon
- If the old module must not be used:
  - create new modules
  - deprecate old module pointer-first to the new hub module

### Case 3: Numbering slot conflicts
- Use pointer/alias policy to preserve numbering convenience.

---

## 5) MASTER INDEX UPDATE (MANDATORY)
After splitting:
- register each new module (RAW link entries)
- update old module entry:
  - mark as updated or deprecated
- ensure no duplicate entrypoints are created

---

## 6) VALIDATION (PASS/FAIL)
PASS IF:
- each new module is atomic and domain-consistent
- each has explicit scope boundaries
- relations wired via UID-only XREF and (optional) canonical REL
- master index updated and integrity checklist passes
- backward compatibility preserved if needed (pointer-only)

REWORK IF:
- split is done but boundaries still bleed
- relations unclear or redundant

FAIL IF:
- old monolith remains authoritative without boundaries
- new modules created but not indexed
- URLs/PATH used in crossrefs
- duplication of meaning persists (two canon truths)

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- split creates multiple conflicting canon modules for the same purpose
- master index not updated
- old module still used as authority while containing outdated rules
- pointers contain rules (must be pointer-only)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: scope boundary enforcement triggers splits
- XREF: UE.KB.STD.RELATION_MODEL.024 | WHY: wiring rules for REL + XREF
- XREF: UE.KB.POL.POINTERS_ALIASES.028 | WHY: aliasing and numbering preservation
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: deprecation and replacement handling
- XREF: UE.KB.CHK.MASTER_INDEX_INTEGRITY.071 | WHY: validate index after split

--- END.
