# KB — COMPETENCE PACK AUTHORING PLAYBOOK (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/70__KB_PACK_AUTHORING_PLAYBOOK.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PLAYBOOK
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PLAYBOOK.PACK_AUTHOR.070
OWNER: SYSTEM
ROLE: Step-by-step playbook for authoring professional competence packs: define scope, ingest world knowledge if needed, build capability map, add templates/checklists/failure modes, define QA gates, validate tags, and register in master index.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created competence pack authoring playbook (deterministic creation workflow)."
- REASON: "Packs drive specialist quality; authoring must be consistent, operational, and auditable."
- IMPACT: "Higher-quality packs, faster onboarding, fewer vague modules."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PLAYBOOK.070

---

## 0) PURPOSE (KB)
Provide a deterministic workflow to create a competence pack that:
- is operational (methods + templates)
- is testable (QA gates)
- uses canonical tags
- has provenance when needed
- can be bound to entities safely

---

## 1) INPUTS
- Role target (entity role)
- Domain (music/narrative/...)
- Gap or requirement (missing slot/tags)
- Desired strength level (L1/L2/L3)

---

## 2) AUTHORING FLOW (DETERMINISTIC)
### Step 1 — Define scope boundary
- What the pack covers
- What it explicitly does not cover
- Primary domain and role focus

### Step 2 — Determine required tags and slots
- Use skill tag taxonomy
- Select 10–30 relevant tags (core + QA)
- Identify which PACK_SLOT(s) this pack supports

### Step 3 — Gather sources (if non-trivial)
- If pack includes non-obvious factual claims:
  - create source records
  - add provenance block

### Step 4 — Create capability map
- Define capabilities C01..Cn (recommended ≥ 5)
- For each:
  - inputs/outputs
  - deterministic steps
  - constraints

### Step 5 — Add templates (cards)
- Capability card template
- QA gate card
- Checklist templates
- Failure mode cards
Optional:
- playbook branching template
- drills template

### Step 6 — Add checklists
- pre-flight
- execution
- post-flight

### Step 7 — Add failure modes
- at least 3 with detection/fix/re-test

### Step 8 — Define QA gates
- pass/rework/fail for each capability
- anti-water checks
- strength classification (L1/L2/L3)

### Step 9 — Validate tags
- ensure all tags exist in taxonomy
- ensure 1–3 tags per capability

### Step 10 — Register and bind
- register pack in KB master index
- bind to at least one entity (if applicable)
- update scorecard for that entity/domain

### Step 11 — Validate with QA standard
- run competence pack QA gates
- if PASS, consider promotion to ACTIVE

---

## 3) OUTPUT CHECKLIST (MINIMUM)
A completed pack must include:
- scope boundary
- ≥5 capabilities (recommended)
- templates index
- checklists
- failure modes
- QA gates
- canonical tags
- provenance if needed
- master-index registration

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- pack is vague (anti-water fails)
- tags not canonical
- no templates/cards exist
- no QA gates exist
- pack not registered in master index
- pack mixes unrelated domains without split

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: pack structure standard
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: QA gates for packs
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical tag taxonomy
- XREF: UE.KB.PROC.WORLD_INGEST.034 | WHY: ingest workflow for world knowledge
- XREF: UE.KB.TPL.PROVENANCE_BLOCK.033 | WHY: provenance template
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: registration/existence rule

--- END.
