# SPC PRO PACK — GATE (G4) — DELIVERY COHERENCE (PROFILE) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/04__GATE__DELIVERY_COHERENCE.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001
OWNER: SYSTEM
ROLE: Gate G4 verifies that the vocal delivery profile is coherent and executable: minimal principles (<=6), clear forbidden styles (2–5), and no contradictions. Prevents take drift and protects intelligibility.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G4 DELIVERY COHERENCE for VOCAL_DIRECTOR."
- REASON: "Contradictory or bloated profiles cause drift and invalidate downstream gates."
- IMPACT: "Stable vocal identity and faster sessions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G4.001

---

## 0) PURPOSE
Ensure a minimal, coherent vocal identity profile exists before arc/contrast decisions.

PASS of G4 is recommended before G5.

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G4 requires:
- VOCAL_STYLE_PROFILE
- FORBIDDEN_STYLES
- COHERENCE_CHECK

Origin tools:
- T06 DELIVERY_PROFILE_PRUNER
- T07 CONTRADICTION_DETECTOR (as needed)

Playbook:
- PB-01 PROFILE REBUILD / PRUNE

---

## 2) THRESHOLDS (STRICT)
### VOCAL_STYLE_PROFILE
- delivery_principles count: 4..6 (<=6 hard max)
- each principle must be actionable (not vibe-only)

### FORBIDDEN_STYLES
- count: 2..5
- must include at least:
  - one intelligibility protection (no masking on P0 attacks)
  - one drift protection (no character switching)

### COHERENCE_CHECK
- contradictions_found: NO (for PASS)
- executability_ok: YES (for PASS)
- reasons: 1–3 bullets

---

## 3) PASS / REWORK / FAIL
### PASS if ALL are true:
- principles <=6 AND actionable
- forbidden styles 2..5 present
- COHERENCE_CHECK: contradictions_found=NO, executability_ok=YES
- no forbidden scope content embedded (mix chains)

### REWORK if:
- profile exists but needs pruning:
  - principles >6
  - forbidden list missing 1–2 items
  - minor contradictions that can be resolved by pruning/section split
- COHERENCE_CHECK indicates issues but fixable

### FAIL if ANY is true:
- profile missing entirely
- contradictions remain (clean vs lo-fi, soft vs scream) without explicit section split plan
- vibe-only profile (non-actionable)
- forbidden list missing entirely
- mix/master chain prescriptions included (scope violation)

Stop rule:
- If FAIL → do not proceed to G5 until repaired.

---

## 4) OUTPUT (G4 VERDICT BLOCK)
G4_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G5 ARC/CONTRAST"
  - if REWORK: "Prune/rebuild profile via T06 (and T07 if needed); rerun G4"
  - if FAIL: "Apply PB-01; rerun G4"

---

## 5) FIX ROUTE
Tools:
- T06 DELIVERY_PROFILE_PRUNER
- T07 CONTRADICTION_DETECTOR (if contradictions present)

Playbook:
- PB-01 PROFILE REBUILD / PRUNE (A4)

After fix:
- rerun G4
- optionally verify G3 if articulation constraints changed significantly

---

## 6) ANTI-SCOPE VIOLATIONS
Forbidden:
- plugin chains/DAW recipes inside profile
- lyric rewrites
Allowed:
- performer-actionable constraints
- forbidden styles list

---

## 7) TRACE
TRACE:
- GATE: G4
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001
- TOOLS: T06/T07
- PLAYBOOK: PB-01

--- END.
