# CHECKLIST — READINESS (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/04__CHECKLISTS/01__CHK__READINESS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CHECKLIST
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CHK.PROMPT_ARCHITECT.READINESS.001
OWNER: SYSTEM
ROLE: Readiness checklist for PROMPT_ARCHITECT before building prompts: verifies required inputs, scope, baseline freeze, and selection of a method (playbook). Produces PASS/REWORK/FAIL.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created readiness checklist for PROMPT_ARCHITECT: inputs, scope, baseline discipline, and method selection."
- REASON: "Most failures start from missing inputs or unfrozen baselines."
- IMPACT: "Faster and cleaner prompt creation runs."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.CHK.READY.001

---

## 0) REQUIRED INPUTS PRESENT
Mark each item.

INPUTS:
- [ ] Target genre/style is stated (primary identity)
- [ ] Language is stated
- [ ] Format is stated (full song / loop / short)
- [ ] Song length target is stated (or default accepted)
- [ ] Vocal mode is stated (single / A-B roles)
- [ ] Key constraints are stated (must-have / must-not)

Optional inputs (nice-to-have):
- [ ] BPM / tempo feel stated
- [ ] Lyric draft provided (if user has it)
- [ ] Reference inspiration given as principles (no “copy exactly”)

If any REQUIRED input missing:
- mark REWORK unless defaults are explicitly allowed.

---

## 1) SCOPE & GOAL CLARITY
- [ ] One-line primary goal is stated (what we optimize for)
- [ ] 1–3 success checks are stated (observable)
- [ ] Out of scope items acknowledged (no mixing domains)

---

## 2) BASELINE DISCIPLINE (IF ITERATING)
If this is a rework/variant run:
- [ ] Baseline prompt is frozen and labeled (BASE_V0/ID)
- [ ] Axis to change is declared (one axis)
- [ ] Patch budget declared (≤ 3 line edits) OR variant count declared

If this is a first build:
- [ ] Baseline discipline not required

---

## 3) METHOD SELECTION (PLAYBOOK)
Select one:
- [ ] PB-01 CORE WORKFLOW (build from scratch)
- [ ] PB-02 ONE-AXIS VARIANTS (experimentation)
- [ ] PB-03 DIAGNOSE & REWORK (gate-aligned fix)
- [ ] PB-04 PATCH MINIMAL CHANGE (single-issue fix)
- [ ] PB-05 VOCAL DIVERSITY BOOST (voice sameness)
- [ ] PB-06 ANTI-REPETITION FIX (repetition)
- [ ] PB-07 STYLE STABILIZER (drift)
- [ ] PB-08 FINAL QA PRECHECK (final pass)

Rule:
- If unsure, default to PB-01 (first build) or PB-03 (after fail).

---

## 4) TRACE FIELDS READY
- [ ] MEMORY_REUSE flag will be recorded (YES/NO)
- [ ] WEB_LOOKUP_USED flag will be recorded (YES/NO)
- [ ] Criteria UIDs (if used) will be listed (UID-only)
- [ ] Gaps will be listed if something is missing

---

## 5) RESULT RULE
PASS:
- all REQUIRED inputs checked
- goal + success checks defined
- method selected
- baseline discipline OK (if iterating)

REWORK:
- missing 1–2 required inputs OR baseline not frozen OR method not selected

FAIL:
- scope unclear + multiple required inputs missing + no method selected

---

## 6) NEXT ACTIONS (IF REWORK/FAIL)
If missing required inputs:
- request/define minimal defaults
- then run PB-01 CORE WORKFLOW

If baseline not frozen:
- freeze baseline, label it, then run PB-02 or PB-04

If method not selected:
- choose PB-01 (first build) or PB-03 (after fail evidence)

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PLAYBOOKS.README.DRAFT.001 | WHY: playbook selection
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 | WHY: iteration discipline
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 | WHY: early sanity gate

--- END.
