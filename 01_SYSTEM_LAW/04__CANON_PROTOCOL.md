# CANON PROTOCOL — AUTHORITY, PROMOTION, CONFLICTS (CANON)

FILE: 01_SYSTEM_LAW/04__CANON_PROTOCOL.md
SCOPE: Universe Engine (All volumes)
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: CANON_PROTOCOL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.ALL.LAW.SYSTEM.CANON.001
OWNER: SYSTEM
ROLE: Defines what is canon, who has authority, how drafts become canon, how contradictions are handled, and how runtime respects snapshot-based RAW navigation.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Aligned with START entrypoint law + boot-first discipline + snapshot/refresh policy; clarified canon states and promotion gates; added explicit conflict handling and deprecation pointers; reinforced 'no guessing' and 'artifact-only outputs'."
- REASON: "Runtime must be auditable and deterministic; canon must not drift via assumptions or hidden links."
- IMPACT: "Canon authority becomes explicit; conflicts handled by protocol; outputs become traceable artifacts."
- CHANGE_ID: UE.CHG.2026-01-19.CANON.001

---

## 0) PURPOSE (LAW)
Canon is the system’s single source of truth for decisions, definitions, and deliverable acceptance.

This protocol guarantees:
- determinism under RAW-only navigation,
- stable authority hierarchy,
- controlled promotion of content into canon,
- explicit handling of contradictions and gaps,
- traceable outputs as artifact-docs.

---

## 1) ABSOLUTE LAWS (MUST)
1.1 Single runtime entrypoint  
Any task execution must be initiated via `START_UNIVERSE_ENGINE`. No side runs.

1.2 Boot-first  
No canon actions (promotion, acceptance, conflict resolution) before BOOT is confirmed by markers.

1.3 RAW-only navigation + snapshot reality  
Runtime may use only RAW links that exist in:
- the ROOT link base snapshot, or
- explicit links the user provided in chat.

No guessing of paths, no assumed “latest online state”.
If the user has not refreshed the snapshot, the link base is treated as fixed.

1.4 No “bare content” outputs  
Any output that matters becomes an artifact-document (draft or final) using system templates/standards.
If a template/entity is missing → GAP must be declared and creation proposed before continuing.

1.5 Canon is not memory  
Assistant memory is not canon. Only canonical documents and registries are canon.

---

## 2) DEFINITIONS
### 2.1 Canon
A statement, rule, entity definition, or deliverable that is:
- written as a document under system standards,
- placed under the correct layer,
- has UID + VERSION + STATUS,
- accepted by the required finish chain (control/validation/QA/doc control/signoff).

### 2.2 Non-canon
Anything that is:
- a chat message without an artifact doc,
- a draft not promoted,
- an idea not accepted by gates,
- external sources not ingested into KB per policy.

### 2.3 Canon states (minimum)
- DRAFT: not authoritative, can be replaced freely
- ACTIVE: authoritative and used
- DEPRECATED: replaced, must point to replacement
- ARCHIVED: historical, no longer referenced (rare, governed)

### 2.4 Promotion
The controlled process that turns a draft into canon using gates and signoff.

### 2.5 Authority (who can decide)
Authority is defined by the system role stack and governance specialists, not by convenience.

---

## 3) CANON AUTHORITY HIERARCHY (WHO OVERRULES WHAT)
When rules conflict, higher layer wins.

### 3.1 Authority stack (highest → lowest)
A) 01_SYSTEM_LAW (L1 laws)  
B) 02_STANDARDS (specs/protocols/templates; must not violate laws)  
C) 03_SYSTEM_ENTITIES (role definitions, realm rules; must obey laws/standards)  
D) 04_KNOWLEDGE_BASE (methods, playbooks, examples; must obey above)  
E) 05_PROJECTS / 06_ASSETS / 08_DATABASES (work outputs; must obey above)  
F) Chat runtime (non-canon unless packaged as artifacts)

### 3.2 Role authority (dispatch + signoff)
- Primary dispatcher: MACHINE_ARCHITECT_SPC
- Law authority: GOVERNANCE_OWNER_SPC
- Standards authority: STANDARDS_OWNER_SPC
- Doc control authority: DOC_CONTROLLER_SPC
- Pipeline authority: PIPELINE_ARCHITECT_SPC
- Packaging authority: INTEGRATION_PACKER_SPC

Final signoff belongs to:
DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

---

## 4) CANON ACCEPTANCE CONTRACT (WHAT “DONE” MEANS)
A deliverable is “done” only if it passes the finish chain:

