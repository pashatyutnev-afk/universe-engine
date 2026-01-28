# SPC PRO PACK — PLAYBOOK (PB-01) — PROFILE_COHERENCE_PATCH (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/01__PB-01__PROFILE_COHERENCE_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-01
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB01.PROFILE_COHERENCE_PATCH.001
OWNER: SYSTEM
ROLE: One-axis repair procedure for delivery profile coherence: prune to <=6 executable principles, define forbidden styles, remove contradictions. Uses T06/T07 artifacts. Rerun G4 (verify G3 if clarity may change).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-01 PROFILE_COHERENCE_PATCH for VOCAL_DIRECTOR."
- REASON: "Contradictory or bloated profiles cause drift and invalidate downstream gates."
- IMPACT: "Executable, stable vocal identity and fewer regressions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB01.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A4 (Profile coherence)

Fixes:
- contradictions between principles
- overload (>6 principles)
- vibe-only / non-actionable profile
- missing forbidden list

Does NOT fix:
- targets (G2)
- breath/density (G6)
- stacking (G7)
- arc (G5)
- take pack (G8)
- scope cleanup (G9)

---

## 1) INPUTS REQUIRED
Must have:
- VOCAL_STYLE_PROFILE (existing) OR user tags/notes sufficient to rebuild
Optional:
- FORBIDDEN_STYLES (existing)
- COHERENCE_CHECK / CONTRADICTIONS_LIST (from T07)
- MUST_HEAR_WORDS.P0 (for clarity-safe forbids)

Tools used:
- T06 DELIVERY_PROFILE_PRUNER
- T07 CONTRADICTION_DETECTOR

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- VOCAL_STYLE_PROFILE.delivery_principles (prune/normalize to 4..6)
- FORBIDDEN_STYLES (2..5)

You may add:
- COHERENCE_CHECK (if missing)

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in this playbook:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES
- BREATH_POLICY / DENSITY_SCAN
- STACKING_* blocks
- PERFORMANCE_ARC_MAP / CONTRAST_LEVERS
- TAKE_* / SESSION_INTENT blocks
- SCOPE_AUDIT (unless running PB-08)

---

## 4) PROCEDURE (STEPS)
Step 1 — Run contradiction detection (T07)
- Produce COHERENCE_CHECK (+ optional contradictions list)
- If contradictions_found=NO and executability_ok=YES and principles<=6:
  - STOP: PB-01 not needed

Step 2 — Rebuild/prune profile (T06)
- Create 4..6 actionable principles
- Remove duplicates and vibe-only
- Resolve conflicts by pruning, not by adding more constraints

Step 3 — Define forbidden styles (T06)
- Ensure at least:
  - no swallowed consonant attacks on P0
  - no character switching between takes
- Keep forbids 2..5

Step 4 — Re-run T07 on the new profile
- contradictions_found must become NO
- executability_ok must become YES

Step 5 — Record changes
- Only replace VOCAL_STYLE_PROFILE and FORBIDDEN_STYLES
- Keep other blocks untouched

---

## 5) RERUN GATES
Required rerun:
- G4

Verification rerun (recommended):
- G3 (if profile changes could affect clarity/attacks)

---

## 6) HARD STOPS
Stop and escalate (do not proceed) if:
- required inputs are missing and cannot be rebuilt (request user tags)
- any scope violation appears during editing (route to PB-08)

---

## 7) SUCCESS CRITERIA
PB-01 is successful when:
- principles count <=6
- COHERENCE_CHECK:
  - contradictions_found=NO
  - executability_ok=YES
- forbidden list exists and is short (2..5)

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-01
- AXIS: A4
- TOOLS: T06, T07
- RERUN: G4 (verify G3)

--- END.
