# SPC PRO PACK — PLAYBOOK (PB-07) — STACKING_SAFE_PATCH (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/07__PB-07__STACKING_SAFE_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-07
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB07.STACKING_SAFE_PATCH.001
OWNER: SYSTEM
ROLE: One-axis repair procedure for stacking safety: explicit stacking decision and, if used, a minimal-first stacking map, protected zones for P0, and QC rules with fail triggers. Uses T11. Rerun G7 then verify G3.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-07 STACKING_SAFE_PATCH for VOCAL_DIRECTOR."
- REASON: "Layering often masks must-hear words; safety requires deterministic protected zones and QC."
- IMPACT: "Bigger hooks without losing P0 intelligibility."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB07.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A5 (Stacking safety)

Fixes:
- missing stacking decision (YES/NO)
- missing protected zones and QC rules
- stacking masking P0 attacks (T6)
- over-broad stacking map (full-line layers)

Does NOT fix:
- targets, profile, arc, breath/density, take pack, scope

---

## 1) INPUTS REQUIRED
Must have:
- MUST_HEAR_WORDS.P0
Optional:
- MUST_HEAR_PHRASES.P0
- section structure labels
- arc notes (if chorus lift needs layering)

Tools used:
- T11 STACKING_SAFE_PLANNER

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- STACKING_DECISION or N_A_DECISION
- STACKING_MAP_BY_SECTION (if stacking_used=YES)
- PROTECTED_ZONES (if stacking_used=YES)
- QC_RULES (if stacking_used=YES)

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in PB-07:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES
- INTELLIGIBILITY checklist/hard fails
- ATTACK_PROTECTION_NOTES
- VOCAL_STYLE_PROFILE / FORBIDDEN_STYLES
- BREATH_POLICY / DENSITY_SCAN
- PERFORMANCE_ARC_MAP / CONTRAST_LEVERS
- TAKE_* / SESSION_INTENT
- SCOPE_AUDIT

---

## 4) PROCEDURE (STEPS)
Step 1 — Decide stacking usage explicitly (T11)
- stacking_used must be YES or NO

Step 2 — If stacking_used=NO
- Output N_A_DECISION with:
  - why
  - alternative_lift_lever

Step 3 — If stacking_used=YES
- Build minimal-first stacking map:
  - avoid full-line doubling
  - prefer tails / specific moments
- Define protected zones:
  - P0 phrases list (if available)
  - “avoid stacking over consonant attacks” on P0 words
- Define QC rules and fail triggers:
  - if P0 becomes less clear → remove/move layers
  - no character switching between layers

Step 4 — Apply patch
- Replace only allowed blocks

---

## 5) RERUN GATES
Required rerun:
- G7
Then verify:
- G3 (stacking changes can affect P0 clarity)

---

## 6) HARD STOPS
Stop if:
- P0 missing (route to PB-02 first)
- breath split is the actual root cause (route to PB-04)
- scope violation appears (route to PB-08)

---

## 7) SUCCESS CRITERIA
PB-07 is successful when:
- stacking decision explicit
- if YES: protected zones exist and QC fail triggers exist
- G7 passes and G3 remains stable (verify)

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-07
- AXIS: A5 (Stacking)
- TOOLS: T11
- RERUN: G7 → (verify) G3

--- END.
