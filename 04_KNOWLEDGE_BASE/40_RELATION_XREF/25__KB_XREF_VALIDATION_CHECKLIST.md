# KB — XREF VALIDATION CHECKLIST (UID-ONLY) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/25__KB_XREF_VALIDATION_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: CHECKLIST
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.CHK.XREF_VALIDATE.025
OWNER: SYSTEM
ROLE: Deterministic checklist to validate XREF blocks for UID-only compliance across KB modules. Prevents URLs/PATH/filenames in XREF and enforces WHY on every line.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created UID-only XREF validation checklist with common failure patterns."
- REASON: "XREF drift is a primary failure mode; a repeatable checklist enables audits and prevents silent non-compliance."
- IMPACT: "Entities and reviewers can quickly PASS/FAIL XREF compliance for any KB module."
- CHANGE_ID: UE.CHG.2026-01-14.KB.CHK.025

---

## 0) PURPOSE (KB)
Validate that any XREF block:
- uses UID-only targets
- includes WHY for each line
- contains no URLs, RAW links, or PATH references
- is minimal and relevant

---

## 1) CHECKLIST (RUN ORDER)
### C1 — XREF block exists
- [ ] XREF block exists (if module schema requires it)
FAIL if missing.

### C2 — UID-only targets
For every line:
- [ ] Target is a UID (not path, not filename, not URL)

FAIL triggers:
- contains `http://` or `https://`
- contains `/` folder separators typical of repo paths
- contains `.md` filename
- contains `RAW:` or `PATH:`

### C3 — WHY present on each line
- [ ] Each XREF line includes `| WHY: ...`
FAIL if any line missing WHY.

### C4 — One UID per line
- [ ] Each XREF line contains exactly one UID
FAIL if multiple UIDs in one line.

### C5 — No navigation content
- [ ] XREF does not act as a link hub or navigation directory
FAIL if it lists many links without reasons or tries to replace master index.

### C6 — Relevance and minimality
- [ ] XREF list is minimal (usually 2–8 items)
- [ ] Each WHY explains necessity
REWORK if too long or redundant.

### C7 — Canonical target existence (best effort)
- [ ] Targets should be stable canonical UIDs (not placeholder text)
FAIL if placeholders like `<UID>` remain.

---

## 2) COMMON FAIL PATTERNS
FP1: PATH used as target
- XREF: 04_KNOWLEDGE_BASE/...  => FAIL

FP2: RAW/URL used as target
- XREF: https://raw... => FAIL

FP3: filename used
- XREF: 01__SOMETHING.md => FAIL

FP4: missing WHY
- XREF: UE.KB.... (no WHY) => FAIL

FP5: multiple UIDs per line
- XREF: UID1, UID2 => FAIL

---

## 3) PASS/REWORK/FAIL RULES
PASS IF:
- C1..C5 PASS
- C6 not worse than REWORK
- no placeholders remain

REWORK IF:
- minimality/relevance issues only (C6)
- but UID-only compliance is clean

FAIL IF:
- any of C1..C5 FAIL
- placeholders remain (C7)

---

## 4) QUICK FIX PROCEDURE
If FAIL:
- replace PATH/URL/filename with correct UID
- add WHY for each line
- split multiple UIDs into separate lines
- remove redundant entries

If REWORK:
- remove non-essential entries
- tighten WHY text

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: canonical uid-only xref policy
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relation vocabulary (when combining REL + XREF)
- XREF: UE.KB.STD.RELATION_MODEL.024 | WHY: defines how XREF coexists with REL

--- END.
