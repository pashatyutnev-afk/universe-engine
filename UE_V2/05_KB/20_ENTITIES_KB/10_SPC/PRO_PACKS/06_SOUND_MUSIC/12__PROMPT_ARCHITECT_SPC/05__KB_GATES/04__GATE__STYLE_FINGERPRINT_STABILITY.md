# GATE — STYLE FINGERPRINT STABILITY (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/05__KB_GATES/04__GATE__STYLE_FINGERPRINT_STABILITY.md

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
UID: UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001
OWNER: SYSTEM
ROLE: Gate for PROMPT_ARCHITECT: checks whether style fingerprint is stable and non-contradictory (anchors, dominance for fusion, clutter limits). Outputs PASS/REWORK/FAIL with fix mapping and recheck plan.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created style fingerprint stability gate: anchor markers + dominance rule + contradiction/clutter checks."
- REASON: "Style drift and genre soup degrade catalog identity and controllability."
- IMPACT: "More consistent genre identity and safer iteration."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.GATE.STYLE.STAB.001

---

## 0) TARGET OUTPUT
TARGET_OUTPUT:
- STYLE_BLOCK (primary)
- Optional: CONSTRAINTS_BLOCK (mix intent direction)
This gate evaluates prompt-level style specification, not audio.

---

## 1) TEST METHOD (DETERMINISTIC)
Run checks:

S1 — Primary style identity exists
- At least one primary genre/style label exists (human-readable).

S2 — Anchor markers exist (3–6 recommended)
Anchors are “roles/markers”, e.g.:
- rhythm feel (one)
- guitar role (one)
- synth role (one)
- drum tone role (optional)
- texture direction (optional)
If anchors < 2 → REWORK/FAIL.
If anchors > 6 → overload risk → REWORK.

S3 — Fusion dominance rule (only if multiple styles)
If the STYLE_BLOCK includes:
- 2+ genre/style labels, OR “fusion/blend/touch”
Then must include dominance rule:
- primary dominates, secondary is a touch
- what must remain primary (1–2 anchors)
If missing → REWORK.

S4 — Contradiction scan
Flag contradictions such as:
- clean aggressive AND lo-fi muddy
- minimal sparse AND dense wall of layers
- half-time stomp AND fast dnb breakcore (without dominance + clarity)
If contradictions exist and not resolved → FAIL (or REWORK if one minor).

S5 — Clutter / inventory ban (prompt-level)
- No long lists of instruments/genres (“everything list”).
Heuristic:
- >3 genre labels OR >14 “style/instrument” items → REWORK (prune needed).

S6 — Mix intent direction is single (if present)
If mix intent specified:
- it should choose one direction (clean/controlled OR raw/gritty), not both.
If conflict → REWORK.

---

## 2) PASS / REWORK / FAIL CRITERIA
PASS:
- S1 PASS
- S2 within range (3–6) OR justified minimal set
- S3 PASS when applicable
- S4 no unresolved contradictions
- S5 not cluttered
- S6 no conflict

REWORK:
- anchors too few/too many
- dominance rule missing for fusion
- minor contradictions that can be solved by pruning
- clutter/inventory detected

FAIL:
- multiple unresolved contradictions
- style is effectively undefined (S1 missing)
- severe genre soup (many genres + no anchors + no dominance)

---

## 3) OUTPUT RECORD (COPY)
GATE_RESULT_RECORD:
- GATE_UID: UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- RESULT: PASS/REWORK/FAIL
- FAILED_CHECKS:
  - <S#>
- EVIDENCE (short):
  - <snippet>
- FIX DIRECTIONS:
  - <action>
- RECHECK:
  - rerun this gate after fix

---

## 4) FIX MAPPING (WHAT TO DO IF FAILS)
If S1 missing:
- Fix: choose a primary genre identity (one label).

If S2 too few:
- Fix: add 2–4 anchors (roles), not inventories.

If S2 too many:
- Fix: prune to 3–6 anchors; keep one lead role.

If S3 missing:
- Fix: add dominance block:
  - primary dominates; secondary touch
  - must stay primary: <anchor(s)>

If S4 contradictions:
- Fix: remove one side OR define dominance and simplify adjectives.

If S5 clutter:
- Fix: delete long lists; keep roles.

If S6 mix conflict:
- Fix: choose one mix direction and remove the other.

Playbook mapping:
- Use PB-07 STYLE FINGERPRINT STABILIZER for full fix.
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
- gate outcome claimed without evidence
- fix is non-actionable
- gate skipped in pipelines requiring stable style

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.STYLE_STABILIZE.001 | WHY: primary fix method
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal fixes
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 | WHY: contract clarity gate runs first

--- END.
