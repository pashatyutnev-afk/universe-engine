# SUNO PHRASEBOOK — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: SUNO_PHRASEBOOK
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.SUNO_PHRASEBOOK.001
OWNER: SYSTEM
ROLE: Defines a controlled library of approved instruction phrases for Suno prompt packs:
hook timing cues, variation cues, UGC cues, intro cues, vocal cues, and mix cues.
Prevents vague prompts and reduces contradictory wording.
This is a phrase *library* (allowed building blocks), not a generator.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Suno Phrasebook CTL: approved phrase library categories for consistent Suno instructions."
- REASON: "Prompts fail when instructions are vague or contradictory; a controlled phrasebook makes prompts consistent."
- IMPACT: "Higher fidelity, fewer wasted takes, easier prompt QA."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.SUNO.PHRASEBOOK.001

---

## 0) PURPOSE (LAW)
This controller provides **approved phrase building blocks** for Suno prompts.
Producers must prefer these phrases to ad-hoc wording.

Rules:
- Choose minimal phrases needed.
- Avoid stacking many similar phrases.
- Never include contradictory phrases from different categories.

---

## 1) PHRASEBOOK CATEGORIES (CANON)
Each prompt instruction may use:
- 1–2 Hook Timing phrases
- 1 Variation phrase
- 1 UGC phrase (if UGC-first)
- 0–1 Intro phrase
- 0–1 Vocal phrase
- 0–1 Mix phrase

---

## 2) HOOK TIMING PHRASES (APPROVED)
- "Bring the hook in early (within the first 15–25 seconds)."
- "Early recognition: stamp the main motif in the first 10 seconds."
- "Start with a strong recognizable motif, then reveal the full hook."

(Choose 1 max.)

---

## 3) VARIATION / REPEAT-SAFE PHRASES (APPROVED)
- "Repeat the chorus with subtle variation (change one line or detail)."
- "Keep the hook consistent but evolve it slightly on repeats."
- "Avoid identical phrase loops; vary the phrasing on returns."

(Choose 1 max.)

---

## 4) UGC PHRASES (APPROVED)
- "Include a clean 10–15 second clip window with a clear cut point."
- "Add a pause/snap moment for edits near the main hook."
- "Make the hook section work as a standalone short clip."

(Choose 1 max when UGC-first.)

---

## 5) INTRO STYLE PHRASES (APPROVED)
- "Minimal intro: get to the groove immediately."
- "Cold open into the hook-adjacent section."
- "Quick signature tag intro, then straight into the groove."

(Choose 0–1.)

---

## 6) VOCAL PHRASES (APPROVED)
Use only when lyrical/vocal direction needs clarity:
- "Clear intelligible lead vocal, front and present."
- "Distinct vocal character; avoid generic pop delivery."
- "Call-and-response feel in the hook."

(Choose 0–1.)

---

## 7) MIX / AESTHETIC PHRASES (APPROVED)
- "Modern, punchy mix with clear low end."
- "Warm, cohesive mix, not harsh."
- "Crisp drums and tight groove."

(Choose 0–1.)

---

## 8) PROHIBITED WORDING (HARD BLOCKERS)
Do not use:
- vague phrases: "make it viral", "make it cool"
- contradictory mixes: "lo-fi clean hi-fi polished"
- conflicting tempos: "slow and fast"
- genre soup: 3+ unrelated genres without fusion recipe

---

## 9) DEPENDENCIES (RAW)
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
