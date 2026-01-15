# SPC PRO PACK — CASE (BAD-004) — CONTRADICTORY / VIBE-ONLY DELIVERY PROFILE (G4 FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/12__CASE__BAD_004.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.004.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating Gate G4 DELIVERY PROFILE COHERENCE as FAIL. Demonstrates a contradictory and vibe-only delivery profile that is not performer-executable and provides no forbidden-styles guardrails.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-004 anchor case: contradictory/vibe-only delivery profile triggers G4 FAIL."
- REASON: "Coherence failures cause drift and make all downstream directions non-deterministic."
- IMPACT: "Forces rebuild/prune of delivery profile before any arc/intelligibility work."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD004.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-004
- TYPE: BAD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: mixed
  - tempo_feel: mid-tempo
  - note: This case isolates delivery-profile coherence failure (not lyrics).

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

### 1.3 MUST-HEAR targets (present)
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) BASELINE_DIRECTION_PACK (BAD PROFILE)
VOCAL_STYLE_PROFILE (bad version):
delivery_principles:
- "пусть будет максимально чисто и студийно"
- "и одновременно чтобы звучало как сломанная кассета lo-fi"
- "очень нежно и мягко"
- "но при этом агрессивно и зло, прям крик"
- "сделай просто красиво и кайфово"
forbidden_styles:
- (missing)

Problems (intentional):
- Contradictions:
  - clean pristine vs broken lo-fi cassette simultaneously
  - gentle soft vs evil scream simultaneously
- Vibe-only statements:
  - “красиво”, “кайфово” with no actionable constraints
- No forbidden list:
  - drift not prevented
- Not performer-executable:
  - too many conflicting requirements

COHERENCE_CHECK (expected):
- contradictions_found: YES
- executability_ok: NO
- notes: profile is contradictory and vibe-only

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001 -> FAIL

Stop rule:
- Do NOT proceed to G5+ until delivery profile is rebuilt/pruned.

---

## 4) WHY (WHY THIS FAILS G4)
- Profile exists but is contradictory (cannot be executed simultaneously).
- Contains vibe-only statements, not measurable constraints.
- Forbidden styles missing → drift guaranteed.
- Therefore it’s not a “small patch” REWORK; it requires rebuild/prune.

---

## 5) FIX ROUTE (PB-01 / PB-08 A4)
Preferred:
- PB-01 (rebuild/prune delivery profile):
  - choose a single coherent character
  - express 4–6 principles
  - add 2–5 forbidden styles that protect P0 clarity

Alternative (only if local):
- PB-08 axis A4 minimal patch:
  - delete contradictory lines
  - replace vibe-only with actionable constraints
  - add forbidden list

Example patch shape (not full rewrite):
delivery_principles (patched):
- clean-aggressive, consonant-forward on P0 phrases
- controlled grit only outside P0 attacks
- medium-low breathiness on hook
forbidden_styles:
- heavy distortion on P0
- breath break inside P0 phrases
- lo-fi “broken cassette” masking on hook

After patch:
- rerun G4 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
