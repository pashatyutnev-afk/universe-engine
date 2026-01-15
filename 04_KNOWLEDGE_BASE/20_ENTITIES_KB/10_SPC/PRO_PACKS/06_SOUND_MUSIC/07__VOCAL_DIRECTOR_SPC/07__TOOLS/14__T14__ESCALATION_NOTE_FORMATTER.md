# SPC PRO PACK — TOOL (T14) — ESCALATION_NOTE_FORMATTER (PRINCIPLES ONLY) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/14__T14__ESCALATION_NOTE_FORMATTER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T14
TOOL_NAME: ESCALATION_NOTE_FORMATTER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T14.ESCALATION_NOTE_FORMATTER.001
OWNER: SYSTEM
ROLE: Formats scope-safe escalation notes to the correct owner when a fix requires changes outside VOCAL_DIRECTOR scope (lyrics, structure, arrangement). Outputs a stable ESCALATION_NOTES block using principles-only requests.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T14 ESCALATION_NOTE_FORMATTER for VOCAL_DIRECTOR."
- REASON: "When issues require owner actions, requests must be structured and scope-safe."
- IMPACT: "Faster resolution of T4/T7/T9 cases; cleaner handoffs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T14.001

---

## 0) PURPOSE
Create a deterministic escalation note (not a solution):
- ESCALATION_NOTES

Used in:
- T4 density/unsingable (lyrics owner)
- T7 arrangement seat conflict (arranger/producer owner)
- T9 scope cleanup conversion (ownership language → escalation)

---

## 1) INPUTS (REQUIRED)
- owner (target recipient role)
- section label (hook/chorus/verse)
- problem statement (1–2 lines)
Optional (recommended):
- line_ids
- copy-exact excerpts (short)
- evidence bullets (why it fails)
- must_keep constraints (P0 words/phrases)
- requested outcome (success criteria)
- gate to rerun

Rules:
- If owner is not specified, tool must request it (do not guess).
- Requests must be principles-only; no exact rewrite text, no exact arrangement edits, no plugin chains.

---

## 2) OUTPUT BLOCK (STABLE NAME)
T14 MUST output:

### ESCALATION_NOTES
- owner:
- section:
- line_ids: (optional list)
- problem:
- evidence:
  - 1)
  - 2) (optional)
- request (principles only):
  - 1)
  - 2) (optional)
- must_keep:
  - 1)
  - 2) (optional)
- forbidden (scope):
  - 1)
  - 2) (optional)
- success_criteria:
  - 1)
  - 2) (optional)
- next_check:
  - "<which gate(s) to rerun after owner response>"

---

## 3) PRINCIPLES-ONLY RULE (ABSOLUTE)
Allowed request styles:
- “reduce density so a safe breath point exists without splitting P0 meaning”
- “ensure perceptual space for P0 consonant attacks in hook”
- “preserve these must-keep words/phrases; do not change them”

Forbidden request styles:
- providing replacement lines/words
- prescribing exact instrument removals/additions as owned action
- mixing/master plugin chains or EQ settings

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Validate owner and section
- If missing → GAP request, stop.

Step 2 — Build problem + evidence
- Problem: 1–2 lines
- Evidence: 1–3 bullets referencing copy-exact excerpts/line_ids if provided

Step 3 — Build principles-only request
- 1–2 bullets, outcome-oriented

Step 4 — Build must_keep list
- include P0 words/phrases (copy-exact) if available

Step 5 — Build forbidden list (scope reminders)
- include:
  - "no lyric rewrite suggestions inside VOCAL_DIRECTOR"
  - "no mix/master chains"
(Keep short.)

Step 6 — Build success_criteria
- 1–2 bullets measurable:
  - “P0 phrase can be delivered in one breath unit”
  - “P0 understood first listen in hook”

Step 7 — Set next_check
- Choose gate(s) impacted:
  - density → rerun G6 → G3
  - arrangement seat → rerun G3 (and G7/G5 if impacted)
  - scope conversion → rerun G9

Step 8 — Output ESCALATION_NOTES

---

## 5) STOP / GAP CONDITIONS
Stop (GAP) if:
- owner missing
- section missing
- no problem statement exists

---

## 6) TRACE
TRACE:
- TOOL: T14
- OUTPUT: ESCALATION_NOTES
- USED_IN: T4/T7/T9 remediation

--- END.
