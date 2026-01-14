# CASE — EDGE (FUSION RISK: MISSING DOMINANCE RULE) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/08__CASE__EDGE_002.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.002
OWNER: SYSTEM
ROLE: Edge-case calibrating fusion risk: multiple style labels without explicit dominance rule. Should trigger Gate 04 REWORK (or FAIL if contradictions/genre soup). Includes minimal fix to reach PASS.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added EDGE case #2: fusion without dominance rule → style drift risk; fix via dominance + anchor pruning."
- REASON: "Fusion prompts commonly drift unless dominance is explicit; need calibration case for Gate 04."
- IMPACT: "More consistent handling of blends and fewer random outputs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.EDGE.002

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-EDGE-002
- TYPE: EDGE
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B optional
  - STYLE: fusion (multiple labels)
- INPUT_INTENT (short):
  - Blend two styles for novelty but keep identity stable (risk: without dominance rule the generator drifts).

---

## 1) PROMPT CONTRACT (EDGE — RISKY FUSION)
STYLE_BLOCK (PROBLEM):
- nu metal + synthwave + industrial rock (all stated)
- ANCHORS (too many / unclear):
  - heavy guitars
  - big synth leads
  - aggressive drums
  - cinematic pads
  - glitch edits
  - retro arps
- (NO dominance rule, no primary vs touch)

STRUCTURE_BLOCK:
- Intro
- Verse
- Chorus (hook)
- Verse 2
- Bridge
- Final chorus
- Outro

NEGATIVE_SPEC_BLOCK:
- avoid genre drift (but not enforced by dominance)
- avoid mud

CONSTRAINTS_BLOCK:
- full song ~3 minutes
- hook should be catchy

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS/REWORK
  NOTE: blocks exist but style definition is risky (may trigger REWORK for overload)

- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> REWORK
  WHY: multiple styles listed without dominance rule; anchors list is cluttered

- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> REWORK/N/A (not the focus; depends on presence of policy)
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> N/A (not specified)
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A

---

## 3) WHY THIS IS EDGE (CALIBRATION NOTES)
WHY_EDGE:
- Fusion is allowed, but without dominance the generator can:
  - randomly pick one style per section
  - produce “genre soup” blends
- Too many anchors create clutter and conflict over “who is lead”.
- This case teaches Gate 04 threshold:
  - fusion requires dominance rule + 3–6 anchors max.

---

## 4) MINIMAL FIX (TO REACH PASS ON GATE 04)
PATCH_PROMPT (MINIMAL CHANGE):
- Keep everything else unchanged.
- Replace STYLE_BLOCK with dominance + pruned anchors:

FIXED_STYLE_BLOCK (COPY):
- PRIMARY: nu metal (dominant)
- SECONDARY: synthwave touch (subtle)
- MUST STAY PRIMARY:
  - guitar role: tight chug riffs (dominant)
  - rhythm feel: heavy groove (consistent)
- ANCHORS (3–6):
  - rhythm feel: heavy groove / half-time feel (one)
  - guitar role: chug riffs (one)
  - synth role: retro arps as subtle layer (one)
  - drum tone: punchy kit + controlled industrial hits (optional)
  - texture direction: clean aggressive (one)

- Add optional negative:
  - "avoid genre drift; keep primary style consistent"

Expected after patch:
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS

Playbook mapping:
- PB-07 STYLE FINGERPRINT STABILIZER
- PB-04 PATCH MIN (axis: style)

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
