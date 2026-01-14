# KB — XREF UID-ONLY REFERENCE RULES (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/05__XREF_UID_ONLY_REFERENCE_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.DICT.XREF_RULES.005
OWNER: SYSTEM
ROLE: Canonical rules for cross-references (XREF) inside KB modules and system docs: UID-only references, strict format, allowed targets, and hard fail conditions. Prevents navigation drift and preserves master-index RAW-only navigation.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Established UID-only XREF policy with strict format and fail conditions."
- REASON: "XREF is a semantic graph; if URLs/PATH leak into XREF, navigation and audit break and entities start guessing."
- IMPACT: "All KB modules can reference each other deterministically via UIDs; RAW navigation stays centralized in master index."
- CHANGE_ID: UE.CHG.2026-01-14.KB.XREF.005

---

## 0) PURPOSE (KB)
Define how to write XREF blocks:
- UID-only references
- consistent formatting
- allowed reference targets
- hard fail conditions

This policy is not a navigation index.
All file opening is performed via KB master index (RAW-only).

---

## 1) ABSOLUTE RULES
1.1 UID-ONLY (ABSOLUTE)
- Every XREF must reference a target by UID only.
- No URLs, no RAW, no PATH, no filenames as targets.

1.2 NO NAVIGATION IN XREF (ABSOLUTE)
- XREF is a semantic cross-reference graph, not a link hub.
- Navigation is handled exclusively by the KB master index.

1.3 STABLE TARGETS ONLY
- XREF must point to stable canonical identifiers (UIDs).
- Do not reference transient drafts without UIDs.

---

## 2) ALLOWED TARGET TYPES
XREF targets may be:
- KB module UID (topics/maps/policies/dictionaries)
- System law UID
- Standards/spec UID
- Entity UID (only if entity UID is canonical)

Forbidden targets:
- raw URLs
- repo paths
- external web links
- “human descriptions” without UID

---

## 3) XREF FORMAT (STRICT)
Use this exact pattern:

XREF:
- XREF: <TARGET_UID> | WHY: <short reason>

Rules:
- One target per line.
- WHY is mandatory and must be concise.
- Do not embed multiple UIDs in one line.

Optional tags (only if needed):
- KIND: depends_on | complements | governed_by | etc. (use REL dictionary if your system keeps REL separate)
(If your KB uses REL and XREF separately, keep XREF for UID pointers only.)

---

## 4) WHERE TO PUT XREF
- Near the end of a KB module, before COMPLIANCE/END.
- In MAP modules, XREF should usually reference related MAP UIDs.
- In TOPIC modules, XREF should reference governance UIDs + key companion modules.

---

## 5) INTERACTION WITH REL
- REL expresses relationship semantics (“depends_on”, “governed_by”, etc.).
- XREF expresses target identity pointers (UIDs) without URLs/PATH.
Recommended:
- Use REL inside RELATED sections (PATH labels allowed only if that section is “PATH ONLY”).
- Use XREF inside XREF sections (UID-only absolute).

If a module standard requires UID-only everywhere:
- Use XREF only.

---

## 6) HARD FAIL CONDITIONS
FAIL IF any:
- XREF contains URL/RAW
- XREF contains PATH or filesystem location
- XREF contains filename instead of UID
- Missing WHY
- Target UID not present / unknown / malformed
- XREF used as “navigation directory”

---

## 7) VALIDATION CHECKLIST (COPY)
XREF VALIDATION:
- [ ] All targets are UIDs
- [ ] No URL/RAW/PATH present
- [ ] WHY present for each
- [ ] One target per line
- [ ] Targets are stable canonical IDs

Result: PASS/FAIL

---

## 8) EXAMPLES
Example (good):
XREF:
- XREF: UE.KB.MAP.TASK_SCOPE.001 | WHY: task→scope selection uses this map
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relations vocabulary used for related blocks

Example (bad):
- XREF: 04_KNOWLEDGE_BASE/10_TOPICS/... (PATH)  => FAIL
- XREF: https://raw.github... (URL)            => FAIL

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relation vocabulary complements XREF policy

--- END.
