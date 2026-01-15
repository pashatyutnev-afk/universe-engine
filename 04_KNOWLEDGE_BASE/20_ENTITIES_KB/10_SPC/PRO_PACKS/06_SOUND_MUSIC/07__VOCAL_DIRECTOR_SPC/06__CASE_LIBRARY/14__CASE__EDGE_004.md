# SPC PRO PACK — CASE (EDGE-004) — PRONUNCIATION / STRESS RISK ON P0 (PB-02 RISK NOTES) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/14__CASE__EDGE_004.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE.004.DRAFT.001
OWNER: SYSTEM
ROLE: EDGE case calibrating pronunciation/stress risk when a MUST-HEAR P0 target is a foreign name/term or stress-ambiguous token. Demonstrates PB-02 requirement: PRONUNCIATION_RISK_NOTES + non-meaning fixes (phonetic spacing) and phrase protection.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created EDGE-004: P0 includes pronunciation/stress risk token; requires PB-02 risk notes."
- REASON: "Pronunciation ambiguity causes inconsistent takes and intelligibility failures; must be addressed explicitly."
- IMPACT: "Stable pronunciation across takes; clearer must-hear delivery without rewriting meaning."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE004.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: EDGE-004
- TYPE: EDGE
- CONTEXT:
  - format: full song
  - language: RU (with foreign name token)
  - vocal_mode: melodic hook
  - tempo_feel: mid-tempo
  - note: Edge is pronunciation/stress ambiguity, not density.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook with foreign/stress-ambiguous token)
[Chorus / Hook]
Я зову тебя: “AURORA” — и свет внутри не гаснет,
Я держу маршрут — меня не согнут.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)

### 1.3 MUST-HEAR targets (P0)
MUST_HEAR_WORDS:
- P0: AURORA, маршрут, согнут
- P1: свет, внутри
- P2: (none)

MUST_HEAR_PHRASES:
- P0: "AURORA", "меня не согнут"
- P1: "свет внутри"

CLARITY_TARGETS:
- Target A: P0 understood on first listen in chorus/hook

---

## 2) EDGE CONDITION (PRONUNCIATION RISK)
Risk description:
- Token "AURORA" can be pronounced multiple ways (stress/phonetics vary).
- Inconsistent pronunciation across takes breaks repeatability and comping.
- If token is unclear, hook loses identity anchor.

---

## 3) PRONUNCIATION_RISK_NOTES (REQUIRED — PB-02 OUTPUT)
PRONUNCIATION_RISK_NOTES (anchor format):
- item: "AURORA"
  - risk:
    - pronunciation ambiguity (RU vs EN adaptation)
    - stress placement inconsistent across takes
  - why:
    - must-hear P0 token; inconsistency breaks recognition
  - non-meaning fixes (allowed):
    - decide ONE pronunciation form for all takes (record it as RULE)
    - use phonetic spacing in delivery (slight separation of syllables)
    - land final vowel/consonant clean; avoid swallow under lift
  - forbidden:
    - changing the token to a different word (meaning/identity change)

MUST_HEAR_PROTECTION_RULE:
- do not stack over "AURORA" attack
- do not insert breath inside token if sung as multi-syllable

---

## 4) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> REWORK (if pronunciation rule not defined) / PASS (if rule defined)
NOTE:
- This case teaches: pronunciation rules are required for stable intelligibility and repeatability.

---

## 5) FIX ROUTE
Primary:
- PB-02 MUST-HEAR WORDS PRIORITY:
  - produce PRONUNCIATION_RISK_NOTES
  - lock one pronunciation rule
Secondary (if still unclear in delivery):
- PB-03 (intelligibility repair) to adjust articulation/timing on the token.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
