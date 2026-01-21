# 01__CASE__GOOD — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/01__CASE__GOOD.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case (GOOD)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 06__CASE_LIBRARY
DOC_TYPE: CASE
CASE_TYPE: GOOD
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.GOOD.001
OWNER: SPC (Music Producer)
ROLE: Calibration anchor for PASS-quality producer outputs.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "GOOD case initialized for Music Producer SPC pack."
- REASON: "Provide a concrete PASS exemplar."
- IMPACT: "Defines what O1/O2 should look like at 8+ quality."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASE.GOOD.001

---

## INTENT
Показать “как выглядит PASS” для типовой задачи продюсера:
- есть ясный O1 (task card)
- есть исполнимый O2 (production exec plan)
- есть validation route + trace
- нет инженерных рецептов и role mixing

---

## INPUTS (MINIMAL)
- TASK_GOAL: "Сделать трек для энергичного ролика (shorts), с сильным hook в первые 8–12 секунд."
- CONSTRAINTS:
  - duration target: ~1:40–2:10
  - hook early
  - high energy, clean vocal intelligibility target
- PLATFORM_INTENT: short-form friendly
- SCOPE_NOTE: prompt authoring handled by Prompt Architect

---

## OUTPUT (EXEMPLAR)

### O1 — PRODUCER_TASK_CARD
- GOAL:
  - "Сделать энергичный трек с ранним хуком, пригодный для нарезок/лупов."
- DELIVERABLES:
  - O2 production plan (sections + arrangement + take notes + acceptance)
  - variant note: short hook loop (optional)
- CONSTRAINTS:
  - hook by 0:12
  - clear lead element (vocal or lead synth) must be readable
  - avoid overcrowding in hook section
- ACCEPTANCE (MIN):
  - hook recognized within 10s
  - lead intelligible over instrumental
  - sections have contrast (energy dips/peaks)
- SCOPE:
  - IN-SCOPE: plan + direction
  - OUT-OF-SCOPE: final prompts, mix recipes, legal
- ROUTING:
  - Prompt → Prompt Architect (UID in real run)
  - Mix translation QA cue → Mix Engineer (UID in real run)

### O2 — PRODUCTION_EXEC_PLAN

#### A) Section Map (time/intent)
- S1: Intro (0:00–0:06) — immediate motion, setup hook
- S2: Hook A (0:06–0:22) — primary hook, minimal overcrowding
- S3: Verse/Drive (0:22–0:46) — groove + space for lead clarity
- S4: Hook B (0:46–1:02) — variation (1 lever change)
- S5: Bridge/Break (1:02–1:16) — contrast drop, reset tension
- S6: Final Hook (1:16–1:55) — peak energy, layered but controlled
- S7: Outro (1:55–2:00) — clean tail

#### B) Dynamics Arc
- Peak targets: S2 and S6
- Contrast lever: density drop at S5, then rebuild
- Hook difference: Hook B changes ONE lever (e.g., harmony lift or rhythm chop), not everything

#### C) Arrangement / Seat Plan (decision-level)
- Foreground:
  - Lead (vocal or lead synth): owns hook phrase, must remain readable
- Mid:
  - Rhythm backbone: drums + bass groove; keep consistent through S2/S3
- Background:
  - textures/pads: support, do not mask consonant attacks
- Masking risks:
  - If lead loses clarity in S2: reduce mid density or simplify texture layer (not “EQ at 3k”)

#### D) Hook Targets (must-hear)
- Must-hear phrase (concept):
  - short, repeatable, 3–6 words or 1–2 melodic motifs
- Test cue:
  - “If listener can hum/quote after 10 seconds → pass hook test”

#### E) Performance / Take Direction
- Delivery:
  - high energy but tight articulation on hook
  - avoid slurred consonants in must-hear phrase
- Phrasing:
  - leave micro-gaps after hook phrase for punch
- Takes:
  - record 2 takes: “tight/clean” and “aggressive/raspy” (if style allows)

#### F) Take Acceptance Criteria
- PASS if:
  - must-hear phrase is intelligible on phone speaker
  - hook phrase feels “front” without fighting drums
- REWORK if:
  - consonants disappear in hook
  - lead buried by mid textures
  - section contrast absent (flat energy)

#### G) Variant Plan (optional)
- Variant V1: “Hook Loop 15s”
  - Use Hook A + small tail for loop
  - Keep identity anchors unchanged (lead motif + groove)

#### H) Validation Route (UID-only in real run)
- CHK-READINESS → CHK-QUALITY → CHK-COMPLIANCE
- GATE-CORE_QUALITY → GATE-CONSISTENCY
- If variant present → re-run CONSISTENCY

#### I) Minimum Trace
- TASK_ID: EXAMPLE.MPROD.GOOD.001
- OUTPUTS: O1,O2,(O3)
- VALIDATIONS:
  - CHK-READINESS: PASS
  - CHK-QUALITY: PASS
  - CHK-COMPLIANCE: PASS
  - GATE-CORE: PASS
  - GATE-CONSISTENCY: PASS
- NEXT_ACTION:
  - handoff to Prompt Architect for prompt compilation
  - run test render and return results for PB-02 loop if needed

---

## RUBRIC (ROUGH SCORES)
- D1 Clarity: 9
- D2 Scope: 9
- D3 Structure: 8
- D4 Seat plan: 8
- D5 Performance notes: 8
- D6 Constraints fit: 8
- D7 Validation/trace: 9
- D8 Consistency: 9
- D9 Variants: 8 (if used)

---

## WHY THIS CASE EXISTS
- Показывает “decision-level” продюсера без инженерных рецептов.
- Показывает как делать hook план тестируемым.
- Показывает как оформлять acceptance и routing.

---
END
