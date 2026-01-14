# GATE — REPETITION CONTROL INTENT (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/05__KB_GATES/03__GATE__REPETITION_CONTROL_INTENT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: KB_GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001
OWNER: SYSTEM
ROLE: Gate for PROMPT_ARCHITECT: checks whether prompt specifies a clear repetition policy (what can repeat and where), verse novelty constraints, and targeted anti-repetition negatives. Outputs PASS/REWORK/FAIL with fix mapping and recheck plan.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created repetition control intent gate: repetition policy + verse novelty + targeted negatives checks."
- REASON: "Repetition is a frequent generator failure; this gate makes anti-repetition intent explicit before generation."
- IMPACT: "Cleaner verses and fewer looped phrases while preserving hook repetition."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.GATE.REPEAT.001

---

## 0) TARGET OUTPUT
TARGET_OUTPUT:
- STRUCTURE_BLOCK (verse/chorus role clarity)
- NEGATIVE_SPEC_BLOCK (repetition-related)
- Optional: NOVELTY_CONSTRAINT_BLOCK (if present)

This gate checks prompt-level intent and constraints, not final audio.

---

## 1) TEST METHOD (DETERMINISTIC)
Run checks:

R1 — Repetition policy defined
Must explicitly state at least one:
- “Repetition allowed only in chorus/hook”
- “Verses must be novel / avoid repeated lines”
If no policy statement → REWORK/FAIL depending on severity.

R2 — Verse novelty constraint present (for full song)
If “full song” or verses exist:
- must include a novelty directive such as:
  - “each verse introduces new imagery/phrasing”
  - “avoid repeating identical lines/phrases in verses”
If absent → REWORK.

R3 — Structure protects chorus vs verse
- Chorus is labeled as hook/chorus
- Verse vs chorus roles are distinct (verse develops, chorus repeats)
If blurred → REWORK (or FAIL if severe).

R4 — Targeted negative specs present (recommended)
At least one negative about repetition, e.g.:
- avoid repeating the same lines in verses
- avoid recycling chorus lines into verses
- avoid repetitive rhyme loops
If none → REWORK unless R1–R3 are strong and compact.

R5 — Not over-banning (avoid killing hook)
If repetition is forbidden everywhere while a chorus/hook is required:
- mark contradiction → REWORK (fix by allowing chorus repetition)
If repetition ban list is excessively long (>14 negatives total):
- overload risk → REWORK.

---

## 2) PASS / REWORK / FAIL CRITERIA
PASS:
- R1 PASS
- R2 PASS (when verses exist)
- R3 PASS
- R5 PASS
- R4 present OR (R1–R3 are very explicit and compact)

REWORK:
- missing one element (R2 or R4) OR
- chorus/verse blur (R3) OR
- over-banning / overload (R5)

FAIL:
- no repetition policy (R1 missing) AND repetition is a known risk
- chorus/hook required but repetition forbidden everywhere (hard contradiction)
- structure is too unclear to apply policy (no verse/chorus separation)

---

## 3) OUTPUT RECORD (COPY)
GATE_RESULT_RECORD:
- GATE_UID: UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- RESULT: PASS/REWORK/FAIL
- FAILED_CHECKS:
  - <R#>
- EVIDENCE (short):
  - <snippet>
- FIX DIRECTIONS:
  - <action>
- RECHECK:
  - rerun this gate after fix

---

## 4) FIX MAPPING (WHAT TO DO IF FAILS)
If R1 missing:
- Fix: add explicit policy statement:
  - “repetition allowed only in chorus/hook; verses must be novel”.

If R2 missing:
- Fix: add verse novelty constraint (one line).

If R3 blurred:
- Fix: clarify chorus label + verse/chorus roles in STRUCTURE_BLOCK.

If R4 missing:
- Fix: add 1–3 targeted repetition negatives.

If R5 contradiction:
- Fix: allow chorus repetition explicitly; restrict bans to verses.

Playbook mapping:
- Use PB-06 ANTI-REPETITION FIX for full method.
- Use PB-04 PATCH MIN for minimal edits.

---

## 5) EXAMPLES (PLACEHOLDER)
EXAMPLES:
- PASS example:
  - <to be filled>
- FAIL example:
  - <to be filled>
- BORDERLINE example:
  - <to be filled>

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- gate result claimed without evidence
- fix is non-actionable (“make less repetitive”)
- gate skipped in pipelines where repetition control is required

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.ANTI_REPEAT.001 | WHY: primary fix method
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal fixes
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 | WHY: contract completeness gate runs first

--- END.
