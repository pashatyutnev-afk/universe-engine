# SPC PRO PACK — CASE (GOOD-004) — BREATH/SINGABILITY PASS ANCHOR (G6) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/16__CASE__GOOD_004.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD.004.DRAFT.001
OWNER: SYSTEM
ROLE: GOOD case anchor for calibrating Gate G6 BREATH/SINGABILITY as PASS. Demonstrates explicit breath policy (allowed/forbidden), must-hear protection rules for P0 phrases, and a minimal risk note to prevent accidental splits.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created GOOD-004 anchor case: breath-safe hook with explicit forbidden splits passes G6."
- REASON: "Pack needs a stable PASS reference for breath policy completeness and P0 protection."
- IMPACT: "Cleaner hook delivery; fewer intelligibility regressions caused by breath placement."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD004.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: GOOD-004
- TYPE: GOOD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus
  - tempo_feel: mid-tempo / half-time
  - note: Focus is breath policy completeness, not density edge.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook)
[Chorus / Hook]
Я вижу маршрут — меня не согнут.
Я возвращаюсь к своему.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
- P1: вижу
- P2: (none)

MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

CLARITY_TARGETS:
- Target A: P0 phrases understood on first listen in chorus/hook
- Target B: No breath split inside P0 phrases

---

## 2) BREATH/SINGABILITY PACK (PASS ANCHOR)
### 2.1 MUST_HEAR_PROTECTION_RULES
- never split P0 phrases:
  - "я вижу маршрут"
  - "я возвращаюсь к своему"
- protect consonant attacks on:
  - маршрут / согнут / возвращаюсь / своему

### 2.2 BREATH_POLICY (allowed/forbidden)
allowed:
- breath before line start (before "я вижу маршрут")
- breath between lines (after "меня не согнут." before next line)
- breath before second P0 phrase (before "я возвращаюсь к своему")

forbidden:
- any breath inside: "я вижу маршрут"
- any breath between: "не" and "согнут"
- any breath inside: "возвращаюсь к своему" (between "возвращаюсь" and "своему")

### 2.3 SINGABILITY_RISK (minimal artifact)
DENSITY_SCAN:
- line_id: Chorus-L1
  - contains_P0: YES
  - risk_level: R1 (consonant-heavy P0)
  - evidence: P0 consonants blur if breath is placed mid-phrase
- line_id: Chorus-L2
  - contains_P0: YES
  - risk_level: R0 (ok) if breath placed between lines

### 2.4 Escalation notes
ESCALATION_NOTES:
- present: NO
- why: text is singable under this breath policy; no rewrite needed

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001 -> PASS

---

## 4) WHY (WHY THIS PASSES G6)
- Breath policy exists and is actionable (allowed + forbidden).
- Explicit P0 protection rules exist (no splits).
- Minimal risk artifact exists (density/risk note).
- No out-of-scope lyric rewrites; escalation not needed.

---

## 5) FIX ROUTE (IF IT EVER REGRESSES)
If someone removes forbidden points or P0 protection:
- apply PB-04 to rebuild breath policy and protection rules.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
