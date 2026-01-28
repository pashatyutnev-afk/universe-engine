# SPC PRO PACK — CASE (BORDERLINE-005) — WEAK PROTECTED ZONES (G7 REWORK) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/22__CASE__BORDERLINE_005.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDERLINE.005.DRAFT.001
OWNER: SYSTEM
ROLE: BORDERLINE anchor for calibrating Gate G7 STACKING CLARITY-SAFE as REWORK when stacking plan exists and is minimal, but protected zones are incomplete/weak and do not explicitly cover P0 phrases + consonant attacks. Demonstrates PB-07 minimal patch.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BORDERLINE-005: protected zones incomplete triggers G7 REWORK; PB-07 strengthens protection."
- REASON: "Without explicit protected zones, even minimal stacking can drift into masking P0."
- IMPACT: "Makes stacking safety deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDER005.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BORDERLINE-005
- TYPE: BORDERLINE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic hook
  - tempo_feel: mid-tempo
  - note: Stacking is minimal, but protection is under-specified.

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
- Final Chorus (HOOK)

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) STACKING PACK (BORDERLINE VERSION)
stacking_used: YES

STACKING_MAP_BY_SECTION (ok/minimal):
- Verse: NONE
- Chorus:
  - mode: DOUBLE
  - where: light double on chorus (not specified further)
- Final Chorus:
  - mode: BACKS
  - where: occasional echoes

QC_RULES (present but generic):
- QC-S1: "Words should stay clear"

PROTECTED_ZONES (weak/incomplete):
- "avoid stacking on important words" (generic)
Missing:
- explicit listing of P0 phrases
- explicit coverage of consonant attacks on P0 words
- explicit fail trigger: "if P0 less clear with stacking → remove"

Why BORDERLINE:
- stacking is not “everywhere”, but protection is too vague to guarantee safety.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001 -> REWORK

---

## 4) WHY (WHY THIS IS BORDERLINE)
- Stacking map exists and is minimal-first → good.
- But protected zones are not explicit and QC is generic:
  - cannot audit whether P0 is truly protected
  - drift risk: doubles may land on P0 attacks
Therefore: REWORK (not FAIL) because a minimal patch can fix it.

---

## 5) FIX ROUTE (PB-07) — MINIMAL PATCH
Apply PB-07 to strengthen protection:

PROTECTED_ZONES (patched):
- P0 phrases:
  - "я вижу маршрут"
  - "я возвращаюсь к своему"
- avoid stacking over consonant attacks on:
  - маршрут / согнут / возвращаюсь / своему

QC_RULES (patched):
- QC-S1: P0 understood on first listen (YES/NO)
- FAIL trigger: if any P0 word becomes less clear with stacking → FAIL (remove/move stacking)
- Minimalism: doubles only on tails outside protected zones

STACKING_MAP clarifier (patched):
- Chorus double only on line tails (outside P0 phrases)
- Final chorus backs only as end-word echo outside protected zones

After patch:
- rerun G7 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
