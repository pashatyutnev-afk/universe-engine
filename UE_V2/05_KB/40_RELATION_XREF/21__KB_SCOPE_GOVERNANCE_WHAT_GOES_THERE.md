# KB — KB_SCOPE.GOVERNANCE: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/21__KB_SCOPE_GOVERNANCE_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.GOVERNANCE.021
OWNER: SYSTEM
ROLE: Define the boundaries and mandatory content rules for KB_SCOPE.GOVERNANCE: protocols and dictionaries that make KB usage deterministic (RAW-only navigation behavior, traceability, anti-drift, maps/dicts rules, master-index existence discipline). Prevents mixing governance with domain craft.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.GOVERNANCE boundaries and content rules (protocols + dictionaries + existence discipline)."
- REASON: "Governance must be stable and enforceable; without boundaries entities drift into invention and navigation breaks."
- IMPACT: "All entity runs start with the same governance baseline; KB remains executable and auditable."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.021

---

## 0) PURPOSE (KB)
KB_SCOPE.GOVERNANCE is the operational baseline that makes KB usage deterministic:
- how entities are allowed to use KB
- how navigation works (master index RAW-only)
- how memory reuse is controlled (anti-drift)
- how gaps are handled (create module vs hard stop)
- how relations/XREF are written (UID-only policy)
- how QA/audit is performed (KB integrity)

Governance is required before any domain work.

---

## 1) ABSOLUTE BOUNDARIES
Governance must NOT:
- teach domain craft methods (belongs to KB_SCOPE.TOPICS.*)
- contain story/music/marketing toolkits (domain topics)
- contain RAW link registries beyond the single KB master index
- become a “second master index” or alternate entrypoint

Governance MAY:
- define rules, policies, standards, dictionaries, and audits
- define selection maps (scope selection) as governance tooling
- reference other governance modules by UID-only (no URL/PATH)

---

## 2) ALLOWED GOVERNANCE CONTENT TYPES
Allowed:
G1) META PROTOCOLS
- KB usage protocol (no-fantasy, trace rules)
- navigation standard (master index SoT)
- excerpting & memory reuse rules
- gap handling protocol
- QA & audit checks

G2) DICTIONARIES / REFERENCE ASSETS
- relation types enum (REL vocabulary)
- XREF UID-only reference rules
- other stable enums used across KB

G3) MAPS (SELECTION LOGIC)
- task → scope selection map
- entity → scope selection map
- scope → folder orientation map (non-navigation)

G4) MASTER-INDEX DISCIPLINE
- registration rules (existence)
- deprecation pointer standards (to prevent duplicates)

---

## 3) FORBIDDEN GOVERNANCE CONTENT TYPES
Forbidden:
- domain “how-to” methods (scene craft, hook engineering, SEO recipes)
- production pipeline step instructions (belongs to Production topics)
- lists of RAW links inside governance modules (must live in master index only)
- unstructured essays without fail conditions

---

## 4) REQUIRED STRUCTURE (MINIMUM)
Any governance module should include:
- Purpose
- Absolute rules
- Definitions (strict)
- Procedure (if protocol/map)
- Fail conditions (hard stop)
- Examples (pass/fail)
- Related (UID-only where required)
- Compliance section

---

## 5) HOW ENTITIES MUST USE GOVERNANCE (MANDATORY FLOW)
Step 1: Confirm governance minimum set exists (registered in master index).  
Step 2: Load/open governance modules via KB master index (RAW-only) OR trusted memory reuse (no drift).  
Step 3: Only then select domain scope (topics) and open domain modules.  
Step 4: Produce output with KB_SOURCES trace.

---

## 6) GOVERNANCE MINIMUM SET (REFERENCE)
This standard does not redefine the list; it points to the minimum-set module:
- UID: UE.KB.STD.SCOPE.GOVERNANCE_MIN.009

Rule:
- If governance minimum set is missing → STOP or create it first (gap fill protocol).

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- domain work starts without governance baseline
- governance module includes RAW links as navigation (other than master index SoT rule)
- governance module provides domain craft methods
- XREF contains URL/PATH or non-UID targets
- multiple “master indexes” appear

---

## 8) EXAMPLES
GOOD governance:
- “KB master index navigation standard”
- “Excerpting and memory reuse rules”
- “XREF UID-only reference rules”
- “Task→scope map”

BAD governance:
- “How to write a great chorus” (domain topic)
- “All marketing strategies” (domain topic)
- “List of all KB RAW links” (master index job)

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.GOVERNANCE_MIN.009 | WHY: defines mandatory governance baseline set
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: usage protocol is governance core
- XREF: UE.KB.TOPIC.META.NAV.002 | WHY: master index navigation standard is governance core
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relation vocabulary used across governance and topics
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossref rules used everywhere
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: existence rule for KB modules
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: prevents duplicate truths via deprecation pointers

--- END.
