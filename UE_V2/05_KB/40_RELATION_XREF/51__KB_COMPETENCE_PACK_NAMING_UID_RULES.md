# KB — COMPETENCE PACK NAMING & UID RULES (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/51__KB_COMPETENCE_PACK_NAMING_UID_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.PACK_NAMING_UID.051
OWNER: SYSTEM
ROLE: Defines deterministic naming and UID rules for competence packs: file naming patterns, pack UID conventions, and collision avoidance. Ensures packs are discoverable, stable, and auditable.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined naming + UID conventions for competence packs with collision guards."
- REASON: "Without deterministic naming and UID patterns, packs collide, become untraceable, and entities cannot bind reliably."
- IMPACT: "Predictable pack IDs and filenames; easier indexing and migration."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.051

---

## 0) PURPOSE (KB)
Define:
- how competence pack files are named
- how pack UIDs are formed
- how to avoid collisions
- how to handle renames and replacements

---

## 1) FILE NAMING RULES (PACK FILES)
Recommended filename pattern:
`XX__PACK__<DOMAIN>__<ROLE>__<SHORT_NAME>.md`

Where:
- XX is local ordering number inside its folder (not global truth)
- DOMAIN is one of: SOUND_MUSIC | NARRATIVE | CHARACTER | WORLD | VISUAL | PRODUCTION | MARKETING | META
- ROLE is the target specialist/role name (snake-ish, uppercase or consistent tokens)
- SHORT_NAME is a brief descriptor

Examples (pattern only):
- `01__PACK__SOUND_MUSIC__VOCAL_DIRECTOR__CORE_COMPETENCE.md`
- `02__PACK__PRODUCTION__RELEASE_MANAGER__SHIP_READY.md`

Rules:
- Keep names explicit and stable.
- If renamed, keep pointer/alias per deprecation standard.

---

## 2) PACK UID CONVENTION (CANON)
Pack UID pattern:
`UE.KB.PACK.<DOMAIN>.<ROLE>.<NNN>`

Where:
- DOMAIN is short token: MUSIC | NARR | CHAR | WORLD | VISUAL | PROD | MKT | META
- ROLE is a stable role token (uppercase in file, dot-token in UID)
- NNN is a numeric sequence per role (001..)

Examples (pattern only):
- `UE.KB.PACK.MUSIC.VOCAL_DIRECTOR.001`
- `UE.KB.PACK.PROD.RELEASE_MANAGER.001`

Rules:
- UIDs are stable; never reuse a UID.
- If a pack is superseded, the new pack gets a new UID; the old becomes deprecated pointer-first.

---

## 3) COLLISION AVOIDANCE RULES
- ROLE token must be unique and stable (use canonical entity naming token, not random).
- If two packs share a role but different scope:
  - differentiate by SHORT_NAME in filename
  - increment NNN in UID
- Do not create two ACTIVE packs with same function (use deprecation standard).

---

## 4) DOMAIN TOKEN TABLE (CANON)
- SOUND_MUSIC → MUSIC
- NARRATIVE   → NARR
- CHARACTER   → CHAR
- WORLD       → WORLD
- VISUAL      → VISUAL
- PRODUCTION  → PROD
- MARKETING   → MKT
- META        → META

---

## 5) RENAME / MOVE RULES
- Prefer not to rename after ACTIVE.
- If rename/move is required:
  - keep old file as POINTER/ALIAS (optional) OR update master index
  - do not change UID
- If semantic replacement:
  - new UID + supersedes/deprecated_by pair

---

## 6) QA CHECKS (PASS/FAIL)
PASS IF:
- filename matches pattern
- UID matches pattern
- no duplicate ACTIVE pack for same function
- pack is registered in master index

FAIL IF:
- UID reused
- two active packs duplicate the same function
- role token ambiguous (not stable)
- pack exists but not indexed

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- pack UID does not follow convention
- pack lacks a role token
- pack duplicates an active pack without deprecation workflow
- UID changes after publication without replacement flow

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: packs are defined by this standard
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: replacement/renames must follow deprecation pointer rules
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: packs must be registered to exist operationally

--- END.
