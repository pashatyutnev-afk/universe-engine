# SPC PRO PACK — PLAYBOOK (PB-04) — BREATH_DENSITY_PATCH (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/04__PB-04__BREATH_DENSITY_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-04
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB04.BREATH_DENSITY_PATCH.001
OWNER: SYSTEM
ROLE: One-axis repair procedure for breath-safety and density risks: define never-split phrase protection, explicit breath policy, and density scan (R0/R1/R2). If R2 indicates no safe breath point, produce escalation note (T14) instead of lyric rewrites. Rerun G6 then verify G3.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-04 BREATH_DENSITY_PATCH for VOCAL_DIRECTOR."
- REASON: "Breath splits and density traps are major intelligibility killers and require deterministic handling."
- IMPACT: "Cleaner hook phrasing and correct escalation when unsingable."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB04.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A3 (Breath/Density safety)

Fixes:
- breath split inside P0 phrase (T2)
- density risk / unsingable risk (T4)
- missing breath policy or phrase protection
- missing density scan

Does NOT fix:
- targets (G2)
- profile (G4)
- arc (G5)
- stacking (G7)
- take pack (G8)
- compliance cleanup (G9)

---

## 1) INPUTS REQUIRED
Must have:
- hook/chorus text (lines)
- MUST_HEAR_PHRASES.P0 (copy-exact) OR explicit signature phrases provided by user
- language label
Optional:
- MUST_HEAR_WORDS.P0 (for contains_P0 marking)
- HOOK_SECTION_LABEL

Tools used:
- T09 BREATH_MAP_BUILDER
- T10 DENSITY_RISK_SCAN
- T14 ESCALATION_NOTE_FORMATTER (only if R2 persists)

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- MUST_HEAR_PROTECTION_RULES
- BREATH_POLICY
- DENSITY_SCAN
Optionally add (only if needed for R2 escalation):
- ESCALATION_TRIGGER
- ESCALATION_NOTES

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in PB-04:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES (do not rewrite; only use copy-exact)
- INTELLIGIBILITY checklist/hard fails
- ATTACK_PROTECTION_NOTES
- VOCAL_STYLE_PROFILE / FORBIDDEN_STYLES
- STACKING_* blocks
- PERFORMANCE_ARC_MAP / CONTRAST_LEVERS
- TAKE_* / SESSION_INTENT
- SCOPE_AUDIT (unless PB-08)

---

## 4) PROCEDURE (STEPS)
Step 1 — Build phrase protection + breath policy (T09)
- Set NEVER_SPLIT_PHRASES from copy-exact P0 phrases
- Define allowed breath points (1–3)
- Define forbidden splits explicitly (1–3), at minimum:
  - no split inside any NEVER_SPLIT_PHRASES item

Step 2 — Run density scan (T10)
- Assign line_ids
- Mark risk_level R0/R1/R2
- Add evidence snippets and fix_hints (scope-safe)

Step 3 — Handle R2 deterministically
If any line is R2:
- Do NOT rewrite lyrics
- Create escalation trigger (inside output pack FULL optional block) and format ESCALATION_NOTES via T14:
  - owner: Lyricist/Songwriter
  - must_keep: P0 words/phrases
  - request: principles only (“create safe breath point without breaking meaning”)
  - next_check: rerun G6 → G3 after owner response

Step 4 — Apply patch
- Replace only allowed blocks

---

## 5) RERUN GATES
Required rerun:
- G6
Then verify:
- G3 (breath changes can impact intelligibility)

---

## 6) HARD STOPS
Stop if:
- phrases required but not provided copy-exact (request exact line)
- language missing (do not infer)
- any lyric rewrite attempt appears (route PB-08)

---

## 7) SUCCESS CRITERIA
PB-04 is successful when:
- explicit forbidden splits exist (no split inside P0 phrases)
- density scan exists with line_ids and risk levels
- if R2 exists, escalation note exists (and pack is not declared READY until owner response)
- G6 passes (or correctly escalates R2)

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-04
- AXIS: A3 (Breath/Density)
- TOOLS: T09, T10 (+ T14 if R2)
- RERUN: G6 → (verify) G3

--- END.
