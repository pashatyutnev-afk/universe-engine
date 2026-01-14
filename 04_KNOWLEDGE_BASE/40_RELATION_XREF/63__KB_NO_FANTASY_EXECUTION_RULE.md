# KB — NO-FANTASY EXECUTION RULE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/63__KB_NO_FANTASY_EXECUTION_RULE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: RULE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.NO_FANTASY_EXEC.063
OWNER: SYSTEM
ROLE: Enforces non-fiction, source-anchored execution when using KB and world knowledge: no invention, deterministic use of modules, strict handling of uncertainty, memory reuse rules, and mandatory disclosure of external lookup.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB no-fantasy execution rule: source-anchored outputs, uncertainty labeling, memory reuse discipline."
- REASON: "Quality and safety depend on preventing invented facts and silent drift; this rule makes execution auditable."
- IMPACT: "Entities produce factual, reproducible outputs with explicit confidence and clear stop conditions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULE.063

---

## 0) PURPOSE (LAW)
Prevent invention and drift when executing with KB:
- use what exists (KB modules, source records)
- do not fabricate facts or sources
- label uncertainty
- disclose web lookup
- stop when required inputs are missing

---

## 1) ABSOLUTE RULES
R1 — No invented facts
- If a claim is not supported by KB modules (or recorded source provenance), it must not be stated as FACT.

R2 — No invented sources
- Never fabricate citations, books, standards, or URLs.
- If source records do not exist, mark provenance as missing and stop or ingest.

R3 — Deterministic KB usage
- Prefer ACTIVE modules.
- Follow procedures as written.
- Do not alter rules “to be nicer” unless allowed by module itself.

R4 — Uncertainty must be labeled
Any uncertain claim must be labeled as:
- HYPOTHESIS with confidence LOW/MED/HIGH
and include a validation path.

R5 — Memory reuse is allowed but must not drift
- If a module was previously opened and remembered:
  - reuse must preserve meaning (no distortion)
  - if unsure, re-open source via master index
- Memory reuse must be declared in trace.

R6 — Web lookup disclosure
- If external browsing influenced output:
  - disclose via WEB_LOOKUP_NOTICE
  - do not treat it as operational truth unless ingested into KB

---

## 2) FACT / HEURISTIC / OPINION / HYPOTHESIS (MANDATORY)
Classification rules:
- FACT: verifiable and stable; backed by KB or source record
- HEURISTIC: best practice; allowed but must be labeled
- OPINION: subjective; label explicitly
- HYPOTHESIS: uncertain; must include validation path

Default:
- If unsure → HEURISTIC or HYPOTHESIS, never FACT.

---

## 3) STOP RULES (HARD STOPS)
Stop the run (or switch to gap fill) if:
- governance baseline missing
- required KB module missing/unregistered
- required pack slot not satisfiable and no gap fill plan allowed
- conflicting sources for critical claims are unresolved
- trace cannot be produced

---

## 4) REQUIRED TRACE (MINIMUM)
Every execution must output:
KB_SOURCES:
- XREF: <KB_MODULE_UID> | WHY: <used for>
MEMORY_REUSE: YES/NO
STATUS_USED: ACTIVE_ONLY | MIXED
WEB_LOOKUP_USED: YES/NO

If WEB_LOOKUP_USED: YES:
- include WEB_LOOKUP_NOTICE template output.

---

## 5) COMMON VIOLATIONS
Violation V1: "I think / probably / likely" stated as FACT
- Fix: label as HYPOTHESIS + confidence + validation path

Violation V2: Using DEPRECATED as authority
- Fix: follow pointer to replacement UID

Violation V3: Using web result without ingestion
- Fix: ingest into KB + source records; or state it’s provisional

Violation V4: Memory drift
- Fix: re-open module; do not paraphrase beyond meaning

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- any invented fact is asserted as sourced truth
- any invented source is cited
- web lookup used but not disclosed
- deprecated authority used
- uncertainty not labeled where present
- trace is missing

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.TPL.WEB_LOOKUP_NOTICE.035 | WHY: mandatory disclosure for live web lookup
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: world knowledge ingestion and authority tiers
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: provenance via source records
- XREF: UE.KB.TPL.PROVENANCE_BLOCK.033 | WHY: provenance block for modules using world knowledge
- XREF: UE.KB.POL.ENTITY_ACCESS.031 | WHY: access control prevents using deprecated authority

--- END.
