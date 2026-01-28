# SPC PRO PACK — KB GATES (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/00__README__GATES.md

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
ROLE: Gate catalog + execution order for VOCAL_DIRECTOR Pro Pack. Defines what is validated, how PASS/REWORK/FAIL works, required evidence artifacts, and which playbooks to use for rework. Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created gates README for VOCAL_DIRECTOR: deterministic gate order, gate list, outcome semantics, and playbook mapping."
- REASON: "Need testable pass/fail logic for vocal delivery, intelligibility, arc contrast, and repeatable takes."
- IMPACT: "Vocal direction outputs become auditable and converge via structured rework."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.GATES.README.001

---

## 0) PURPOSE
This folder defines GATES used to validate VOCAL_DIRECTOR outputs:
- make failures diagnosable
- enforce intelligibility-first
- prevent vague “sing better” outputs
- ensure repeatability across takes

Rule:
- If a gate depends on missing inputs (lyrics/structure/must-hear targets), the run must STOP/GAP rather than guessing.

---

## 1) PASS / REWORK / FAIL (SEMANTICS)
- PASS:
  - gate conditions satisfied; output can be used as “READY”
- REWORK:
  - gate not satisfied but fix is local and deterministic (apply specific playbook patch)
- FAIL:
  - critical missing artifacts, scope violations, or contradictions; must rebuild baseline or escalate owners

---

## 2) DETERMINISTIC GATE ORDER (RUN SEQUENCE)
Run gates in this order (stop on FAIL; on REWORK apply playbook then rerun affected gates):

G1 — INPUT READINESS (STOP/GAP)
G2 — MUST-HEAR TARGETS (P0/P1)
G3 — INTELLIGIBILITY (PASS/FAIL vs must-hear)
G4 — DELIVERY PROFILE COHERENCE (no contradictions)
G5 — SECTION ARC / VERSE→CHORUS CONTRAST
G6 — BREATH & SINGABILITY (no must-hear splits)
G7 — STACKING CLARITY-SAFE (if stacking used)
G8 — TAKE PACK REPEATABILITY + QC HARD FAILS
G9 — OWNERSHIP / SCOPE COMPLIANCE (no lyric rewrite, no mix chain)

---

## 3) GATE LIST (FILES IN THIS FOLDER)
Each gate has its own file with:
- PURPOSE
- INPUTS REQUIRED
- PASS / REWORK / FAIL conditions
- REQUIRED EVIDENCE (what must exist in output pack)
- FIX ROUTE (which playbook to apply)

Planned gates (one file each):

01__GATE__INPUT_READINESS.md
- validates: minimum inputs present (lyrics + structure + language)

02__GATE__MUST_HEAR_TARGETS.md
- validates: P0/P1 targets exist and are testable (short, prioritized)

03__GATE__INTELLIGIBILITY_PASS.md
- validates: explicit pass criteria for P0/P1 clarity + no breath splits inside P0

04__GATE__DELIVERY_PROFILE_COHERENCE.md
- validates: delivery profile is coherent, non-contradictory, executable

05__GATE__ARC_CONTRAST.md
- validates: arc map exists; verse→chorus contrast uses 1–3 levers

06__GATE__BREATH_SINGABILITY.md
- validates: breath policy exists; unsingable-risk flagged; escalation notes created when needed

07__GATE__STACKING_CLARITY_SAFE.md
- validates: stacking map (or N/A) + protected zones; P0 clarity protected

08__GATE__TAKE_PACK_REPEATABILITY.md
- validates: take goals per section + QC hard fails + repeatability rules + comp notes

09__GATE__SCOPE_COMPLIANCE.md
- validates: no lyric meaning edits; no structure ownership; no mix/master chain prescriptions; escalations are properly addressed

---

## 4) REQUIRED EVIDENCE ARTIFACTS (MINIMUM READY PACK)
A run can be “READY” only if these exist (unless marked N/A with reason):
- MUST_HEAR_WORDS (P0/P1/P2) + MUST_HEAR_PHRASES (if needed)
- INTELLIGIBILITY_GATES_CHECKLIST (pass/fail conditions)
- VOCAL_STYLE_PROFILE (principles + forbidden styles)
- PERFORMANCE_ARC_MAP (by section)
- PHRASING_TIMING_NOTES + BREATH_POLICY
- STACKING_MAP (or N/A) + PROTECTED_ZONES (if stacking)
- TAKE_GOALS_BY_SECTION + QC_HARD_FAILS + REPEATABILITY_RULES + COMP_NOTES
- ESCALATION_NOTES (if any out-of-scope fix is required)
- TRACE (memory/web + applied UIDs + gaps)

If MUST_HEAR or INTELLIGIBILITY_GATES are missing → FAIL (not ready).

---

## 5) PLAYBOOK MAPPING (FIX ROUTES)
When a gate returns REWORK/FAIL, apply:

- G1 INPUT READINESS → PB-01 intake step (STOP/GAP)
- G2 MUST-HEAR TARGETS → PB-02
- G3 INTELLIGIBILITY → PB-03 (repair) and/or PB-04 (density/breath escalation)
- G4 DELIVERY PROFILE COHERENCE → PB-01 (profile prune) or PB-08 (one-axis patch A4)
- G5 ARC/CONTRAST → PB-05 (or PB-08 axis A2)
- G6 BREATH/SINGABILITY → PB-04 (or PB-08 axis A1/A3)
- G7 STACKING → PB-07 (or PB-08 axis A5)
- G8 TAKE PACK → PB-06
- G9 SCOPE COMPLIANCE → immediate FAIL + rewrite outputs to remove violations; escalate owners (no patching by mixing)

---

## 6) COMMON FAILURE MODES (WHAT GATES MUST CATCH)
- must-hear targets not defined (“make it clear” only)
- breath breaks inside hook words
- stacking everywhere (masking consonants)
- arc flat (verse and chorus indistinguishable)
- contradictory delivery (“clean” + “lo-fi grit” simultaneously)
- attempt to rewrite lyrics instead of escalation
- attempt to “fix performance” by mix chain recipes

---

## 7) EXPANSION RULE (WHEN ADDING NEW GATES)
Add a new gate only if:
- a repeatable failure mode exists
- fix route is deterministic (playbook exists or can be created)
- required evidence can be stated in a checklist
After adding:
- update this README (gate list + order + mapping)
- add at least 1 GOOD + 1 BAD case for the new gate (future L3 requirement)

---

## 8) DOC CONTROL CHECK (MANDATORY)
- Exactly one STATUS and one LOCK
- Version/UID present
- Gate order is deterministic
- No out-of-scope policies introduced here
- No fictional entities/UIDs (gates are pack docs; placeholders allowed only for future docs in this folder)

--- END.
