# SPC PRO PACK — GATE (G3) — INTELLIGIBILITY (P0-FIRST) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/03__GATE__INTELLIGIBILITY.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
OWNER: SYSTEM
ROLE: Gate G3 verifies intelligibility: P0 targets must be understood on first listen in the hook, and the pack must contain explicit checklist criteria, hard-fail triggers, and repair routing. This gate protects downstream arc/breath/stacking decisions from masking errors.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G3 INTELLIGIBILITY (P0-first) for VOCAL_DIRECTOR."
- REASON: "Without testable intelligibility criteria, outputs drift and hook recognition collapses."
- IMPACT: "Standardizes clarity QA and deterministic repairs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G3.001

---

## 0) PURPOSE
Ensure intelligibility is testable and protected:
- P0 is the primary pass criterion.
- Hard fails stop progression.

PASS of G3 is recommended before proceeding to G4..G8.

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G3 requires:
- INTELLIGIBILITY_GATES_CHECKLIST
- HARD_FAIL_TRIGGERS
- (recommended) ATTACK_PROTECTION_NOTES
Optional:
- MASKING_RISKS
- REPAIR_ROUTE (may be provided by T15)

Origin tools:
- T04 INTELLIGIBILITY_CHECKLIST_BUILDER
- T05 CONSONANT_ATTACK_PROTECTOR
- T15 REPAIR_ROUTER (optional)

---

## 2) CHECKLIST (MANDATORY A..E)
INTELLIGIBILITY_GATES_CHECKLIST must include:
- Gate A: P0 first listen (YES/NO)
- Gate B: P1 second listen (YES/NO or N/A)
- Gate C: no breath split inside P0 (YES/NO)
- Gate D: consonant attacks protected (YES/NO)
- Gate E: hook clarity >= verse (YES/NO or N/A)

---

## 3) HARD FAIL TRIGGERS (MANDATORY)
HARD_FAIL_TRIGGERS must include:
- HF-1: any P0 item not understood on first listen in hook
- HF-2: breath split inside any P0 phrase
- HF-3: consonant attacks on P0 swallowed/masked

Optional:
- HF-4: hook clarity drops vs verse baseline
- HF-5: stacking reduces P0 clarity

Hard fail rule:
- If any HF is true → STATUS cannot be PASS.

---

## 4) PASS / REWORK / FAIL
### PASS if ALL are true:
- checklist A..E present
- hard fail triggers present
- Gate A (P0 first listen) is enforced as primary target
- no hard fail is triggered (HF-1/2/3 not true)

### REWORK if:
- artifacts exist but incomplete:
  - missing 1+ checklist items
  - hard fail list incomplete
  - attack protection notes missing for some P0 targets
(Repairable without new inputs.)

### FAIL if ANY is true:
- checklist missing entirely
- P0 first listen is not treated as a hard requirement
- hard fail triggers are missing
- a hard fail is observed in test (HF-1 or HF-2 or HF-3)

Stop rule:
- If FAIL → do not proceed to G4..G8 until repaired.

---

## 5) OUTPUT (G3 VERDICT BLOCK)
G3_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G4 DELIVERY COHERENCE"
  - if REWORK: "Complete checklist/attack notes via T04/T05; rerun G3"
  - if FAIL: "Classify type (T1..T7) and apply PB; rerun G3 (and related gate if needed)"

---

## 6) FIX ROUTE (DETERMINISTIC)
Default tools:
- T04 + T05

If root cause is:
- T1 consonant loss / T5 delivery masking → PB-03 (A1), rerun G3
- T2 breath split / T4 density trap → PB-04 (A3), rerun G6 → then G3
- T6 stacking masking → PB-07 (A5), rerun G7 → then G3
- T7 arrangement seat conflict → escalate via T14, then rerun G3 after owner response
- T3 targets wrong → PB-02, rerun G2 → then G3

Routing tool:
- T15 REPAIR_ROUTER

---

## 7) ANTI-SCOPE VIOLATIONS
Forbidden fixes at G3:
- lyric rewrites
- mix/master chain prescriptions

Allowed:
- performance directives (attack/breath/stacking placement)
- escalation notes (principles only)

---

## 8) TRACE
TRACE:
- GATE: G3
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
- TOOLS: T04, T05 (optional T15)
- PLAYBOOKS: PB-03/PB-04/PB-07/PB-02
- ESCALATION: T14 (for T7)

--- END.
