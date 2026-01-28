# GATE — PROMPT CONTRACT CLARITY (KEY-CANDIDATE) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/05__KB_GATES/01__GATE__PROMPT_CONTRACT_CLARITY.md

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
UID: UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001
OWNER: SYSTEM
ROLE: Key-candidate gate for PROMPT_ARCHITECT: checks prompt contract completeness, internal consistency, and control density. Produces PASS/REWORK/FAIL with actionable fixes and recheck method.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created prompt contract clarity gate: required blocks, contradiction detection, overload detection, and fix mapping."
- REASON: "Most failures start with vague or contradictory prompts; this gate is a cheap early filter."
- IMPACT: "Higher controllability and fewer wasted generations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.GATE.PROMPT.CLARITY.001

---

## 0) TARGET OUTPUT
TARGET_OUTPUT:
- Prompt Contract text (STYLE/STRUCTURE/VOCALS/NEGATIVES/CONSTRAINTS blocks)
- Optional: patch/variant delta notes (if present)

---

## 1) TEST METHOD (DETERMINISTIC)
Run checks in order:

C1 — Required blocks present
- STYLE_BLOCK present
- STRUCTURE_BLOCK present (if full song)
- VOCAL_INTENT_BLOCK present (if vocals are specified as requirement)
- NEGATIVE_SPEC_BLOCK present
- CONSTRAINTS_BLOCK present (duration/format)

C2 — Section clarity
- If “full song”:
  - at least Verse + Chorus present
  - Chorus is explicitly labeled as hook/chorus
- If “loop/short”:
  - loop segment and hook intent is stated

C3 — Contradiction scan (lightweight)
Flag contradictions such as:
- “clean aggressive mix” AND “lo-fi muddy”
- “half-time stomp” AND “fast dnb breakcore” without dominance rule
- “minimal sparse arrangement” AND “dense wall of layers”
Rule:
- If conflicting specs exist, require dominance rule or remove one side.

C4 — Control density scan (overload)
Heuristic limits:
- more than ~14 “positive spec” lines OR
- more than ~14 negatives OR
- more than 3 separate genre labels
→ overload risk

C5 — Specificity where it matters
Must explicitly specify at least:
- one rhythm feel OR one primary groove descriptor
- one vocal plan (single or roles)
- one hook/chorus intent (explicit)

C6 — Anti-fantasy / authority discipline (pack-level)
- No URLs/PATH used as “authority” references in operational parts (if present)
- No claims like “this gate exists” without UID

---

## 2) PASS / REWORK / FAIL CRITERIA
PASS:
- C1 PASS
- C2 PASS
- C3 no unresolved contradictions
- C4 not overloaded (or overload justified with simplification note)
- C5 PASS

REWORK:
- missing one non-core block OR
- minor contradiction exists but fix is straightforward OR
- overload present but can be reduced by pruning

FAIL:
- missing core blocks (STYLE or NEGATIVES or CONSTRAINTS) OR
- multiple contradictions OR
- extreme overload (e.g., genre soup + long negatives) OR
- structure is absent for full song (no verse/chorus separation)

---

## 3) OUTPUT RECORD (COPY)
GATE_RESULT_RECORD:
- GATE_UID: UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- RESULT: PASS/REWORK/FAIL
- FAILED_CHECKS:
  - <C#>
- EVIDENCE (short):
  - <snippet>
- FIX DIRECTIONS:
  - <action>
- RECHECK:
  - rerun this gate after fix

---

## 4) FIX MAPPING (WHAT TO DO IF FAILS)
If C1 missing blocks:
- Fix: add missing block(s) using CORE WORKFLOW PB-01.

If C2 structure unclear:
- Fix: strengthen STRUCTURE_BLOCK; label chorus/hook explicitly.

If C3 contradictions:
- Fix: remove conflicting spec OR add dominance rule (“primary + touch”).

If C4 overload:
- Fix: prune to 3–6 anchors; cut negatives to top 8–12; remove inventory lists.

If C5 too vague:
- Fix: add explicit rhythm feel + vocal plan + hook intent.

Playbook mapping:
- Use PB-01 CORE WORKFLOW when multiple fixes needed.
- Use PB-04 PATCH MIN when single localized fix.

---

## 5) EXAMPLES (PLACEHOLDER)
(Replace with real examples from your catalog.)

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
- gate outcome is ignored inside a pipeline requiring it
- result is claimed without listing failed checks and evidence
- “fix” is non-actionable (“make it better”)

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.CORE.001 | WHY: builds contracts that pass this gate
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal fixes for REWORK
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.GATES.README.DRAFT.001 | WHY: gate map

--- END.
