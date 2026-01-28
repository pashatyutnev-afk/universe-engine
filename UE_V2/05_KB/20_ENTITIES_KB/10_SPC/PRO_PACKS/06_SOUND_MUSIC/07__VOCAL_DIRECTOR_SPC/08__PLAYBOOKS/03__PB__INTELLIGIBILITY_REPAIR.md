# SPC PRO PACK — PLAYBOOK (PB-03) — ATTACK_CLARITY_PATCH (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/03__PB-03__ATTACK_CLARITY_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-03
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB03.ATTACK_CLARITY_PATCH.001
OWNER: SYSTEM
ROLE: One-axis repair procedure for intelligibility failures driven by swallowed consonant attacks or delivery masking on P0 targets. Produces/repairs ATTACK_PROTECTION_NOTES (target→<=3 directives→pass_test) and ensures hard fail framing exists. Rerun G3.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-03 ATTACK_CLARITY_PATCH for VOCAL_DIRECTOR."
- REASON: "Most clarity failures are attack-level and should be fixed by performer directives, not by rewriting or mixing."
- IMPACT: "Higher P0 recognition and fewer regressions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB03.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A1 (Attack/clarity micro-directives)

Fixes:
- consonant loss / swallow on P0 (T1)
- delivery masking on P0 attacks (T5 default path)
- missing or weak ATTACK_PROTECTION_NOTES
- missing pass_test for targets

Does NOT fix:
- targets definition (G2)
- breath/density (G6)
- stacking masking (G7)
- profile contradictions (G4)
- arc (G5)
- take pack (G8)
- scope cleanup (G9)

---

## 1) INPUTS REQUIRED
Must have:
- MUST_HEAR_WORDS.P0
Optional (recommended):
- MUST_HEAR_PHRASES.P0
- INTELLIGIBILITY_GATES_CHECKLIST / HARD_FAIL_TRIGGERS (from T04)
- notes about which words fail (if observed)

Tools used:
- T05 CONSONANT_ATTACK_PROTECTOR
- T04 INTELLIGIBILITY_CHECKLIST_BUILDER (only if checklist/hard fails missing)

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- ATTACK_PROTECTION_NOTES
Optionally add if missing:
- INTELLIGIBILITY_GATES_CHECKLIST
- HARD_FAIL_TRIGGERS

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in PB-03:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES
- VOCAL_STYLE_PROFILE / FORBIDDEN_STYLES
- BREATH_POLICY / DENSITY_SCAN
- STACKING_* blocks
- PERFORMANCE_ARC_MAP / CONTRAST_LEVERS
- TAKE_* / SESSION_INTENT
- SCOPE_AUDIT

---

## 4) PROCEDURE (STEPS)
Step 1 — Ensure intelligibility framing exists
- If INTELLIGIBILITY_GATES_CHECKLIST or HARD_FAIL_TRIGGERS missing:
  - run T04 to create them
- Do not change existing targets; only create missing QA scaffolding

Step 2 — Generate/repair ATTACK_PROTECTION_NOTES (T05)
For each P0 target:
- write 1..3 directives (hard max 3)
- add pass_test:
  - “On first listen, '<target>' is recognized in the hook.”
Optional:
- add do_not_do (1 line) if a common failure is known

Step 3 — Keep directives minimal
- remove any directive that is:
  - mixing advice
  - lyric edit
  - redundant

Step 4 — Apply patch
- Replace only allowed blocks

---

## 5) RERUN GATES
Required rerun:
- G3

Verification:
- If any other axis was touched (should not happen), revert; one-axis rule.

---

## 6) HARD STOPS
Stop if:
- P0 is missing (route to PB-02 first)
- scope violation appears (route to PB-08)
- breath split is the actual root cause (route to PB-04)

---

## 7) SUCCESS CRITERIA
PB-03 is successful when:
- every P0 target has:
  - <=3 directives
  - a pass_test
- hard fails HF-1/HF-3 are addressable via directives
- no forbidden content present

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-03
- AXIS: A1 (Attacks/Clarity)
- TOOLS: T05 (+ T04 if missing)
- RERUN: G3

--- END.
