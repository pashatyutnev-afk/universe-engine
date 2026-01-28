# 04__CASE__EDGE_001 — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/04__CASE__EDGE_001.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case (EDGE)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 06__CASE_LIBRARY
DOC_TYPE: CASE
CASE_TYPE: EDGE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001
OWNER: SPC (Music Producer)
ROLE: Edge-case calibration for conflicting constraints + variants + routing discipline.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "EDGE case initialized for Music Producer SPC pack."
- REASON: "Test constraint conflict handling + identity anchors + routing without scope drift."
- IMPACT: "Defines pass behavior under conflicting requirements."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASE.EDGE.001

---

## INTENT
Крайний кейс, где легко сломаться:
- одновременно просят “вокал супер читаемый” и “максимально плотный саунд”
- нужно 2–3 варианта (short loop / full / instrumental)
- есть ограничение “не трогай промпты/инженерию” (отдельные роли)

Цель кейса:
- показать дисциплину: identify conflict → выбрать стратегию → описать тесты → routing notes.

---

## INPUTS (EDGE)
- TASK_GOAL:
  - "Сделай трек для клипа и для shorts одновременно."
- CONSTRAINTS:
  - hook by 0:10
  - very dense “wall” sound
  - vocal must be intelligible on phone
  - need variants:
    - V1: 15s hook loop
    - V2: full track
    - V3: instrumental
- ROLE_SPLIT:
  - Prompt Architect does final prompts
  - Mix Engineer handles technical mixing

---

## OUTPUT (EDGE-PASS EXEMPLAR)

### O1 — PRODUCER_TASK_CARD (EDGE VERSION)
- GOAL:
  - "Сделать плотный трек с ранним хуком и сохраняемой читаемостью вокала; подготовить 3 варианта."
- DELIVERABLES:
  - O2 production exec plan
  - O3 variants plan (3 variants)
  - routing notes for Prompt/Mix roles
- CONSTRAINTS (explicit):
  - C1: hook <= 0:10
  - C2: density high
  - C3: vocal intelligible on phone
  - C4: variants V1/V2/V3
- CONFLICT FLAG (explicit):
  - "C2 vs C3 конфликт: плотность может съесть читаемость"
- ACCEPTANCE (testable):
  - A1: hook узнаётся <=10s (blind recall test)
  - A2: must-hear phrase читается на phone speaker
  - A3: плотность сохраняется, но lead остаётся “front”
  - A4: variants не ломают identity anchors
- SCOPE:
  - producer decisions only
  - no engineering recipes, no prompt authoring takeover
- ROUTING:
  - Prompt compilation → Prompt Architect
  - Mix translation & loudness targets → Mix Engineer (no numbers here)

### O2 — PRODUCTION_EXEC_PLAN (CONFLICT-AWARE)

#### A) Conflict resolution strategy
- Strategy S:
  - keep density, but enforce “lead clarity window”:
    - in hook, reserve micro-space around must-hear phrase by arrangement decisions:
      - reduce mid-layer density during phrase
      - avoid competing transient elements on the same beats
  - note: this is arrangement-level, not EQ recipe.

#### B) Section map (timed for both formats)
- S1: 0:00–0:05 setup motion
- S2: 0:05–0:20 Hook A (must-hear phrase appears by 0:10)
- S3: 0:20–0:45 Drive/Verse (dense but controlled)
- S4: 0:45–1:05 Hook B (ONE lever change)
- S5: 1:05–1:20 Break (contrast drop)
- S6: 1:20–1:55 Final Hook (peak density, controlled windows)
- S7: 1:55–2:05 Outro

#### C) Arrangement / Seat plan with "clarity windows"
- Foreground:
  - lead + hook motif
- Mid:
  - main groove stack (drums/bass)
- Background:
  - texture wall
- Clarity window rule:
  - during must-hear phrase: reduce competing mid textures by arrangement choice
  - outside phrase: density can return

#### D) Variant anchors (identity)
- Identity anchors (must not change):
  - hook motif
  - core groove pattern
  - lead character (type/role)
- Allowed changes:
  - duration and section selection
  - background texture density
  - small lever change per variant (not multiple)

#### E) Variant plan (O3 preview)
- V1 Hook Loop 15s:
  - use S2 (0:05–0:20) cut to 0:15 loop-ready
  - keep anchors, simplify background tails for clean loop
- V2 Full:
  - full structure as above
- V3 Instrumental:
  - keep hook motif transferred to lead synth
  - ensure hook still recognizable <=10s (no vocal)

#### F) Validation route + edge gate use
- CHK-READINESS → CHK-QUALITY → CHK-COMPLIANCE
- GATE-CORE_QUALITY → GATE-CONSISTENCY
- EDGE:
  - run EDGE gate for conflict/variants discipline
  - if FAIL → PB-02 one-axis repair (axis=variants or compliance)

#### G) Routing notes (no takeover)
- Prompt Architect:
  - needs: section map + hook placement + identity anchors + variant rules
- Mix Engineer:
  - needs: “clarity window” intent + phone intelligibility as acceptance test
  - (no numeric loudness instructions here)

---

## EDGE FAIL MODES (WHAT THIS CASE PREVENTS)
- solving conflict by engineering recipes (forbidden)
- ignoring conflict (density kills vocal) and hoping it works
- variants that drift identity anchors
- multi-axis chaotic changes

---

## RUBRIC (ROUGH SCORES)
- D1 Clarity: 8
- D2 Scope: 9
- D3 Structure: 8
- D4 Seat plan: 8
- D5 Performance notes: 7
- D6 Constraints fit: 9
- D7 Validation/trace: 8
- D8 Consistency: 8
- D9 Variants: 9

OVERALL: PASS (EDGE)

---

## REQUIRED UID REFERENCES
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- EDGE GATE:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001

---
END
