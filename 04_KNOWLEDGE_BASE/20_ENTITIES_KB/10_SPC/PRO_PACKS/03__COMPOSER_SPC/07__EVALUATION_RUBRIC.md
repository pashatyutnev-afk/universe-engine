# 07__EVALUATION_RUBRIC — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/07__EVALUATION_RUBRIC.md
SCOPE: KB — SPC Pro Pack — Music Producer — Evaluation Rubric
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: EVALUATION_RUBRIC
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
OWNER: SPC (Music Producer)
ROLE: Scoring rubric (0–10) for producer outputs O1/O2; used by gates and regression guard.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Evaluation rubric initialized for Music Producer SPC pack."
- REASON: "Standardize pass thresholds and polish targets."
- IMPACT: "Enables deterministic PASS/REWORK decisions."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.RUBRIC.001

---

## SCORING RULES
- Score each dimension 0–10
- PASS guidance:
  - No dimension below 6
  - Average >= 7.0
- EXCELLENT guidance:
  - No dimension below 8
  - Average >= 8.5

If any dimension <=4 → REWORK (or FAIL if compliance).

---

## DIMENSIONS

### D1 — Clarity & executability (O1/O2)
0–3: vague, not runnable  
4–6: runnable but unclear in parts  
7–8: clear steps + testable criteria  
9–10: instantly runnable, minimal ambiguity

### D2 — Arrangement architecture (layers/roles)
0–3: no layer roles, generic wording  
4–6: partial layer roles, weak hierarchy  
7–8: clear foreground/mid/bed roles per section  
9–10: robust hierarchy + space plan for lead

### D3 — Energy curve & density planning
0–3: flat, no density strategy  
4–6: basic build notes, unclear peaks/dips  
7–8: section density map + perceivable arc  
9–10: strong peak/dip clarity + reset strategy

### D4 — Groove & rhythm system (intent)
0–3: “nice beat” only  
4–6: some role hints, not systematic  
7–8: drum/bass roles + groove identity + micro-variation rules  
9–10: groove identity stable across repeats/variants

### D5 — Hook support & readability
0–3: hook not protected, clutter risk  
4–6: hook exists, spotlight rule unclear  
7–8: spotlight window + lead space + reinforcement plan  
9–10: hook is unmissable, clean focus, minimal clutter

### D6 — Contrast & transitions plan
0–3: no contrast/transitions  
4–6: contrast exists but lever unclear  
7–8: explicit contrast lever + transition intents  
9–10: transitions reinforce arc, no accidental resets

### D7 — Variant discipline (if applicable)
0–3: variants rewrite everything  
4–6: partial discipline, anchors drift  
7–8: one lever per variant, anchors stable  
9–10: variant set is portfolio-safe + acceptance per variant

### D8 — Consistency & scope discipline
0–3: contradictions + scope takeover (engineering/prompt)  
4–6: minor drift, needs cleanup  
7–8: consistent terms, routing notes, no forbidden content  
9–10: clean handoffs + stable anchors across artifacts

### D9 — Validation trace & routing readiness
0–3: no trace, no rerun plan  
4–6: trace partial  
7–8: checklists + gates + one-axis patch plan present  
9–10: regression-ready trace + minimal rerun sets explicit

---

## SUMMARY OUTPUT FORMAT (MANDATORY)
When used, output:
- RUBRIC_UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- SCORES:
  - D1: _
  - D2: _
  - ...
  - D9: _
- AVG_SCORE: _
- DECISION_HINT:
  - PASS / REWORK / EXCELLENT
- TOP_ISSUES (max 3):
  - <dimension + reason>
- RECOMMENDED_AXIS (if REWORK):
  - <one axis>

---

## REQUIRED UID REFERENCES
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001
- REGRESSION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001

---
END
