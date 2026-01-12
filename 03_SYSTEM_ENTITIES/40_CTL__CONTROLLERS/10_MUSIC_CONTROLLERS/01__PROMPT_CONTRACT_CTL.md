# PROMPT CONTRACT — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: PROMPT_CONTRACT
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.PROMPT_CONTRACT.001
OWNER: SYSTEM
ROLE: Defines the mandatory structure and constraints for platform-native prompt packs (Suno/Udio):
field schema, ordering rules, length limits, variant rules, negative spec rules, and prohibited patterns.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Prompt Contract CTL: required prompt-pack schema, ordering, length limits, variant rules, and prohibitions."
- REASON: "Without a contract, prompts drift, contradict themselves, and waste takes."
- IMPACT: "Higher prompt fidelity + repeatable production + cleaner QA/VAL gating."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.PROMPT.CONTRACT.001

---

## 0) PURPOSE (LAW)
This controller defines **what a valid prompt pack must look like**.
All engines/orchestrators/specialists that output prompts must follow this contract.

---

## 1) CONTRACT PRINCIPLES (ABSOLUTE)
- Contract defines **structure + limits**, not creative content.
- Prompts must be **platform-native** (Suno pack always; Udio optional).
- Prompts must be **non-contradictory**: tags, instruction, negatives must align.
- Identity anchors (Style Fingerprint) must be **encoded early**.
- Variants must preserve identity; only change duration/section density/intro method.

---

## 2) REQUIRED OUTPUT PACKS (MANDATORY)
### 2.1 SUNO PACK (ALWAYS)
A valid output MUST include:
- Suno.Lyrics
- Suno.Styles
- Suno.Instruction
- Suno.Negative

### 2.2 UDIO PACK (OPTIONAL)
If produced, MUST include:
- Udio.Tags
- Udio.Instruction
- Udio.Negative
- Udio.Lyrics (only if lyrical)

---

## 3) FIELD SCHEMA (MANDATORY)

### 3.1 Suno.Lyrics
Allowed modes:
- LYRICAL: RU by default (unless track says otherwise)
- INSTRUMENTAL: use exact token `Instrumental`

Allowed section labels:
- [Verse]
- [Chorus]
- [Bridge]
- [Outro]
- [Intro] (optional)

Rules:
- Lyrics must not be a full poem dump; must be “song-structured”.
- Chorus repeat must have at least 1 small variation if repeats exist.

### 3.2 Suno.Styles (tag list)
- Ordered list of tags (6–12 recommended).
- Hard max: 16 tags.
- Must follow Tag Ordering Rule (Section 4).

### 3.3 Suno.Instruction
- Short executable paragraph (not an essay).
- Must include:
  - hook timing intent (e.g., “hook early” with window)
  - repetition/variation intent (“repeat with variation”)
  - UGC clip window intent (at least one)
  - signature tag placement intent (early + loop imprint) if defined

### 3.4 Suno.Negative
- Concrete avoid list.
- Recommended: 8–20 items.
- Hard max: 30 items.
- No vague “bad/boring” negatives.

---

## 4) TAG ORDERING RULE (MANDATORY)
Tag order must follow:
1) genre family (primary)
2) era / reference vibe (optional)
3) instrumentation palette
4) groove / tempo feel
5) vocal style (if lyrical)
6) mood / emotion
7) mix aesthetic traits
8) signature tag hint

Rule:
- Do NOT list conflicting genres as equals unless Fusion Recipe explicitly defines it.
- If fusion exists, describe it in instruction as “A with B influence on <axis>”.

---

## 5) LENGTH LIMITS (SAFETY)
These are operational constraints to avoid “prompt bloat”.

- Suno.Instruction: max 3–6 lines equivalent (compact paragraph).
- Negative list: max 30 bullets.
- Tag list: max 16 tags.
- Lyrics: keep proportional to variant (SHORT vs FULL).

---

## 6) VARIANT RULES (MANDATORY)
A “variant pack” is allowed only if:
- identity anchors remain unchanged
- only these knobs may change:
  - duration target
  - section budgets (how many lines in verse/chorus)
  - intro entry method (direct vs primed)
  - density (more/less lyrics)

Mandatory variant names:
- SHORT
- FULL
- ALT_INTRO (optional)

---

## 7) PROHIBITED PATTERNS (HARD BLOCKERS)
Prompts must not include:
- contradictory instructions (e.g., “slow ballad” + “fast upbeat”)
- conflicting tag sets (e.g., 3 unrelated genres without fusion rules)
- “spam repeat” cues (encouraging identical phrase loops)
- “wall of negatives” that kills the vibe (too long/too generic)
- instructions that violate Duration Policy or UGC Ruleset (handled by other CTL but must not contradict)

---

## 8) REQUIRED CONSISTENCY CHECKS (PRE-VAL)
Before shipping a prompt pack, the producer must confirm:
- tags align with instruction (no contradictions)
- negatives do not contradict required anchors
- hook timing intent exists
- at least one UGC-friendly moment intent exists
- chorus repeat-safe intent exists if chorus repeats
- if lyrics PD-only mode is used: prompt does not request copyrighted text

---

## 9) DEPENDENCY REFERENCES (RAW)
These are not optional in usage; they are the standard policy sources.

- Duration Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- UGC Viral Ruleset CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md
- Negative Spec Library CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

Validator alignment:
- Prompt Fidelity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
