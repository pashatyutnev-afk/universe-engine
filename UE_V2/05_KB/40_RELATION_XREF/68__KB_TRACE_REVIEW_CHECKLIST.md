# KB — RUN TRACE REVIEW CHECKLIST (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/68__KB_TRACE_REVIEW_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: CHECKLIST
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.CHK.TRACE_REVIEW.068
OWNER: SYSTEM
ROLE: Deterministic checklist to review RUN_TRACE blocks: UID-only compliance, flag coherence, web lookup disclosure correctness, and minimal-but-sufficient source listing.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created run trace review checklist to validate trace integrity."
- REASON: "Trace must be truthful and consistent; otherwise audits and certifications are meaningless."
- IMPACT: "Reliable trace verification for QA/VAL and certification workflows."
- CHANGE_ID: UE.CHG.2026-01-14.KB.CHK.068

---

## 0) PURPOSE (KB)
Validate that a run’s trace:
- is present and structured
- uses UID-only references
- has coherent flags
- discloses web lookup correctly
- lists sources minimally but sufficiently

---

## 1) CHECKLIST (RUN ORDER)
T1 — Trace block present
- [ ] RUN_TRACE exists
FAIL if missing.

T2 — KB_SOURCES present when KB used
- [ ] KB_SOURCES list exists and has entries
REWORK if too few entries; FAIL if empty while KB was used.

T3 — UID-only compliance
For every KB_SOURCES line:
- [ ] Uses UID, not URL/PATH/filename
- [ ] Contains `| WHY:`
FAIL if any violation.

T4 — Flag coherence
- [ ] MEMORY_REUSE is YES if remembered content used
- [ ] STATUS_USED is MIXED if any DRAFT used
- [ ] STATUS_USED is ACTIVE_ONLY only if all sources are ACTIVE and no drafts used
FAIL if contradictions.

T5 — Web lookup disclosure
- [ ] WEB_LOOKUP_USED is YES if external lookup influenced decisions
- [ ] If YES: WEB_LOOKUP_NOTICE included
FAIL if lookup used but not disclosed.

T6 — No deprecated authority
- [ ] Trace does not cite deprecated modules as authority (pointer-only resolution allowed but must cite canon)
FAIL if deprecated authority used.

T7 — Minimal but sufficient listing
- [ ] Sources listed are the actual drivers (not a giant list)
REWORK if list is bloated or missing key drivers.

---

## 2) RESULT RULES
PASS IF:
- T1, T3, T4, T5 PASS
- T2 PASS or acceptable with explanation
- no deprecated authority

REWORK IF:
- source list needs cleanup (T2/T7)
- minor incoherence that can be fixed without re-running work

FAIL IF:
- missing trace
- UID-only violation
- web lookup not disclosed
- flags contradict reality
- deprecated authority used

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- any URL/PATH appears in KB_SOURCES
- WEB_LOOKUP_USED is NO while lookup occurred
- STATUS_USED marked ACTIVE_ONLY while drafts were used
- MEMORY_REUSE marked NO while reusing memory

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: defines minimum trace block format
- XREF: UE.KB.TPL.WEB_LOOKUP_NOTICE.035 | WHY: required when lookup is used
- XREF: UE.KB.POL.ENTITY_ACCESS.031 | WHY: status-based access and deprecated restrictions
- XREF: UE.KB.RULE.NO_FANTASY_EXEC.063 | WHY: execution integrity depends on truthful trace

--- END.
