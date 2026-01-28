# SPC PRO PACK — PLAYBOOKS (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/00__README__PLAYBOOKS.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PLAYBOOKS.README.DRAFT.001
OWNER: SYSTEM
ROLE: Playbook catalog + routing map for VOCAL_DIRECTOR Pro Pack. Defines which method to use, required inputs/outputs, and stop/escalation rules. Not a navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created playbook README for VOCAL_DIRECTOR: method catalog + routing + output contracts."
- REASON: "Pack requires deterministic execution patterns; prevents vague ‘sing better’ directions."
- IMPACT: "Vocal direction becomes repeatable and gate-checkable."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB.README.001

---

## 0) PURPOSE
This folder contains VOCAL_DIRECTOR execution methods (“playbooks”):
- what to do
- when to do it
- what inputs are required
- what outputs must be produced
- when to STOP / mark GAP / escalate

Rule:
- If a run can’t pick a playbook deterministically, it must STOP and request missing inputs.

---

## 1) NON-NEGOTIABLE GLOBAL RULES
- Intelligibility-first: must-hear words + gates checklist is required for READY outputs.
- No lyric rewrites inside this pack: only escalation notes to Lyricist/Songwriter.
- No arrangement ownership: only seat-conflict escalation notes.
- No mix/master chains: only priority notes (principles), never processing recipes.
- One-axis discipline for rework: fix one dimension at a time.

---

## 2) ROUTING (WHICH PLAYBOOK TO USE)
Use this decision map (top-down):

R0 — Missing critical inputs?
- If lyric draft missing OR no section structure → STOP/GAP (request inputs)

R1 — New track / first vocal direction pass?
- Use PB-01 CORE VOCAL DIRECTION WORKFLOW

R2 — Hook words not landing / lyrics not understood?
- Use PB-03 INTELLIGIBILITY DIAGNOSE & REPAIR
- If repair requires text change → PB-04 BREATH & DENSITY + escalate (do not rewrite)

R3 — Verse/chorus sound too similar / arc flat?
- Use PB-05 SECTION ARC DESIGN

R4 — Takes are inconsistent / performer keeps drifting?
- Use PB-06 TAKE DIRECTION PACK

R5 — Backings/harmonies are needed but risk masking?
- Use PB-07 STACKING/HARMONY MINIMAL PLAN

R6 — Iteration after a fail (QA notes exist)?
- Use PB-08 ONE-AXIS PATCH LOOP (choose axis: intelligibility OR arc OR phrasing OR delivery)

---

## 3) REQUIRED OUTPUT CONTRACT (ALL PLAYBOOKS)
Every playbook output must include (unless explicitly marked N/A):
- VOCAL_DELIVERY_PROFILE (principles)
- PERFORMANCE_ARC_MAP (by section)
- MUST_HEAR_WORDS (priority list)
- INTELLIGIBILITY_GATES_CHECKLIST (pass/fail conditions)
- PHRASING_TIMING_NOTES (accent + breath policy)
- STACKING_PLAN (high-level) OR N/A with reason
- RECORDING_DIRECTION_PACK (take goals + QC hard fails)
- ESCALATION_NOTES (if required)
- TRACE:
  - MEMORY_REUSE: YES/NO
  - WEB_LOOKUP_USED: YES/NO
  - UIDS_APPLIED: UID list
  - GAPS: placeholders encountered

If MUST_HEAR_WORDS or INTELLIGIBILITY_GATES are missing → NOT READY.

---

## 4) PLAYBOOK LIST (PLANNED SET)
All playbooks in this pack must follow the same internal format:
- PURPOSE
- INPUTS (minimum)
- OUTPUTS (mandatory)
- STEPS (deterministic)
- STOP / ESCALATE
- COMMON FAIL MODES

### PB-01 — CORE VOCAL DIRECTION WORKFLOW
FILE: 01__PLAYBOOK__CORE_VOCAL_DIRECTION_WORKFLOW.md
Use when:
- first pass direction for a track (no prior QA notes)

