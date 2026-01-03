# 🎼 CHARACTER ORCHESTRATOR
## Canonical Orchestration Engine Specification  
**LEVEL: L2 · ORCHESTRATOR · CHARACTER COORDINATION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_ID: L2-ORC-CHARACTER-ORCHESTRATOR-001
- NAME: Character Orchestrator
- CLASS: Orchestrator Engine
- CATEGORY: Character Systems Coordination
- LEVEL: L2 (System Coordination Layer)
- STATUS: FINAL
- AUTHORITY: Orchestration Layer
- FAILURE_MODE: fail-closed
- EDITABLE: false
- MUTATION_ALLOWED: false

### ABSOLUTE RULE
> Orchestrator never invents.  
> It only coordinates what already exists.

---

## 1. PURPOSE

Character Orchestrator coordinates **multiple Character Engines** into a
**single coherent character behavior flow**.

Он:
- управляет порядком вызова Character Engines
- разрешает конфликты между их результатами
- агрегирует выходы в единое состояние персонажа
- гарантирует, что персонаж действует как целое

Он **НЕ**:
- определяет личность (Character Core Engine)
- генерирует мотивации
- переписывает психологию
- принимает канонические решения
- создаёт контент

---

## 2. ORCHESTRATION MODEL

Character behavior is produced as a **pipeline**, not as a single decision.

### Canonical flow example:

1. Character Core Engine  
2. Character Psychology Engine  
3. Motivation & Desire Engine  
4. Moral & Value Engine  
5. Relationship Engine  
6. Dialogue Engine / Action Output

Character Orchestrator:
- задаёт порядок
- контролирует зависимости
- собирает итог

---

## 3. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)

- Invocation order management
- Dependency resolution between Character Engines
- Conflict arbitration (non-canonical)
- Aggregation of character state
- State consistency checks
- Propagation of constraints

---

### OUT-OF-SCOPE (FORBIDDEN)

- Изменение Core Identity
- Переписывание памяти персонажа
- Генерация диалогов напрямую
- Сюжетные решения
- Каноническое утверждение изменений

Out-of-scope is absolute.

---

## 4. INPUT ARTIFACT — CHARACTER_CONTEXT

### REQUIRED FIELDS

- `trace_id`
- `character_uid`
- `world_state_ref`
- `scene_context`
- `active_constraints`
- `requested_output_type`

Missing field → **rejected**.

---

## 5. OUTPUT ARTIFACT — CHARACTER_STATE_SNAPSHOT

### OUTPUT CONTAINS

- `character_uid`
- `trace_id`
- `resolved_traits`
- `active_motivations`
- `emotional_state`
- `behavioral_constraints`
- `allowed_actions`
- `blocked_actions`
- `confidence_level`

Output is **ephemeral**, not canonical.

---

## 6. ENGINE INTERACTIONS

### READS FROM (Allowed)

- Character Core Engine
- Character Psychology Engine
- Motivation & Desire Engine
- Moral & Value Engine
- Relationship Engine
- Growth & Trauma Engine

---

### WRITES TO (Allowed)

- Dialogue Engine
- Action Selection Engines
- Narrative Engines (constraints only)

---

### FORBIDDEN INTERACTIONS

- Governance Engines
- World Canon Engines
- Knowledge Base as authority
- Production Engines

---

## 7. CONFLICT RESOLUTION RULES

When engines disagree:

Priority order (descending):

1. Character Core Engine
2. Moral & Value Engine
3. Trauma & Growth Engine
4. Motivation & Desire Engine
5. Relationship Engine
6. Dialogue / Expression Engines

Conflict without resolution → **blocked output**.

---

## 8. FAILURE CONDITIONS

### CRITICAL

- Missing Character Core
- Circular dependency detected
- Output contradicts Core Identity
- Undefined engine priority

**Reaction:**
- Abort orchestration
- Emit orchestration error
- Require system-level correction

---

## 9. TRACE & AUDIT

- Uses `trace_id` from upstream request
- Emits orchestration summary to Audit Log (optional)
- Does not create canonical records

---

## 10. NON-GOALS

- Not a personality designer
- Not a plot controller
- Not a psychological simulator
- Not a writer

---

## 11. GOVERNANCE POSITION

Character Orchestrator:
- is a coordinator, not an authority
- does not define truth
- does not own character data
- ensures internal coherence only

---

## 12. FINAL STATEMENT

A character is not a module.  
It is the harmony of many systems.

---

**STATUS:** Character Orchestrator v1.0  
**CANON:** FIXED · ORCHESTRATION AUTHORITY
