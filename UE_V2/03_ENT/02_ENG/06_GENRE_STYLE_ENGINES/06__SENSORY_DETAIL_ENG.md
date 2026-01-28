# SENSORY DETAIL ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/06__SENSORY_DETAIL_ENG.md
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
UID: UE.ENG.STYLE.SENSORY.DETAIL.001
OWNER: SYSTEM
ROLE: Defines deterministic sensory detail constraints: which senses to emphasize, texture palettes, detail density bounds, sensory anti-pattern rules, and validation gates (without writing scenes or production execution).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Sensory Detail Engine created: sensory palette schema, emphasis rules, density bounds, anti-pattern rules, and drift gates."
- REASON: "Style needs a deterministic layer for sensory priority to keep outputs vivid and consistent without becoming prose writing."
- IMPACT: "Narrative and production can apply consistent sensory emphasis; avoids flat or overwritten output."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.SENSORY.DETAIL.001

---

## 0) PURPOSE (LAW)
This engine owns **SENSORY DETAIL constraints**:
- defines which sensory channels are prioritized (sight/sound/smell/touch/taste/proprioception/temperature)
- defines texture palettes (controlled tags) and detail density bounds
- defines when to compress vs expand details (by scope)
- defines anti-pattern rules (purple prose, generic sensory blur, mismatch with atmosphere)
- emits gates to detect sensory drift and overload

Hard rule:
- This engine outputs constraints/palettes only. It does NOT write scenes and does NOT specify camera/editing/sound recipes.

Guarantees:
- a SENSORY_PALETTE exists
- a DETAIL_DENSITY_PROFILE exists
- gates detect overload/emptiness and contradictions with atmosphere/tone

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define plot/meaning/structure (NARRATIVE owns)
- define character psychology or motives (CHARACTER owns)
- define world laws/ecology (WORLD owns)
- define event mechanics primitives (EXPRESSION owns)
- define production implementation (lighting, shot list, mixing, Foley design) — PRODUCTION owns
- define symbolism/metaphor mapping (SYMBOLISM/METAPHOR engines own)

Also forbidden:
- turning this engine into prose generator (“write vivid paragraph”). Constraints only.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONE_PROFILE (recommended)
- MOOD_PROFILE (recommended)
- ATMOSPHERE_LAYER_SPEC (recommended)
- RESONANCE_PROFILE (optional)
- SYMBOL_MAP (optional)
- METAPHOR_MAP (optional)
- SCENE_PACK (optional)

PRODUCES:
- SENSORY_PALETTE
- DETAIL_DENSITY_PROFILE
- SENSORY_GATES_REPORT

