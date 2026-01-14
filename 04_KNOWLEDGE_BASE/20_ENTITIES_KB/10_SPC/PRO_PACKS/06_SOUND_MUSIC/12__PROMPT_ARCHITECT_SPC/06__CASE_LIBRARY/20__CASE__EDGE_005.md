# CASE — EDGE (LYRICS PROVIDED / COMPLIANCE BOUNDARY) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/20__CASE__EDGE_005.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.005
OWNER: SYSTEM
ROLE: Edge-case calibrating COMPLIANCE boundaries when user provides lyrics or references: avoid large paste into KB sources, avoid “copy exactly” instructions, and record safe use as constraints/principles. Links to compliance checklist expectations.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added EDGE case #5: safe handling of provided lyrics and style references; compliance-first behavior."
- REASON: "Prompts often include copyrighted lyrics or requests to copy artists; pack must handle safely and deterministically."
- IMPACT: "Fewer compliance breaches and cleaner prompt contracts."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.EDGE.005

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-EDGE-005
- TYPE: EDGE
- CONTEXT:
  - FORMAT: any
  - INPUT: user provides lyrics text or asks to write “exactly like artist X”
- INPUT_INTENT (short):
  - Use the user’s own lyrics OR a short excerpt; ensure no “copy exact artist” instructions remain; record safe constraints.

---

## 1) EDGE SCENARIO (WHAT HAPPENS)
Scenario A (lyrics provided):
- User pastes lyrics (may be long).
Risk:
- KB becomes a storage for large external text.
- Contract becomes non-deterministic if lyrics are not clearly bounded.

Scenario B (“exactly like X”):
- User demands exact imitation of a known artist.
Risk:
- Must be rewritten into principles/genre descriptors.

---

## 2) EXPECTED COMPLIANCE OUTCOME (UID-ONLY)
EXPECTED_COMPLIANCE:
- UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001 -> PASS
  if:
  - lyrics are treated as user-provided input (not stored as external source dump)
  - style reference is rewritten into principles (no “copy exactly”)
  - trace flags recorded

- UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001 -> REWORK/FAIL
  if:
  - large lyrics copied into KB_SOURCES
  - “copy exactly X 1:1” remains in contract
  - unsafe instructions remain

---

## 3) SAFE HANDLING PATTERN (WHAT TO DO)
SAFE_PATTERN:
- If lyrics are user-authored:
  - allow using them as-is in prompt contract
  - keep them in the prompt contract only (not KB_SOURCES)
- If lyrics are not user-authored or unclear:
  - use only high-level constraints:
    - theme, mood, meter/rhyme principles
  - avoid copying large text
- If “exactly like X” request exists:
  - rewrite to:
    - genre + era + production principles
    - anchor roles
    - “inspired by” principles (no identity cloning)

Trace rules:
- record MEMORY_REUSE + WEB_LOOKUP_USED
- if any external source used to inform principles, record it in KB_SOURCES as extracted principles only.

---

## 4) MINIMAL FIX (IF REWORK)
If contract contains “copy exactly X”:
- Replace with:
  - PRIMARY genre identity
  - 3–6 anchors
  - dominance rule (if touch)
  - avoid artist-name mimicry

If lyrics paste is too long:
- Keep only:
  - chorus hook lines (short) OR summary of lyrical constraints
- Or request user to provide only the key hook lines for the prompt (operationally minimal).

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
