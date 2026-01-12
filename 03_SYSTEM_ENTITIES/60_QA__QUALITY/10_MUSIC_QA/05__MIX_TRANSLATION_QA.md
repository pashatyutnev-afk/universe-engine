# MIX TRANSLATION — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/05__MIX_TRANSLATION_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: MIX_TRANSLATION
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.MIX_TRANSLATION.001
OWNER: SYSTEM
ROLE: A pragmatic “translation” check:
does the mix remain clear and pleasant across common listening environments (phone speaker, earbuds, car)?
Flags muddy low-end, harshness, buried vocals, and over-compression issues.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Mix Translation QA: procedure across devices, PASS/WARN/FAIL, and fix suggestions."
- REASON: "Tracks fail in the real world when they only sound okay on one device."
- IMPACT: "More reliable releases and fewer listener drop-offs."
- CHANGE_ID: UE.CHG.2026-01-12.QA.MIX_TRANSLATION.001

---

## 0) PURPOSE (LAW)
Answer:
**“Does the mix translate across basic devices?”**

This is a heuristic check. It does not set exact EQ values; it flags issues.

---

## 1) INPUTS
- audio take (candidate)
- optional: lyrical vs instrumental marker
- test devices (minimum 2):
  - phone speaker
  - earbuds/headphones
  - (optional) car / small bluetooth speaker

---

## 2) PROCEDURE (HOW TO RUN)
1) Listen 15–30 seconds on device A (phone speaker).
2) Listen same segment on device B (earbuds/headphones).
3) If possible, listen on device C (car/speaker).
4) Check items below and output result + notes.

---

## 3) TRANSLATION CHECKLIST
### C1 — Low end clarity
- bass not muddy/boomy
- kick/bass relationship not smeared

### C2 — Mid clarity / vocal intelligibility
- vocal not buried (if lyrical)
- main motif clearly audible (if instrumental)

### C3 — High harshness
- no painful sibilance/harsh cymbals
- not overly bright

### C4 — Dynamics / punch
- not flattened to death
- groove still breathes

### C5 — Mono compatibility (phone speaker)
- core elements remain audible in mono-ish playback

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- no major translation problems
- vocals/motif remain clear across devices

WARN when:
- one issue exists but fixable (e.g., slight mud or slight harshness)

FAIL when:
- major mud/harshness/buried vocals makes it unpleasant or unclear on common devices

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
- LOW_END_TIGHTEN:
  - reduce mud, clarify kick/bass separation (conceptual)
- VOCAL_FORWARD:
  - increase intelligibility / reduce masking
- TAME_HARSHNESS:
  - reduce harsh highs / sibilance
- RESTORE_DYNAMICS:
  - reduce over-compression / allow punch

---

## 6) OUTPUT TEMPLATE (MANDATORY)
MIX_TRANSLATION_QA_RESULT:
- TRACK_UID:
- TAKE_ID:
- TEST_DEVICES: [phone, earbuds, car?]
- RESULT: {PASS | WARN | FAIL}
- NOTES:
  - 3–9 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
Related negative pack:
- Negative Spec Library CTL (NO_MUDDY_LOW_END)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

Used in gate ORC:
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
