# SPC PRO PACK — GATE (G5) — ARC / CONTRAST (<=3 LEVERS) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/05__GATE__ARC_CONTRAST.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001
OWNER: SYSTEM
ROLE: Gate G5 verifies performance arc and contrast: hook must have lift/release role, contrast levers must be 1–3, and QC checks must confirm lift without harming intelligibility. Prevents flat hooks and lever overload.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G5 ARC/CONTRAST for VOCAL_DIRECTOR."
- REASON: "Without explicit arc/levers, verse and chorus collapse into the same performance and hook impact becomes accidental."
- IMPACT: "Consistent lift with minimal performer overload."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G5.001

---

## 0) PURPOSE
Ensure a minimal, coherent arc exists:
- hook = lift/release
- levers <=3
- intelligibility preserved

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G5 requires:
- PERFORMANCE_ARC_MAP
- CONTRAST_LEVERS
- QC_ARC_CHECKS

Origin tool:
- T08 ARC_LEVER_SELECTOR

Playbook:
- PB-05 ARC / CONTRAST FIX

---

## 2) THRESHOLDS (STRICT)
### PERFORMANCE_ARC_MAP
- must include at least Verse + Chorus(HOOK)
- hook labeled as lift/release (not flat)
- optional bridge/reset and final chorus high lift

### CONTRAST_LEVERS
- lever_count: 1..3 (hard maximum = 3)
- lever settings must be explicit (not “more emotion”)
- levers should not require masking P0

### QC_ARC_CHECKS
Must include:
- chorus_lift_present: YES (for PASS)
- lever_count_ok (<=3): YES (for PASS)
- intelligibility_preserved: YES (for PASS)
- bridge_contrast_present: YES/NO or N/A

---

## 3) PASS / REWORK / FAIL
### PASS if ALL are true:
- arc map exists and hook is lift/release
- lever_count 1..3
- QC checks present and all PASS-critical flags are YES:
  - chorus_lift_present YES
  - lever_count_ok YES
  - intelligibility_preserved YES

### REWORK if:
- arc map exists but:
  - lever_count >3 OR
  - lever definitions vague OR
  - lift exists but QC incomplete
- intelligibility_preserved uncertain (needs safer lever choice)

### FAIL if ANY is true:
- arc map missing entirely
- levers missing entirely
- arc explicitly forbids lift (flat by design)
- lever_count_ok is NO and cannot be pruned with given data
- intelligibility_preserved is NO due to lever choice and cannot be corrected within <=3 levers

Stop rule:
- If FAIL → do not proceed to G6 until repaired.

---

## 4) OUTPUT (G5 VERDICT BLOCK)
G5_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G6 BREATH/SINGABILITY"
  - if REWORK: "Prune/rebuild levers via T08; rerun G5"
  - if FAIL: "Apply PB-05; rerun G5 (then verify G3)"

---

## 5) FIX ROUTE
Tool:
- T08 ARC_LEVER_SELECTOR

Playbook:
- PB-05 ARC / CONTRAST FIX (A2)

Verification:
- If intensity lever materially changes chorus delivery, verify G3 (intelligibility preserved).

---

## 6) ANTI-SCOPE VIOLATIONS
Forbidden:
- mix/master chain advice
- lyric rewrite
Allowed:
- performance-level arc design
- lever settings in human-executable terms

---

## 7) TRACE
TRACE:
- GATE: G5
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001
- TOOL: T08
- PLAYBOOK: PB-05

--- END.
