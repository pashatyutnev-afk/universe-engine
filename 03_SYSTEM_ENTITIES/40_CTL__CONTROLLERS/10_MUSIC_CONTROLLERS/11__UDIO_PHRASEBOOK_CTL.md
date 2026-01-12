# UDIO PHRASEBOOK — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: UDIO_PHRASEBOOK
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.UDIO_PHRASEBOOK.001
OWNER: SYSTEM
ROLE: Approved phrase library for Udio prompt packs (sound-bible style):
compact wording patterns for palette, vocals, structure, hook timing, UGC moments, variation rules, and mix principles.
Prevents vague/contradictory prompts and improves prompt fidelity.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Rebuilt Udio Phrasebook CTL: standardized categories and approved phrases for Udio instructions."
- REASON: "Stub was non-operational; Udio prompts need consistent executable wording."
- IMPACT: "Higher prompt clarity, fewer contradictions, easier VAL/QA gating."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.UDIO.PHRASEBOOK.001

---

## 0) PURPOSE (LAW)
This controller provides **approved phrase building blocks** for UDIO prompts.
Producers must prefer these phrases over ad-hoc wording.

RULES:
- Choose the minimum phrases needed.
- Never include contradictory phrases.
- Do not stack multiple near-duplicates (“more of the same”).
- Phrasebook = allowed blocks, not a generator.

---

## 1) USAGE CONTRACT (MANDATORY)
For an Udio prompt pack, instruction should typically use:
- 1 phrase from (HOOK TIMING)
- 1 phrase from (REPEAT-SAFE / VARIATION)
- 0–1 phrase from (UGC)
- 0–1 phrase from (INTRO)
- 0–2 phrases from (PALETTE / INSTRUMENTATION)
- 0–1 phrase from (VOCAL DELIVERY) if vocal
- 0–1 phrase from (MIX PRINCIPLES)

Do not exceed:
- 6 total phrases in instruction (recommended)
- 10 total phrases in instruction (hard max)

---

## 2) PALETTE / INSTRUMENTATION PHRASES (APPROVED)
Pick 1–2 max.
- "Focused, cohesive palette with a clear signature timbre."
- "Dominant instrument family stays consistent across the track."
- "Tight groove-first instrumentation; avoid cluttered layers."
- "Use a recognizable signature sound tag as an identity stamp."

---

## 3) VOCAL DELIVERY PHRASES (APPROVED)
Pick 0–1 (only if vocal).
- "Clear, intelligible lead vocal; front and present."
- "Distinct vocal character; avoid generic pop delivery."
- "Call-and-response feel in the hook section."
- "Avoid muddy consonants; keep phrasing crisp."

---

## 4) STRUCTURE + HOOK TIMING PHRASES (APPROVED)
Pick 1 max.
- "Bring the hook in early; stamp the main motif within the first 15–25 seconds."
- "Early recognition: introduce the signature motif in the first 10 seconds."
- "Cold open into hook-adjacent material; no long build."

---

## 5) REPEAT-SAFE / VARIATION PHRASES (APPROVED)
Pick 1 max.
- "Repeat the hook with subtle variation (change one line or detail)."
- "Keep the hook consistent, but evolve it slightly on returns."
- "Avoid identical phrase loops; vary phrasing and cadence on repeats."

---

## 6) UGC PHRASES (APPROVED)
Pick 0–1 (use when UGC-first).
- "Include a clean 10–15 second clip window with a clear cut point."
- "Add a pause/snap moment near the hook for edits."
- "Make the hook section work as a standalone short clip."

---

## 7) INTRO STYLE PHRASES (APPROVED)
Pick 0–1.
- "Minimal intro: get to the groove immediately."
- "Quick identity stamp first, then straight into the main groove."
- "No ambient intro; start with a recognizable motif."

---

## 8) ANTI-CLICHÉ / ANTI-DRIFT PHRASES (APPROVED)
Pick 0–1 (only if drift risk exists).
- "Stay within the core genre identity; avoid genre-soup switching."
- "Keep the signature palette stable; do not add random instruments."
- "Avoid cliché chant spam; keep repeats purposeful."

---

## 9) MIX TARGETS (PRINCIPLES) PHRASES (APPROVED)
Pick 0–1 (principles, not exact settings).
- "Punchy, clean mix with clear low end and a stable center."
- "Cohesive mix; avoid harshness and excessive smear."
- "Crisp drums, tight groove, and controlled dynamics."

---

## 10) PROHIBITED WORDING (HARD BLOCKERS)
Do NOT use:
- vague phrases: "make it viral", "make it cool", "make it better"
- contradictions: "lo-fi polished hi-fi", "slow fast", "sad party anthem"
- 3+ unrelated genres without fusion recipe
- instruction bloat (walls of text)
- negatives that cancel the identity anchors

---

## 11) DEPENDENCIES (RAW)
Must align with:
- Prompt Contract CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- Duration Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- UGC Viral Ruleset CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

Validator alignment:
- Prompt Fidelity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
