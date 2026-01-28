# SPC PRO PACK — GATE (G9) — SCOPE / OWNERSHIP COMPLIANCE (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/09__GATE__SCOPE_COMPLIANCE.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001
OWNER: SYSTEM
ROLE: Gate G9 enforces VOCAL_DIRECTOR boundaries and ownership discipline. It validates that outputs do not contain out-of-scope actions (lyric rewrites, structure ownership, mix/master chains) and that any required changes are expressed only as escalation notes to the correct owner.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G9: Scope/Ownership Compliance for VOCAL_DIRECTOR Pro Pack."
- REASON: "Without explicit boundary enforcement, specialists overstep and outputs become non-auditable."
- IMPACT: "Keeps work deterministic; prevents silent cross-role edits; protects responsibilities model."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.SCOPE.001

---

## 0) PURPOSE
This gate answers:
- Does the output remain within VOCAL_DIRECTOR scope and respect ownership boundaries?

Scope enforcement is mandatory:
- violations are not “preferences”; they are FAIL conditions.

---

## 1) REQUIRED INPUTS
Input to validate:
- the produced VOCAL_DIRECTOR output pack (text)

Reference boundary rules:
- VOCAL_DIRECTOR boundaries (absolute) from the entity contract.

---

## 2) ABSOLUTE BOUNDARIES (WHAT IS FORBIDDEN)
Forbidden actions in VOCAL_DIRECTOR outputs:

F1 — Lyric meaning edits / rewrites
- VOCAL_DIRECTOR must not rewrite or replace lyric text.
Allowed:
- escalation notes requesting changes.

F2 — Song structure ownership
- cannot add/remove sections or “rewrite structure” inside this pack.
Allowed:
- escalation request to Songwriter.

F3 — Arrangement ownership
- cannot prescribe arrangement composition decisions.
Allowed:
- seat/space requests as principles to Arranger/Producer.

F4 — Mix/master processing chains
- cannot prescribe EQ/compression/reverb chains, DAW recipes, plugin settings.
Allowed:
- priority notes as principles (e.g., “keep vocal seat clear”) without technical chain.

F5 — Fantasy / guessing beyond inputs
- cannot assert facts not grounded in inputs or recorded knowledge.
Allowed:
- mark GAP; request missing inputs.

---

## 3) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if:
- none of F1–F5 violations appear in the output pack
- any needed out-of-scope changes are expressed only as ESCALATION_NOTES with owner specified

### REWORK
REWORK if:
- minor phrasing implies ownership but can be reworded into escalation
- minor “mix-ish” language appears but can be replaced by principle-level seat notes
Fix route:
- rewrite offending lines as escalation/principles (no new content)

### FAIL
FAIL if ANY occurs:
- direct lyric rewrites or replacement text provided (F1)
- direct structure edits ordered as if VOCAL_DIRECTOR owns structure (F2)
- explicit mix/master chain recipes (F4)
- claims that require missing inputs but are asserted as fact (F5)
FAIL implies:
- NOT READY; offending content must be removed and replaced by escalation/GAP notes.

---

## 4) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:
- SCOPE_AUDIT:
  - lyric_rewrite_present: YES/NO
  - structure_edit_present: YES/NO
  - arrangement_ownership_present: YES/NO
  - mix_chain_present: YES/NO
  - guessing_present: YES/NO
- ESCALATION_NOTES (if any):
  - owner specified: YES/NO

---

## 5) FIX ROUTE (REMEDIATION)
If REWORK:
- Replace violations with:
  - escalation notes (owner + minimal request + reason)
  - or principle-level seat notes (no chains)

If FAIL:
- Remove offending text
- Rebuild output pack boundary-safe:
  - use PB-01 baseline rebuild
  - or PB-08 one-axis patch, but only if fix is truly local and does not hide a larger violation

After remediation:
- rerun G9.

---

## 6) COMMON VIOLATIONS (EXAMPLES)
- “Replace this line with …” (lyric rewrite) → FAIL
- “Add a pre-chorus” (structure ownership) → FAIL
- “Use a multiband compressor on vocals” (mix chain) → FAIL
- “This word must be pronounced X” without language/stress info (guessing) → REWORK/FAIL depending on evidence

---

## 7) OUTPUT FORMAT (MANDATORY)
G9_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - SCOPE_AUDIT:
  - ESCALATION_NOTES:
- NEXT_STEP:
  - if PASS: "Pack output is scope-compliant"
  - if REWORK/FAIL: "Remove violations, convert to escalation/GAP, rerun G9"

--- END.