### PB-02 — MUST-HEAR WORDS EXTRACTION & PRIORITY
FILE: 02__PLAYBOOK__MUST_HEAR_WORDS_PRIORITY.md
Use when:
- hook clarity is critical; need a ranked must-hear list before any take direction

### PB-03 — INTELLIGIBILITY DIAGNOSE & REPAIR (NO LYRIC CHANGE)
FILE: 03__PLAYBOOK__INTELLIGIBILITY_DIAGNOSE_REPAIR.md
Use when:
- words are not understood; consonants vanish; hook is mushy
Output focus:
- articulation/breath/phrasing fixes without meaning edits

### PB-04 — BREATH & DENSITY FIX + ESCALATION RULES
FILE: 04__PLAYBOOK__BREATH_DENSITY_ESCALATION.md
Use when:
- lines are physically unsingable at tempo; breath breaks destroy must-hear words
Output focus:
- breath policy + escalation requests (do not rewrite)

### PB-05 — SECTION ARC DESIGN (VERSE→CHORUS CONTRAST)
FILE: 05__PLAYBOOK__SECTION_ARC_CONTRAST.md
Use when:
- performance arc is flat; verse/chorus indistinguishable; energy mapping unclear

### PB-06 — TAKE DIRECTION PACK (GOALS + QC HARD FAILS)
FILE: 06__PLAYBOOK__TAKE_DIRECTION_PACK.md
Use when:
- need repeatable takes; vocalist drifts; comping becomes inconsistent
Output focus:
- take goals per section + QC checklist + risk lines

### PB-07 — STACKING/HARMONY MINIMAL PLAN (CLARITY-SAFE)
FILE: 07__PLAYBOOK__STACKING_MINIMAL_PLAN.md
Use when:
- want hook lift without masking intelligibility
Output focus:
- where/why stacking; “minimal-first” strategy

### PB-08 — ONE-AXIS PATCH LOOP (POST-QA)
FILE: 08__PLAYBOOK__ONE_AXIS_PATCH_LOOP.md
Use when:
- iterative fix after failure
Axis choices (one per patch):
- intelligibility OR arc OR phrasing/timing OR delivery profile OR stacking
Rule:
- patch must be minimal; preserve what works

---

## 5) PLAYBOOK–SCOPE ALIGNMENT (GUARDRAILS)
Any playbook must remain inside VOCAL_DIRECTOR scope:
- delivery/arc/intelligibility/phrasing/stacking(high-level)/take pack
Hard boundary:
- no lyrics meaning edits
- no arrangement ownership
- no mix/master chains

If a playbook step requires out-of-scope work:
- it must produce an escalation note instead.

---

## 6) NEXT FILES TO CREATE (IN THIS FOLDER)
Create these files next (one-by-one):
1) 01__PLAYBOOK__CORE_VOCAL_DIRECTION_WORKFLOW.md
2) 02__PLAYBOOK__MUST_HEAR_WORDS_PRIORITY.md
3) 03__PLAYBOOK__INTELLIGIBILITY_DIAGNOSE_REPAIR.md
4) 04__PLAYBOOK__BREATH_DENSITY_ESCALATION.md
5) 05__PLAYBOOK__SECTION_ARC_CONTRAST.md
6) 06__PLAYBOOK__TAKE_DIRECTION_PACK.md
7) 07__PLAYBOOK__STACKING_MINIMAL_PLAN.md
8) 08__PLAYBOOK__ONE_AXIS_PATCH_LOOP.md

---

## 7) DOC CONTROL CHECK (MANDATORY)
- Exactly one STATUS and one LOCK
- Version/UID present
- Routing is deterministic (no “maybe”)
- Outputs are listed as mandatory
- No fictional entities/UIDs (placeholders only as GAP)

--- END.
