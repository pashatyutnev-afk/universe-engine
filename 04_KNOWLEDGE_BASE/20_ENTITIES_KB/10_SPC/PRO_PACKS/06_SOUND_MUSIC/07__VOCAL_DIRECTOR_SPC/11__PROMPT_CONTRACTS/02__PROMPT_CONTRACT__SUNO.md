# SPC PRO PACK — PROMPT CONTRACT (SUNO) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/11__PROMPT_CONTRACTS/02__PROMPT_CONTRACT__SUNO.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PROMPT_CONTRACT
PLATFORM: SUNO
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PROMPT.VOCAL_DIRECTOR.SUNO.001
OWNER: SYSTEM
ROLE: SUNO prompt contract template for VOCAL_DIRECTOR. Converts output-pack artifacts into SUNO-friendly prompt text: style tags + vocal performance constraints + negative spec. Does NOT rewrite lyrics; lyrics are pasted as-is by user.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created SUNO prompt contract template for VOCAL_DIRECTOR."
- REASON: "SUNO needs compact style + constraints, while lyrics are provided separately and must remain unchanged."
- IMPACT: "More consistent vocal clarity and hook recognition in SUNO runs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PROMPT.VD.SUNO.001

---

## 0) PURPOSE
SUNO contract generates:
- a copy-ready SUNO prompt string (style + constraints)
- guidance for the lyrics field (paste as-is; no edits)
- negative spec to avoid intelligibility failures

---

## 1) INPUT SOURCE (DERIVE ONLY)
Derived only from:
- OUTPUT PACK MIN / STD / FULL

No invented details.

---

## 2) SUNO FIELD MODEL (PRACTICAL)
SUNO typically uses:
- Style/Prompt text (where we place constraints)
- Lyrics field (user pastes lyrics)

Rule:
- This contract never rewrites lyrics.
- It may only instruct how to deliver lyrics.

---

## 3) SCOPE RULE (ABSOLUTE)
FORBIDDEN:
- lyric rewrites / replacement lines
- mix/master plugin chains or DAW recipes
- claiming ownership over structure/arrangement (use escalation outside contract)

---

## 4) CONTRACT BLOCKS (STABLE) — ORDER
1) PROMPT_HEADER
2) PROMPT_CORE
3) PROMPT_ARC (optional; FULL)
4) PROMPT_BREATH (optional; STD/FULL)
5) PROMPT_STACKING (optional; STD/FULL)
6) NEGATIVE_SPEC
7) SCOPE_NOTICE
8) LYRICS_FIELD_RULES
9) COPY_READY_PROMPT

COPY_READY_PROMPT must be last.

---

## 5) TEMPLATE (FILL-IN)
### 1) PROMPT_HEADER
PROMPT_HEADER:
- platform: SUNO
- tier: MIN | STD | FULL
- language:
- hook_section_label:
- bpm (optional):
- genre_style_tags (optional):
  - "<comma-separated style tags>"
- vocal_mode (optional): rap | sing | mixed

### 2) PROMPT_CORE
PROMPT_CORE:
- must_hear_targets:
  - P0: <comma list>
  - P1: <comma list or N/A>
- must_hear_phrases:
  - P0:
    - "<copy-exact phrase>"
- vocal_style:
  - "<1–2 lines from delivery principles (if available)>"
- clarity_constraints:
  - "P0 understood on first listen in hook"
  - "consonant-forward attacks on P0"
  - "keep hook words clearer than verses"

### 3) PROMPT_ARC (optional; FULL)
PROMPT_ARC:
- arc:
  - "Verse baseline -> Chorus lift/release"
- levers (<=3):
  - "<Intensity: verse->chorus>"
  - "<Articulation focus: verse->chorus>"
  - "<Optional third lever>"

### 4) PROMPT_BREATH (optional; STD/FULL)
PROMPT_BREATH:
- never_split_phrases:
  - "<P0 phrase>"
- breath_policy:
  - allowed: "before/after P0 phrases, between lines"
  - forbidden: "inside P0 phrases"

### 5) PROMPT_STACKING (optional; STD/FULL)
PROMPT_STACKING:
- stacking_used: YES/NO
- if YES:
  - rule: "minimal-first stacking; avoid layers over P0 attacks"
  - hint: "doubles on tails only"

### 6) NEGATIVE_SPEC
NEGATIVE_SPEC:
- avoid:
  - "breath splits inside must-hear phrases"
  - "swallowed consonants on P0 words"
  - "muddy chorus where words disappear"
  - "character switching between takes"
  - "stacking that masks P0" (if stacking_used=YES)

### 7) SCOPE_NOTICE
SCOPE_NOTICE:
- lyric_rewrite: FORBIDDEN
- mix_chain: FORBIDDEN
- lyrics: "PASTE AS-IS"

### 8) LYRICS_FIELD_RULES
LYRICS_FIELD_RULES:
- paste_lyrics_as_is: YES
- do_not_edit_words: YES
- keep_section_labels (recommended): YES
- if stress/word is problematic:
  - escalate outside SUNO prompt; do not rewrite here

### 9) COPY_READY_PROMPT (LAST)
COPY_READY_PROMPT:
- "<single copy-ready SUNO prompt string assembled from rules below>"

---

## 6) ASSEMBLY RULES (COPY_READY_PROMPT)
Assemble in this order:
1) Genre/style tags (if provided) as comma list
2) Language + vocal mode
3) Hook clarity directive:
   - “P0 words must be clearly understood first listen in hook”
4) List P0 must-hear words (comma)
5) Add “never split” phrase constraint (1–2 phrases max)
6) Add 1–2 vocal style principles (if available)
7) Add stacking note (if used)
8) Append NEGATIVE_SPEC as “avoid: …”

Keep it compact (one paragraph).

---

## 7) MINIMUM QUALITY CHECK
Contract is valid only if:
- P0 present
- never-split phrase included if phrases exist
- avoid list includes breath split + consonant swallow
- scope notice present

---

## 8) TRACE
TRACE:
- CONTRACT: SUNO
- UID: UE.KB.SPC.PROMPT.VOCAL_DIRECTOR.SUNO.001
- SOURCE: OUTPUT PACKS (MIN/STD/FULL)

--- END.
