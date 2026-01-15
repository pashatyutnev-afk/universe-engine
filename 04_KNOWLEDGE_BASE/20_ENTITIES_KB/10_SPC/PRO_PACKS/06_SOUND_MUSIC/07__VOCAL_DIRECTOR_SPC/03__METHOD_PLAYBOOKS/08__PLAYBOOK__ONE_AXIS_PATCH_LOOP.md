# SPC PRO PACK — PLAYBOOK (PB-08) — ONE-AXIS PATCH LOOP (POST-QA) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/08__PLAYBOOK__ONE_AXIS_PATCH_LOOP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PB.ONE_AXIS.001
OWNER: SYSTEM
ROLE: Deterministic post-QA iteration loop for VOCAL_DIRECTOR: freeze baseline, choose ONE axis to change, apply minimal patch, record expected effect, and log decision after results. Prevents chaotic rework and preserves what already works.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PB-08 one-axis patch loop for vocal direction rework."
- REASON: "Multi-axis changes destroy diagnosability; vocal direction must converge via minimal, traceable patches."
- IMPACT: "Faster convergence, stable vocal character, audit-ready decisions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB08.001

---

## 0) PURPOSE
Use this playbook when:
- QA notes exist (fails/soft fails)
- you must improve an existing vocal direction pack
- you need traceable iteration with minimal changes

Primary objective:
- Improve one dimension at a time without breaking other working parts.

---

## 1) REQUIRED INPUTS (MINIMUM)
STOP/GAP if missing:
- BASELINE_DIRECTION_PACK (exact text / exact decisions)
- QA_NOTES:
  - what failed (hard/soft)
  - where (section/line)
  - which targets (P0/P1 if intelligibility)
- SECTION STRUCTURE

Recommended:
- MUST_HEAR targets + gates checklist
- take recordings notes (textual)
- previous patch log (if any)

---

## 2) REQUIRED OUTPUTS (MANDATORY)
This playbook MUST produce:
- BASELINE_FREEZE_RECORD
- AXIS_DECLARATION (one axis only)
- PATCH_V1 (minimal delta)
- EXPECTED_EFFECT
- QC_RECHECK_RULES (what to verify after patch)
- DECISION_RECORD (after run)
- TRACE (memory/web + gaps)

NOT READY rule:
- If baseline is not frozen → STOP (cannot compare).

---

## 3) ONE-AXIS MENU (ALLOWED)
Choose exactly ONE axis per patch:

A1 — INTELLIGIBILITY
- adjust articulation, breath, stacking reductions on P0, phrasing grouping
(Use PB-03/PB-04/PB-07 tactics)

A2 — ARC / CONTRAST
- adjust section intensity curve or 1–2 contrast levers
(Use PB-05 tactics)

A3 — PHRASING / TIMING
- adjust accent placement, vowel length, micro-timing constraints
(Use PB-01/PB-03 tactics)

A4 — DELIVERY PROFILE
- prune contradictions; adjust 1–2 delivery principles; keep character stable
(Use PB-01 tactics)

A5 — STACKING PLAN
- remove/move stacking; protect zones; keep minimal
(Use PB-07 tactics)

Forbidden:
- changing lyrics text (ownership violation)
- changing song structure (ownership violation)
- prescribing mix/master chains (out of scope)

---

## 4) WORKFLOW (DETERMINISTIC STEPS)
### STEP 1 — Freeze baseline
Create BASELINE_FREEZE_RECORD:
- BASE_ID: BASE_V0
- what is included: full baseline direction pack
- what is excluded: none
Rule:
- baseline must be copy-pastable exact text.

### STEP 2 — Select axis (one only)
Pick axis based on QA_NOTES:
- P0 not understood → A1 (Intelligibility)
- chorus lift missing → A2 (Arc/Contrast)
- timing smear on hook → A3 (Phrasing/Timing)
- delivery contradictions → A4 (Delivery Profile)
- stacking masks words → A5 (Stacking Plan)

Record AXIS_DECLARATION:
- axis = A1..A5
- reason = 1 line

### STEP 3 — Write EXPECTED_EFFECT
One sentence, testable:
- “After patch, P0 words are understood on first listen in chorus.”

### STEP 4 — Apply PATCH_V1 (minimal delta)
Rules:
- change ≤ 1–3 lines/constraints
- touch only one relevant block
- do not rewrite entire sections
- preserve all non-target working parts

### STEP 5 — Define QC_RECHECK_RULES
List what to recheck (YES/NO):
- Q1: fixed failure is resolved
- Q2: other working gates did not regress
- Q3: character consistency preserved across takes

### STEP 6 — Decision record (after run)
Record:
- RESULT: PASS/REWORK/FAIL
- DECISION: KEEP / REVERT / TRY_NEXT_AXIS
- NOTE: what changed and what improved

---

## 5) COMMON FAIL MODES
- patch touches multiple axes (invalid)
- patch is a rewrite (delta too big)
- baseline not frozen (no comparison)
- expected effect not stated (no learnings)
- “fix” uses lyric rewrite or mix chain advice (scope violation)

---

## 6) OUTPUT TEMPLATE (COPY)
### BASELINE_FREEZE_RECORD
- base_id:
- included:
- hash(optional):

### AXIS_DECLARATION
- axis:
- reason:

### EXPECTED_EFFECT
- statement:

### PATCH_V1 (MINIMAL)
- changed_lines:
- unchanged_blocks:

### QC_RECHECK_RULES
- Q1:
- Q2:
- Q3:

### DECISION_RECORD
- result:
- decision:
- note:

### TRACE
- MEMORY_REUSE:
- WEB_LOOKUP_USED:
- GAPS:

--- END.