1) READINESS_CHECK_CTL (preflight)
2) Relevant VAL checks (compliance)
3) Relevant QA gates (acceptance)
4) DOC_CONTROLLER_SPC (format, UID, naming, placement)
5) MACHINE_ARCHITECT_SPC (final signoff)

If any step fails → deliverable stays non-canon (DRAFT) and must be revised as an artifact.

---

## 5) PROMOTION FLOW (DRAFT → ACTIVE)
### 5.1 Minimum promotion steps
1) Draft artifact is produced with:
   - UID (or provisional UID if governed)
   - VERSION (start at 1.0.0)
   - STATUS: DRAFT
   - RUN_NOTE or CHANGE_NOTE

2) Controllers apply constraints (CTL)
3) Validators produce violations if needed (VAL)
4) QA applies acceptance gate(s) (QA)
5) Doc control verifies:
   - naming rules
   - UID rules
   - required header fields
   - correct layer placement
6) Signoff:
   - MACHINE_ARCHITECT_SPC approves canonization
7) Status changes to ACTIVE (or subsystem-specific READY → ACTIVE)

### 5.2 Promotion is reversible only by protocol
If an ACTIVE item must be changed:
- follow versioning policy (SEMVER + CHANGE_ID)
- if breaking or forbidden by LOCK: create replacement and deprecate old.

---

## 6) CONTRADICTION HANDLING PROTOCOL (MANDATORY)
When two canonical items conflict:

Step 1 — Declare contradiction  
- Identify the two UIDs and the exact conflicting statements.

Step 2 — Determine authority  
- Apply the layer hierarchy (Section 3.1).

Step 3 — Choose resolution type  
A) Clarification (MINOR/PATCH)  
B) Replacement + deprecation (preferred for FIXED or breaking changes)  
C) Scope split (create two scoped docs and update references)

Step 4 — Record outcome  
- Update via CHANGE_NOTE + CHANGE_ID (or create new doc + deprecate old)
- Ensure old doc contains replacement pointers if deprecated.

Runtime must STOP if it cannot confirm markers or lacks RAW links to the conflicting docs.

---

## 7) KNOWLEDGE GAP HANDLING (MISSING CANON)
When required rules/templates/entities are missing:

1) Declare GAP (what is missing and why it blocks the route)
2) Select the correct template for the missing entity/doc type
3) Produce a minimal viable canonical artifact (DRAFT is allowed)
4) Route it through the finish chain or explicitly mark it as blocking
5) Resume the original task only after the gap is resolved or formally blocked

No “temporary guessing” is allowed.

---

## 8) DEPRECATION & REPLACEMENT (CANON SAFE REWRITE)
When replacing canon:
- Never delete identity
- Old doc becomes DEPRECATED
- Old doc must include:
  - REPLACED_BY_UID
  - REPLACED_BY_RAW
- Replacement doc starts as VERSION 1.0.0 (new UID)

If LOCK: FIXED blocks editing the old doc:
- create a deprecation pointer record in the appropriate registry/log (governed),
- and ensure future routing uses the replacement.

---

## 9) RUNTIME VS REPO TRUTH (SNAPSHOT LAW)
### 9.1 Runtime truth
Runtime reads:
- ROOT link base snapshot + user-provided RAW links.
If the repo has newer versions, runtime does not assume they exist unless provided by snapshot refresh.

### 9.2 Repo truth
Repo may evolve, but runtime must not “jump” to unprovided files.

This prevents:
- drifting canon
- hidden dependency on “latest master”
- accidental use of unreviewed rules

---

## 10) OUTPUT ARTIFACT RULE (CANON PACKAGING)
Anything that leaves the system as a result must be an artifact doc:
- track cards, prompts, release packs, passports, specs, rules
- structured, versioned, auditable

If the user wants “just content”, system still packages it as an artifact doc by default.

---

## 11) KB SCOPE (BOUNDARIES FOR CANON KNOWLEDGE)
Canon knowledge is accepted only within explicit boundaries.

Minimum KB scope declaration (when creating KB modules or using KB as authority):
- KB INPUTS: what sources are allowed
- KB OUTPUTS: what artifacts are produced
- KB BOUNDARIES: what the KB must not decide
- KB RAW REFERENCES: the exact raw links used

If scope is not explicit → the KB output is non-canon (draft guidance only).

---

## 12) INTERFACES (RAW ONLY)
- Versioning & Change Policy:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- Naming Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md
- Runtime Entrypoint:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01__START_UNIVERSE_ENGINE.md

---

LOCK: FIXED
--- END.
