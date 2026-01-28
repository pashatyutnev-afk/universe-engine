# Prompt Compiler Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 12_TREND_GENRE_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: TREND_GENRE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.2
UID: UE.ENG.TG.PROMPT_COMPILER.001
OWNER: SYSTEM
ROLE: Compiles deterministic, platform-native prompt packs (Suno/Udio) from taxonomy + fusion + fingerprint + hook blueprint + UGC map + duration strategy + negative specs.

Outputs paste-ready prompts and variant packs, enabling high prompt fidelity and low drift.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created prompt compiler: standardized prompt pack schema, tag ordering, negative spec compression, and variant compilation."
- REASON: "Unstructured prompts cause drift and inconsistent results; we need a compiler."
- IMPACT: "Higher prompt fidelity, faster generation, less wasted takes."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.PROMPT.COMPILER.001
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line + added explicit mandatory SUNO pack output rule; preserved original intent."
- REASON: "Operational safety; ensure always paste-ready output."
- IMPACT: "No missing prompt packs; easier audits."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.TG.PROMPT.COMPILER.002

---

## 0) PURPOSE (LAW)
This engine converts all planning artifacts into a **paste-ready Prompt Pack**.

It must:
- preserve identity anchors (fingerprint)
- encode fusion without contradictions
- encode hook timing + repetition geometry
- embed UGC moments and clip windows
- respect duration strategy and platform policies
- compress negative specs into a short, effective list

---

## 1) INPUTS (CONSUMES)
- Genre Taxonomy output (primary family tags)
- Fusion Recipe Pack (optional)
- Style Fingerprint Pack (anchors/forbiddens + platform encoding)
- Viral Hook Blueprint (timing + geometry)
- UGC Moment Map (clip windows + moments)
- Earworm Hook Stack (H1/H2/S-tag/Q-line)
- Duration Strategy output (short/full targets)
- Prompt Contract CTL (rules for structure and allowed fields)
- Phrasebooks (Suno/Udio CTL phrase sets)
- Negative Spec Library CTL (avoid list)

---

## 2) OUTPUTS (PRODUCES)
Mandatory:
- **SUNO PROMPT PACK** (always)
Optional:
- UDIO PROMPT PACK
- Variant Packs:
  - SHORT
  - FULL
  - ALT_INTRO (if needed)
- Prompt Fidelity Notes (what must be preserved)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Genre Taxonomy",
  "Fusion Recipe (optional)",
  "Style Fingerprint",
  "Viral Hook Blueprint",
  "UGC Moment Map",
  "Earworm Hook Stack",
  "Duration Strategy",
  "Prompt Contract CTL",
  "Phrasebooks CTL",
  "Negative Spec Library CTL"
]
PRODUCES: [
  "Suno Prompt Pack (mandatory)",
  "Udio Prompt Pack (optional)",
  "Variant Packs (short/full/alt intro)",
  "Prompt Fidelity Notes"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS//PROMPTS/"

---

## 4) CORE LAW — SUNO PACK IS MANDATORY
Regardless of platform preference, this engine **always outputs a Suno Prompt Pack**.
Udio pack is optional.

---

## 5) PROMPT PACK STRUCTURE (STANDARD)

### 5.1 SUNO PACK FIELDS (MANDATORY)
- SUNO.LYRICS:
  - RU by default (or “Instrumental”)
  - must use section labels where needed (Verse/Chorus/Bridge etc.)
- SUNO.STYLES:
  - ordered list of tags (6–12)
- SUNO.INSTRUCTION:
  - short paragraph encoding:
    - hook timing window
    - repetition geometry
    - UGC moment placement
    - signature tag placement (S-tag)
- SUNO.NEGATIVE:
  - compact avoid list (short, concrete)

### 5.2 UDIO PACK FIELDS (OPTIONAL)
- UDIO.TAGS:
- UDIO.INSTRUCTION:
- UDIO.NEGATIVE:
- UDIO.LYRICS (if applicable)

---

## 6) TAG ORDERING RULE (IMPORTANT)
Order matters. Use this order:
1) genre family (primary)
2) era / reference vibe (if used)
3) instrumentation palette
4) groove/tempo feel
5) vocal style (if lyrical)
6) mood/emotion
7) mix aesthetic
8) signature tag hint

Never stack contradictory genres without fusion phrasing.

---

## 7) FUSION ENCODING (SAFE)
If Fusion Recipe exists:
- encode fusion as “A with B influence in <axis> during <section>”
- do NOT list A and B as equal if ratio is not equal
- keep A identity first in tags/instruction

---

## 8) HOOK + UGC ENCODING (EXECUTABLE)
Compiler must translate:
- Viral Hook Blueprint timing windows
- Earworm Hook Stack (H1/H2/S-tag/Q-line)
- UGC Moment Map clip windows

Into:
- short instruction lines that a generator can follow

Example patterns:
- “Hook by 0:12, repeat with variation, include a pause snap before second hook”
- “Make a clean 12–15s clip window centered on the quote line”

---

## 9) NEGATIVE SPEC COMPRESSION
Negative list must be:
- short (8–20 items max)
- concrete (“no long intro”, “no muddy vocals”, “no random genre switch”)
- derived from:
  - fingerprint forbiddens
  - policy forbiddens
  - failure fixes

---

## 10) VARIANT COMPILATION (SHORT/FULL/ALT)
Compiler produces variants by changing only:
- duration target
- section budgets / hook density
- intro entry method

Do not change fingerprint anchors between variants.

---

## 11) OUTPUT SCHEMA (PASTE READY)
Compiler output must be written exactly as:

### SUNO PROMPT PACK — <VARIANT NAME>
Suno.Lyrics:
...
Suno.Styles:
- ...
Suno.Instruction:
...
Suno.Negative:
- ...

(And optional Udio pack following similar format.)

---

## 12) FAILURE MODES & FIX
1) Model ignores prompt  
- Fix: reduce tags, strengthen instruction, tighten negatives, simplify fusion.

2) Output drifts off identity  
- Fix: move anchors earlier; repeat signature tag; remove conflicting tags.

3) Hook timing fails  
- Fix: make timing explicit; remove long intro cues.

4) Too many negatives → bland output  
- Fix: remove generic negatives; keep only “hard blockers”.

---

## 13) HANDOFFS (XREF)
Used by:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
