# 02__PLAYBOOK__DIAGNOSE_AND_REWORK — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/03__METHOD_PLAYBOOKS/02__PLAYBOOK__DIAGNOSE_AND_REWORK.md
SCOPE: KB — SPC Pro Pack — Composer — Playbook (Diagnose & Rework)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: PLAYBOOK
PLAYBOOK_TYPE: DIAGNOSE_AND_REWORK
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001
OWNER: SPC (Composer)
ROLE: One-axis repair workflow for composition outputs failing checklists/gates (motif/harmony/melody/contrast).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Diagnose & Rework playbook initialized for Composer SPC pack."
- REASON: "Stop chaotic rewrites and preserve musical identity."
- IMPACT: "Enforces one-axis, patch log, and rerun set."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.PB.REWORK.001

---

## GOAL
Чинить композиционные проблемы быстро и безопасно:
- не терять identity anchors,
- не ломать уже рабочие блоки,
- избегать хаотичных “переписать всё”.

---

## ENTRY TRIGGERS (WHEN TO USE)
Use this playbook when:
- any checklist FAIL/REWORK
- any gate FAIL/REWORK
- motif is not recognizable / not hummable
- harmony conflicts with mood/genre intent
- melody contour is flat or too random
- repetition creates “same loop” fatigue
- contradictions appear (tonal center, hook placement, contrast)

---

## HARD RULES
- ONE-AXIS ONLY per repair loop
- Minimal patch: smallest edit to fix the failing signal
- Preserve identity anchors unless axis=variants/identity
- After patch → rerun minimum set
- If hard limit (scope breach) → stop and remove

---

## REPAIR AXES (CHOOSE ONE)
- clarity (tests/wording/executability)
- structure (form map, order, scanability)
- motif (hook identity, recognizability, variation rules)
- harmony (tonal logic, tension ladder, cadences)
- melody (contour, register, targets)
- consistency (contradictions/term drift)
- compliance (scope breach)
- edge (conflicting constraints strategy)

---

## DIAGNOSE (FIND ROOT CAUSE)

### Step D1 — Capture failure
Record:
- FAIL_SOURCE: <CHK|GATE|RUBRIC|HUMAN_REVIEW>
- FAIL_UID: <...>
- FAIL_SIGNAL: <short description>

### Step D2 — Map to musical axis
Common mapping:
- “не запоминается” → motif
- “не тянет эмоционально” → harmony or contrast
- “мелодия не ведёт” → melody
- “всё одинаково” → structure or repetition control (motif/melody)
- “противоречия” → consistency
- “слишком размыто” → clarity
- “лезет в микс/цифры” → compliance

### Step D3 — Define smallest fix
Write:
- MIN_PATCH_INTENT (1 sentence)
- WHAT MUST NOT CHANGE (identity anchors list)

---

## PATCH (ONE AXIS)

### Patch format (MANDATORY)
- AXIS_CHANGED: <one axis>
- BEFORE: (1–3 bullets)
- PATCH: (1–5 bullets, concrete edits)
- AFTER: (1–3 bullets)

Axis-specific guidance:
- motif:
  - tighten motif description (contour + rhythm cell)
  - add recognition test
  - add 1–2 variation rules that preserve identity
- harmony:
  - clarify tonal center / modal color
  - adjust tension ladder placement
  - define cadence intent at arrivals
- melody:
  - set register per section
  - enforce contour constraint (rise/fall) + target moments
- structure:
  - fix hook placement window
  - re-order form for contrast
- clarity:
  - convert “vibe words” into testable criteria
- compliance:
  - remove engineering/illegal certainty, add routing note
- consistency:
  - reconcile contradictions (one source of truth)

---

## RERUN (MINIMUM SET)
After each patch loop:
1) Rerun the failed item (same CHK/GATE)
2) Rerun CONSISTENCY gate
3) If axis was motif/harmony/melody → rerun CORE_OUTPUT_QUALITY gate
4) If edge/conflicts present → rerun EDGE_CASES gate

Record:
- RERUN:
  - <UID>: <PASS|REWORK|FAIL>
  - <UID>: <PASS|REWORK|FAIL>

---

## STOP CONDITIONS
Stop and escalate when:
- same failure repeats twice after patch
- patch breaks other passing areas (ping-pong)
- contradictions persist after 2 loops
- missing inputs prevent resolution (readiness)
- hard limit exists (scope breach)

---

## PATCH LOG (MANDATORY)
Use this block each loop:
- CHANGE_ID:
- AXIS_CHANGED:
- FAIL_SOURCE:
- FAIL_UID:
- BEFORE:
- PATCH:
- AFTER:
- RERUN:
- DECISION: <CONTINUE|STOP|READY>

---

## EXIT CONDITIONS
- READY when rerun set passes and anchors remain stable.
- Otherwise loop again (still one-axis) or STOP.

---

## REQUIRED UID REFERENCES
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.COMPOSER.REGRESSION_GUARD.001
- RUBRIC:
  - UE.KB.SPC.PACK.COMPOSER.RUBRIC.001
- GATES:
  - UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.EDGE_CASES.001

---
END