DEPENDS_ON:
- [06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG, 06_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG]
(soft) [06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG, 06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG, 06_GENRE_STYLE_ENGINES/05__METAPHOR_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/STYLE/SENSORY/
OPTIONAL:
- KB/STYLE/SENSORY (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Sensory Channel: SIGHT, SOUND, SMELL, TOUCH, TASTE, TEMPERATURE, PROPRIOCEPTION.
- Sensory Palette: controlled list of texture tags and allowed carriers per channel.
- Detail Density: bounded amount of sensory detail per scope (not word-count, but density targets).
- Compression Rule: when to reduce detail to avoid overload.
- Expansion Rule: when to enrich detail to increase vividness.
- Overwrite: sensory overload / purple-prose risk.
- Flatness: too generic/no sensory specificity.

Enums (baseline):
- channel: SIGHT|SOUND|SMELL|TOUCH|TASTE|TEMPERATURE|PROPRIOCEPTION
- scope: GLOBAL|ARC|SCENE_WINDOW
- density_target: 0..100
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- sensory channel priorities
- texture tag palettes per channel
- density bounds and compress/expand rules
- anti-pattern rules (generic/overwritten/mismatched)
- validation gates

OUT OF SCOPE (HARD):
- writing actual descriptive prose
- production execution (sound design/mix/camera/lighting)
- world physics/ecology (only consumes their context)
- symbolism/metaphor meaning ownership

COLLISION RULE:
- If request is “write the paragraph” → narrative/scene engines (this engine provides constraints)
- If request is “design sound mix / Foley list” → production sound engines
- If request is “choose metaphors” → metaphor engine; sensory engine only defines channels and texture constraints
- If request is “symbol meaning” → symbolism engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: SENSORY_PALETTE defines per-channel priorities and allowed texture tags.
R2 (HARD) MUST: DETAIL_DENSITY_PROFILE defines density targets/bounds per scope.
R3 (HARD) MUST: include compression and expansion rules (when/why) as testable constraints.
R4 (HARD) MUST: include anti-pattern rules for FLATNESS and OVERWRITE.
R5 (HARD) MUST: compatibility checks vs ATMOSPHERE (no “warm cozy textures” if atmosphere forbids).
R6 (HARD) FORBIDDEN: embedding actual prose or production shot/sound recipes.
R7 (SOFT) SHOULD: allow symbol/metaphor carriers as optional “sensory hooks” without redefining meaning.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: SENSORY_PALETTE
- MUST:
  - palette_id
  - version
  - base_refs (tone_profile_id, mood_profile_id, atmosphere_spec_id)
  - channel_priorities[] (non-empty)
  - channel_textures[] (non-empty)
  - forbidden_textures[] (optional)
  - anti_style_rules[] (non-empty)
  - validation_checks[] (non-empty)
- CHANNEL PRIORITY (minimum):
  - channel (SIGHT|SOUND|SMELL|TOUCH|TASTE|TEMPERATURE|PROPRIOCEPTION)
  - priority (0..100)
  - scope (GLOBAL|ARC|SCENE_WINDOW)
- CHANNEL TEXTURE (minimum):
  - channel
  - texture_tags[] (non-empty; controlled)
  - allowed_carriers[] (optional: OBJECT|SPACE|WEATHER|BODY|MATERIAL|SOUND_MOTIF|PHRASE)
  - forbidden_carriers[] (optional)
  - notes
- VALIDATION:
  - at least one channel priority per declared scope
  - channel_textures non-empty and each has texture_tags
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/SENSORY/SENSORY_PALETTE.md

---

ARTIFACT: DETAIL_DENSITY_PROFILE
- MUST:
  - density_profile_id
  - version
  - density_targets[] (non-empty)
  - compression_rules[] (non-empty)
  - expansion_rules[] (non-empty)
  - bounds (min,max within 0..100)
  - checks[] (non-empty)
- DENSITY TARGET (minimum):
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - target (0..100)
  - bounds (min,max)
  - channel_bias[] (optional: channel priority deltas)
- COMPRESSION RULE (minimum):
  - rule_id
  - trigger (testable)
  - action (testable)
  - severity_if_ignored (S0|S1|S2|S3)
- EXPANSION RULE (minimum):
  - rule_id
  - trigger (testable)
  - action (testable)
  - severity_if_ignored (S0|S1|S2|S3)
- VALIDATION:
  - bounds valid and include targets
  - compression_rules and expansion_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/SENSORY/DETAIL_DENSITY_PROFILE.md

---

ARTIFACT: SENSORY_GATES_REPORT
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
  - G1_CHANNELS_MISSING (S0)
  - G2_TEXTURE_EMPTY (S0)
  - G3_DENSITY_BOUNDS_INVALID (S0)
  - G4_OVERWRITE_RISK (S1)
  - G5_FLATNESS_RISK (S1)
  - G6_CONTRADICTS_ATMOSPHERE (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/SENSORY/SENSORY_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load tone/mood/atmosphere (+ resonance/symbol/metaphor optional).
2) Define channel priorities per scope.
3) Define texture tags per channel (palette).
4) Define density targets and bounds per scope.
5) Define compression rules (avoid overwrite) and expansion rules (avoid flatness).
6) Run gates: missing channels, empty textures, density invalid, contradictions vs atmosphere.
7) Emit: palette + density profile + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing channel priorities or missing channel textures.
- S0-2: any required lists empty (texture_tags, density_targets, compression/expansion rules).
- S0-3: bounds invalid or outside 0..100.
- S0-4: produced artifacts missing schema fields.
- S0-5: engine outputs prose or production recipes (owner collision).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- tone/mood + atmosphere define what the world/scene should feel like
- resonance/symbol/metaphor optionally provide “hooks” to emphasize

Downstream:
- narrative scene engines can apply sensory constraints when writing/constructing scenes
- production engines can implement sensory emphasis into sound/visual design (outside this engine)
- QA/consistency engines can validate outputs against gate reports

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  06_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md
- Family template:
  06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

--- END.

LOCK: OPEN
