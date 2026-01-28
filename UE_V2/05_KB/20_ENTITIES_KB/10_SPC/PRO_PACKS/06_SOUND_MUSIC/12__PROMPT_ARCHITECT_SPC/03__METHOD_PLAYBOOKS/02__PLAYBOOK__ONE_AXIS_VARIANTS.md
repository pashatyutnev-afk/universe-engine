# PLAYBOOK — ONE-AXIS VARIANTS (A/B LEARNING) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/02__PLAYBOOK__ONE_AXIS_VARIANTS.md

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
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.ONE_AXIS.001
OWNER: SYSTEM
ROLE: Deterministic playbook to produce controlled prompt variants that change exactly one axis at a time, enabling learning and QA convergence without identity drift.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created one-axis variants playbook: axis taxonomy, baseline lock, variant log, and comparison procedure."
- REASON: "Without controlled variants, iteration becomes random and you can't learn what fixed the problem."
- IMPACT: "Faster convergence and less drift/collision."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.ONEAXIS.001

---

## 0) INPUTS (REQUIRED)
- BASELINE_PROMPT_CONTRACT (the current best prompt)
- PRIMARY_GOAL (what we try to improve)
- AXIS_CANDIDATES (choose 1–3)
- VARIANT_COUNT (2–5)

If baseline is not stable:
- do not variant; run CORE WORKFLOW or PATCH first.

---

## 1) OUTPUTS
- VARIANT_SET (V1..Vn) where each variant changes only one axis
- VARIANT_LOG (what changed, why, expected effect)
- COMPARISON_MINI (how to decide winner)

---

## 2) AXIS TAXONOMY (CANON)
You may only change one axis per variant.

AXIS_LIST:
- AX1 HOOK EMPHASIS
  - earlier/clearer hook, chorus distinctness, hook density

- AX2 VOCAL CONTRAST
  - role separation, delivery mode constraints, call/response

- AX3 REPETITION CONTROL
  - verse novelty constraints, negative specs vs repeats

- AX4 STYLE FINGERPRINT
  - anchor markers, dominance rule, reduce clutter/drift

- AX5 TEXTURE INTENSITY
  - glitchiness / industrial hits density / synth role intensity

- AX6 RHYTHM FEEL
  - half-time vs driving, groove emphasis (without changing genre)

- AX7 MIX INTENT (principles)
  - tighten low end, reduce mud, dynamic clarity (principle-level only)

Rule:
- If you change AX4 style fingerprint, do not also change AX6 rhythm feel in same variant.

---

## 3) METHOD (DETERMINISTIC)
### Step 1 — Lock baseline (no silent edits)
- Name baseline: BASE_V0
- Freeze it (copy it exactly).
- If you notice a baseline issue: stop and make a PATCH playbook first.

### Step 2 — Choose variant design plan
- Select 2–5 variants:
  - each variant picks exactly one axis from AXIS_LIST
- Ensure coverage:
  - at least 1 variant targets the primary failure
  - others explore near-neighbor axes

### Step 3 — Apply axis change (minimal delta)
For each variant:
- keep all blocks identical except:
  - the axis block you modify
- keep changes small:
  - add/replace 1–3 lines max in a block
  - do not rewrite the whole block

### Step 4 — Write expectation statement
For each variant:
- “If this works, we should hear/see: <observable>”

### Step 5 — Run comparison mini-check
After generating outputs:
- score quick criteria:
  - hook clarity
  - chorus distinctness
  - vocal separation
  - repetition control
  - style consistency
Pick:
- WINNER (best overall)
- KEEPERS (2nd best for other goals)
- LOSERS (what failed)

### Step 6 — Promote winner to new baseline
- BASE_V1 = WINNER variant
- record: which axis changed + what it improved

---

## 4) VARIANT LOG TEMPLATE (COPY)
VARIANT_LOG:
- BASELINE_ID: BASE_V0
- DATE: YYYY-MM-DD
- PRIMARY_GOAL:
- VARIANTS:
  - V1:
    - AXIS: AX?
    - CHANGE (delta):
    - EXPECTED EFFECT:
    - RESULT (after gen):
    - DECISION: WINNER / KEEPER / LOSER
  - V2:
    - AXIS:
    - CHANGE:
    - EXPECTED:
    - RESULT:
    - DECISION:
- NEW_BASELINE:
  - BASE_V1 = <V?>
  - WHY:

---

## 5) COMPARISON MINI (FAST)
COMPARISON_MINI:
- [ ] Hook is identifiable quickly
- [ ] Chorus feels distinct
- [ ] Voices feel different (if multi-voice)
- [ ] Verses are not repetitive
- [ ] Style markers remain consistent
- [ ] No new obvious artifacts introduced

Decision rule:
- If a variant improves primary goal but breaks identity → KEEPER, not WINNER.
- WINNER must improve without introducing critical new fails.

---

## 6) COMMON FAIL MODES (AND FIXES)
F1 — Variants accidentally change multiple axes
- Fix: enforce “delta block only”; compare baseline and variant text line-by-line.

F2 — Changes are too big to learn from
- Fix: reduce delta to 1–3 lines.

F3 — No clear winner
- Fix: run second round focusing only on primary axis with smaller deltas.

---

## 7) TRACE (MINIMUM)
TRACE_NOTES:
- BASELINE_ID:
- AXES_TESTED:
- WINNER_AXIS:
- NEW_BASELINE_ID:
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO
- GAPS (missing criteria uids):

--- END.
