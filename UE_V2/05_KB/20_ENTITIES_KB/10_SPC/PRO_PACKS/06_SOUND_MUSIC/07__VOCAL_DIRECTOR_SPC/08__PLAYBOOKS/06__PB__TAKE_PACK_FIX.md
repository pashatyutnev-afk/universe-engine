# SPC PRO PACK — PLAYBOOK (PB-06) — TAKE_PACK_PATCH (REPEATABILITY) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/06__PB-06__TAKE_PACK_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-06
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB06.TAKE_PACK_PATCH.001
OWNER: SYSTEM
ROLE: One-axis repair procedure for the take/recording plan: generates or repairs SESSION_INTENT, TAKE_GOALS_BY_SECTION, RISK_LINES, REPEATABILITY_RULES, QC_HARD_FAILS, and COMP_NOTES using T12. Rerun G8.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-06 TAKE_PACK_PATCH for VOCAL_DIRECTOR."
- REASON: "Without a repeatable take plan, sessions drift and comps become inconsistent."
- IMPACT: "Higher usable take rate and stable comps."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB06.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A6 (Take pack repeatability)

Fixes:
- missing or incomplete take pack
- goals per section not within 2..4
- repeatability rules <3
- QC hard fails missing HF-1..HF-3
- comp notes missing critical constraints

Does NOT fix:
- targets, profile, arc, breath/density, stacking, scope

---

## 1) INPUTS REQUIRED
Must have:
- section structure (Verse/Chorus/Hook)
- MUST_HEAR_WORDS.P0 (for QC hard fails)
Optional:
- MUST_HEAR_PHRASES.P0
- breath/density notes (T09/T10)
- stacking decision (T11)
- arc/levers (T08)

Tools used:
- T12 TAKE_PACK_BUILDER

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- SESSION_INTENT
- TAKE_GOALS_BY_SECTION
- RISK_LINES
- REPEATABILITY_RULES
- QC_HARD_FAILS
- COMP_NOTES
Optional (if already used elsewhere and missing):
- QC_SOFT_FAILS

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in PB-06:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES
- INTELLIGIBILITY checklist/hard fails
- ATTACK_PROTECTION_NOTES
- VOCAL_STYLE_PROFILE / FORBIDDEN_STYLES
- BREATH_POLICY / DENSITY_SCAN
- STACKING_* blocks
- PERFORMANCE_ARC_MAP / CONTRAST_LEVERS
- SCOPE_AUDIT

---

## 4) PROCEDURE (STEPS)
Step 1 — Build/repair take pack (T12)
- Ensure:
  - goals per section = 2..4
  - repeatability rules >=3
  - QC hard fails include HF-1..HF-3
  - comp notes include “no comp across different P0 pronunciations”

Step 2 — Mark risk lines
- Use density scan and must-hear phrases if available
- Keep 1..6 risk lines

Step 3 — Apply patch
- Replace only allowed blocks

Step 4 — Sanity check thresholds
- If thresholds not met, re-run T12 with stricter constraints (still within PB-06)

---

## 5) RERUN GATES
Required rerun:
- G8

---

## 6) HARD STOPS
Stop if:
- P0 missing (route to PB-02 first)
- structure missing (route to T01/G1)
- scope violation appears (route to PB-08)

---

## 7) SUCCESS CRITERIA
PB-06 is successful when:
- TAKE_GOALS_BY_SECTION has 2..4 goals per section
- REPEATABILITY_RULES >=3
- QC_HARD_FAILS includes HF-1..HF-3
- COMP_NOTES includes comp safety constraints
- G8 passes

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-06
- AXIS: A6 (Take pack)
- TOOLS: T12
- RERUN: G8

--- END.
