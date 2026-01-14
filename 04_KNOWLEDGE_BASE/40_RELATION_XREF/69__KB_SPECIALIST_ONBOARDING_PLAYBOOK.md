# KB — SPECIALIST ONBOARDING PLAYBOOK (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/69__KB_SPECIALIST_ONBOARDING_PLAYBOOK.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PLAYBOOK
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PLAYBOOK.SPC_ONBOARD.069
OWNER: SYSTEM
ROLE: Step-by-step playbook to onboard a new SPC specialist into the KB system: connector setup, minimum pack slots, competence pack bindings, scorecard, slot satisfaction, readiness gate, and trace discipline (no-fantasy).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created SPC onboarding playbook for KB-driven specialist quality."
- REASON: "Specialists need deterministic onboarding; otherwise they produce low-quality outputs and drift into invention."
- IMPACT: "Consistent specialist setup, measurable competence coverage, and faster promotion to ACTIVE readiness."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PLAYBOOK.069

---

## 0) PURPOSE (KB)
Onboard any SPC specialist so it becomes operational:
- knows how to use KB
- is bound to competence packs
- satisfies minimum slots
- has coverage evidence
- follows trace + no-fantasy discipline

---

## 1) INPUTS
- Specialist entity UID + role
- Primary domain (music/narrative/...)
- Access policy (active-first)
- Skill tag taxonomy

---

## 2) ONBOARDING STEPS (DETERMINISTIC)
### Step 1 — Add Entity↔KB connector
- Embed connector block into the entity doc (UID-only).
- Ensure governance minimum set is required.

Output:
- entity has REQUIRED_SCOPES and selection map UIDs.

### Step 2 — Identify minimum pack slots
- Use ENTITY_MIN_PACKS map:
  - for SPC: governance baseline + domain core + domain QA

Output:
- list of required PACK_SLOTS.

### Step 3 — Bind real competence packs (or plan them)
- Bind REQUIRED_PACK_UIDS to satisfy each slot.
- If packs do not exist:
  - create roadmap entries and gap records.

Output:
- ENTITY_COMPETENCE_PACKS block filled.

### Step 4 — Build coverage scorecard
- Use scorecard template.
- Mark covered vs missing tags.
- Compute coverage percent.

Output:
- scorecard + prioritized gaps.

### Step 5 — Validate slot satisfaction
- For each required slot:
  - run slot satisfaction checklist
  - record PASS/REWORK/FAIL

Output:
- slot results.

### Step 6 — Run readiness minimum gate
- Use readiness minimum gate checklist:
  - governance loaded
  - slots satisfied
  - coverage exists
  - trace discipline ready

Output:
- readiness PASS/REWORK/FAIL.

### Step 7 — Train with drills (optional but recommended)
- Use drills template to push critical capabilities to L2/L3.

Output:
- improved pack strength.

### Step 8 — Enforce no-fantasy + trace
- Every run must output RUN_TRACE.
- Web lookup must be disclosed.
- Memory reuse must be declared.

Output:
- trace-compliant runs.

---

## 3) OUTPUT ARTIFACTS (MINIMUM)
Onboarding produces:
- connector block in entity doc
- competence pack bindings
- coverage scorecard
- slot satisfaction results
- readiness gate result
- (optional) roadmap and gap records

---

## 4) COMMON BLOCKERS + FIXES
Blocker: no packs exist
- Fix: create roadmap + gap priority + ingest workflow

Blocker: low coverage
- Fix: extend packs, create missing packs (P1 first)

Blocker: drift/invention
- Fix: enforce no-fantasy rule, re-open modules, add provenance

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- specialist has no connector
- required slots not satisfied
- no scorecard evidence
- trace omitted
- deprecated authority used
- invention presented as fact

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.PLAYBOOK.NAV_QUICKSTART.062 | WHY: navigation quickstart for KB usage
- XREF: UE.KB.STD.ENTITY_KB_CONNECTOR.037 | WHY: connector requirements
- XREF: UE.KB.TPL.ENTITY_KB_CONNECTOR.038 | WHY: connector implementation template
- XREF: UE.KB.MAP.ENTITY_MIN_PACKS.050 | WHY: minimum pack slots per entity class/domain
- XREF: UE.KB.MAP.SLOT_TO_TAGS.053 | WHY: slot-to-tag mapping
- XREF: UE.KB.TPL.SKILL_TAG_SCORECARD.041 | WHY: coverage scorecard
- XREF: UE.KB.CHK.SLOT_SATISFY.054 | WHY: slot satisfaction checklist
- XREF: UE.KB.GATE.ENTITY_READY_MIN.055 | WHY: readiness minimum gate
- XREF: UE.KB.RULE.NO_FANTASY_EXEC.063 | WHY: no-fantasy execution rule
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: run trace minimum standard

--- END.
