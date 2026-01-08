# METAPHOR ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/05__METAPHOR_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.STYLE.METAPHOR.001
OWNER: SYSTEM
ROLE: Defines deterministic metaphor constraints: metaphor mappings (source->target), allowed frames, transformation rules, usage bounds, and validation gates preventing metaphor drift into plot/theme ownership.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Metaphor Engine created: metaphor map schema, frame rules, mapping constraints, and drift gates."
- REASON: "Symbol palettes need mapping logic; metaphor rules must stay in style layer without becoming narrative meaning."
- IMPACT: "Creators can apply consistent metaphor language across scenes and media without breaking canon boundaries."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.METAPHOR.001

---

## 0) PURPOSE (LAW)
This engine owns **METAPHOR constraints**:
- metaphor = controlled mapping of one frame/domain to another (SOURCE -> TARGET)
- defines allowed metaphor frames and transformation rules
- defines usage bounds and forbidden mappings to avoid drift
- provides gates to detect cliché overload and accidental meaning takeover

Hard rule:
- Metaphor outputs are **constraints**; they do not declare story theme as truth or determine plot.

Guarantees:
- METAPHOR_MAP exists (mappings + frames)
- METAPHOR_RULESET exists (must/forbidden)
- gates detect drift, cliché overload, and contradiction with tone/mood/resonance

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define author theme/meaning as primary (NARRATIVE Theme & Meaning owns)
- define plot structure or beats (NARRATIVE owns)
- define character psychology or values (CHARACTER owns)
- define world laws/physics (WORLD owns)
- define production implementation (camera/editing/music)
- define symbol palette itself (SYMBOLISM engine owns symbol list + associations; this engine owns mapping rules)

Also forbidden:
- turning metaphors into lore rules or cosmology (world engines)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONE_PROFILE (recommended)
- MOOD_PROFILE (recommended)
- RESONANCE_PROFILE (optional)
- SYMBOL_MAP (optional but recommended)
- SCENE_PACK (optional)

PRODUCES:
- METAPHOR_MAP
- METAPHOR_RULESET
- METAPHOR_GATES_REPORT

