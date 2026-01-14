# KB — RULES (GOVERNANCE LAW) (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 00_KB_GOVERNANCE
DOC_TYPE: RULE
INDEX_TYPE: GOVERNANCE_RULESET
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULES.GOV.001
OWNER: SYSTEM
ROLE: Operational rule set for Knowledge Base usage: RAW-only navigation, UID-only XREF, no-fantasy execution, trace discipline, ACTIVE-first access, and hard-stop protocols for gaps/contradictions.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Established KB governance rules: deterministic NAV, no-fantasy, trace, ACTIVE-first, and stop/ingest protocols."
- REASON: "KB is the quality backbone; rules must prevent drift, invention, and broken navigation."
- IMPACT: "Entities use KB reproducibly; audits and certification become possible."
- CHANGE_ID: UE.CHG.2026-01-14.KB.GOV.RULES.001

---

## 0) PURPOSE (LAW)
These rules govern how ANY entity uses the Knowledge Base.
They apply before domain knowledge.

---

## 1) NAVIGATION LAW (ABSOLUTE)
R1 — Single entrypoint
- KB navigation/existence authority is ONLY:
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

R2 — RAW-only navigation
- Any KB module must be opened via RAW link from the master index.
- PATH is a label only; PATH must not be used as navigation mechanism.

R3 — Existence rule
- If a KB file is not registered in the master index, it is NON-CANON / ignored operationally.

---

## 2) NO-FANTASY EXECUTION (ABSOLUTE)
R4 — No invented facts
- Do not state as FACT anything not supported by:
  - opened KB modules (from master index), OR
  - already-opened modules reused from memory without distortion.

R5 — No invented sources
- Never fabricate citations, standards, URLs, or “I read it somewhere”.

R6 — Missing knowledge → STOP or GAP
- If required knowledge is missing:
  - STOP, OR
  - create a GAP record and follow ingest workflow.
- No “silent fill” by guessing.

---

## 3) XREF / REL DISCIPLINE (ABSOLUTE)
R7 — UID-only XREF
- Operational cross-references MUST be UID-only.
- URLs/PATH must not appear in XREF authority blocks.

R8 — REL is semantic, XREF is linking
- REL types express meaning (depends_on, governed_by, validated_by, supersedes).
- XREF lists related UIDs for navigation-of-meaning (not URLs).

---

## 4) TRACE DISCIPLINE (MANDATORY)
R9 — Every KB-driven output must include RUN_TRACE
Minimum fields:
- KB_SOURCES (UID-only) + WHY
- MEMORY_REUSE: YES/NO
- STATUS_USED: ACTIVE_ONLY | MIXED
- WEB_LOOKUP_USED: YES/NO (+ notice if YES)

R10 — No trace, no authority
- If trace is missing, output must not claim compliance/authority.

---

## 5) ACCESS POLICY (ACTIVE-FIRST)
R11 — ACTIVE-first
- Prefer ACTIVE modules.
- If any DRAFT module is used → STATUS_USED must be MIXED.

R12 — DEPRECATED is not authority
- Deprecated modules may be used only as pointers to replacements.

---

## 6) HARD STOPS (GATES)
R13 — Stop on contradictions (critical)
- If CRITICAL/MAJOR contradiction is detected and unresolved:
  - STOP or trigger contradiction protocol.
- Do not proceed as if resolved.

R14 — Stop on governance missing
- If governance minimum set is missing/unavailable:
  - STOP.

R15 — Stop on broken navigation
- If RAW links are missing/broken for required modules:
  - STOP and fix master index integrity.

---

## 7) CREATION / UPDATE DISCIPLINE (CONTROL)
R16 — Version + change note
- Any meaningful change requires version bump and CHANGE_NOTE update.

R17 — Audit for high impact
- Mandatory audit events for:
  - governance changes
  - taxonomy changes
  - master index changes
  - deprecations/replacements
  - certifications

R18 — No duplicates
- Do not create duplicate “same meaning” modules.
- Aliases are POINTER-only.

---

## 8) MINIMUM GOVERNANCE SET (OPERATIONAL)
For any KB run, the minimum governance context is:
- this file (RULES KB)
- XREF rules
- REL types
- doc control (when creating/updating/certifying)

---

## 9) HARD FAIL CONDITIONS (ABSOLUTE)
FAIL IF:
- KB navigation not via master index RAW
- unregistered file treated as existing
- any invented fact/source presented as KB-backed truth
- URL/PATH used as operational authority reference (instead of UID-only)
- trace omitted or lied about
- deprecated module treated as authority

---

## 10) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: minimum trace structure
- XREF: UE.KB.RULE.NO_FANTASY_EXEC.063 | WHY: execution integrity baseline
- XREF: UE.KB.PROC.GAP_HANDLING.066 | WHY: how to handle missing knowledge
- XREF: UE.KB.PROC.CONTRADICTIONS.065 | WHY: how to handle contradictions
- XREF: UE.KB.CHK.MASTER_INDEX_INTEGRITY.071 | WHY: index integrity gate

--- END.
