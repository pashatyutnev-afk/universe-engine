# KB — MASTER INDEX POINTERS / ALIASES POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/28__KB_MASTER_INDEX_POINTERS_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.POINTERS_ALIASES.028
OWNER: SYSTEM
ROLE: Policy governing POINTER/ALIAS KB modules: when they are allowed, how they must be written (pointer-only), how they are registered in master index, and how to prevent authority duplication.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined policy for pointer/alias modules and how master index must treat them."
- REASON: "Aliases are useful for navigation convenience but can create duplicate truths if not constrained."
- IMPACT: "Safe aliasing: one canonical authority, pointers for convenience, no semantic drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.028

---

## 0) PURPOSE (KB)
Pointer/alias modules exist to:
- preserve naming/numbering convenience
- maintain backward compatibility for older references
- avoid breaking links when reorganizing

They must never create a second authoritative copy of rules.

---

## 1) ABSOLUTE RULES
R1 — Canon remains single source of truth
- A pointer/alias must point to exactly one canonical target UID.
- It must not redefine, expand, or modify the canon.

R2 — Pointer-only body
- Pointer modules must contain only:
  - canonical target UID
  - short reason/note
  - XREF to canonical target UID
- No procedures, no extra rules.

R3 — UID-only references
- Pointer target is expressed as UID only.
- No URLs/PATH in the pointer body.

R4 — Master index must mark pointers
- Pointer entries in master index must be clearly marked as POINTER/ALIAS.
- Canonical target entry remains the authoritative one.

---

## 2) WHEN POINTERS ARE ALLOWED
Allowed cases:
- P1: duplicate naming/numbering convenience (a “slot” reserved by numbering)
- P2: backward compatibility for renamed files
- P3: migration bridge during restructuring
- P4: alias entry for human usability, while canon is elsewhere

Not allowed:
- creating pointer to avoid writing a proper module
- using pointers as “mini indexes” of many targets

---

## 3) POINTER MODULE SCHEMA (STRICT)
A pointer module MUST include:
- Header with KB_TYPE: POINTER
- A pointer declaration block:
  - CANON_TARGET_UID: <UID>
  - NOTE: <short>
- XREF:
  - XREF: <CANON_TARGET_UID> | WHY: canonical authority

Recommended:
- Title includes "POINTER:" prefix.

Forbidden:
- REL blocks (pointers should not encode semantics)
- multiple targets
- any content that can be “used” as a rule

---

## 4) MASTER INDEX REGISTRATION RULES (POINTER)
In KB master index, pointer entry should include:
- TITLE suffix: "(POINTER)"
- UID of pointer module
- Optional: CANON_TARGET_UID for clarity

Rule:
- Consumers must follow CANON_TARGET_UID to the authoritative module.

---

## 5) AUDIT RULES
PASS IF:
- pointer has exactly one target UID
- pointer contains no extra rules
- pointer is marked in master index
- canonical module exists and is registered

FAIL IF:
- pointer contains procedures/rules
- pointer points to missing/nonexistent UID
- pointer lists multiple targets
- pointer is used as authority in outputs instead of canon

---

## 6) EXAMPLES
GOOD pointer:
- "POINTER: Depracation Standard"
- CANON_TARGET_UID: UE.KB.STD.DEPRECATION_POINTER.007
- XREF to that UID

BAD pointer:
- includes “small additional notes/rules”
- includes URL or PATH
- points to 3 different UIDs

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- any non-pointer content appears (procedures, rules, essays)
- more than one target UID
- missing XREF to target
- missing or invalid CANON_TARGET_UID
- pointer not labeled as such in master index

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: master index registration/existence rules
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: deprecation often requires pointers/aliases
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossref policy (no URL/PATH)

--- END.
