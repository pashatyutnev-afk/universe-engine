# SPC PRO PACK — CASE (EDGE-001) — FAST DENSITY TRAP (PB-04 ESCALATION) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/04__CASE__EDGE_001.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE.001.DRAFT.001
OWNER: SYSTEM
ROLE: EDGE case calibrating singability failures under fast, dense rap delivery. Demonstrates density scan + breath policy + escalation note (no lyric rewrite). Primary fix route: PB-04.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created EDGE-001: fast rap density trap; breath breaks would split P0; requires PB-04 escalation discipline."
- REASON: "Edge conditions teach the boundary where performance fixes stop working and lyric/structure revisions must be requested."
- IMPACT: "Prevents impossible takes and protects intelligibility-first policy."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE001.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: EDGE-001
- TYPE: EDGE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: fast rap verse + melodic hook
  - tempo_feel: fast delivery over half-time beat (dense 16ths feel)
  - note: The verse line density is intentionally extreme.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (dense verse line + hook reference)
[Verse (dense line — focus)]
Я выхожу из себя без “призов”, выключаю чужие замки, перезапущу этот старый обман, пока не верну себе главный сигнал.

[Hook reference]
Я возвращаюсь к своему.

### 1.2 Structure labels
STRUCTURE:
- Intro
- Verse 1 (FAST RAP)
- Chorus (HOOK)
- Verse 2
- Chorus
- Outro

### 1.3 MUST-HEAR targets (P0)
MUST_HEAR_WORDS:
- P0: перезапущу, верну, главный, сигнал
- P1: выключаю, замки, обман
- P2: (optional) призов

MUST_HEAR_PHRASES:
- P0: "верну себе главный сигнал"
- P1: (N/A)

CLARITY_TARGETS:
- Target A: P0 phrase understood on first listen in Verse (FAST RAP)
- Target B: No breath split inside P0 phrase

---

## 2) BASELINE_DIRECTION_PACK (SHORT)
### 2.1 Delivery intent
- Verse: high-speed articulation, consonant-forward on P0 phrase
- Hook: clean lift, P0 clarity preserved

### 2.2 Singability risk statement (the edge)
- The verse line contains multiple clauses with no natural breath points.
- Any breath inserted inside the P0 phrase (“верну себе главный сигнал”) destroys intelligibility.

---

## 3) DENSITY_SCAN + BREATH_POLICY (EDGE EVIDENCE)
DENSITY_SCAN:
- line_id: Verse1-L1
  - contains_P0: YES (P0 phrase embedded)
  - flags: long phrase, multiple consonant clusters, clause chain, fast delivery implied
  - risk_level: R2 (unsingable-risk)
  - evidence: breath would be forced inside P0 phrase at realistic delivery speed

MUST_HEAR_PROTECTION_RULES:
- never split P0 phrase: "верну себе главный сигнал"
- protect consonant attacks on: верну / главный / сигнал

BREATH_POLICY:
- allowed:
  - breath BEFORE the clause that contains P0 phrase
  - breath AFTER the full P0 phrase completes
- forbidden:
  - any breath between "верну" and "сигнал" (inside P0 phrase)

---

## 4) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001 -> REWORK (or FAIL depending on actual constraints)
NOTE:
- This case is designed to teach the boundary: performance fixes may not be sufficient; escalation may be required.

---

## 5) WHY (EDGE LOGIC)
- G1 PASS: inputs exist (lyrics/structure/language context).
- G2 PASS: P0 targets are short and phrase promoted.
- G6 triggers REWORK/FAIL risk:
  - density scan flags R2 unsingable-risk
  - breath cannot be placed safely at tempo without harming P0 phrase
- Therefore:
  - PB-04 must be applied to decide FIX vs ESCALATE.

---

## 6) FIX ROUTE (PB-04) — DECISION
Apply PB-04:

Fix attempt (performance-safe) is limited to:
- grouping the line into chunks WITHOUT word changes
- moving breath BEFORE the clause containing P0 phrase
- articulation emphasis on P0 consonants

If still failing (likely at extreme tempo):
- ESCALATE to Lyricist/Songwriter (no rewrite inside pack)

ESCALATION_NOTES (anchor):
- owner: Lyricist/Songwriter
- line_id: Verse1-L1
- problem: "unsingable density at rap speed; P0 phrase intelligibility fails unless breath splits inside P0"
- constraint: "preserve meaning intent; keep P0 phrase concept and key words"
- request:
  - "split into two lines OR shorten clause chain before P0 phrase"
  - "reduce consonant clusters immediately before P0 phrase"
- must_keep:
  - P0 words: перезапущу / верну / главный / сигнал
  - phrase intent: "верну себе главный сигнал" (core message)

---

## 7) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
