# PROMPT FIDELITY — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: PROMPT_FIDELITY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.PROMPT_FIDELITY.001
OWNER: SYSTEM
ROLE: Validates prompt-pack compliance and internal consistency:
required fields exist, tag/instruction/negative sets are non-contradictory,
identity anchors are present early, UGC and duration constraints are not violated,
and negatives are concrete and not bloated.

Aligned to Prompt Contract + Phrasebooks + Negative Spec Library.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Prompt Fidelity validator: schema checks, contradiction detection, bloat control, and required fix actions."
- REASON: "Most wasted takes come from broken prompts: contradictions, bloat, missing anchors, vague negatives."
- IMPACT: "Higher generation fidelity, fewer repeats, cleaner gate decisions."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.PROMPT_FIDELITY.001

---

## 0) PURPOSE (LAW)
Answer:
**“Is the prompt pack valid, consistent, and compliant with the prompt contract?”**

This validator checks prompt-pack structure and contradiction/bloat risks.

---

## 1) INPUTS (CONSUMES)
Required:
- PROMPT_PACK (Suno mandatory; Udio optional)
  - Suno.Lyrics
  - Suno.Styles (tags)
  - Suno.Instruction
  - Suno.Negative
- DURATION_MODE: {SHORT | FULL | ALT_INTRO}
- UGC_INTENT: {YES | NO}
- STYLE_FINGERPRINT_ANCHORS (list) (recommended)
- SELECTED_NEGATIVE_PACKS (optional list of pack ids)

Optional:
- Udio pack fields if produced:
  - Udio.Tags
  - Udio.Instruction
  - Udio.Negative
  - Udio.Lyrics (if lyrical)

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | FIX_SCHEMA | REMOVE_CONTRADICTIONS | REDUCE_BLOAT | ADD_ANCHORS | FIX_NEGATIVES | ALIGN_DURATION_UGC}
- RETEST_NOTES: 1–2 actions max

---

## 3) RULE SOURCES (CTL) — RAW
Prompt Contract CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

Suno Phrasebook CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md

Udio Phrasebook CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md

Negative Spec Library CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

Duration Policy CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

UGC Viral Ruleset CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — Required schema fields exist
FAIL if any mandatory Suno field missing:
- Lyrics / Styles / Instruction / Negative

If Udio pack exists:
- FAIL if Tags/Instruction/Negative missing.

---

### CHECK B — Tag count and ordering constraints
WARN if:
- Suno.Styles tag count > 16 (bloat risk)
- tag order likely violates contract (genre soup)
FAIL if:
- tags contain contradictory genres as equals without fusion notes

---

### CHECK C — Instruction length and clarity
WARN if instruction is too long (essay) or contains many unrelated clauses.
FAIL if instruction is contradictory (e.g., "slow ballad" + "fast upbeat").

---

### CHECK D — Contradiction detection (core)
FAIL if:
- tags say X and negatives forbid X
- instruction requests X and negatives forbid X
- tags conflict strongly with each other (3+ unrelated genres)
WARN if:
- mild tension exists but fixable (remove one tag)

---

### CHECK E — Anchor presence (recommended)
If anchors provided:
- WARN if anchors are not represented in tags/instruction
FAIL only if the pack explicitly contradicts anchors.

---

### CHECK F — Negative list quality
WARN if:
- negatives are vague ("bad", "boring")
- too many negatives (>30) or duplicate-heavy
FAIL if:
- negative list cancels required identity (e.g., forbids core palette)

---

### CHECK G — Duration/UGC alignment
WARN if:
- UGC_INTENT=YES but no instruction cue exists for clip window/edit point
- DURATION_MODE=SHORT but instruction implies long build
FAIL if:
- explicit contradictions to duration policy (“long ambient intro”) in SHORT mode

---

## 5) DECISION LOGIC
PASS when:
- schema complete
- no contradictions
- bloat within limits
- duration/UGC alignment OK

WARN when:
- minor bloat or mild contradictions fixable with 1 action
- anchors missing in wording but not contradicted

FAIL when:
- missing mandatory fields
- hard contradictions present
- excessive bloat that destroys prompt fidelity
- explicit violation of SHORT/UGC constraints

---

## 6) REQUIRED ACTIONS (STANDARD)
- FIX_SCHEMA: add missing mandatory fields
- REMOVE_CONTRADICTIONS: remove conflicting tags or reword instruction
- REDUCE_BLOAT: cut tags and negatives to within contract limits
- ADD_ANCHORS: add identity anchors into tags/instruction
- FIX_NEGATIVES: remove vague items, dedup, keep concrete blockers
- ALIGN_DURATION_UGC: update instruction to match mode and UGC rules

---

## 7) OUTPUT SCHEMA (MANDATORY)
PROMPT_FIDELITY_VAL_RESULT:
- TRACK_UID:
- VARIANT_LABEL:
- DURATION_MODE:
- UGC_INTENT:
- SUNO_FIELDS_PRESENT: YES/NO
- UDIO_FIELDS_PRESENT: YES/NO/NA
- TAG_COUNT:
- NEGATIVE_COUNT:
- CONTRADICTIONS_FOUND: (list)
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
