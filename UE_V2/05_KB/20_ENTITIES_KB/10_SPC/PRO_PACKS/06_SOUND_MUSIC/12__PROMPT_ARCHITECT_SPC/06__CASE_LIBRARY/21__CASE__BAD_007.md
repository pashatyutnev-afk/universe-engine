# CASE — BAD (COMPLIANCE FAIL: "COPY EXACTLY" NOT REMOVED) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/21__CASE__BAD_007.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.007
OWNER: SYSTEM
ROLE: BAD case calibrating COMPLIANCE FAIL: prompt contract contains explicit “copy exactly a specific artist/band 1:1” instruction, which must be rewritten into principles. Demonstrates the required fix behavior.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BAD case #7: compliance fail when 'copy exactly' instruction remains."
- REASON: "Need a clear FAIL anchor for IP boundary and safe prompting discipline."
- IMPACT: "Prevents unsafe imitation instructions from entering prompt contracts."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BAD.007

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-007
- TYPE: BAD
- CONTEXT:
  - FORMAT: any
  - RISK: style-cloning instruction
- INPUT_INTENT (short):
  - User requests an exact copy of a known artist’s style.

---

## 1) BAD PROMPT ELEMENT (EXAMPLE)
BAD_INSTRUCTION:
- "Make it exactly like <specific artist/band> 1:1. Same vocals, same sound, same everything."

Why this is bad:
- It attempts identity-level imitation rather than using genre principles.

---

## 2) EXPECTED COMPLIANCE OUTCOME (UID-ONLY)
EXPECTED_RESULTS:
- UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001 -> FAIL
  WHY: “copy exactly” instruction not removed; violates IP boundary policy

Optional additional effects:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> REWORK/FAIL
  WHY: contract includes forbidden instruction; must be rewritten

---

## 3) REQUIRED FIX BEHAVIOR (WHAT TO DO INSTEAD)
FIX_REQUIRED:
- Replace “copy exactly” with:
  - PRIMARY genre identity
  - SECONDARY touch (optional)
  - 3–6 anchors (roles, not inventories)
  - mix intent principles (one direction)
  - vocal delivery principles (no identity cloning)
- Remove artist-name mimicry and any “same vocals” demands.

Safe rewrite template (principles):
- PRIMARY: <genre label>
- SECONDARY: <touch label>
- ANCHORS: rhythm feel + lead role + support role + texture direction
- VOCALS: delivery + range/timbre principles (no identity claim)
- CONSTRAINTS: duration + hook + repetition policy

---

## 4) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
