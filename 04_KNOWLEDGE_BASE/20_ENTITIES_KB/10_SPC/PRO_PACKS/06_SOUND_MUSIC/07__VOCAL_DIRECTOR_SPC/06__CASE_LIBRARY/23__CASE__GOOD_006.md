# SPC PRO PACK — CASE (GOOD-006) — TAKE PACK PASS ANCHOR (G8) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/23__CASE__GOOD_006.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD.006.DRAFT.001
OWNER: SYSTEM
ROLE: GOOD case anchor for calibrating Gate G8 TAKE PACK REPEATABILITY as PASS. Demonstrates a complete take direction pack: 2–4 goals per section, repeatability rules, QC hard fails tied to P0 must-hear targets, and comp notes for assembly.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created GOOD-006 anchor case: complete take pack passes G8."
- REASON: "Pack needs a stable PASS reference for repeatable takes and comp-safe rules."
- IMPACT: "Faster sessions, less drift, more usable takes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD006.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: GOOD-006
- TYPE: GOOD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: rap verse + melodic hook
  - tempo_feel: mid-tempo / half-time
  - note: Focus = take pack completeness and QC.

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
- Chorus
- Bridge
- Final Chorus

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
- P1: вижу
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) TAKE DIRECTION PACK (PASS ANCHOR)
### 2.1 SESSION_INTENT
- identity: clean-aggressive, consonant-forward on hook
- priorities: P0 clarity > arc lift > texture
- forbidden: breath split inside P0; distortion masking P0; pronunciation drift

### 2.2 TAKE_GOALS_BY_SECTION (2–4 goals)
- Verse:
  - goal: stable diction baseline; keep rhythm tight
  - goal: keep intensity in band (50–60)
- Chorus (HOOK):
  - goal: P0 clarity first on hook phrases
  - goal: lift via energy (75–80), not via masking distortion
  - goal: land consonant attacks clean on P0 words
- Bridge:
  - goal: reset intensity (60–65); keep clarity
  - goal: keep character stable (no new identity)
- Final Chorus:
  - goal: biggest lift (80–85) while preserving P0 clarity
  - goal: same pronunciation as Chorus 1/2

### 2.3 RISK_LINES
- Chorus-L1: “я вижу маршрут” — consonant attack risk on “маршрут”
- Chorus-L2: “не согнут” — final consonant risk on “т”
- Chorus-L3: “возвращаюсь к своему” — phrase integrity risk

### 2.4 REPEATABILITY_RULES (>=3)
- Rule 1: P0 pronunciation fixed across takes (no variants)
- Rule 2: Chorus intensity band must stay within target range (±5)
- Rule 3: Hook articulation policy stays consonant-forward
- Rule 4 (optional): No new grit mode introduced mid-session

### 2.5 QC_HARD_FAILS
- HF-1: any P0 word/phrase not understood on first listen in chorus
- HF-2: breath split inside P0 phrases
- HF-3: distortion/rough delivery masks P0 attacks
- HF-4: chorus lift absent vs verse (if arc requires lift)

### 2.6 QC_SOFT_FAILS
- SF-1: minor timing smear not on P0
- SF-2: verse energy slightly off band but usable

### 2.7 COMP_NOTES
- Do not comp across different pronunciations of P0 words.
- Prefer comping within same character band (no mixing clean vs gritty).
- Splice only outside P0 phrases (safe zones).
- Keep hook take pronunciation consistent between chorus repeats.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001 -> PASS

---

## 4) WHY (WHY THIS PASSES G8)
- Goals per section are limited (2–3) and executable.
- Repeatability rules exist and prevent drift.
- QC hard fails are explicit and tied to P0 targets.
- Comp notes prevent audible artifacts.

---

## 5) FIX ROUTE (IF IT REGRESSES)
If goals bloat or QC disappears:
- apply PB-06 to rebuild take pack and rerun G8.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
