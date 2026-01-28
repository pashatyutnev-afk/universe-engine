# CASE — BORDERLINE (STYLE ANCHORS SLIGHTLY OVER LIMIT) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/13__CASE__BORDERLINE_003.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.003
OWNER: SYSTEM
ROLE: Borderline case calibrating Gate 04 REWORK threshold: style identity is clear, but anchor list is slightly too long (7–8) and includes multiple near-lead roles. Should be REWORK (not FAIL) and fixed by pruning to 3–6 anchors and one lead.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BORDERLINE case #3: anchors slightly over limit → Gate 04 REWORK with minimal prune patch."
- REASON: "Need calibration between PASS (3–6 anchors) and FAIL (genre soup): this is a near-pass pruning case."
- IMPACT: "Improves consistency of style stability decisions and minimal patch behavior."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BORDERLINE.003

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BL-003
- TYPE: BORDERLINE
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B optional
  - STYLE: nu metal (primary) + industrial touch
- INPUT_INTENT (short):
  - Stable nu metal identity with small industrial touches, but the style block is slightly cluttered.

---

## 1) PROMPT CONTRACT (BORDERLINE EXAMPLE)
STYLE_BLOCK (NEAR-PASS BUT CLUTTERED):
- PRIMARY: nu metal (dominant)
- SECONDARY: industrial touch (subtle)
- ANCHORS (7–8, too many):
  1) rhythm feel: half-time stomp
  2) guitar role: tight chug riffs (lead)
  3) synth role: glitch accents
  4) synth role: retro arps (another near-lead)
  5) drum tone: hybrid kit + electronic hits
  6) texture direction: clean aggressive
  7) atmosphere: cold metallic ambience pads
  8) editing: stutter edits (some)

STRUCTURE_BLOCK:
- verse/chorus present (not focus)

NEGATIVE_SPEC_BLOCK:
- avoid genre drift; keep primary style consistent
- avoid clutter (but anchors currently cluttered)

CONSTRAINTS_BLOCK:
- full song ~3 minutes

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS/REWORK
  NOTE: depends on how strict overload heuristics are; mostly readable

- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> REWORK
  WHY: anchors exceed recommended 3–6; multiple near-lead synth roles increase drift risk

Other gates:
- voice/repetition: N/A
- one-axis: N/A

---

## 3) WHY THIS IS BORDERLINE
WHY_BORDERLINE:
- Primary + touch identity is correct.
- No hard contradictions or genre soup.
- Only issue is slight clutter:
  - 7–8 anchors and too many “lead-ish” synth ideas.
→ This should be REWORK, because a minimal prune yields a stable fingerprint.

Threshold taught:
- PASS target: 3–6 anchors
- one lead role only (guitar OR synth lead), the rest support roles.

---

## 4) MINIMAL PRUNE PATCH (TO REACH PASS ON GATE 04)
PATCH_PROMPT (MINIMAL CHANGE):
- Keep everything else unchanged.
- Prune anchors to 5 (example):
  - rhythm feel: half-time stomp
  - guitar role: tight chug riffs (lead)
  - synth role: glitch accents (support)  (REMOVE retro arps)
  - drum tone: hybrid kit + controlled electronic hits
  - texture direction: clean aggressive
- Optional:
  - keep ambience pads only if they are subtle, otherwise remove
  - keep stutter edits as "sparingly" or remove

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
