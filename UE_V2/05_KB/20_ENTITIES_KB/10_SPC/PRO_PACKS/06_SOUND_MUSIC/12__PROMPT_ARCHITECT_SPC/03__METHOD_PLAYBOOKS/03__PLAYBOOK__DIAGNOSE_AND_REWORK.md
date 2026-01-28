# PLAYBOOK — DIAGNOSE & REWORK (GATE-ALIGNED) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/03__PLAYBOOK__DIAGNOSE_AND_REWORK.md

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
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001
OWNER: SYSTEM
ROLE: Deterministic diagnosis and rework playbook: convert QA/VAL failures into minimal prompt patches aligned to failed criteria, with recheck steps, loop limits, and escalation rules.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created diagnose & rework playbook: failure triage, axis mapping, patch strategy, and recheck protocol aligned to criteria UIDs."
- REASON: "Without gate-aligned rework, iteration becomes random and repeats failures."
- IMPACT: "Faster convergence to PASS with minimal identity drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.DIAG.001

---

## 0) INPUTS (REQUIRED)
- BASELINE_PROMPT_CONTRACT (the prompt used)
- QA_RESULT_RECORD and/or VAL_VIOLATION_RECORD(s)
- FAILED_CRITERIA_UIDS (UID-only)
- OUTPUT_OBSERVATIONS (short evidence notes)
- REWORK_BUDGET:
  - max loops for this issue (default 3)

If failed criteria UIDs are missing:
- STOP: request criteria UID(s) (no opinion-only rework).

---

## 1) OUTPUTS
- DIAGNOSIS_SUMMARY (what failed, why it likely failed)
- PATCH_PLAN (change 1–2 axes only)
- PATCH_PROMPT (minimal delta instructions)
- RECHECK_PLAN (which gates/checklists to re-run)
- REWORK_RECORD (trace + loop count)

---

## 2) TRIAGE (FAST)
Triage questions:
1) Is this a CRITICAL fail (core readability/hook/voice collapse)?
   - YES → fix first; do not chase polish.
2) Is failure about:
   - structure/hook (AX1)
   - vocals (AX2)
   - repetition (AX3)
   - style drift (AX4)
   - texture overload (AX5)
   - rhythm feel mismatch (AX6)
   - mix intent/mud (AX7)
3) Is the baseline prompt itself contradictory/overloaded?
   - YES → run PATCH MINIMAL CHANGE playbook first.

STOP CONDITIONS:
- missing input (lyrics missing but required) AND cannot infer safely
- missing criteria modules (unknown gate) → GAP

---

## 3) FAILURE TAXONOMY → AXIS MAP
Map each failed criterion to a primary axis (and optional secondary).

FAILURE_TO_AXIS_MAP:
- F-HOOK (hook too late / weak) -> AX1 HOOK EMPHASIS
- F-STRUCTURE (chorus not distinct / mush) -> AX1 + (optional AX4)
- F-VOICE_SAME (same singer) -> AX2 VOCAL CONTRAST
- F-REPEAT (repeated phrases/patterns) -> AX3 REPETITION CONTROL
- F-DRIFT (genre identity drift) -> AX4 STYLE FINGERPRINT
- F-CLUTTER (too busy / too many layers) -> AX5 TEXTURE INTENSITY
- F-FEEL (groove mismatch) -> AX6 RHYTHM FEEL
- F-MUD (muddy low end) -> AX7 MIX INTENT + (optional AX5)

Rule:
- Choose ONE primary axis per rework loop.

---

## 4) PATCH STRATEGY (MINIMAL DELTA)
General rule:
- Change 1–3 lines in one block.
- Keep other blocks untouched.

Patch lever toolkit (by axis):

AX1 HOOK EMPHASIS:
- strengthen chorus label + hook instruction
- reduce verse complexity
- add “hook appears early / chorus repeats” constraint

AX2 VOCAL CONTRAST:
- explicit role ownership per section
- stronger contrast principles (range/timbre/attack)
- targeted negative: “avoid identical vocal timbre across sections”

AX3 REPETITION CONTROL:
- verse novelty constraint
- negative: “avoid repeating same lines/patterns in verses”
- allow repetition only in chorus/hook

AX4 STYLE FINGERPRINT:
- reduce anchors to 3–4
- enforce primary + touch dominance
- remove conflicting genre descriptors

AX5 TEXTURE INTENSITY:
- reduce glitch/industrial density
- clarify synth role (support vs lead)
- negative: “avoid excessive stutter edits” if causing chaos

AX6 RHYTHM FEEL:
- specify feel clearly (half-time stomp vs driving)
- keep genre unchanged; only groove emphasis

AX7 MIX INTENT:
- add principle: “tight low end, avoid muddy sub”
- negative: “avoid uncontrolled sub-bass”
- do not over-spec mastering targets

---

## 5) RECHECK PLAN (CRITERIA-ALIGNED)
After patch, re-run:
- the failed gate/checklist UIDs
- plus 1 stability check (identity drift)

RECHECK_TEMPLATE:
- RECHECK_UIDS (UID-only):
  - <failed criterion uid>
  - <support criterion uid>
- PASS looks like:
  - <observable>

If checkpoints are placeholders/unknown:
- run internal mini checklist and mark GAP.

---

## 6) LOOP LIMITS & ESCALATION
Default loop limit:
- 3 attempts on the same issue.

If still failing after limit:
- ESCALATE:
  - switch axis only if evidence suggests wrong axis
  - OR call VOCAL DIVERSITY playbook (if voice issue persists)
  - OR simplify baseline (reduce constraints) and restart PB-01

Failover conditions:
- if repeated fails suggest generator limitation → change tool/model settings (out of scope here) OR adjust expectations.

---

## 7) REWORK RECORD (COPY)
REWORK_RECORD:
- RW_UID: RW-YYYYMMDD-001
- DATE: YYYY-MM-DD
- BASELINE_ID:
- FAILED_CRITERIA_UIDS (UID-only):
  - <uid>
- PRIMARY_AXIS:
- EVIDENCE (short):
- PATCH_DELTA (what changed):
- EXPECTED EFFECT:
- RECHECK_UIDS (UID-only):
  - <uid>
- RESULT: PASS/REWORK/FAIL
- LOOP_COUNT:
- NEXT ACTION:
  - CONTINUE / ESCALATE / STOP(GAP)
- TRACE:
  - MEMORY_REUSE: YES/NO
  - WEB_LOOKUP_USED: YES/NO

---

## 8) COMMON FAIL MODES (AND FIXES)
F1 — Patch changes too many things
- Fix: revert; apply one-axis rule strictly.

F2 — No criterion UID provided
- Fix: stop; request criterion UID(s) (no guessing).

F3 — Rework loop without learning
- Fix: enforce variant log + expected effect statements.

---

## 9) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.ONE_AXIS.001 | WHY: controlled experimentation after diagnosis
- UE.KB.VAL.TPL.VIOLATION.001 | WHY: violation records carry criterion UID + evidence
- UE.KB.QA.STD.CONNECTOR.001 | WHY: QA result record structure and trace
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.POLICY.DRAFT.001 | WHY: minimal change and anti-pattern constraints

--- END.
