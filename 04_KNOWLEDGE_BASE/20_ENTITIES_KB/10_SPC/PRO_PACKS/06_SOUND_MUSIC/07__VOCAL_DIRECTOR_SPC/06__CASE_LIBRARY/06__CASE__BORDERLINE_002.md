# SPC PRO PACK — CASE (BORDERLINE-002) — BREATH POLICY INCOMPLETE (G6 REWORK) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/06__CASE__BORDERLINE_002.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDERLINE.002.DRAFT.001
OWNER: SYSTEM
ROLE: BORDERLINE anchor for calibrating G6 BREATH/SINGABILITY as REWORK: breath policy exists but lacks forbidden points and explicit P0 protection. Demonstrates minimal PB-04 patch needed to reach PASS.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BORDERLINE-002: incomplete breath policy triggers G6 REWORK; PB-04 fixes."
- REASON: "Teaches threshold: breath policy must explicitly protect P0 phrases and define forbidden splits."
- IMPACT: "Improves hook clarity and prevents accidental P0 breaks."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDER002.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BORDERLINE-002
- TYPE: BORDERLINE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus
  - tempo_feel: mid-tempo
  - note: Not extreme density; failure is policy incompleteness.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook)
[Chorus / Hook]
Поме́хи в голове — но я вижу маршрут,
Поме́хи в душе — но меня не согнут.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут
- P1: голове, душе
- P2: (optional) помехи

MUST_HEAR_PHRASES:
- P0: "вижу маршрут", "не согнут"
- P1: (N/A)

CLARITY_TARGETS:
- Target A: P0 understood on first listen in chorus

---

## 2) BASELINE_DIRECTION_PACK (SHORT)
### 2.1 Breath policy (incomplete — the problem)
BREATH_POLICY:
- allowed:
  - "breathe where comfortable"
- forbidden:
  - (missing)

MUST_HEAR_PROTECTION_RULES:
- (missing)

DENSITY_SCAN:
- (missing)

Why this is borderline:
- breath policy exists (so not FAIL), but it is not actionable and does not protect P0.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001 -> REWORK

---

## 4) WHY (WHY THIS IS BORDERLINE)
- Breath policy is present but not actionable:
  - no forbidden breath points
  - no explicit P0 protection
- No density/risk artifact present.
- This should trigger G6 REWORK (not FAIL) because a minimal patch can fix it.

---

## 5) FIX ROUTE (PB-04) — MINIMAL PATCH
Apply PB-04:

Add MUST_HEAR_PROTECTION_RULES:
- never split P0 phrases: "вижу маршрут", "не согнут"

Replace breath policy with allowed/forbidden:
BREATH_POLICY (patched):
- allowed:
  - breath before "вижу маршрут"
  - breath after line end
- forbidden:
  - breath inside "вижу маршрут"
  - breath between "не" and "согнут"

Add minimal risk note:
DENSITY_SCAN (patched):
- line_id: Chorus-L1
  - risk_level: R1 (dense-ish on consonants)
  - evidence: P0 consonants blur if breath placed mid-phrase

After patch:
- rerun G6 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
