# 🌫️ ATMOSPHERE ENGINE
## Canonical Genre & Style Engine Specification  
**LEVEL: L2 · GENRE_STYLE_ENGINE · ATMOSPHERE CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_ID: L2-GEN-ATMOSPHERE-ENGINE-001
- NAME: Atmosphere Engine
- CLASS: Genre & Style Engine
- CATEGORY: Mood, Tone & Sensory Field
- LEVEL: L2 (Style Control Layer)
- STATUS: FINAL
- AUTHORITY: Genre / Style Layer
- FAILURE_MODE: fail-closed
- EDITABLE: false
- MUTATION_ALLOWED: false

### ABSOLUTE RULE
> Atmosphere is not decoration.  
> Atmosphere is the emotional physics of the scene.

---

## 1. PURPOSE

Atmosphere Engine defines and maintains the **emotional and sensory field**
of scenes, worlds and narratives.

Он:
- задаёт общее ощущение среды
- формирует настроение сцены
- управляет тональностью восприятия
- обеспечивает стилевую целостность атмосферы

Он **НЕ**:
- управляет сюжетом
- создаёт события
- определяет характер персонажей
- принимает канонические решения
- генерирует визуал или звук напрямую

---

## 2. ATMOSPHERE MODEL

Atmosphere is composed of layered parameters:

- **Emotional Tone** (страх, надежда, меланхолия, напряжение)
- **Sensory Density** (насыщенность ощущений)
- **Environmental Mood** (давление среды)
- **Temporal Feel** (медленно / тревожно / рвано)
- **Stability Level** (устойчивость / хрупкость)
- **Contrast Field** (свет ↔ тьма, тепло ↔ холод)

Canonical relation:
`environment + tone + context → perceived atmosphere`

---

## 3. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)

- Definition of atmospheric profiles
- Mood consistency enforcement
- Cross-scene atmospheric continuity
- Constraint export to:
  - Visual Engines
  - Sound & Music Engines
  - Narrative Engines
- Detection of tonal dissonance

---

### OUT-OF-SCOPE (FORBIDDEN)

- Scene composition
- Lighting design
- Music composition
- Emotional arcs (Tension Engine)
- Symbolic interpretation

Out-of-scope is absolute.

---

## 4. INPUT ARTIFACT — ATMOSPHERE_REQUEST

### REQUIRED FIELDS

- `trace_id`
- `scope_type` (scene / location / world)
- `scope_uid`
- `genre_context`
- `desired_tone`
- `intensity_level`
- `constraints`
- `dependencies`

Missing field → **rejected**.

---

## 5. OUTPUT ARTIFACT — ATMOSPHERE_PROFILE

### OUTPUT CONTAINS

- `trace_id`
- `atmosphere_uid`
- `emotional_field`
- `sensory_weight`
- `allowed_style_range`
- `forbidden_shifts`
- `continuity_notes`
- `confidence_level`

Output is **descriptive**, not generative.

---

## 6. ENGINE INTERACTIONS

### READS FROM (Allowed)

- Genre Engine
- Tone & Mood Engine
- World Structure Engine
- Narrative Context Engines

---

### WRITES TO (Allowed)

- Visual Cinema Engines
- Sound & Music Engines
- Expression Engines
- Narrative Engines (constraints only)

---

### FORBIDDEN INTERACTIONS

- Governance Engines
- Character Core Engines
- Production Engines
- Knowledge Base as authority

---

## 7. ATMOSPHERIC CONSISTENCY RULES

- Atmosphere must align with genre
- Abrupt tonal shifts require justification
- Atmosphere cannot contradict world rules
- Sustained scenes require stable mood baseline

Violations → flagged for correction.

---

## 8. FAILURE CONDITIONS

### CRITICAL

- Undefined atmosphere for active scene
- Tone contradicts genre constraints
- Impossible emotional state for context
- Atmospheric oscillation without cause

**Reaction:**
- Block downstream expression
- Emit style violation
- Require redefinition

---

## 9. TRACE & AUDIT

- All atmosphere profiles use `trace_id`
- Major shifts logged to Audit Log Engine
- No canonical mutation allowed

---

## 10. NON-GOALS

- Not a lighting engine
- Not a sound designer
- Not a dramatist
- Not a storyteller

---

## 11. GOVERNANCE POSITION

Atmosphere Engine:
- controls how the world is felt
- constrains expression layers
- preserves stylistic coherence

---

## 12. FINAL STATEMENT

Atmosphere is the silence  
that speaks before any action.

---

**STATUS:** Atmosphere Engine v1.0  
**CANON:** FIXED · STYLE & MOOD AUTHORITY
