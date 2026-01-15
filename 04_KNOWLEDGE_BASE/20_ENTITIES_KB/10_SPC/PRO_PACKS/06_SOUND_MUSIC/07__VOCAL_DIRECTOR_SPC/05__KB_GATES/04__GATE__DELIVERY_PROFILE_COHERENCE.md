# SPC PRO PACK — GATE (G4) — DELIVERY PROFILE COHERENCE (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/04__GATE__DELIVERY_PROFILE_COHERENCE.md

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
ROLE: Gate G4 validates that the VOCAL_STYLE_PROFILE (delivery profile) is coherent, non-contradictory, executable, and stable across sections. Prevents “genre-soup inside voice” and performer-unexecutable direction.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G4: Delivery Profile Coherence for VOCAL_DIRECTOR Pro Pack."
- REASON: "Contradictory delivery directives cause drift across takes; coherence is required for repeatability."
- IMPACT: "Stable vocal character and cleaner comping; fewer unusable takes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.DELIVERY.001

---

## 0) PURPOSE
This gate answers:
- Is the vocal delivery profile coherent and executable?

It validates the existence and quality of:
- VOCAL_STYLE_PROFILE (principles)
- FORBIDDEN_STYLES list
- section modulation notes (if any)

---

## 1) REQUIRED INPUTS
Prerequisites:
- G1 PASS (inputs exist)

Inputs to validate:
- VOCAL_STYLE_PROFILE:
  - delivery_principles
  - forbidden_styles
  - (optional) section intensity map

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if ALL are true:
- VOCAL_STYLE_PROFILE exists
- delivery_principles are stated as principles (not vague vibes)
- no direct contradictions exist
  - example contradiction: “clean pristine” AND “lo-fi broken distortion” as simultaneous requirements
- forbidden_styles are present (at least 2–5) and prevent drift
- profile is performer-executable:
  - ≤ ~6 core principles (compact)
  - avoids long inventories of micro-instructions

### REWORK
REWORK if:
- profile exists but is too large (inventory-like) and not executable
- contradictions are likely (conflicting principles) but can be fixed by pruning
- forbidden_styles missing or too weak
Fix route:
- PB-01 (rebuild/prune delivery profile)
- or PB-08 axis A4 (delivery profile) minimal patch

### FAIL
FAIL if:
- profile missing entirely
- profile is vibe-only (“sing better”, “cool voice”) with no actionable principles
- profile introduces out-of-scope prescriptions (mix/master chains)
- profile requires changing lyrics meaning to work (ownership violation)
FAIL implies:
- NOT READY; rebuild baseline direction pack (PB-01) before proceeding.

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:
- VOCAL_STYLE_PROFILE:
  - delivery_principles:
  - forbidden_styles:
  - section_intensity_map (optional):
- COHERENCE_CHECK:
  - contradictions_found: YES/NO
  - executability_ok: YES/NO
  - notes:

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If REWORK:
- apply PB-01 profile pruning
OR
- apply PB-08 (AXIS=A4) minimal patch

If FAIL:
- rebuild baseline via PB-01, then rerun G4.

Proceed to G5 only after PASS.

---

## 5) COMMON FAIL MODES
- Too many principles; performer overload.
- Contradictory tone/delivery requirements.
- Missing forbidden styles; drift between takes.
- “Fix by mixing” advice embedded (out of scope).
- Profile changes across sections without an arc plan (arc should be in G5).

---

## 6) OUTPUT FORMAT (MANDATORY)
G4_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - VOCAL_STYLE_PROFILE:
  - COHERENCE_CHECK:
- NEXT_STEP:
  - if PASS: "Proceed to G5 ARC / CONTRAST"
  - if REWORK/FAIL: "Apply PB-01 or PB-08(A4) and rerun G4"

--- END.
