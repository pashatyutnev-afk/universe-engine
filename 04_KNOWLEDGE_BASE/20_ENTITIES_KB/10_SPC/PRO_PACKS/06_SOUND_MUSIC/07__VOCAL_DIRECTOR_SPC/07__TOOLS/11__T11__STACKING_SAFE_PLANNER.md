# SPC PRO PACK — TOOL (T11) — STACKING_SAFE_PLANNER (YES/NO + PROTECTION) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/11__T11__STACKING_SAFE_PLANNER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T11
TOOL_NAME: STACKING_SAFE_PLANNER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T11.STACKING_SAFE_PLANNER.001
OWNER: SYSTEM
ROLE: Produces a clarity-safe stacking plan: explicit stacking decision (YES/NO). If YES, outputs minimal-first stacking map, explicit protected zones for P0, and QC rules with fail triggers preventing intelligibility loss. No mixing chain advice.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T11 STACKING_SAFE_PLANNER for VOCAL_DIRECTOR."
- REASON: "Uncontrolled layering is a top cause of P0 masking."
- IMPACT: "Safe lift without sacrificing must-hear clarity."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T11.001

---

## 0) PURPOSE
Generate stacking decision and (if used) stacking safety artifacts:
- STACKING_DECISION / N_A_DECISION
- STACKING_MAP_BY_SECTION (if YES)
- PROTECTED_ZONES (if YES)
- QC_RULES (if YES)

Supports Gate:
- G7 STACKING SAFE
Verification:
- Re-check G3 after stacking changes

---

## 1) INPUTS (REQUIRED)
- MUST_HEAR_WORDS.P0 (required for protected zones)
Optional:
- MUST_HEAR_PHRASES.P0
- section structure labels (Verse/Chorus/Bridge)
- arc notes (if chorus lift requires layering)

Rules:
- If P0 missing → STOP (cannot define protected zones).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T11 MUST output:

### STACKING_DECISION (or N_A_DECISION)
STACKING_DECISION:
- stacking_used: YES/NO
- why:
  - 1)

If NO, note alternative:
N_A_DECISION:
- stacking_used: NO
- why:
- alternative_lift_lever:

If YES, must also output:

### STACKING_MAP_BY_SECTION
- Verse:
- Chorus:
- Bridge (optional):
- Final Chorus (optional):

### PROTECTED_ZONES
- P0 phrases:
  - "<phrase>" (if available)
- avoid stacking over consonant attacks on:
  - <comma P0 list>

### QC_RULES
- QC-S1:
- QC-S2:
- QC-S3:
- FAIL_TRIGGERS:
  - 1)
  - 2)

---

## 3) THRESHOLDS (STRICT)
- stacking_used must be explicit YES/NO
If YES:
- minimal-first rule must be enforced:
  - layers only where needed (tails, specific words), not full-line by default
- protected zones must include:
  - P0 attacks list (mandatory)
  - P0 phrases list (if phrases exist)
- QC rules must include fail triggers tied to P0 clarity

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Decide stacking_used (YES/NO)
Default:
- If no need for extra lift → NO
- If arc requires lift and single lead cannot deliver desired size without masking → YES (minimal-first)
(Decision is explicit; no implicit stacking.)

Step 2 — If stacking_used=NO
- Output N_A_DECISION with:
  - why
  - alternative_lift_lever (e.g., intensity lever or articulation lever)

Step 3 — If stacking_used=YES
- Build STACKING_MAP_BY_SECTION with minimal-first placements:
  - Verse: usually none or very light
  - Chorus: minimal doubles on tails (not on P0 attacks)
- Build PROTECTED_ZONES:
  - list P0 phrases (copy-exact) if available
  - list P0 words for “avoid stacking on attacks”
- Build QC_RULES:
  - QC-S1: P0 first listen remains YES
  - QC-S2: if clarity drops → remove/move layers
  - QC-S3: no character switching between layers
  - FAIL_TRIGGERS must explicitly mention:
    - P0 becomes less clear
    - consonant attacks smear

Step 4 — Output stable blocks

---

## 5) STOP / GAP CONDITIONS
Stop and request missing inputs if:
- P0 list missing
- stacking decision cannot be made because hook/arc intent is unknown (ask which tier: MIN/STD/FULL and whether layering is desired)

---

## 6) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- mixing/master chain advice (“EQ the doubles” etc.)
- inventing P0 items
- “stack everywhere” plans

Allowed:
- performer placement constraints (where layers should/should not happen)

---

## 7) TRACE
TRACE:
- TOOL: T11
- OUTPUTS: STACKING_DECISION/N_A_DECISION (+ map/protection/QC if YES)
- SUPPORTS_GATE: G7
- VERIFY: G3 after stacking

--- END.
