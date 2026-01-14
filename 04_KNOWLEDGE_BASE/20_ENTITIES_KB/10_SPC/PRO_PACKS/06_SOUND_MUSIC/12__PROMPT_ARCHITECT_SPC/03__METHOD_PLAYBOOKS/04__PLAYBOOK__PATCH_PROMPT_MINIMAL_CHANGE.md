# PLAYBOOK — PATCH PROMPT (MINIMAL CHANGE) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/04__PLAYBOOK__PATCH_PROMPT_MINIMAL_CHANGE.md

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
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001
OWNER: SYSTEM
ROLE: Deterministic minimal-change patch method: modify baseline prompt with smallest possible delta to fix one issue while preserving identity. Includes rollback discipline, patch templates, and recheck criteria.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created minimal-change patch playbook: delta rules, patch templates, rollback, and recheck promotion discipline."
- REASON: "Most failures should be fixed with small deltas; large rewrites destroy learning and identity."
- IMPACT: "Higher stability and faster convergence to PASS."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.PATCH.001

---

## 0) INPUTS (REQUIRED)
- BASELINE_PROMPT_CONTRACT (frozen text)
- SINGLE_PRIMARY_ISSUE (one issue only)
- FAILED_CRITERION_UID (preferred, UID-only) OR observable symptom
- PATCH_BUDGET:
  - max 1–3 line edits
- RECHECK_UIDS (UID-only) (if available)

If more than one primary issue exists:
- do not patch; use DIAGNOSE & REWORK first.

---

## 1) OUTPUTS
- PATCH_PROMPT (delta instructions)
- PATCHED_PROMPT_CONTRACT (baseline + delta)
- RECHECK_MINI
- PATCH_LOG (what changed and why)

---

## 2) WHEN TO USE / WHEN NOT TO USE
USE WHEN:
- output is close to PASS and fails one dimension (voice sameness OR repetition OR hook weak OR clutter)
- baseline identity is good and must be preserved

DO NOT USE WHEN:
- baseline is contradictory/overloaded
- multiple critical fails exist
- structure is missing (no chorus identity)
→ use CORE WORKFLOW or DIAGNOSE.

---

## 3) DELTA RULES (ABSOLUTE)
D1 — Preserve 90% of baseline text
- Only change the smallest block necessary.

D2 — One axis only
- Patch targets one axis (hook OR vocals OR repetition OR drift OR clutter OR feel OR mud).

D3 — Max edits
- add/replace ≤ 3 lines OR ≤ 12 words per line change (heuristic).

D4 — No block reshuffle
- Keep block order identical.
- Do not rewrite the whole contract.

D5 — Always include recheck
- Define what to verify post-generation.

Rollback rule:
- If patch introduces new critical fail → revert to baseline immediately.

---

## 4) PATCH TEMPLATES (COPY)
### Template A — Hook weak / chorus unclear
PATCH_PROMPT:
- Keep everything the same.
- Update STRUCTURE_BLOCK:
  - Explicitly label CHORUS as HOOK.
  - Add: "Hook is clear and appears early; chorus distinct from verses."
- Optional negative:
  - "avoid verse-like chorus; avoid monotone dynamics"
RECHECK:
- hook clarity
- chorus distinctness

### Template B — Same singer syndrome
PATCH_PROMPT:
- Keep everything the same.
- Update VOCAL_INTENT_BLOCK:
  - Add explicit role ownership per section (A verses, B chorus).
  - Add contrast principles (range/timbre/attack).
- Add targeted negative:
  - "avoid identical vocal timbre across sections"
RECHECK:
- voice contrast across sections
- chorus lead difference

### Template C — Repetition in verses
PATCH_PROMPT:
- Keep everything the same.
- Update NEGATIVE_SPEC_BLOCK:
  - Add: "avoid repeating the same lines/phrases in verses"
- Update STRUCTURE_BLOCK:
  - Add: "verses must use varied phrasing; repetition only in chorus"
RECHECK:
- verse novelty
- repetition limited to chorus

### Template D — Style drift / random fusion
PATCH_PROMPT:
- Keep everything the same.
- Update STYLE_BLOCK:
  - Reduce anchors to 3–4.
  - Add dominance rule: "primary genre dominates; secondary is a subtle touch".
  - Remove conflicting adjectives.
RECHECK:
- style fingerprint present
- no “random mix” feeling

### Template E — Too busy / clutter
PATCH_PROMPT:
- Keep everything the same.
- Update STYLE_BLOCK or CONSTRAINTS:
  - reduce texture density (fewer glitch/stutter)
  - specify synth role: support not lead (or vice versa) — one line only
- Add negative:
  - "avoid excessive stutter edits / overlayering"
RECHECK:
- clarity
- hook still dominant

### Template F — Muddy low end (principle-level)
PATCH_PROMPT:
- Keep everything the same.
- Update CONSTRAINTS:
  - "tight low end; avoid muddy sub; clean aggressive mix"
- Add negative:
  - "avoid uncontrolled sub-bass"
RECHECK:
- low end clarity (subjective but observable in listening)

---

## 5) PATCH LOG (COPY)
PATCH_LOG:
- PATCH_UID: PATCH-YYYYMMDD-001
- BASELINE_ID:
- PRIMARY_ISSUE:
- FAILED_CRITERION_UID (UID-only):
- AXIS:
- DELTA (exact lines changed):
- EXPECTED EFFECT:
- RECHECK_UIDS (UID-only):
  - <uid>
- RESULT: PASS/REWORK/FAIL
- ROLLBACK_USED: YES/NO
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO

---

## 6) PROMOTION RULE (NEW BASELINE)
If patch passes recheck and does not introduce new critical fails:
- promote to BASELINE_NEXT
- record axis changed + evidence

If patch fails:
- rollback
- run DIAGNOSE & REWORK with evidence

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- patch changes multiple axes
- patch rewrites most of the prompt
- patch applied without baseline freeze
- no recheck defined
- patch success claimed without evidence

---

## 8) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001 | WHY: multi-issue failures need diagnosis playbook
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.ONE_AXIS.001 | WHY: variants for learning after patch
- UE.KB.VAL.STD.CONNECTOR.001 | WHY: criterion-anchored fixes
- UE.KB.QA.STD.CONNECTOR.001 | WHY: recheck discipline

--- END.
