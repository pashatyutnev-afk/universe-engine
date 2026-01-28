# KB — MEMORY REUSE & REFRESH POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/64__KB_MEMORY_REUSE_AND_REFRESH_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.MEMORY_REFRESH.064
OWNER: SYSTEM
ROLE: Defines deterministic rules for reusing previously opened KB knowledge from memory without drift, when re-open via master index is required, and how to refresh volatile knowledge (world sources) over time.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created memory reuse and refresh policy to prevent drift while enabling efficient runs."
- REASON: "Entities often reuse knowledge; without rules, memory paraphrasing drifts and becomes fantasy."
- IMPACT: "Safe reuse of previously read modules, explicit refresh triggers, and auditable disclosure."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.064

---

## 0) PURPOSE (KB)
Define:
- when memory reuse is allowed
- how to avoid meaning drift
- when re-opening the module is mandatory
- how to refresh knowledge derived from changing external sources

---

## 1) ABSOLUTE RULES
R1 — Memory reuse must preserve meaning
- Reuse is allowed only if the assistant is confident the meaning is unchanged.
- If unsure, re-open module via master index.

R2 — Always declare memory reuse
- Any run that uses remembered content must set:
  - MEMORY_REUSE: YES

R3 — Never “upgrade” memory with assumptions
- Do not add new facts or rules not present in the remembered module.
- If new info is needed, ingest it properly.

R4 — Volatile knowledge requires refresh discipline
- Any module built from OFFICIAL_DOC/ARTICLE sources should be periodically reviewed.

---

## 2) MEMORY REUSE: ALLOWED VS REQUIRED RE-OPEN
### 2.1 Allowed memory reuse (no re-open required)
Allowed if all true:
- module is ACTIVE and LOCK FIXED
- usage is routine and low-risk
- no contradictions detected
- no need for exact wording or thresholds

### 2.2 Mandatory re-open
Re-open required if any true:
- high-risk task (governance, law, certification, deprecation)
- exact thresholds/wording matters
- contradiction or ambiguity appears
- module status might have changed since last use
- the run relies on multiple modules with tight dependencies
- the assistant is not confident about the exact directive

---

## 3) DRIFT GUARDS (HOW TO REUSE SAFELY)
When reusing from memory:
- restate only what is necessary
- avoid creative paraphrase of rules (keep close to original)
- do not invent examples as if they were in the module
- if user asks “are you sure” → re-open source

---

## 4) REFRESH POLICY FOR WORLD KNOWLEDGE
### 4.1 Refresh triggers
Refresh required when:
- SOURCE_RECORD DATE_ACCESSED exceeds its refresh interval
- official docs change version
- a contradiction is reported by newer higher-tier source
- entity outputs show regression linked to that knowledge

### 4.2 Refresh procedure (summary)
- re-check primary sources (tier-first)
- create updated source record(s)
- update KB module with version bump + change note
- record audit event
- if behavior changes, publish release notes

---

## 5) MINIMUM DISCLOSURE (TRACE)
Any run must emit:
MEMORY_REUSE: YES/NO
If YES:
- optionally list which module UIDs were reused from memory

If refresh was performed:
- disclose in audit/release notes (outside this policy’s scope)

---

## 6) PASS/FAIL
PASS IF:
- memory reuse is declared
- re-open occurs for high-risk cases
- no new facts are invented during reuse
- refresh triggers are respected for volatile knowledge

FAIL IF:
- memory reuse used as excuse to guess
- rules drift from original meaning
- high-risk tasks executed without re-open when needed
- volatile sources never refreshed

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- assistant outputs a rule as FACT while unsure and does not re-open
- contradictions detected but ignored
- memory reuse not declared
- refresh triggers ignored for volatile knowledge used in ACTIVE modules

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULE.NO_FANTASY_EXEC.063 | WHY: no-fantasy execution requires drift control
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: world knowledge ingestion and tiers
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: refresh intervals and access dates live in source records
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: refresh updates must be auditable

--- END.
