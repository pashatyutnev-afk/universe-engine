# KB — KB_SCOPE.META: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/12__KB_SCOPE_META_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.META.012
OWNER: SYSTEM
ROLE: Define the purpose and strict content rules for KB_SCOPE.META modules: KB operational protocols, navigation standards, anti-drift rules, audit/QA, and gap-handling. Prevents mixing meta governance with domain competence topics.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.META content boundaries and usage rules."
- REASON: "META ensures KB determinism and quality; mixing it with domain topics causes confusion and drift."
- IMPACT: "Entities can reliably follow KB protocols, navigation laws, and audit rules across all domains."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.012

---

## 0) PURPOSE (KB)
KB_SCOPE.META is the operational brain of KB:
- how KB is used
- how navigation works
- how memory reuse is controlled
- how gaps are handled
- how QA/audit is performed

META modules govern KB usage behavior (not domain craft).

---

## 1) ABSOLUTE BOUNDARIES (NO MIXING)
META must NOT contain:
- domain skill methods (narrative/music/marketing craft)
- content production guidelines specific to a domain
- long domain toolkits
These belong to:
- KB_SCOPE.TOPICS.<DOMAIN>

META MAY reference domain modules only as examples (UID-only).

---

## 2) ALLOWED META CONTENT TYPES
Allowed:
1) USAGE PROTOCOLS
- no-fantasy rule
- RAW-only navigation behavior
- trace requirements (KB_SOURCES)

2) NAVIGATION STANDARDS
- master index SoT
- existence rule
- sub-index role (maps vs registries)

3) ANTI-DRIFT / MEMORY RULES
- excerpting constraints
- memory reuse rules
- high-stakes triggers

4) GAP-HANDLING PROTOCOLS
- create module vs hard stop
- atomicity guidance

5) QA / AUDIT STANDARDS
- module-level and KB-wide checks
- deprecation policies (if grouped under meta; otherwise in xref standards)

---

## 3) FORBIDDEN META CONTENT TYPES
Forbidden:
- "how to write dialogue"
- "how to engineer hooks"
- "marketing title recipes"
(Those are topics.)

Forbidden:
- embedding RAW links (belongs to master index)
- turning a META module into a “second master index”

---

## 4) REQUIRED META STRUCTURE (MINIMUM)
Every META module should include:
- Purpose
- Rules (absolute)
- Definitions
- Procedure (if protocol)
- Fail conditions (hard stop)
- Examples (pass/fail)
- Related (UID-only where required)

---

## 5) HOW ENTITIES USE META
- META modules must be loaded as part of governance baseline.
- Entities must apply META rules before opening/using domain topics.
- META is referenced in KB_SOURCES trace whenever it governs the output.

---

## 6) QUALITY RULES (META)
- Must be deterministic (no vague advice).
- Must define fail conditions.
- Must not conflict with System Law; if conflict is discovered, META must defer to law authority order.

---

## 7) EXAMPLES
GOOD META:
- "KB master index navigation standard"
- "Excerpting and memory reuse rules"
- "KB QA & audit checks"

BAD META:
- "Best music production tips"
- "How to write marketing copy" (topic domain)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.GOVERNANCE_MIN.009 | WHY: META modules are part of governance minimum set
- XREF: UE.KB.STD.SCOPE.TOPICS.011 | WHY: topics boundary complements meta boundary
- XREF: UE.KB.STD.SCOPE.REFERENCE.010 | WHY: reference vs meta separation

--- END.
