# SPC PRO PACK — PROMPT CONTRACT (UNIVERSAL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/11__PROMPT_CONTRACTS/01__PROMPT_CONTRACT__UNIVERSAL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PROMPT_CONTRACT
PLATFORM: UNIVERSAL
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PROMPT.VOCAL_DIRECTOR.UNIVERSAL.001
OWNER: SYSTEM
ROLE: Universal prompt contract template for VOCAL_DIRECTOR. Converts output-pack artifacts into a compact, copy-ready prompt blueprint using stable contract blocks. Platform-neutral.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created UNIVERSAL prompt contract template for VOCAL_DIRECTOR."
- REASON: "Need a stable intermediate contract that can be adapted to any platform formatting."
- IMPACT: "Less prompt drift, better repeatability."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PROMPT.VD.UNI.001

---

## 0) PURPOSE
UNIVERSAL Prompt Contract is the platform-neutral template.
It is used to generate:
- SUNO prompt contracts
- UDIO prompt contracts
- future platforms

---

## 1) INPUT SOURCE (DERIVE ONLY)
This contract must be derived ONLY from:
- OUTPUT PACK MIN / STD / FULL
No invented details are allowed.

---

## 2) SCOPE RULE (ABSOLUTE)
FORBIDDEN in contract and in COPY_READY_PROMPT:
- lyric rewrites / replacement lines
- mix/master plugin chains or DAW recipes
- ownership claims (structure/arrangement) outside escalation language

If needed:
- use ESCALATION_NOTES separately (not inside prompt contract).

---

## 3) CONTRACT BLOCKS (STABLE)
Contract output must use these blocks only, in this order:

1) PROMPT_HEADER
2) PROMPT_CORE
3) PROMPT_ARC (optional)
4) PROMPT_BREATH (optional)
5) PROMPT_STACKING (optional)
6) NEGATIVE_SPEC
7) SCOPE_NOTICE
8) COPY_READY_PROMPT

Rule:
- COPY_READY_PROMPT must be last.

---

## 4) TEMPLATE (FILL-IN)
### 1) PROMPT_HEADER
PROMPT_HEADER:
- platform: UNIVERSAL
- tier: MIN | STD | FULL
- language:
- hook_section_label:
- vocal_mode (optional): rap | sing | mixed
- notes (optional):

### 2) PROMPT_CORE
PROMPT_CORE:
- vocal_style:
  - "<1–2 lines from VOCAL_STYLE_PROFILE (if available)>"
- vocal_delivery_constraints:
  - "<consonant clarity / attack protection emphasis>"
- must_hear_targets:
  - P0: <comma list>
  - P1: <comma list or N/A>
- must_hear_phrases:
  - P0:
    - "<phrase>"
  - P1:
    - "<phrase>" (optional)

### 3) PROMPT_ARC (optional; FULL)
PROMPT_ARC:
- arc_map:
  - "<Verse baseline>"
  - "<Chorus lift>"
- contrast_levers:
  - "<L1 intensity: verse->chorus>"
  - "<L3 articulation: verse->chorus>"
  - "<optional third lever>"

### 4) PROMPT_BREATH (optional; STD/FULL)
PROMPT_BREATH:
- breath_policy:
  - allowed: "<short>"
  - forbidden: "<short>"
- never_split_phrases:
  - "<P0 phrase>"

### 5) PROMPT_STACKING (optional; STD/FULL)
PROMPT_STACKING:
- stacking_used: YES/NO
- if YES:
  - protected_zones:
    - "<P0 phrases and P0 attacks must stay clear>"
  - stacking_hint:
    - "<minimal-first: doubles on tails only>"

### 6) NEGATIVE_SPEC
NEGATIVE_SPEC:
- avoid:
  - "breath split inside P0 phrases"
  - "swallowed consonant attacks on P0"
  - "stacking that reduces P0 clarity" (if stacking used)
  - "vocal character switching between takes"
  - "muddy chorus where words disappear"

### 7) SCOPE_NOTICE
SCOPE_NOTICE:
- lyric_rewrite: FORBIDDEN
- mix_chain: FORBIDDEN
- ownership: ESCALATE_ONLY

### 8) COPY_READY_PROMPT (LAST)
COPY_READY_PROMPT:
- "<assemble a single compact prompt string using rules below>"

---

## 5) ASSEMBLY RULES (COPY_READY_PROMPT)
When assembling COPY_READY_PROMPT:
1) Start with: language + vocal mode (if known)
2) Add: “must-hear targets” (P0 first)
3) Add: “must-hear phrases never split” (if phrases exist)
4) Add: key vocal style principles (max 2)
5) Add: arc instruction (if FULL; max 2 lines)
6) Add: stacking constraint (if used; minimal-first)
7) Append NEGATIVE_SPEC as short “avoid” list
8) Keep it compact:
   - prefer commas and short clauses
   - avoid long paragraphs

---

## 6) MINIMUM QUALITY CHECK
Contract is valid only if:
- P0 present
- never-split phrases included when phrases exist
- avoid list includes intelligibility risks
- no forbidden content present

---

## 7) TRACE
TRACE:
- CONTRACT: UNIVERSAL
- UID: UE.KB.SPC.PROMPT.VOCAL_DIRECTOR.UNIVERSAL.001
- SOURCE: OUTPUT PACKS (MIN/STD/FULL)

--- END.
