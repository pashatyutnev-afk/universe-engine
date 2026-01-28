# KB — KB_SCOPE.TOPICS: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/11__KB_SCOPE_TOPICS_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.TOPICS.011
OWNER: SYSTEM
ROLE: Define the purpose and strict content rules for KB_SCOPE.TOPICS domain modules: what topics are, how they must be atomic/operational, and what must never be placed inside Topics (navigation laws, RAW links, governance).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.TOPICS content boundaries, module structure, and operational requirements."
- REASON: "Topics are the main quality backbone for specialist competence; without boundaries Topics drift into indexes or essays."
- IMPACT: "Domain knowledge becomes reusable, auditable, and executable by entities with consistent structure and QA gates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.011

---

## 0) PURPOSE (KB)
KB_SCOPE.TOPICS holds domain competence modules that teach entities how to do work:
- operational methods
- professional toolkits
- checklists and gates (domain-level)
- templates/cards for execution
- repeatable procedures

Topics are designed to make specialists “super-pro” in their domain.

---

## 1) ABSOLUTE BOUNDARIES (NO MIXING)
Topics must NOT contain:
- RAW links (navigation belongs to master index)
- folder indexes or existence registries (navigation/governance)
- system law authority text (laws live in 01_SYSTEM_LAW)
- “how KB works” protocols (belongs to META/GOVERNANCE)

Topics MAY reference other modules:
- via UID-only XREF, or via allowed RELATED blocks per module standard.

---

## 2) ALLOWED TOPIC CONTENT TYPES
Allowed:
1) METHOD (step-by-step)
- deterministic procedure with inputs/outputs

2) TOOLKIT
- a set of techniques + decision rules + examples

3) QUALITY GATES (domain)
- pass/rework/fail criteria specific to the domain

4) TEMPLATES / CARDS
- copy blocks for consistent execution (scorecards, briefs, direction cards)

5) PROFESSIONAL COMPETENCE PACKS
- “what a top specialist knows” expressed as operational rules, not essays

---

## 3) FORBIDDEN TOPIC CONTENT TYPES
Forbidden:
- navigation instructions that replace master index
- “random tips” without procedure or gates
- long essays without operational structure
- duplicated governance rules
- multiple unrelated functions in one file (breaks atomicity)

---

## 4) REQUIRED TOPIC STRUCTURE (MINIMUM)
Every TOPIC module must include:
- Purpose
- When to use / when not
- Definitions (strict)
- Inputs / Outputs (minimum)
- Procedure (step-by-step)
- Templates (copy)
- QA gates (PASS/REWORK/FAIL)
- Related (UID-only if required by XREF policy)
- Compliance (source lock / no fantasy / trace rule if applicable)

---

## 5) ATOMICITY RULE (STRICT)
One TOPIC = one operational function.
If a file grows too wide:
- split into 2–5 atomic topics
- keep a short “overview topic” only if it primarily maps to atomic topics (still not an index)

---

## 6) HOW ENTITIES USE TOPICS
Step 1: Determine task class and domain scope (via maps).  
Step 2: Load required governance baseline.  
Step 3: Open 1–3 core topics for the task (RAW-only).  
Step 4: Apply procedure and templates.  
Step 5: Run QA gates.  
Step 6: Output KB_SOURCES trace.

---

## 7) QUALITY RULES FOR TOPICS
- Topics should be actionable in a single run.
- Examples must demonstrate PASS and FAIL.
- Avoid platform/tool specificity unless needed.
- Keep language concrete; avoid vague advice.

---

## 8) EXAMPLES
GOOD TOPIC:
- “Hook Engineering” (procedure + hook card + QA tests)
- “Mix Translation QA” (matrix + defects + fixes + scorecard)

BAD TOPIC:
- “All about marketing” (too broad)
- “Index of all narrative docs” (navigation, not topic)

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: topics must follow no-fantasy and trace rules
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: topics must keep UID-only crossrefs (no URL/PATH)
- XREF: UE.KB.STD.SCOPE.REFERENCE.010 | WHY: reference scope boundaries complement topics scope

--- END.
