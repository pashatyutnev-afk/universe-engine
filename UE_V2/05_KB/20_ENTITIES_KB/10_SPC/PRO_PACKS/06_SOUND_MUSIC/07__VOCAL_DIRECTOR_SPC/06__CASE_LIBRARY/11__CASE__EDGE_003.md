# SPC PRO PACK — CASE (EDGE-003) — CHORUS LIFT CONFLICTS WITH INTELLIGIBILITY (PB-05 + PB-03) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/11__CASE__EDGE_003.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE.003.DRAFT.001
OWNER: SYSTEM
ROLE: EDGE case calibrating the conflict between chorus lift (arc/contrast) and P0 intelligibility. Demonstrates that a valid arc concept can still require REWORK when lift levers mask must-hear words. Fix route requires coordinated minimal changes: PB-05 (arc lever pruning/rebalance) + PB-03 (intelligibility repair directives).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created EDGE-003: chorus lift conflicts with intelligibility; requires PB-05 + PB-03."
- REASON: "Teaches boundary: lift must not be achieved by sacrificing P0 clarity; otherwise arc gate must REWORK."
- IMPACT: "Prevents ‘big chorus, unreadable hook’ failure pattern; enforces intelligibility-first while keeping lift."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE003.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: EDGE-003
- TYPE: EDGE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus with aggressive lift attempt
  - tempo_feel: mid-tempo
  - note: Edge is the conflict: lift lever choice masks P0.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook)
[Chorus / Hook]
Поме́хи в голове — но я вижу маршрут,
Поме́хи в душе — но меня не согнут.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)
- Final Chorus (HOOK)

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут
- P1: вижу
- P2: (optional) помехи

MUST_HEAR_PHRASES:
- P0: "вижу маршрут", "не согнут"

CLARITY_TARGETS:
- Target A: P0 understood on first listen in chorus/hook
- Target B: chorus clarity >= verse clarity

---

## 2) BASELINE_DIRECTION_PACK (CONFLICT VERSION)
### 2.1 ARC intent (good)
- Verse: restrained baseline
- Chorus: strong lift (release)

### 2.2 CONTRAST_LEVERS (bad combination that creates conflict)
Lever L1 — ENERGY/INTENSITY:
- Verse: 55
- Chorus: 85

Lever L2 — DELIVERY MODE:
- Verse: clean-aggressive
- Chorus: aggressive/shout + heavy grit (applied across full lines)

Problem:
- L2 applied globally on chorus lines causes consonant masking on P0 words (маршрут/согнут).

### 2.3 Observed failure (textual observation)
FAILURE OBSERVATION:
- In lifted chorus delivery, listener cannot understand P0 on first listen:
  - "маршрут" becomes blur ("...рут")
  - "согнут" loses final consonant ("...ну")

---

## 3) FAILURE_MAP (EDGE EVIDENCE) — PB-03 STYLE
FAILURE_MAP:
- target: "маршрут" (P0)
  - where: Chorus-L1
  - symptom: consonant loss under grit/shout lift
  - severity: S0
  - types: T5 (masking by delivery) + T1 (consonant loss)
- target: "согнут" (P0)
  - where: Chorus-L2
  - symptom: final consonant swallowed at peak intensity
  - severity: S0
  - types: T5 + T1

---

## 4) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> REWORK
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001 -> REWORK

Why G5 is REWORK (not PASS):
- lift exists, but it violates intelligibility preservation requirement for P0 (bad trade).

---

## 5) WHY (EDGE LOGIC)
- Arc “lift” is correct in concept, but lever selection is unsafe:
  - using DELIVERY MODE as global chorus lever masks P0
- Therefore:
  - We must keep lift while shifting levers to clarity-safe choices.

---

## 6) FIX ROUTE (PB-05 + PB-03) — MINIMAL, TRACEABLE
### 6.1 PB-05 (Arc/Contrast rebalance) — reduce conflict
Goal:
- Keep chorus lift but make it intelligibility-safe.

Minimal patch (example):
- Keep L1 ENERGY/INTENSITY lift (Verse 55 → Chorus 80–85)
- Replace L2 DELIVERY MODE (global shout/grit) with L3 ARTICULATION FOCUS for P0:
  - Chorus: consonant-forward on P0 phrases
  - Grit allowed only outside P0 attacks (localized, not global)

Result:
- lever_count remains <=3
- lift remains audible
- P0 becomes protectable

### 6.2 PB-03 (Intelligibility repair directives) — targeted fixes
REPAIR_DIRECTIVES (no lyric change):
- target: маршрут
  - directive: reduce grit ONLY on the “марш-рут” attack; land “р/ш/т” clearly; shorten vowel before final consonant
  - pass_test: understood on first listen in chorus
- target: согнут
  - directive: land final “т” clean; avoid growl on last consonant; keep lift via energy not via consonant-masking
  - pass_test: understood on first listen in chorus

UPDATED_INTELLIGIBILITY_GATES (must become YES):
- Gate A (P0 first listen): YES
- Gate D (consonant attacks protected): YES

### 6.3 Optional: PB-08 (one-axis patch discipline)
If patching needs iteration:
- AXIS=A2 first (arc lever rebalance)
- then AXIS=A1 (intelligibility)
Never change multiple axes in one patch.

---

## 7) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
