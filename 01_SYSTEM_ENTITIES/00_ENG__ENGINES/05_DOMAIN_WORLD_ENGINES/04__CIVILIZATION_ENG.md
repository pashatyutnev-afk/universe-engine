# 🏙️ CIVILIZATION ENGINE
## Canonical World Engine Specification  
**LEVEL: L2 · DOMAIN_WORLD_ENGINE · CIVILIZATION SYSTEMS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_ID: L2-WORLD-CIVILIZATION-ENGINE-001
- NAME: Civilization Engine
- CLASS: Domain World Engine
- CATEGORY: Societal Structures & Institutions
- LEVEL: L2 (World Core)
- STATUS: FINAL
- AUTHORITY: World Layer
- FAILURE_MODE: fail-closed
- EDITABLE: false
- MUTATION_ALLOWED: false

### ABSOLUTE RULE
> A civilization is not a backdrop.  
> It is a system of rules that shapes every action within it.

---

## 1. PURPOSE

Civilization Engine defines and enforces **macro-level societal structures** of a world.

Он:
- описывает устройство цивилизаций
- формирует институты, нормы и иерархии
- задаёт ограничения и возможности для персонажей и событий
- обеспечивает системную правдоподобность мира

Он **НЕ**:
- пишет историю (Narrative Engines)
- управляет персонажами напрямую (Character Engines)
- принимает канонические решения (Governance)
- визуализирует мир (Expression / Visual Engines)

---

## 2. CIVILIZATION MODEL

A civilization is defined by immutable components:

- **Governance Structure** (власть, управление)
- **Social Hierarchy** (классы, касты, роли)
- **Economic System** (ресурсы, обмен, производство)
- **Cultural Norms** (ценности, табу, традиции)
- **Legal Framework** (законы, наказания)
- **Technological Level** (допустимые технологии)
- **Belief Systems** (религии, идеологии, мифы)

Canonical principle:
`civilization_rules → social_behavior → narrative constraints`

---

## 3. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)

- Definition of civilization archetypes
- Registration of societal rules
- Constraint export to:
  - Character Engines
  - Narrative Engines
  - World Law Engine
- Consistency validation across locations and epochs
- Civilization-level conflict conditions

---

### OUT-OF-SCOPE (FORBIDDEN)

- Writing historical events
- Creating individual cultures in isolation (Culture Engine)
- Character motivation design
- Plot progression
- Direct content generation

Out-of-scope is absolute.

---

## 4. INPUT ARTIFACT — CIVILIZATION_REQUEST

### REQUIRED FIELDS

- `request_id`
- `trace_id`
- `world_uid`
- `civilization_uid`
- `epoch_uid`
- `governance_model`
- `economic_model`
- `social_structure`
- `belief_framework`
- `constraints`
- `dependencies`

Missing field → **rejected**.

---

## 5. OUTPUT ARTIFACT — CIVILIZATION_SCHEMA

### OUTPUT CONTAINS

- `civilization_uid`
- `trace_id`
- `institution_map`
- `allowed_social_actions`
- `forbidden_social_actions`
- `systemic_tensions`
- `interaction_constraints`
- `notes_for_world_engines`

Output is **descriptive & restrictive**, not executable.

---

## 6. INTERACTIONS

### READS FROM (Allowed)

- World Structure Engine
- Timeline & Epoch Engine
- Geography & Location Engine
- Mythology & Belief Engine
- Economy & Resource Engine

### WRITES TO (Allowed)

- Character Engines (social limits)
- Narrative Engines (macro constraints)
- Conflict & Power Engine
- World Law Engine

### FORBIDDEN INTERACTION

- Production Engines
- Specialists as authority
- Knowledge Base as canon source (reference only)

---

## 7. VALIDATION RULES

- Every social rule must originate from a defined institution
- No civilization rule may contradict World Law
- Character actions must be possible within civilization constraints
- Civilization drift across epochs must be explicit

### Drift Levels

- MINOR: local variation
- MAJOR: institutional inconsistency
- CRITICAL: civilization breaks its own foundation

---

## 8. FAILURE CONDITIONS

### CRITICAL

- civilization_uid not registered
- conflicting institutions without resolution
- laws contradict world laws
- undefined governance structure

**Reaction:**
- Block world pipeline
- Emit audit violation
- Require correction or governance escalation

---

## 9. TRACE & AUDIT

- Every civilization has persistent `trace_id`
- Structural changes require Change Control
- Conflicts logged via Audit Log Engine

---

## 10. NON-GOALS

- Not a culture writer
- Not a historian
- Not a storyteller
- Not a political simulator
- Not a moral judge

---

## 11. GOVERNANCE POSITION

Civilization Engine:
- defines the rules of collective life
- limits narrative freedom for realism
- ensures systemic coherence of societies

It cannot mutate canon independently.

---

## 12. FINAL STATEMENT

Civilizations shape stories  
before stories shape civilizations.

---

**STATUS:** Civilization Engine v1.0  
**CANON:** FIXED · WORLD STRUCTURE AUTHORITY
