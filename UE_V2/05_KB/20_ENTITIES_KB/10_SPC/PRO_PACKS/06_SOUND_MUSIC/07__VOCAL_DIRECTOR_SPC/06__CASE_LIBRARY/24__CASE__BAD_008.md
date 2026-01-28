# SPC PRO PACK — CASE (BAD-008) — SCOPE VIOLATION (LYRIC REWRITE / MIX CHAIN) (G9 FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/24__CASE__BAD_008.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.008.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating Gate G9 SCOPE/OWNERSHIP COMPLIANCE as FAIL. Demonstrates two forbidden violations: (F1) lyric rewrite and (F4) mix/master processing chain prescriptions. Teaches remediation: convert to escalation/principle-level notes only.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-008 anchor case: lyric rewrite + mix chain advice triggers G9 FAIL."
- REASON: "Scope violations break the entity model and make outputs non-auditable."
- IMPACT: "Enforces strict boundaries and correct escalation behavior."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD008.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-008
- TYPE: BAD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: mixed
  - tempo_feel: mid-tempo
  - note: This case intentionally violates scope rules.

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

### 1.3 Must-hear targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут
MUST_HEAR_PHRASES:
- P0: "вижу маршрут", "не согнут"

---

## 2) BASELINE_DIRECTION_PACK (BAD — VIOLATIONS)
### 2.1 Violation F1 — lyric rewrite (forbidden)
BAD INSTRUCTION (illegal):
- "Заменим слово ‘Поме́хи’ на ‘Сбо́и’ прямо в тексте: ‘Сбо́и в голове…’"
Why illegal:
- VOCAL_DIRECTOR must not rewrite/replace lyric text.

### 2.2 Violation F4 — mix/master chain prescription (forbidden)
BAD INSTRUCTION (illegal):
- "Сделай цепочку: EQ срез 200–300Hz, компрессор 4:1, сатурация, de-esser, plate reverb, multiband для низов."
Why illegal:
- VOCAL_DIRECTOR must not prescribe plugin chains/DAW recipes.

### 2.3 Scope audit (expected)
SCOPE_AUDIT:
- lyric_rewrite_present: YES
- mix_chain_present: YES
- structure_edit_present: NO
- guessing_present: NO

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001 -> FAIL

Stop rule:
- Must remove violations before pack can be READY.

---

## 4) WHY (WHY THIS FAILS G9)
- Contains direct lyric rewrite (F1).
- Contains explicit mix/master chain recipe (F4).
Any one of these is an automatic FAIL.

---

## 5) REMEDIATION (HOW TO FIX WITHOUT VIOLATING SCOPE)
### 5.1 Replace lyric rewrite with escalation note (allowed)
ESCALATION_NOTES (correct):
- owner: Lyricist/Songwriter
- problem: "stress/word choice issue on ‘Поме́хи’ impacts singability/recognition"
- request: "consider alternate synonym while preserving meaning"
- must_keep: P0 clarity and hook meaning
Rule:
- VOCAL_DIRECTOR does not provide the replacement text; only requests.

### 5.2 Replace mix chain with principle-level seat note (allowed)
Principle-level note (correct):
- "Ensure vocal seat remains clear on P0 words; avoid masking during hook attacks."
No plugin chain details.

After remediation:
- rerun G9 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
