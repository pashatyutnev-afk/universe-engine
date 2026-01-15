# SPC PRO PACK — CASE (BAD-006) — BREATH SPLITS INSIDE P0 (G6 FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/17__CASE__BAD_006.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.006.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating Gate G6 BREATH/SINGABILITY as FAIL: breath breaks occur inside P0 must-hear phrases. Demonstrates hard rule: any breath split inside P0 is an automatic FAIL; must be fixed by PB-04.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-006 anchor case: breath split inside P0 triggers G6 FAIL."
- REASON: "Breath splits inside must-hear phrases destroy intelligibility and cannot be treated as minor issue."
- IMPACT: "Enforces strict P0 protection and correct breath placement."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD006.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-006
- TYPE: BAD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus
  - tempo_feel: mid-tempo
  - note: Failure is a forbidden breath split inside P0 phrase.

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
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

CLARITY_TARGETS:
- Target A: P0 understood on first listen in chorus/hook

---

## 2) BASELINE_DIRECTION_PACK (BAD — SPLIT INSIDE P0)
Bad breath instruction (what NOT to do):
- "Сделай вдох внутри фразы для драматизма: ‘я вижу / маршрут’."
- "И во второй строке: ‘я возвращаюсь / к своему’."

This explicitly violates P0 protection.

BREATH_POLICY (bad):
- allowed: "anywhere for drama"
- forbidden: (missing)

MUST_HEAR_PROTECTION_RULES:
- (missing)

---

## 3) EVIDENCE OF VIOLATION (CONCRETE)
Forbidden splits (exact):
- Split #1 inside P0 phrase:
  - "я вижу / маршрут"  (breath between "вижу" and "маршрут")
- Split #2 inside P0 phrase:
  - "я возвращаюсь / к своему" (breath between "возвращаюсь" and "к своему")

Why this is hard fail:
- must-hear phrase becomes fragmented; first-listen recognition drops.

---

## 4) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001 -> FAIL
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> FAIL (likely, because P0 is broken)

Stop rule:
- Not ready. Must fix breath policy before proceeding.

---

## 5) WHY (WHY THIS FAILS)
- G6 requires:
  - forbidden breath points defined
  - explicit P0 protection (“never split P0 phrases”)
- This pack does the opposite: instructs splitting P0.
Therefore: FAIL.

---

## 6) FIX ROUTE (PB-04) — MINIMAL PATCH
Apply PB-04:

MUST_HEAR_PROTECTION_RULES (patched):
- never split:
  - "я вижу маршрут"
  - "я возвращаюсь к своему"

BREATH_POLICY (patched):
- allowed:
  - breath before "я вижу маршрут"
  - breath between lines
  - breath before "я возвращаюсь к своему"
- forbidden:
  - any breath inside P0 phrases

After patch:
- rerun G6 → expected PASS.

---

## 7) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
