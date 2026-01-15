# SPC PRO PACK — GATE (G7) — STACKING CLARITY-SAFE (PROTECT P0) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/07__GATE__STACKING_CLARITY_SAFE.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001
OWNER: SYSTEM
ROLE: Gate G7 validates that any stacking/harmony plan is clarity-safe: protected zones exist for P0 must-hear targets, stacking is minimal-first, QC rules are declared, and stacking never reduces intelligibility. Allows explicit N/A when stacking is avoided for clarity.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G7: Stacking clarity-safe (protect P0) for VOCAL_DIRECTOR Pro Pack."
- REASON: "Layering commonly masks consonants; gate enforces protected zones and minimalism."
- IMPACT: "Hook lift can be added without destroying intelligibility."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.STACK.001

---

## 0) PURPOSE
This gate answers:
- Is stacking/harmony used in a way that preserves P0 intelligibility?

Validates:
- STACKING_MAP (or explicit N/A decision)
- PROTECTED_ZONES for P0
- QC rules for stacking impact

---

## 1) REQUIRED INPUTS
Prerequisites:
- G1 PASS (inputs exist)
- G2 PASS (must-hear targets exist)

Inputs to validate:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES (P0)
- STACKING_MAP_BY_SECTION OR N_A_DECISION
- PROTECTED_ZONES (if stacking used)
- QC_RULES (if stacking used)

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if one of the following is true:

A) STACKING USED (clarity-safe):
- STACKING_MAP exists (by section) AND
- PROTECTED_ZONES exist and explicitly cover P0 phrases AND
- QC_RULES exist with at least:
  - P0 understood on first listen (YES/NO)
  - stacking increases lift without masking (YES/NO)
- minimal-first constraint is followed:
  - no “stack everywhere” across whole chorus by default

OR

B) STACKING NOT USED (explicit N/A):
- N_A_DECISION exists:
  - stacking_used: NO
  - why (clarity fragile / density high / identity reasons)
  - alternative lift lever (arc/delivery)
In N/A case, PROTECTED_ZONES and QC_RULES are optional.

### REWORK
REWORK if:
- stacking map exists but protected zones missing
- stacking exists but QC rules missing
- stacking is too broad and likely masks P0 but can be reduced
Fix route:
- PB-07 to rebuild minimal stacking + protected zones + QC

### FAIL
FAIL if:
- stacking is applied over P0 targets without protection
- stacking reduces intelligibility by design (“make it thick even if words blur”)
- stacking plan is absent but stacking is demanded (inconsistent)
- stacking is used as a “mix fix” (scope violation) or requires processing recipes
FAIL implies:
- NOT READY; rebuild stacking layer with PB-07 or set explicit N/A.

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:

If stacking_used = YES:
- STACKING_MAP_BY_SECTION:
- PROTECTED_ZONES:
- QC_RULES:
- MINIMALISM_NOTE:
  - “limited interventions” confirmation

If stacking_used = NO:
- N_A_DECISION:
  - stacking_used:
  - why:
  - alternative_lift_lever:

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If REWORK/FAIL:
- Apply PB-07 STACKING/HARMONY MINIMAL PLAN
- Rerun G7, then proceed to G8 only if PASS.

---

## 5) COMMON FAIL MODES
- Doubles/backs everywhere in chorus → consonants vanish.
- Harmonies placed on consonant-heavy P0 phrases.
- No protected zones; no QC checks.
- Attempt to solve performance issues by mix chain advice.

---

## 6) OUTPUT FORMAT (MANDATORY)
G7_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - stacking_used:
  - if YES: STACKING_MAP / PROTECTED_ZONES / QC_RULES
  - if NO: N_A_DECISION
- NEXT_STEP:
  - if PASS: "Proceed to G8 TAKE PACK REPEATABILITY"
  - if REWORK/FAIL: "Apply PB-07 and rerun G7"

--- END.
