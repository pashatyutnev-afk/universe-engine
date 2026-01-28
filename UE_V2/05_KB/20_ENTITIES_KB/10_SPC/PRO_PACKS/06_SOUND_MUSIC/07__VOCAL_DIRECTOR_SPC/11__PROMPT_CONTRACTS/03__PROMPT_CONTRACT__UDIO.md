# SPC PRO PACK — PROMPT CONTRACT (UDIO) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/11__PROMPT_CONTRACTS/03__PROMPT_CONTRACT__UDIO.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PROMPT_CONTRACT
PLATFORM: UDIO
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PROMPT.VOCAL_DIRECTOR.UDIO.001
OWNER: SYSTEM
ROLE: UDIO prompt contract template for VOCAL_DIRECTOR. Converts output-pack artifacts into UDIO-friendly prompt text: compact constraints, must-hear targets, breath protection, optional arc and stacking constraints, plus negative spec. Does NOT rewrite lyrics; lyrics are pasted as-is by user.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created UDIO prompt contract template for VOCAL_DIRECTOR."
- REASON: "Need deterministic UDIO prompt structure that preserves intelligibility without scope violations."
- IMPACT: "More consistent vocal clarity and hook recognition in UDIO runs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PROMPT.VD.UDIO.001

---

## 0) PURPOSE
UDIO contract generates:
- a copy-ready UDIO prompt string (constraints + negatives)
- rules for the lyrics field (paste as-is)

---

## 1) INPUT SOURCE (DERIVE ONLY)
Derived only from:
- OUTPUT PACK MIN / STD / FULL
No invented details.

---

## 2) SCOPE RULE (ABSOLUTE)
FORBIDDEN:
- lyric rewrites / replacement lines
- mix/master plugin chains or DAW recipes
- ownership overreach (structure/arrangement) outside escalation

---

## 3) CONTRACT BLOCKS (STABLE) — ORDER
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

## 4) TEMPLATE (FILL-IN)
### 1) PROMPT_HEADER
PROMPT_HEADER:
- platform: UDIO
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
  - "P0 must be clearly understood on first listen in hook"
  - "consonant-forward attacks on P0"
  - "avoid masking; keep chorus words clearer than verse"

### 3) PROMPT_ARC (optional; FULL)
PROMPT_ARC:
- arc:
  - "Verse baseline -> Chorus lift/release"
- levers (<=3):
  - "<Intensity verse->chorus>"
  - "<Articulation verse->chorus>"
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
  - rule: "minimal-first; avoid layers over P0 attacks"
  - hint: "doubles on tails only"

### 6) NEGATIVE_SPEC
NEGATIVE_SPEC:
- avoid:
  - "breath splits inside must-hear phrases"
  - "swallowed consonants on P0"
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

### 9) COPY_READY_PROMPT (LAST)
COPY_READY_PROMPT:
- "<single copy-ready UDIO prompt string assembled from rules below>"

---

## 5) ASSEMBLY RULES (COPY_READY_PROMPT)
Assemble in this order:
1) Genre/style tags (if provided)
2) Language + vocal mode
3) Must-hear directive + P0 list
4) Never-split phrase constraint (1–2 phrases)
5) 1–2 style principles
6) Arc note (if FULL; 1–2 clauses)
7) Stacking note (if used)
8) Append “avoid:” list

Keep it one compact paragraph.

---

## 6) MINIMUM QUALITY CHECK
Contract is valid only if:
- P0 present
- breath split avoidance present
- scope notice present
- no forbidden content present

---

## 7) TRACE
TRACE:
- CONTRACT: UDIO
- UID: UE.KB.SPC.PROMPT.VOCAL_DIRECTOR.UDIO.001
- SOURCE: OUTPUT PACKS (MIN/STD/FULL)

--- END.
