# SPC PRO PACK — GATES (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/00__README__GATES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: README
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.GATES.README.DRAFT.001
OWNER: SYSTEM
ROLE: Map of gates (G1..G9) for VOCAL_DIRECTOR Pro Pack: what each gate verifies, required input artifacts, and standard fix routes (tools/playbooks). Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created VOCAL_DIRECTOR gates README: G1..G9 catalog + required artifacts + fix routing."
- REASON: "Need deterministic QA pipeline and a clear order of checks."
- IMPACT: "Consistent quality and faster triage."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.GATES.README.001

---

## 0) PURPOSE
Gates are the QA checkpoints for VOCAL_DIRECTOR outputs.
They:
- define what “PASS” means in testable terms
- define REWORK vs FAIL
- map failures to tools and playbooks

Order is fixed:
G1 → G2 → G3 → G4 → G5 → G6 → G7 → G8 → G9

---

## 1) REQUIRED ARTIFACT BLOCKS (GLOBAL)
Across the full pack, gates rely on stable artifact blocks:
- MIN_INPUTS_CHECK
- HOOK_SECTION_LABEL
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES / CLARITY_TARGETS
- INTELLIGIBILITY_GATES_CHECKLIST / HARD_FAIL_TRIGGERS
- VOCAL_STYLE_PROFILE / FORBIDDEN_STYLES / COHERENCE_CHECK
- PERFORMANCE_ARC_MAP / CONTRAST_LEVERS / QC_ARC_CHECKS
- MUST_HEAR_PROTECTION_RULES / BREATH_POLICY / DENSITY_SCAN
- STACKING_MAP_BY_SECTION / PROTECTED_ZONES / QC_RULES
- TAKE_GOALS_BY_SECTION / REPEATABILITY_RULES / QC_HARD_FAILS / COMP_NOTES
- SCOPE_AUDIT / ESCALATION_NOTES

---

## 2) GATE CATALOG (WHAT EACH GATE CHECKS)
### G1 — INPUT READINESS
Checks:
- minimum inputs exist and hook is identifiable
Artifacts:
- MIN_INPUTS_CHECK, HOOK_SECTION_LABEL
Fix:
- Tool T01

### G2 — MUST-HEAR TARGETS
Checks:
- P0/P1 thresholds + phrase promotion correctness
Artifacts:
- MUST_HEAR_WORDS, MUST_HEAR_PHRASES, CLARITY_TARGETS
Fix:
- Tools T02/T03; Playbook PB-02

### G3 — INTELLIGIBILITY
Checks:
- checklist A..E + hard fails + P0-first constraint
Artifacts:
- INTELLIGIBILITY_GATES_CHECKLIST, HARD_FAIL_TRIGGERS, ATTACK_PROTECTION_NOTES
Fix:
- Tools T04/T05; Playbook PB-03 (or PB-04 if breath)

### G4 — DELIVERY COHERENCE
Checks:
- coherent, executable delivery profile + forbidden styles
Artifacts:
- VOCAL_STYLE_PROFILE, FORBIDDEN_STYLES, COHERENCE_CHECK
Fix:
- Tools T06/T07; Playbook PB-01

### G5 — ARC / CONTRAST
Checks:
- hook lift exists; levers <=3; intelligibility preserved
Artifacts:
- PERFORMANCE_ARC_MAP, CONTRAST_LEVERS, QC_ARC_CHECKS
Fix:
- Tool T08; Playbook PB-05

### G6 — BREATH / SINGABILITY
Checks:
- P0 phrases protected; allowed/forbidden breath points; density scan
Artifacts:
- MUST_HEAR_PROTECTION_RULES, BREATH_POLICY, DENSITY_SCAN
Fix:
- Tools T09/T10; Playbook PB-04; Escalate via T14 if R2

### G7 — STACKING SAFE
Checks:
- explicit stacking decision; protected zones; QC fail triggers
Artifacts:
- STACKING_MAP_BY_SECTION, PROTECTED_ZONES, QC_RULES
Fix:
- Tool T11; Playbook PB-07

### G8 — TAKE PACK
Checks:
- goals 2–4/section; repeatability rules >=3; QC hard fails + comp notes
Artifacts:
- TAKE_GOALS_BY_SECTION, REPEATABILITY_RULES, QC_HARD_FAILS, COMP_NOTES
Fix:
- Tool T12; Playbook PB-06

### G9 — SCOPE COMPLIANCE
Checks:
- no lyric rewrite; no mix chain; no ownership overreach; no guessing
Artifacts:
- SCOPE_AUDIT (+ VIOLATIONS_FOUND if any)
Fix:
- Tool T13; Escalation T14; Playbook PB-08 (cleanup)

---

## 3) REWORK VS FAIL (SHORT)
REWORK:
- artifacts exist but thresholds incomplete/bloated; minimal patch possible

FAIL:
- required artifact missing OR hard fail trigger OR forbidden content present

Hard stops:
- G1 FAIL → stop (missing inputs)
- G9 FAIL → remove forbidden content before proceeding

---

## 4) NEXT FILES (ORDER)
Proceed in numeric order:
- 01__GATE__INPUT_READINESS.md
- 02__GATE__MUST_HEAR.md
- 03__GATE__INTELLIGIBILITY.md
- 04__GATE__DELIVERY_COHERENCE.md
- 05__GATE__ARC_CONTRAST.md
- 06__GATE__BREATH_SINGABILITY.md
- 07__GATE__STACKING_SAFE.md
- 08__GATE__TAKE_PACK.md
- 09__GATE__SCOPE_COMPLIANCE.md

--- END.
