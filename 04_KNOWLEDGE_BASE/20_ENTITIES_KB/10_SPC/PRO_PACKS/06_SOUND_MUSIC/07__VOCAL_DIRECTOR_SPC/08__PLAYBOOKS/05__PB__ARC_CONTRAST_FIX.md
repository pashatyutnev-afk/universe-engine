# SPC PRO PACK — PLAYBOOK (PB-05) — ARC_LEVER_PATCH (<=3 LEVERS) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/05__PB-05__ARC_LEVER_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-05
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB05.ARC_LEVER_PATCH.001
OWNER: SYSTEM
ROLE: One-axis repair procedure for performance arc and contrast: create/repair arc map and prune contrast levers to <=3 using T08. Ensures controlled hook lift without overload. Rerun G5 and verify G3 if intensity/texture changes impact clarity.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-05 ARC_LEVER_PATCH for VOCAL_DIRECTOR."
- REASON: "Flat arcs or lever overload cause weak hooks or chaotic delivery."
- IMPACT: "Controlled lift with minimal performer overload."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB05.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A2 (Arc/Contrast)

Fixes:
- flat arc (no hook lift)
- lever overload (>3)
- vague or contradictory lever settings
- missing QC_ARC_CHECKS

Does NOT fix:
- targets (G2)
- breath/density (G6)
- stacking (G7)
- profile coherence (G4) (unless done in separate iteration)
- take pack (G8)
- scope cleanup (G9)

---

## 1) INPUTS REQUIRED
Must have:
- section structure with hook/chorus label
Optional (recommended):
- VOCAL_STYLE_PROFILE
- MUST_HEAR_WORDS.P0 (for clarity-safe lever choice)
- any notes about desired lift

Tools used:
- T08 ARC_LEVER_SELECTOR

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- PERFORMANCE_ARC_MAP
- CONTRAST_LEVERS
- QC_ARC_CHECKS

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in PB-05:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES
- INTELLIGIBILITY checklist/hard fails
- ATTACK_PROTECTION_NOTES
- VOCAL_STYLE_PROFILE / FORBIDDEN_STYLES
- BREATH_POLICY / DENSITY_SCAN
- STACKING_* blocks
- TAKE_* / SESSION_INTENT
- SCOPE_AUDIT

---

## 4) PROCEDURE (STEPS)
Step 1 — Build/repair arc map (T08)
- Define Verse baseline and Chorus lift

Step 2 — Select/prune levers to <=3 (T08)
- Prefer clarity-safe levers:
  - intensity + articulation
- Avoid levers that likely mask P0 attacks unless required by genre and still testable

Step 3 — Define explicit verse→chorus settings
- Each lever must have a verse_setting and chorus_setting
- No vibe-only language without executable settings

Step 4 — Output QC_ARC_CHECKS
- chorus_lift_present must be YES
- lever_count_ok must be YES

Step 5 — Apply patch
- Replace only allowed blocks

---

## 5) RERUN GATES
Required rerun:
- G5

Verification rerun:
- G3 (if intensity/texture levers were materially changed)

---

## 6) HARD STOPS
Stop if:
- hook/chorus section cannot be identified (route to T01/G1)
- any lyric rewrite appears (route to PB-08)

---

## 7) SUCCESS CRITERIA
PB-05 is successful when:
- levers <=3
- chorus lift present
- QC_ARC_CHECKS exist and are consistent
- G5 passes (and G3 stays stable if verified)

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-05
- AXIS: A2 (Arc/Contrast)
- TOOLS: T08
- RERUN: G5 → (verify) G3

--- END.