DEPENDS_ON:
- [06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG]
(soft) [06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG, 06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/STYLE/METAPHOR/
OPTIONAL:
- KB/STYLE/METAPHOR (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Metaphor Frame: a conceptual domain (e.g., “WAR”, “ILLNESS”, “MACHINE”, “OCEAN”).
- Mapping: SOURCE_FRAME -> TARGET_FRAME mapping with allowed carriers.
- Carrier: where metaphor manifests (image, phrasing, sound motif label, action pattern).
- Transform Rule: how the mapping is applied or varied (invert, intensify, fragment, literalize).
- Cliché: overused mapping; must be capped or forbidden by rules.
- Drift: metaphor begins to imply unintended plot/meaning takeover.

Enums (baseline):
- carrier_type: VISUAL_OBJECT|COLOR|SOUND_MOTIF|PHRASE|ACTION|TEXTURE
- scope: GLOBAL|ARC|SCENE_WINDOW
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- metaphor frames and mapping definitions
- transformation rules and constraints
- usage bounds (frequency, intensity, cliché caps)
- gates and drift detection

OUT OF SCOPE (HARD):
- symbol associations (symbolism engine)
- narrative theme/meaning statements
- production shot/music plans
- plot outcomes

COLLISION RULE:
- If request is “what does it mean in the story” → narrative Theme & Meaning engine
- If request is “which symbols carry it” → symbolism engine (this engine can reference symbol_ids but not redefine them)
- If request is “how to shoot/score it” → production engines (this engine gives carriers and constraints only)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: METAPHOR_MAP defines frames and mappings with allowed carriers.
R2 (HARD) MUST: each mapping declares forbidden transformations (what not to do) and a cliché risk.
R3 (HARD) MUST: METAPHOR_RULESET defines MUST/FORBIDDEN/ALLOWED rules with scope and severity.
R4 (HARD) MUST: usage bounds exist (frequency/intensity caps) to prevent saturation.
R5 (HARD) FORBIDDEN: mapping that forces plot outcomes or declares theme truth as fact.
R6 (SOFT) SHOULD: include “refresh strategies” (how to vary without cliché) as constraints.
R7 (HARD) MUST: gates detect empty maps, missing carriers, cliché overload, and contradictions with tone/mood/resonance.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: METAPHOR_MAP
- MUST:
  - metaphor_map_id
  - version
  - base_refs (tone_profile_id, mood_profile_id)
  - frames[] (non-empty)
  - mappings[] (non-empty)
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- FRAME (minimum):
  - frame_id
  - name
  - descriptors[] (optional)
  - allowed_carriers[] (optional carrier_type list)
  - forbidden_carriers[] (optional)
- MAPPING (minimum):
  - mapping_id
  - source_frame_id
  - target_frame_id
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - allowed_carriers[] (non-empty)
  - suggested_symbol_refs[] (optional: symbol_ids)
  - transformation_rules_allowed[] (non-empty)
  - transformation_rules_forbidden[] (optional)
  - intensity_bounds (min,max within 0..100)
  - frequency_cap (optional; testable)
  - cliché_risk (LOW|MEDIUM|HIGH)
  - drift_risks[] (optional)
  - notes
- VALIDATION:
  - frames non-empty
  - mappings non-empty
  - each mapping references existing frame ids
  - allowed_carriers non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/METAPHOR/METAPHOR_MAP.md

---

ARTIFACT: METAPHOR_RULESET
- MUST:
  - ruleset_id
  - version
  - rules[] (non-empty)
  - cliché_policy (required)
  - checks[] (non-empty)
- CLICHÉ POLICY (minimum):
  - policy_id
  - max_high_risk_mappings_per_arc (optional)
  - refresh_required_after_use (optional)
  - forbidden_default_mappings[] (optional)
  - action_on_breach (CLAMP|SUBSTITUTE|REMOVE|FLAG_DRIFT)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - statement (testable)
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - rules non-empty
  - cliché_policy exists
  - at least one FORBIDDEN rule
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/METAPHOR/METAPHOR_RULESET.md

---

ARTIFACT: METAPHOR_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- GATE (minimum):
  - gate_id
  - name
  - pass_condition
  - fail_condition
  - severity_if_fail (S0|S1|S2|S3)
- Minimum required gates:
  - G1_FRAMES_EMPTY (S0)
  - G2_MAPPINGS_EMPTY (S0)
  - G3_CARRIER_MISSING (S0)
  - G4_CLICHÉ_OVER_CAP (S1)
  - G5_CONTRADICTS_TONE_MOOD_RESONANCE (S2)
  - G6_DRIFT_TO_THEME_OR_PLOT (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/METAPHOR/METAPHOR_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load tone/mood (+ symbolism/resonance optional).
2) Define frames:
   - controlled list of metaphor domains
3) Define mappings:
   - source->target, allowed carriers, transform rules, bounds
4) Define cliché policy and anti-style rules.
5) Define conflict rules (what to do if mapping clashes with tone).
6) Run gates (empties, clichés, drift, contradictions).
7) Emit: metaphor map + ruleset + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: frames[] empty or mappings[] empty.
- S0-2: any mapping missing allowed_carriers or frame references invalid.
- S0-3: produced artifacts missing required schema fields.
- S0-4: mapping forces plot outcomes or theme truth (owner collision).
- S0-5: hidden dependency on tone/mood not declared.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- tone/mood sets acceptable direction
- symbolism can provide carriers (optional)
- resonance can constrain persistence/aftertaste (optional)

Downstream:
- sensory detail engine can materialize metaphor via sensory priorities
- production engines can implement carriers visually/aurally (outside this engine)
- narrative engines can use metaphors, but cannot treat them as plot logic

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  06_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md
- Family template:
  06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

--- END.

LOCK: OPEN
