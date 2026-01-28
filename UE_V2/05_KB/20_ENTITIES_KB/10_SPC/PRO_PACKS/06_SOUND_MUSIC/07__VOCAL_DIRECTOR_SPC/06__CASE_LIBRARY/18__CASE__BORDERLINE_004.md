# SPC PRO PACK — CASE (BORDERLINE-004) — TAKE GOALS OVERLOAD / WEAK QC (G8 REWORK) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/18__CASE__BORDERLINE_004.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDERLINE.004.DRAFT.001
OWNER: SYSTEM
ROLE: BORDERLINE anchor for calibrating Gate G8 TAKE PACK REPEATABILITY as REWORK when take goals are overloaded/vibe-like and QC hard fails are incomplete. Demonstrates PB-06 minimal patch: reduce goals to 2–4 per section, add repeatability rules and hard fails.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BORDERLINE-004: take goals overload + weak QC triggers G8 REWORK; PB-06 fixes."
- REASON: "Too many goals per section overload the performer and breaks repeatability; missing hard fails makes QC subjective."
- IMPACT: "Enforces comp-friendly take plan and stable character across takes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDER004.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BORDERLINE-004
- TYPE: BORDERLINE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: rap verse + melodic chorus
  - tempo_feel: mid-tempo
  - note: Inputs exist; failure is take-pack executability.

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

### 1.3 Must-hear targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) TAKE PACK (BORDERLINE VERSION — OVERLOAD)
### 2.1 TAKE_GOALS_BY_SECTION (too many / vague)
Verse goals (bad):
- be emotional
- keep it cool
- be tight
- be loose
- smile in voice
- sound angry
- make it cinematic

Chorus goals (bad):
- louder
- bigger
- clearer
- more aggressive
- more soft
- more grit
- more clean
- more energy
- more feeling

Problems:
- goals are contradictory (aggressive vs soft vs clean vs grit)
- goals are vibe-only and untestable
- >4 goals per section (overload)

### 2.2 QC_HARD_FAILS (incomplete)
QC_HARD_FAILS:
- (missing explicit P0 hard fail)
- "если не нравится — перезаписать" (vibe-only)

### 2.3 REPEATABILITY_RULES (missing)
- (missing)

### 2.4 COMP_NOTES (missing)
- (missing)

Why BORDERLINE:
- a take pack exists (so not FAIL), but it is not executable and lacks QC structure.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001 -> REWORK

---

## 4) WHY (WHY THIS IS BORDERLINE)
- Pack contains a take goals list, but:
  - goals >4 and contradictory
  - QC hard fails missing
  - repeatability rules missing
  - comp notes missing
- This is REWORK (not FAIL) because PB-06 can rebuild it deterministically.

---

## 5) FIX ROUTE (PB-06) — MINIMAL PATCH
Apply PB-06 TAKE DIRECTION PACK:

Patched shape (example):
TAKE_GOALS_BY_SECTION (2–4 goals max):
- Verse:
  - goal: stable diction baseline
  - goal: keep rhythm tight
- Chorus:
  - goal: P0 clarity first on hook phrases
  - goal: lift via energy (not distortion)
  - goal: no breath splits inside P0
- Final Chorus:
  - goal: biggest lift, keep P0 consonant attacks clean

REPEATABILITY_RULES (>=3):
- keep same pronunciation for P0 across takes
- keep chorus intensity within target band
- keep articulation policy stable on hook

QC_HARD_FAILS:
- P0 not understood on first listen
- breath split inside P0 phrase
- distortion masks P0 words

COMP_NOTES:
- do not comp across different pronunciations
- splice only outside P0 phrases

After patch:
- rerun G8 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
