# KB — PROFESSIONAL COMPETENCE PACK (STANDARD) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/36__KB_PROFESSIONAL_COMPETENCE_PACK_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.COMP_PACK.036
OWNER: SYSTEM
ROLE: Defines the canonical structure for “Professional Competence Packs” used by entities (especially specialists). Ensures each entity has: skill map, methods, tools, checklists, failure modes, and measurable quality gates.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced a universal competence pack standard for entity knowledge modules."
- REASON: "Quality depends on professional mastery; knowledge must be operational, testable, and reusable."
- IMPACT: "Entities can be trained/anchored by packs; QA can validate competence coverage."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.036

---

## 0) PURPOSE (LAW)
This standard defines how to store “what a professional must know and do”:
- not encyclopedic dumps
- operational capability (procedures + tools + gates)
- consistent across all entity classes

---

## 1) WHERE IT APPLIES
Applies to:
- SPC specialists (primary)
- ENG/ORC/CTL/VAL/QA (as needed)
- any domain pack (music, narrative, research, production, etc.)

---

## 2) COMPETENCE PACK — REQUIRED SECTIONS (MUST)
A competence pack is a KB module with the following blocks:

### 2.1 Competence Identity
- PACK_NAME
- TARGET_ENTITY_CLASS (SPC/ENG/ORC/CTL/VAL/QA)
- DOMAIN (music/narrative/world/research/etc.)
- SCOPE_BOUNDARY (what is included/excluded)
- PREREQUISITES (skills assumed)

### 2.2 Skill Map (Capabilities)
- CAPABILITIES list (C01..Cn)
Each capability includes:
- definition
- inputs
- outputs
- common contexts
- constraints

### 2.3 Core Methods (How-to)
For each capability:
- METHOD steps (deterministic)
- decision points
- minimal templates/forms
- examples (short)

### 2.4 Tools & Artifacts
- tools (software/technique)
- artifacts produced (docs/packs/checklists)
- recommended structures

### 2.5 Checklists
- pre-flight checklist (before work)
- execution checklist (during)
- post-flight checklist (after)

### 2.6 Failure Modes (Anti-patterns)
- common mistakes
- symptoms
- root causes
- fixes
- preventions

### 2.7 Quality Gates (Measurable)
- PASS / REWORK / FAIL criteria
- sampling method (how to check)
- thresholds (if applicable)

### 2.8 Vocabulary & Definitions
- key terms
- disambiguations
- “do not confuse X with Y”

### 2.9 Practice Drills (Optional but recommended)
- drills to improve capability
- micro-tasks
- evaluation rubric

### 2.10 Provenance (Required for non-trivial claims)
- SOURCE_RECORD_UIDS list
- FACT vs HEURISTIC labeling
- confidence notes

---

## 3) ATOMICITY RULE (STRICT)
- One competence pack = one domain + one role focus.
- Do not mix unrelated domains in a single pack.
- If pack becomes too large: split into sub-packs and XREF them.

---

## 4) LEVELING (OPTIONAL)
You may annotate capabilities by levels:
- L1: baseline
- L2: strong
- L3: expert
But levels must map to measurable gates (section 2.7).

---

## 5) MINIMUM QUALITY (PASS CONDITIONS)
PASS if:
- has at least 5 capabilities
- each capability has method + checklist + gate
- failure modes exist for at least 3 capabilities
- scope boundary is explicit
- provenance exists for any non-obvious factual claims

REWORK if:
- missing gates or checklists
- too much theory, not enough operational steps

FAIL if:
- vague content only (“be creative”, “do better”)
- no measurable checks
- invented facts presented as authoritative
- scope boundary missing

---

## 6) NAMING / UID RULES (LOCAL)
- File names follow KB naming convention.
- UID must be unique and stable.
- XREF uses UID-only (no PATH/URL).

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.MODULE_SCHEMA.023 | WHY: base schema requirements for KB modules
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: provenance records
- XREF: UE.KB.PROC.WORLD_INGEST.034 | WHY: ingest workflow for world knowledge into packs
- XREF: UE.KB.TOPIC.META.QA_AUDIT.005 | WHY: QA/audit expectations for KB content

--- END.
