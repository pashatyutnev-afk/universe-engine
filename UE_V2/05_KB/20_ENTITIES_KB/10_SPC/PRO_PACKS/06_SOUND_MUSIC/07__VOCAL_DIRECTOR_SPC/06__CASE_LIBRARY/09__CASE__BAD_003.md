# SPC PRO PACK — CASE (BAD-003) — NO INTELLIGIBILITY CHECKLIST (G3 FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/09__CASE__BAD_003.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.003.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating G3 INTELLIGIBILITY PASS as FAIL: MUST-HEAR targets exist but INTELLIGIBILITY_GATES_CHECKLIST and hard-fail triggers are missing, making clarity non-testable.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-003 anchor case: intelligibility checklist missing triggers G3 FAIL."
- REASON: "Without explicit pass/fail criteria, intelligibility cannot be validated and rework cannot be deterministic."
- IMPACT: "Forces creation of a checklist + hard fails via PB-03/PB-04."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD003.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-003
- TYPE: BAD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus
  - tempo_feel: mid-tempo
  - note: This case isolates the “missing checklist” failure, not performance or lyrics.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook)
[Chorus / Hook]
Я вижу маршрут — но меня не согнут.
Я возвращаюсь к своему.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)

### 1.3 MUST-HEAR targets (present)
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
- P1: вижу
- P2: (none)

MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

CLARITY_TARGETS:
- Target A: P0 understood on first listen in chorus/hook

---

## 2) BASELINE_DIRECTION_PACK (BAD VERSION)
What exists (insufficient):
- "Сделай припев разборчивым, чтобы слова было слышно."
- "В припевах чуть больше энергии."

What is missing:
- INTELLIGIBILITY_GATES_CHECKLIST (YES/NO checks)
- HARD_FAIL_TRIGGERS
- breath split rules for P0 phrases

This makes the output non-testable and non-auditable.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> FAIL

Stop rule:
- Do NOT proceed to G4..G9 when G3 FAIL.

---

## 4) WHY (WHY THIS FAILS)
- G2 PASS: targets exist and are testable.
- G3 FAIL: checklist is missing:
  - no Gate A/B/C/D/E checks
  - no hard-fail triggers
  - no repair routing guidance
Result:
- You cannot determine PASS/REWORK, and you cannot select deterministic fixes.

---

## 5) FIX ROUTE (PB-03 / PB-04)
Apply PB-03 to generate:
- INTELLIGIBILITY_GATES_CHECKLIST:
  - Gate A: P0 first listen YES/NO
  - Gate C: no breath split inside P0 YES/NO
  - Gate D: consonant attacks protected YES/NO
- HARD_FAIL_TRIGGERS:
  - HF-1 P0 not understood
  - HF-2 breath split in P0

If density/breath trap discovered during PB-03:
- apply PB-04 for breath policy + escalation formatting

After patch:
- rerun G3 → expected PASS, proceed to G4.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
