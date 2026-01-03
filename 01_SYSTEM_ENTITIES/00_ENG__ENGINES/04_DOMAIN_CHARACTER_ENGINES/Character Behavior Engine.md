# 🧩 CHARACTER BEHAVIOR ENGINE
## Canonical Character Engine Specification  
**LEVEL: L2 · DOMAIN_CHARACTER_ENGINE · BEHAVIOR CONSISTENCY · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_ID: L2-CHAR-BEHAVIOR-ENGINE-001
- NAME: Character Behavior Engine
- CLASS: Domain Character Engine
- CATEGORY: Behavior & Action Logic
- LEVEL: L2 (Character Core)
- STATUS: FINAL
- AUTHORITY: Character Layer
- FAILURE_MODE: fail-closed
- EDITABLE: false
- MUTATION_ALLOWED: false

### ABSOLUTE RULE
> If a character behaves without internal cause —  
> the character is broken.

---

## 1. PURPOSE

Character Behavior Engine defines and enforces **behavioral coherence** of a character.

Он:
- связывает стимул → внутреннее состояние → действие
- удерживает поведение в рамках личности и контекста
- предотвращает «кукольные» действия ради сюжета

Он **НЕ**:
- пишет диалоги (Dialogue Engine)
- определяет личность (Character Core Engine)
- определяет травмы/рост (Growth & Trauma Engine)
- принимает канонические решения (Governance)

---

## 2. BEHAVIOR MODEL

Behavior = function of:

- **Identity** (кто он)
- **Motivation** (чего хочет)
- **Constraints** (что нельзя)
- **Context** (где и что происходит)
- **State** (что он сейчас чувствует/думает)

Canonical mapping:
`stimulus -> appraisal -> internal_state -> intent -> action -> consequence`

---

## 3. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)

- Behavior rule definition (abstract)
- Action plausibility checks (character-side)
- Consistency enforcement across scenes
- Behavior drift detection
- Behavior constraints export to other engines

---

### OUT-OF-SCOPE (FORBIDDEN)

- Identity mutation
- Motivation invention without source
- World law override
- Plot forcing
- Scene writing
- Dialogue writing
- Format adaptation

Out-of-scope is absolute.

---

## 4. INPUT ARTIFACT — BEHAVIOR_REQUEST

### REQUIRED FIELDS

- `request_id`
- `trace_id`
- `character_uid`
- `context_uid`
- `stimulus`
- `current_state`
- `allowed_actions`
- `constraints`
- `dependencies`

Missing field → **rejected**.

---

## 5. OUTPUT ARTIFACT — BEHAVIOR_CONSTRAINTS

### OUTPUT CONTAINS

- `character_uid`
- `trace_id`
- `behavior_intent`
- `permitted_action_band` (allowed / risky / forbidden)
- `justification_facts` (only facts, no opinions)
- `consistency_flags`
- `notes_for_scene_engines`

Result is **advisory**, not executable.

---

## 6. INTERACTIONS

### READS FROM (Allowed)

- Character Core Engine (identity)
- Motivation & Desire Engine (motives)
- Moral & Value Engine (values)
- Relationship Engine (social ties)
- World Law Engine (external constraints)
- Narrative Logic Engine (causal chain)

### WRITES TO (Allowed)

- Scene Construction Engine (constraints)
- Dialogue Engine (behavioral tone hints)
- Continuity engines (flags)

### FORBIDDEN INTERACTION

- Production engines
- Specialists as authority
- Knowledge base as authority (KB may be reference only via governance)

---

## 7. VALIDATION RULES

- Every action must have an internal driver (intent)
- Intent must be compatible with identity + motives
- If action contradicts identity:
  - it must be justified by explicit state change
  - or marked as drift

### Drift Levels

- MINOR: small inconsistency, recoverable
- MAJOR: repeated inconsistency, requires correction
- CRITICAL: action breaks identity core → block downstream

---

## 8. FAILURE CONDITIONS

### CRITICAL

- character_uid not registered
- action without intent
- repeated major drift without resolution

**Reaction:**
- Block character pipeline
- Emit violation record
- Require governance / correction pass

---

## 9. TRACE & AUDIT

- Every request has `trace_id`
- Any CRITICAL drift is logged via Audit Log Engine
- Any behavior override requires Change Control

---

## 10. NON-GOALS

- Not a storyteller
- Not a director
- Not an actor coach
- Not a dialogue writer
- Not a moral judge

---

## 11. GOVERNANCE POSITION

Character Behavior Engine:
- enforces internal coherence
- protects characters from plot abuse
- supports realism and believability

It cannot approve canon changes.

---

## 12. FINAL STATEMENT

A character is believable  
when actions follow inner logic.

---

**STATUS:** Character Behavior Engine v1.0  
**CANON:** FIXED · CONSISTENCY ENFORCER
