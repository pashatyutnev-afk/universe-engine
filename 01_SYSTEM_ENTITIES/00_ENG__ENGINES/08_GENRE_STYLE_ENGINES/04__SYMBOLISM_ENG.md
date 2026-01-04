# 🜁 SYMBOLISM ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · STYLE ENGINE · MEANING LAYER · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__SYMBOLISM_ENG.md
- ENGINE_ID: L3-STYLE-SYMBOLISM-ENGINE-004
- UID: UE.ENT.ENG.STYLE.SYMBOLISM
- NAME: Symbolism Engine
- CLASS: Style Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (symbol integrity)
- EDITABLE: true

### ABSOLUTE RULE
> A symbol without a mapped meaning is decoration. Decoration spam is noise.

---

## 1. PURPOSE

Symbolism Engine defines a **bounded symbol system**:
- symbol registry (what is a symbol, what it means)
- activation rules (when it appears)
- recurrence/decay rules (anti-spam)
- symbol-to-theme/resonance hooks (meaning coherence)
- misuse detection (random symbols, contradictory meanings)

It produces:
- **SYMBOL_SYSTEM**
- symbol maps per arc/sequence
- symbol integrity checks

This engine prevents “pretty objects” that carry no meaning.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define symbol schema and controlled symbol types
- Register symbols with explicit meanings and constraints
- Define recurrence patterns and decay rules
- Define activation triggers (events, moods, conflicts)
- Define symbol interplay (pairs, oppositions, evolutions)
- Validate symbols do not contradict world logic and tone constraints
- Emit Symbol System for scene/dialogue/visual composition engines

### OUT-OF-SCOPE (FORBIDDEN)
- Defining theme meaning itself (Theme & Meaning Engine owns theme)
- Plot decisions
- Canon authority decisions
- Writing prose — only system + constraints

---

## 3. SYMBOL SYSTEM MODEL

### 3.1 Output — SYMBOL_SYSTEM (required fields)
- `ss_id`
- `scope` = PROJECT | ARC | SEQUENCE
- `symbol_registry` (list of SYMBOL_SPEC)
- `symbol_map_by_window` (where symbols appear)
- `interactions` (optional list: symbol relations)
- `anti_spam_gates` (hard rules)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Symbol Object — SYMBOL_SPEC (required fields)
- `symbol_id`
- `name`
- `type` = OBJECT | PLACE | WEATHER | COLOR | SOUND | GESTURE | CREATURE | RITUAL | TECHNOLOGY | TEXT_FRAGMENT
- `core_meaning` (one sentence)
- `secondary_meanings` (0–2 max)
- `polarity` = LIGHT | DARK | NEUTRAL | SHIFTING
- `activation_triggers` (refs: events/conflicts/moods/anchors)
- `recurrence_rule` (frequency + constraints)
- `decay_rule` (when to stop or mutate)
- `evolution_rule` (optional: how meaning changes across arc)
- `forbidden_usages` (list)
- `world_alignment` = OK | RISK | VIOLATION
- `tone_alignment` = OK | RISK | VIOLATION
- `notes`

Missing any required field → REJECT.

### 3.3 Window Placement (required fields)
- `window_id`
- `time_ref`
- `symbols_used` (list of symbol_id)
- `mode` = SUBTLE | CLEAR | EMPHATIC
- `purpose` (reinforce meaning / contrast / foreshadow / echo)
- `notes`

Missing any required field → REJECT.

---

## 4. ANTI-SPAM GATES (HARD)

- Every symbol must have `core_meaning`.
- Secondary meanings max 2.
- Recurrence is bounded:
  - no symbol may appear in > 30% of windows unless it is a “core spine symbol” explicitly marked by recurrence_rule.
- Decay rule is mandatory:
  - a symbol must either fade, mutate, invert, or resolve.
- Contradictory meanings are forbidden:
  - if polarity is LIGHT, it cannot be used as DARK without evolution_rule.

---

## 5. CONTROLLED VOCABULARY (STANDARD)

Symbol purposes:
- FORESHADOW
- ECHO
- CONTRAST
- REINFORCE
- WARNING
- MEMORY_TRIGGER
- IDENTITY_MARKER
- WORLD_RULE_SIGNAL

Recurrence patterns:
- SPARSE (rare)
- RHYTHMIC (intentional cadence)
- CLUSTERED (only near turning points)
- SPINE (recurs across entire arc; must be justified)

---

## 6. INPUT ARTIFACTS

### 6.1 INPUT — SYMBOLISM_REQUEST
**REQUIRED FIELDS**
- `sym_req_id`
- `timestamp`
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `emotional_resonance_map_ref` (recommended)
- `world_package_ref` (recommended)
- `constraints_refs` (required)
- `theme_hooks_ref` (optional: allowed theme anchors)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 7. OUTPUT ARTIFACTS

### 7.1 OUTPUT — SYMBOL_SYSTEM
(see model above)

### 7.2 OUTPUT — SYMBOLISM_VERDICT
- `sym_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 8. CORE OPERATIONS

- OP_01: INGEST_TONE_RESONANCE_WORLD_CONSTRAINTS
- OP_02: REGISTER_SYMBOL_CANDIDATES (bounded set)
- OP_03: ASSIGN_CORE_AND_SECONDARY_MEANINGS
- OP_04: DEFINE_TRIGGERS_AND_PLACEMENT_WINDOWS
- OP_05: DEFINE_RECURRENCE_DECAY_EVOLUTION_RULES
- OP_06: DEFINE_INTERACTIONS (optional)
- OP_07: RUN_ANTI_SPAM_AND_ALIGNMENT_CHECKS
- OP_08: EMIT_SYMBOL_SYSTEM

---

## 9. MISUSE DETECTION

Hard violations (INVALID):
- symbols with no meaning
- symbols used against polarity without evolution_rule
- symbol meanings contradict world logic without justification
- symbol spam (recurrence gate violation)

Soft violations (PARTIAL):
- too many symbols introduced without payoff
- mode too emphatic too often (heavy-handedness)

Repair suggestions:
- remove symbols
- merge meanings
- add evolution rule
- reduce emphasis mode
- define payoff/resolution window

---

## 10. DEPENDENCIES

### REQUIRED
- Tone Profile
- Constraints refs

### OPTIONAL
- Mood curve
- Emotional resonance map
- World package
- Theme hooks

### FORBIDDEN
- unlimited symbol lists
- symbols that exist only for aesthetics
- contradictory meaning use without evolution

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Registry missing meanings/recurrence/decay
- Alignment violations with tone/world
- Spam gates repeatedly violated
- Symbol map has no purpose (just placements)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - reduce registry size
  - clarify meanings
  - enforce recurrence/decay
  - align polarity/evolution

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into metaphor and sensory detail planning

---

## 13. NON-GOALS
- Does not decide theme content
- Does not write prose
- Does not create plot

---

## 14. FINAL STATEMENT

Symbols are meaning with a handle.
Map them — or they become noise.

---

**STATUS:** Symbolism Engine v1.0  
**REALM:** ACTIVE
