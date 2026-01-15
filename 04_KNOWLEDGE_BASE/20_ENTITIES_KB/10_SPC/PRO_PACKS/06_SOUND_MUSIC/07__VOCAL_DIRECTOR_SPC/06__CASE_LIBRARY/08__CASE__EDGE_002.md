# SPC PRO PACK — CASE (EDGE-002) — AGGRESSIVE DELIVERY MASKS P0 (G3 REWORK / G4 REWORK) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/08__CASE__EDGE_002.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE.002.DRAFT.001
OWNER: SYSTEM
ROLE: EDGE case calibrating the boundary where aggressive delivery mode masks consonants and breaks P0 intelligibility. Demonstrates diagnose + one-axis patch routing: PB-03 (repair) and PB-08 (axis A1/A4).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created EDGE-002: aggressive delivery masks P0; requires intelligibility repair and/or delivery profile patch."
- REASON: "Extreme vocal modes frequently destroy intelligibility; pack needs an edge reference for correct, minimal, traceable fixes."
- IMPACT: "Prevents ‘scream through hook’ failures and preserves must-hear targets."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE002.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: EDGE-002
- TYPE: EDGE
- CONTEXT:
  - format: full song / hook-driven
  - language: RU
  - vocal_mode: aggressive (distorted/shout) on chorus
  - tempo_feel: mid-tempo
  - note: The edge is the delivery mode, not text density.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook)
[Chorus / Hook]
Я вижу маршрут —
Но меня не согнут.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут
- P1: вижу
- P2: (none)

MUST_HEAR_PHRASES:
- P0: "вижу маршрут", "не согнут"

CLARITY_TARGETS:
- Target A: P0 understood on first listen in chorus/hook
- Target B: chorus clarity >= verse clarity

---

## 2) BASELINE_DIRECTION_PACK (BAD EDGE VERSION)
### 2.1 Delivery profile (problematic)
delivery_principles:
- "максимально агрессивно в припеве, пусть звучит грязно"
- "чем больше хрип/дисторшн, тем лучше"
forbidden_styles:
- (missing)

Problem:
- This profile directly encourages masking consonants on P0 targets and is not coherence-safe.

### 2.2 Observed failure (textual observation)
FAILURE OBSERVATION:
- Listener hears “...рут” / “...нут” blur; cannot distinguish “маршрут” and “согнут” on first listen.

---

## 3) FAILURE_MAP (EDGE EVIDENCE) — PB-03 STYLE
FAILURE_MAP:
- target: "маршрут" (P0)
  - where: Chorus-L1
  - symptom: consonant loss / vowel smear under aggressive mode
  - severity: S0 (P0 not understood)
  - types: T5 (masking by delivery) + T1 (consonant loss)
- target: "согнут" (P0)
  - where: Chorus-L2
  - symptom: final consonant swallowed
  - severity: S0
  - types: T5 + T1

---

## 4) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> REWORK
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001 -> REWORK
NOTE:
- Not FAIL because a minimal patch can fix it without rewriting lyrics or structure.

---

## 5) WHY (EDGE LOGIC)
- Targets exist (G2 assumed PASS).
- Intelligibility fails because delivery mode masks consonants (T5).
- Delivery profile is not coherence-safe (encourages masking; forbidden list missing).
- Therefore: fix must be one-axis:
  - axis A1 (Intelligibility repair) OR
  - axis A4 (Delivery profile patch)
Prefer A1 first; if profile still contradicts clarity, patch A4.

---

## 6) FIX ROUTE (MINIMAL, TRACEABLE)
### Option 1 — PB-03 (Intelligibility repair) — ONE AXIS = A1
REPAIR_DIRECTIVES (no lyric change):
- target: маршрут
  - directive: reduce distortion ONLY on the P0 attack; land “р/ш/т” clearly; shorten vowel before final consonant
  - pass_test: P0 understood on first listen
- target: согнут
  - directive: land final “т” clean; avoid growl on last consonant; keep aggression on surrounding syllables

UPDATED_INTELLIGIBILITY_GATES:
- Gate A: P0 understood first listen (must become YES)

### Option 2 — PB-08 axis A4 (Delivery profile coherence patch)
PATCH_V1 (minimal):
- change: replace “грязно любой ценой” with “агрессия сохраняется, но P0 атаки — clean and consonant-forward”
- add forbidden_styles:
  - “heavy distortion on P0 words”
  - “vowel-only chorus”
Expected effect:
- keep aggression, restore consonant clarity on must-hear words

After patch:
- rerun G3 + G4.

---

## 7) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
