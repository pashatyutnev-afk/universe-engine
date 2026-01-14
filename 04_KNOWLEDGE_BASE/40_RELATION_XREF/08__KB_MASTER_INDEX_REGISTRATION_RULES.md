# KB — MASTER INDEX REGISTRATION RULES (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/08__KB_MASTER_INDEX_REGISTRATION_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.MASTER_INDEX_REG.008
OWNER: SYSTEM
ROLE: Canonical rules for registering KB modules in the KB master index (RAW-only navigation): existence rule, required fields per entry, deprecation marking, no-duplicate entrypoints, and audit checks.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Established KB master index registration standard: existence rule, entry schema, and audit checks."
- REASON: "KB navigation must be executable from a single file; unregistered modules must be treated as non-existent operationally."
- IMPACT: "Deterministic KB navigation and existence enforcement; prevents silent drift and lost documents."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.008

---

## 0) PURPOSE (KB)
Define how KB modules become operationally real:
- registration in KB master index
- RAW-only navigation
- strict entry schema
- deprecation markings
- audit checks

This standard does not replace the master index; it defines its rules.

---

## 1) ABSOLUTE EXISTENCE RULE
- A KB module exists operationally ONLY if registered in the KB master index with a valid RAW link.
- If a file exists in repo but is not registered → NON-CANON / ignored.
- No entity may treat an unregistered KB module as authoritative.

---

## 2) MASTER INDEX SINGLE ENTRYPOINT RULE
- There must be exactly one KB master index file for the layer.
- Any duplicates/aliases must be removed or converted into POINTER-only files.

---

## 3) REQUIRED ENTRY SCHEMA (PER MODULE)
Each module entry in the master index must include:
- NN — Human title
- PATH: <repo path label> (human-readable)
- RAW: <raw link> (navigation mechanism)
Optional but recommended:
- UID: <module UID>
- STATUS: ACTIVE/DEPRECATED/DRAFT
- TAGS: <short tags>

Rules:
- RAW is mandatory.
- PATH is a label only.
- UID should match the module header UID exactly (if included).

---

## 4) REGISTRATION PROCEDURE (DETERMINISTIC)
Step 1 — Create or update KB module file
- Must have standard header and UID.

Step 2 — Add module entry to master index
- Use required entry schema (§3).

Step 3 — Validate RAW link
- It must open the intended file content.

Step 4 — Run duplication check
- Ensure no other ACTIVE module covers the same function.

Step 5 — Commit change note
- Ensure module and index changes are properly versioned/logged.

---

## 5) DEPRECATION IN MASTER INDEX
When a module is deprecated:
- Keep the entry in master index (for audit and trace).
- Mark clearly:
  - STATUS: DEPRECATED
  - Title suffix: "(DEPRECATED)"
- Ensure the deprecated module points to the replacement UID (per deprecation standard).

---

## 6) WHAT MUST NOT BE IN MASTER INDEX
- No non-canonical “extra indexes” that try to become entrypoints.
- No external links as replacement for RAW.
- No folders-only entries without actual module file.
- No “temporary” modules without registration.

---

## 7) AUDIT CHECKLIST (PASS/FAIL)
PASS IF:
- every KB module file has a master-index entry
- every entry has valid RAW
- there is only one master index entrypoint
- deprecated modules are marked and pointer-first
- no unregistered KB modules are used by entities

FAIL IF:
- missing RAW links
- broken RAW links
- multiple entrypoints
- unregistered modules used in outputs

---

## 8) EXAMPLES
Example entry (good):
01 — KNOWLEDGE BASE USAGE PROTOCOL
PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/01__META__KNOWLEDGE_BASE_USAGE_PROTOCOL.md
RAW: <raw link>
UID: UE.KB.TOPIC.META.USAGE.001
STATUS: DRAFT

Example entry (bad):
- only PATH, no RAW → FAIL
- RAW points to different file than PATH label → FAIL

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.TOPIC.META.NAV.002 | WHY: master-index navigation standard defines one-file navigation mode
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: deprecation handling and pointer-first rules
- XREF: UE.KB.TOPIC.META.QA_AUDIT.005 | WHY: audit checks for KB integrity

--- END.
