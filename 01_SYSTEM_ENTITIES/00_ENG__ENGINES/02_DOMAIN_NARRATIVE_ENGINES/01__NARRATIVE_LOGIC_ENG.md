# 🧠 NARRATIVE LOGIC ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · NARRATIVE CAUSALITY · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__NARRATIVE_LOGIC_ENG.md
- ENGINE_ID: L2-DOM-NARRATIVE-LOGIC-ENGINE-001
- UID: UE.ENT.ENG.DOM.NARRATIVE.NARRATIVE_LOGIC
- NAME: Narrative Logic Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Causality, Constraints & Narrative Validity
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for output validity)
- EDITABLE: true (domain evolution allowed via project-level process)
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> A narrative output is invalid if causality and constraints cannot explain why events happen.

---

## 1. PURPOSE

Narrative Logic Engine defines the **logical skeleton** of story causality.

It guarantees:
- cause → effect integrity
- constraint compliance (world/character rules)
- motivation linkage
- consequence propagation
- detection of “magic teleport” logic (events with no causal bridge)

This engine is about *narrative validity*, not factual truth.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Validate causal chains between events
- Enforce constraints (world laws, character limits)
- Ensure motivations explain actions
- Ensure consequences exist for major actions
- Produce logic verdicts for scenes/plots
- Suggest minimal fixes (non-binding) to repair logic

### OUT-OF-SCOPE (FORBIDDEN)
- Choosing themes (Theme Engine)
- Pacing decisions (Pacing Engine)
- Reveal strategy (Twist/Reveal Engine)
- Canon authority decisions (Governance)
- Real-world truth validation (validators)

---

## 3. NARRATIVE LOGIC MODEL

### 3.1 Core Constructs

- EVENT: something that happens
- CAUSE: why it happens
- INTENT: what an agent wants
- CONSTRAINT: what is allowed/forbidden
- CONSEQUENCE: what changes because of the event
- LINK: explicit bridge between events

### 3.2 Logic Requirements (minimum)
For every major EVENT:
- at least one CAUSE
- at least one CONSTRAINT reference (even “none” is explicit)
- at least one CONSEQUENCE
- if agent-driven: INTENT must be present

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — NARRATIVE_EVENT_SET
**REQUIRED FIELDS**
- `set_id`
- `timestamp`
- `events` (list)
- `constraints_refs` (world/character constraints)
- `context_goal`
- `trace_id` (optional; required if used in governance-bound pipeline)

Each event must include:
- `event_id`
- `actors` (uids or names)
- `intent` (optional if non-agent)
- `cause_refs` (list; may be empty for minor events)
- `consequence_refs` (list; required for major events)
- `stakes_level` (LOW/MEDIUM/HIGH)
- `notes`

Missing set fields → REJECT.

### 4.2 INPUT — SCENE_LOGIC_REQUEST
**REQUIRED FIELDS**
- `scene_id`
- `timestamp`
- `scene_summary`
- `events_in_scene` (list)
- `constraints_refs`
- `trace_id` (optional)

Missing any field → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — LOGIC_VERDICT
- `target_id` (set_id or scene_id)
- `verdict` = VALID | INVALID | PARTIAL
- `breaks` (list of causal/constraint breaks)
- `missing_links` (list)
- `repair_suggestions` (list; non-binding)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL
- `trace_id` (if provided)

### 5.2 OUTPUT — CAUSAL_CHAIN_MAP
- explicit mapping: event → causes → consequences
- used by downstream engines (structure/arc/continuity)

---

## 6. CORE OPERATIONS

- OP_01: BUILD_CAUSAL_CHAIN
- OP_02: DETECT_MISSING_CAUSES
- OP_03: DETECT_CONSTRAINT_VIOLATIONS
- OP_04: DETECT_CONSEQUENCE_GAPS
- OP_05: EMIT_LOGIC_VERDICT

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline only (outputs are domain artifacts)

### READ
- Narrative engines (structure/arc/scene/pacing/continuity)
- Orchestrators (if used as pipeline step)

### DELETE
- Allowed for drafts (domain layer), forbidden for governance traces

---

## 8. DEPENDENCIES

### REQUIRED
- World Law / World Structure constraints (domain inputs)
- Character Motivation constraints (domain inputs)
- If trace-bound: Audit Log Engine (record usage)

### FORBIDDEN
- Using chat text as canon authority
- Overriding governance locks or approvals

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED FOR VALIDITY)

CRITICAL:
- Major events without cause and without consequence
- Constraint violation with no narrative justification path
- Actor action with no intent or motivation link
- Chains that contradict declared world laws

Reaction:
- Verdict INVALID (CRITICAL)
- Provide minimal repair suggestions

---

## 10. TRACE RULES

- trace_id is optional unless pipeline requires governance trace
- if trace_id present, it must be propagated downstream

---

## 11. NON-GOALS
- Does not control pacing
- Does not pick reveals
- Does not set theme
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Narrative logic is the spine.
No causality → no believable story.

---

**STATUS:** Narrative Logic Engine v1.0  
**DOMAIN:** ACTIVE
