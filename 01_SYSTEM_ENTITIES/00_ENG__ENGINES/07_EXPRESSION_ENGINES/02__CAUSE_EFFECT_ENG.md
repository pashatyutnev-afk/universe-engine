# 🔗 CAUSE–EFFECT ENGINE
## Canonical Expression Logic Engine Specification  
**LEVEL: L2 · EXPRESSION_ENGINE · CAUSAL LOGIC · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_ID: L2-EXP-CAUSE-EFFECT-ENGINE-001
- NAME: Cause–Effect Engine
- CLASS: Expression Engine
- CATEGORY: Causal Logic & Consequence
- LEVEL: L2 (Expression Logic Layer)
- STATUS: FINAL
- AUTHORITY: Expression Layer
- FAILURE_MODE: fail-closed
- EDITABLE: false
- MUTATION_ALLOWED: false

### ABSOLUTE RULE
> No effect exists without a cause.  
> No cause is valid without consequences.

---

## 1. PURPOSE

Cause–Effect Engine enforces **causal consistency** between actions, events and outcomes.

Он:
- связывает действия с последствиями
- запрещает «магические» эффекты без причин
- обеспечивает логическую непрерывность мира
- формирует цепочки последствий во времени

Он **НЕ**:
- создаёт события (Event Engine)
- управляет драмой (Dramatic Arc Engine)
- определяет моральную оценку
- принимает канонические решения
- генерирует сюжет

---

## 2. CAUSAL MODEL

Every causal unit consists of:

- **Cause** — действие / событие / состояние
- **Context** — условия среды
- **Trigger** — точка активации
- **Effect** — результат
- **Propagation** — вторичные последствия
- **Latency** — задержка эффекта

Canonical relation:
`cause + context → effect → downstream effects`

---

## 3. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)

- Validation of cause–effect links
- Construction of consequence chains
- Detection of broken causality
- Enforcement of logical continuity
- Export of consequences to:
  - Narrative Engines
  - World Engines
  - Character Orchestrators

---

### OUT-OF-SCOPE (FORBIDDEN)

- Defining event importance
- Emotional evaluation
- Plot escalation
- Timeline authority
- Retroactive causality fixes

Out-of-scope is absolute.

---

## 4. INPUT ARTIFACT — CAUSAL_REQUEST

### REQUIRED FIELDS

- `trace_id`
- `cause_uid`
- `cause_type`
- `actor_uid` (optional)
- `world_context`
- `temporal_context`
- `constraints`
- `requested_depth`

Missing field → **rejected**.

---

## 5. OUTPUT ARTIFACT — CAUSAL_CHAIN

### OUTPUT CONTAINS

- `trace_id`
- `validated_cause`
- `direct_effects`
- `secondary_effects`
- `blocked_effects`
- `latency_map`
- `causal_conflicts`
- `confidence_score`

Output is **descriptive**, not prescriptive.

---

## 6. ENGINE INTERACTIONS

### READS FROM (Allowed)

- Event Engine
- World Law Engine
- Timeline & Epoch Engine
- Character Orchestrator
- Civilization Engine

---

### WRITES TO (Allowed)

- Narrative Engines (constraints)
- Conflict Engine
- Resolution Engine
- Expression Engines

---

### FORBIDDEN INTERACTIONS

- Governance Engines
- Production Engines
- Knowledge Base as authority
- Direct content output

---

## 7. CAUSAL VALIDATION RULES

- Effects must be reachable from causes
- Context must allow the effect
- Time must flow forward
- One cause may have multiple effects
- Effect without cause → invalid
- Cause without any effect → flagged

---

## 8. FAILURE CONDITIONS

### CRITICAL

- Effect precedes cause
- Effect contradicts world laws
- Infinite causal loop
- Missing context for validation

**Reaction:**
- Block chain
- Emit causal violation
- Require upstream correction

---

## 9. TRACE & AUDIT

- All causal chains share `trace_id`
- Violations logged to Audit Log Engine
- No canonical mutation allowed

---

## 10. NON-GOALS

- Not a storyteller
- Not a dramatist
- Not a simulator of chance
- Not a moral judge

---

## 11. GOVERNANCE POSITION

Cause–Effect Engine:
- enforces logic, not meaning
- constrains stories, not writes them
- guarantees that the world behaves consistently

---

## 12. FINAL STATEMENT

Stories break when causality breaks.  
Logic is invisible — until it fails.

---

**STATUS:** Cause–Effect Engine v1.0  
**CANON:** FIXED · CAUSAL LOGIC AUTHORITY
