# KB — WORLD KNOWLEDGE INGEST WORKFLOW (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/34__KB_WORLD_KNOWLEDGE_INGEST_WORKFLOW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PROC.WORLD_INGEST.034
OWNER: SYSTEM
ROLE: Deterministic workflow for converting external world knowledge into stable KB modules: research → source records → synthesis → module creation → QA/audit → master-index registration → refresh scheduling.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created deterministic world knowledge ingest workflow for KB."
- REASON: "Entities must benefit from global knowledge without improvisation; ingestion must be auditable and repeatable."
- IMPACT: "Consistent KB expansion with provenance, controlled confidence, and reduced drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PROC.034

---

## 0) PURPOSE (KB)
Turn external knowledge into operational KB modules safely:
- capture provenance as source records
- synthesize into deterministic methods (not copied text)
- validate quality and contradictions
- register in master index for existence
- schedule refresh for volatile sources

---

## 1) INPUTS / OUTPUTS
INPUTS:
- A target skill/knowledge gap (what entities need)
- Candidate external sources (papers/standards/docs)
- Target KB scope and module type (topic/standard/checklist)

OUTPUTS:
- SOURCE RECORD(s) (stable provenance)
- KB module (atomic, operational)
- QA result (PASS/REWORK/FAIL)
- Master-index registration entry
- Refresh notes (if needed)

---

## 2) WORKFLOW (DETERMINISTIC)
### Step 1 — Define the gap precisely
- What task fails without this knowledge?
- Which entity class needs it?
- Which KB_SCOPE should contain it?

### Step 2 — Find sources (tier-first)
- Prefer T2/T1 tiers: standards, official docs, papers.
- Use lower tiers only to discover better sources.

### Step 3 — Create SOURCE RECORDS
For each chosen source:
- assign SOURCE_RECORD_UID
- record stable identifiers (DOI/ISBN/standard ID)
- record date accessed + tier + default confidence
- record scope limits

### Step 4 — Extract method (synthesis)
Convert external info into:
- definitions
- step-by-step procedure
- templates/cards
- QA gates (pass/rework/fail)
Label content:
- FACT vs HEURISTIC vs HYPOTHESIS

### Step 5 — Create KB module (atomic)
- choose module type (TOPIC/STANDARD/CHECKLIST/etc.)
- follow KB module schema standard
- include provenance block if world knowledge is used

### Step 6 — Contradiction check
If sources conflict:
- record conflict in provenance
- resolve using tier order or mark as hypothesis
- block ACTIVE promotion if unresolved and high-stakes

### Step 7 — QA / Audit
Run checks:
- schema completeness
- scope boundary purity
- no invention
- operational templates present
- XREF UID-only compliance
- relation semantics correctness

### Step 8 — Register in master index
- add PATH label + RAW link entry
- include UID and status if the index schema supports it
- enforce existence rule (unregistered = non-existent)

### Step 9 — Promote lifecycle (optional)
- keep as DRAFT until enough examples/tests exist
- promote to ACTIVE when ready (per status/lock policy)

### Step 10 — Refresh scheduling
- set refresh interval based on source type
- record next review date if volatile
- if a source updates, ingest delta as KB change with version bump

---

## 3) QUALITY GATES (PASS/FAIL)
PASS IF:
- source records exist for non-trivial claims
- module is atomic and operational (procedure + templates + QA)
- provenance block present when world knowledge is used
- registered in master index
- no URL/PATH in XREF
- contradictions handled or labeled

REWORK IF:
- module operational but lacks examples or clarity
- provenance exists but confidence labeling incomplete

FAIL IF:
- missing provenance for core claims
- copied large verbatim text
- invention/hallucinated facts
- unregistered module treated as operational

---

## 4) “DO NOT DO” LIST
- do not browse and then execute from memory without ingestion
- do not store external URLs as XREF targets
- do not turn KB into a dump of copied articles
- do not promote to ACTIVE with unresolved contradictions

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: authority tiers and ingestion principles
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: source record schema
- XREF: UE.KB.TPL.PROVENANCE_BLOCK.033 | WHY: provenance block template
- XREF: UE.KB.STD.MODULE_SCHEMA.023 | WHY: KB module schema (required)
- XREF: UE.KB.TOPIC.META.QA_AUDIT.005 | WHY: audit and QA checks
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: registration/existence rule

--- END.
