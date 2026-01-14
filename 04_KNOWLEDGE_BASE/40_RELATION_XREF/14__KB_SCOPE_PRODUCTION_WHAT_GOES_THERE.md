# KB — KB_SCOPE.TOPICS.PRODUCTION: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/14__KB_SCOPE_PRODUCTION_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.PRODUCTION.014
OWNER: SYSTEM
ROLE: Define the boundaries and required content types for Production topics: pipelines, workflows, handoffs, format adaptation, release packs, and QA gates. Ensures production is operational and reusable across domains.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.TOPICS.PRODUCTION boundaries: pipelines, handoffs, release packs, and QA gates."
- REASON: "Production is the glue layer; without boundaries it drifts into domain craft or becomes vague project management."
- IMPACT: "Entities can execute consistent production workflows with deterministic handoffs and release readiness."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.014

---

## 0) PURPOSE (KB)
Production topics define how work becomes a deliverable:
- pipeline steps
- roles/handoffs
- formats and adaptations
- QA gates and rubrics
- packaging and release packs

Production is domain-agnostic where possible and supports multiple domains.

---

## 1) ABSOLUTE BOUNDARIES
Production topics must NOT:
- teach domain craft in depth (belongs to domain topics)
- redefine KB governance (belongs to META/GOVERNANCE)
- become navigation indexes (belongs to master index)

Production topics MAY:
- reference domain topics by UID-only when needed for a pipeline step.

---

## 2) ALLOWED PRODUCTION TOPIC TYPES
Allowed:
- PIPELINES (step-by-step workflows)
- HANDOFF STANDARDS (what inputs/outputs must be passed)
- FORMAT ADAPTATION (book/series/shorts/game)
- RELEASE PACK CHECKLISTS (what must ship)
- QA GATES / RUBRICS (PASS/REWORK/FAIL)
- VERSIONING/DELIVERY NAMING (delivery discipline, packaging rules)

---

## 3) FORBIDDEN PRODUCTION CONTENT
Forbidden:
- "how to write dialogue" (narrative craft)
- "how to engineer hooks" (music craft)
- "how to do SEO" (marketing craft)
- “KB rules” (meta)
- embedding RAW links or acting as index

---

## 4) REQUIRED STRUCTURE (MINIMUM)
Each Production topic should include:
- Purpose
- When to use
- Definitions
- Inputs/Outputs
- Procedure (pipeline steps)
- Handoff templates (copy)
- QA gates (pass/rework/fail)
- Related (UID-only where required)
- Compliance (source lock, trace if needed)

---

## 5) CORE ASSETS PRODUCTION MUST GOVERN
- Release Pack: inventory of artifacts to ship
- Variant Strategy: full/short/loop/instrumental (if relevant)
- Quality Gates: translation checks, naturalness checks, regression guards
- Versioning: how versions advance and how changes are recorded

---

## 6) HOW ENTITIES USE PRODUCTION TOPICS
- ORC uses production topics to orchestrate steps and handoffs.
- CTL uses production topics to enforce readiness and constraints.
- VAL/QA uses production topics to apply gates and rubrics.
- SPC/ENG uses production topics when their output is part of a pipeline.

---

## 7) EXAMPLES
GOOD PRODUCTION TOPIC:
- "Release Pack Checklist"
- "Versioning & Delivery Naming"
- "QA Gates & Rubrics"

BAD PRODUCTION TOPIC:
- "All about cinematography" (visual craft)
- "How to write marketing hooks" (marketing craft)
- "KB master index rules" (meta)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.TOPICS.011 | WHY: production is a topics domain and follows topics standard
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: production outputs must follow no-fantasy and trace
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossrefs in production modules

--- END.
