# SYMBOLISM ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG.md
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
UID: UE.ENG.STYLE.SYMBOLISM.001
OWNER: SYSTEM
ROLE: Defines deterministic symbolism constraints: symbol palette, allowed carriers, mapping rules (symbol -> intended associations), usage bounds, and validation gates preventing accidental meaning drift and owner-collisions with narrative theme.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Symbolism Engine created: symbol map schema, carrier rules, usage bounds, anti-symbol rules, and drift gates."
- REASON: "Style layer needs explicit symbol constraints without turning into Theme & Meaning or plot."
- IMPACT: "Creators can reuse consistent symbolic language while keeping narrative ownership separate."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.SYMBOLISM.001

---

## 0) PURPOSE (LAW)
This engine owns **SYMBOLISM constraints**:
- defines a symbol palette (symbols as reusable style carriers)
- defines intended associations and forbidden associations
- defines how symbols may appear (carriers) and bounds of usage
- defines anti-symbol rules (what NOT to use to avoid genre drift)
- emits gates to detect unintended meaning drift

Hard rule:
- Symbolism here is a **constraint language**, not the story’s theme or message.
- Symbolism outputs must be compatible with tone/mood/atmosphere/resonance constraints.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define author theme/meaning as primary (NARRATIVE Theme & Meaning owns)
- define plot choices or reveals (NARRATIVE owns)
- define character psychology or moral systems (CHARACTER owns)
- define world laws/cosmology (WORLD owns)
- define production shot design or art direction specifics (PRODUCTION owns)
- define metaphors as mapping mechanics (METAPHOR engine owns metaphor rules; this engine owns symbol palette + associations)

Also forbidden:
- turning symbol list into lore bible (world/KB owns lore storage, this engine outputs constraints only)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONE_PROFILE (recommended)
- MOOD_PROFILE (recommended)
- ATMOSPHERE_LAYER_SPEC (optional)
- RESONANCE_PROFILE (optional)
- WORLD_STRUCTURE_MODEL (optional)
- SCENE_PACK (optional)

PRODUCES:
- SYMBOL_MAP
- SYMBOL_USAGE_RULESET
- SYMBOLISM_GATES_REPORT

DEPENDS_ON:
- [06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG]
(soft) [06_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG, 06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/STYLE/SYMBOLISM/
OPTIONAL:
- KB/STYLE/SYMBOLISM (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Symbol: a reusable signifier used as a style carrier (object, motif, gesture, sound cue label).
- Carrier: where the symbol can manifest (VISUAL_OBJECT, COLOR, SOUND_MOTIF, PHRASE, PLACE, ACTION).
- Association: intended reading/affect link (not “theme truth”).
- Meaning Drift: symbol begins to imply unintended associations due to misuse or overuse.
- Saturation: usage frequency/intensity beyond allowed bounds.

Enums (baseline):
- carrier_type: VISUAL_OBJECT|COLOR|SOUND_MOTIF|PHRASE|PLACE|ACTION|TEXTURE
- scope: GLOBAL|ARC|SCENE_WINDOW
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- symbol palette and controlled associations
- carrier rules and usage bounds
- anti-symbol constraints and drift detection

OUT OF SCOPE (HARD):
- declaring “the theme/message” (narrative theme engine)
- mapping metaphor logic (metaphor engine)
- production execution (how to shoot/score it)

COLLISION RULE:
- If request is “what is the theme meaning of this” → narrative Theme & Meaning engine
- If request is “metaphor mapping rules” → `05__METAPHOR_ENG`
- If request is “how to depict symbol visually” → production engines (this engine gives carriers and bounds only)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: SYMBOL_MAP defines symbols with allowed carriers and intended associations.
R2 (HARD) MUST: SYMBOL_USAGE_RULESET defines frequency/saturation bounds per scope.
R3 (HARD) MUST: include forbidden symbols or forbidden carriers to prevent drift.
R4 (HARD) MUST: symbols must be compatible with tone/mood constraints; conflicts require explicit resolution.
R5 (HARD) FORBIDDEN: claiming story theme or plot outcomes as symbol “facts”.
R6 (SOFT) SHOULD: include “misread risks” and mitigations (still constraints, not narrative).
R7 (HARD) MUST: gates detect (a) saturation (b) contradiction (c) meaning drift.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: SYMBOL_MAP
- MUST:
  - symbol_map_id
  - version
  - base_refs (tone_profile_id, mood_profile_id)
  - symbols[] (non-empty)
  - forbidden_symbols[] (optional)
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- SYMBOL (minimum):
  - symbol_id
  - name
  - carriers_allowed[] (non-empty; carrier_type)
  - carriers_forbidden[] (optional)
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - intended_associations[] (non-empty; controlled descriptors)
  - forbidden_associations[] (optional)
  - resonance_links[] (optional: resonance target ids)
  - mood_links[] (optional: mood tags)
  - saturation_bounds:
    - max_per_scene_window (optional)
    - max_per_arc (optional)
    - max_intensity (0..100 optional)
  - misread_risks[] (optional)
  - notes
- VALIDATION:
  - symbols non-empty
  - carriers_allowed non-empty for each symbol
  - intended_associations non-empty for each symbol
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/SYMBOLISM/SYMBOL_MAP.md

---

ARTIFACT: SYMBOL_USAGE_RULESET
- MUST:
  - ruleset_id
  - version
  - rules[] (non-empty)
  - saturation_model (required)
  - checks[] (non-empty)
- SATURATION MODEL (minimum):
  - model_id
  - measures[] (e.g., COUNT, INTENSITY)
  - thresholds (per scope)
  - action_on_breach (CLAMP|SUBSTITUTE|REMOVE|FLAG_DRIFT)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - statement (testable)
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - rules non-empty
  - at least one FORBIDDEN rule
  - saturation_model defined
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/SYMBOLISM/SYMBOL_USAGE_RULESET.md

---

ARTIFACT: SYMBOLISM_GATES_REPORT
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
  - G1_SYMBOLS_EMPTY (S0)
  - G2_CARRIER_EMPTY (S0)
  - G3_ASSOCIATION_EMPTY (S0)
  - G4_SATURATION_BREACH (S1)
  - G5_MEANING_DRIFT_RISK (S1)
  - G6_CONTRADICTS_TONE_MOOD (S2)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/SYMBOLISM/SYMBOLISM_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load tone/mood (+ atmosphere/resonance optional).
2) Define symbol palette:
   - stable ids, carriers allowed, intended associations
3) Define usage bounds:
   - saturation bounds by scope
4) Define anti-symbol constraints:
   - forbidden symbols/carries/associations
5) Define conflict rules:
   - what to do if symbol implies unwanted tone
6) Run gates:
   - empties, saturation risk, contradictions
7) Emit: symbol map + usage ruleset + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: symbols[] empty.
- S0-2: any symbol lacks carriers_allowed or intended_associations.
- S0-3: produced artifacts missing required schema fields.
- S0-4: symbolism outputs claim narrative theme/plot outcomes as facts.
- S0-5: hidden dependency on tone/mood not declared.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- tone/mood provides direction
- atmosphere/resonance provide context (optional)

Downstream:
- metaphor engine may use symbol palette as carriers (but cannot redefine symbol associations silently)
- sensory detail engine can choose sensory emphasis for symbols
- production engines implement carriers visually/aurally within constraints
- narrative engines can select symbols, but must respect usage bounds and forbidden rules

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  06_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md
- Family template:
  06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

--- END.

LOCK: OPEN
