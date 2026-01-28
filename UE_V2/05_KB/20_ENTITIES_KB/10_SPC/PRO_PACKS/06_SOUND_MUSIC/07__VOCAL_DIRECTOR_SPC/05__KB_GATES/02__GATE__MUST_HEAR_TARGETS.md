# SPC PRO PACK — GATE (G2) — MUST-HEAR TARGETS (P0/P1) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/02__GATE__MUST_HEAR_TARGETS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
OWNER: SYSTEM
ROLE: Gate G2 validates that intelligibility targets are explicitly defined as MUST-HEAR words/phrases with priorities (P0/P1/P2). Without targets, vocal direction cannot be tested and becomes subjective.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G2: Must-Hear Targets (P0/P1) for VOCAL_DIRECTOR Pro Pack."
- REASON: "Intelligibility-first requires explicit, testable targets before prescribing delivery fixes."
- IMPACT: "QC becomes pass/fail; take direction focuses on what must land."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.MUSTHEAR.001

---

## 0) PURPOSE
This gate answers:
- Are the intelligibility targets defined, prioritized, and testable?

Targets are:
- MUST_HEAR_WORDS (P0/P1/P2)
- MUST_HEAR_PHRASES (when meaning depends on multi-word units)

---

## 1) REQUIRED INPUTS
Prerequisite:
- G1 must PASS (lyrics + structure + language exist)

Inputs required for this gate:
- LYRIC_DRAFT (hook lines)
- HOOK SECTION identifiable (from structure)

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if ALL are true:
- P0 exists AND has 3–8 items (words or phrases)
- P0 items are meaning carriers (not filler)
- P1 exists OR is explicitly N/A with reason (rare)
- Phrase promotion is used when necessary:
  - if meaning depends on multi-word unit, it appears in MUST_HEAR_PHRASES

Additionally:
- Clarity targets exist (at least one PASS condition statement):
  - “P0 understood on first listen in chorus/hook.”

### REWORK
REWORK if any of these holds:
- P0 exists but is too long (>8) or untestable
- P0 contains filler/stop-words
- No phrases, but meaning clearly depends on a phrase
- P1 is bloated (>12) and not prioritized
- No clarity targets defined

Fix route:
- apply PB-02 to refine and re-rank.

### FAIL
FAIL if any of these holds:
- P0 missing entirely
- MUST_HEAR targets absent (no P0/P1/P2 block)
- Hook section cannot be identified (G1 should have caught; treat as FAIL/STOP)
FAIL implies:
- NOT READY; stop progression to G3 until fixed.

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:
- MUST_HEAR_WORDS:
  - P0:
  - P1:
  - P2:
- MUST_HEAR_PHRASES:
  - P0:
  - P1:
- CLARITY_TARGETS (PASS):
  - Target A:
  - Target B (optional):
- NOTES:
  - why items are in P0 (short)

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If REWORK or FAIL:
- Apply: PB-02 MUST-HEAR WORDS PRIORITY
- Rerun: G2 then proceed to G3 only after PASS

No other vocal-direction playbook should proceed without G2 PASS.

---

## 5) COMMON FAIL MODES
- P0 list is a paragraph (untestable)
- P0 filled with “и/но/это/я” style fillers
- no phrase promotion; meaning is in phrase, but only words listed
- no clarity targets; “make clear” only
- targets exist but don’t align to chorus/hook section

---

## 6) OUTPUT FORMAT (MANDATORY)
G2_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - MUST_HEAR_WORDS(P0/P1/P2):
  - MUST_HEAR_PHRASES(P0/P1):
  - CLARITY_TARGETS:
  - NOTES:
- NEXT_STEP:
  - if PASS: "Proceed to G3 INTELLIGIBILITY PASS"
  - if REWORK/FAIL: "Apply PB-02 and rerun G2"

--- END.
