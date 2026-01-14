# KB — WEB LOOKUP USAGE NOTICE (TEMPLATE) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/35__KB_WEB_LOOKUP_USAGE_NOTICE_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.WEB_LOOKUP_NOTICE.035
OWNER: SYSTEM
ROLE: Canonical template for declaring live web lookup usage during a run, including what was looked up, why, what was ingested into KB (if any), and confidence limits. Prevents silent fallback and preserves determinism.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created web lookup usage notice template to declare external lookup and its limits."
- REASON: "Live web is non-deterministic; if used, it must be explicitly disclosed and converted into KB modules for future determinism."
- IMPACT: "Transparent runs, reduced hallucination risk, and a clear path to ingestion."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.035

---

## 0) PURPOSE (KB)
When live web lookup is used, the run must disclose it:
- what was queried
- why it was necessary
- what tier of sources was used
- what was ingested into KB (if applicable)
- what remains uncertain

This is a notice template; it does not store the knowledge itself.

---

## 1) WEB LOOKUP NOTICE (COPY)
WEB_LOOKUP_NOTICE:
- USED: YES/NO
- WHY: <freshness / niche detail / verification / contradiction resolution>
- QUERIES:
  - Q: "<query text>"
  - Q: "<query text>"
- SOURCE_TIERS_USED: <T2/T3/T4> (as applicable)
- SUMMARY_OF_FINDINGS:
  - <short bullet, no long quotes>
- LIMITS:
  - <what could be outdated/uncertain>
- ACTION:
  - INGEST_REQUIRED: YES/NO
  - IF YES: create/update KB module(s) + source records
  - SOURCE_RECORD_UIDS: <list> (if created)
- CONFIDENCE: HIGH/MED/LOW

---

## 2) RULES (STRICT)
- Do not hide web lookup usage.
- Do not treat web lookup as operational guidance unless ingested into KB.
- Do not paste large verbatim content from web sources.
- Prefer primary sources; record source tier.

---

## 3) WHEN THIS NOTICE IS REQUIRED
Required if:
- any external browsing influenced decisions, rules, or factual claims
- the user asked for “latest/current”
- niche technical details were verified via web

Not required if:
- run uses only KB and internal canon (RAW) with no browsing.

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- web lookup was used but not disclosed
- web results are treated as operational truth without ingestion
- long verbatim copying from web
- claims presented as FACT with no provenance path

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: governs world knowledge ingestion and tiers
- XREF: UE.KB.PROC.WORLD_INGEST.034 | WHY: workflow to ingest web findings into KB
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: provenance via source records
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: no-fantasy + trace discipline

--- END.
