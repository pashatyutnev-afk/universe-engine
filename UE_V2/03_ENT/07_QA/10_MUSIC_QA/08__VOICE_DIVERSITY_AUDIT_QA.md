# VOICE DIVERSITY AUDIT — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/08__VOICE_DIVERSITY_AUDIT_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: VOICE_DIVERSITY_AUDIT
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.VOICE_DIVERSITY_AUDIT.001
OWNER: SYSTEM
ROLE: A perception-level vocal diversity audit:
answers “do these tracks sound like the same singer?” even if validators pass.
Used periodically across a group/album to keep the catalog from collapsing into one voice.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Voice Diversity Audit QA: listening protocol across multiple tracks and corrective actions."
- REASON: "Known failure mode: many outputs feel like one vocalist; QA catches perceptual sameness."
- IMPACT: "More believable rosters and stronger differentiation."
- CHANGE_ID: UE.CHG.2026-01-12.QA.VOICE_DIVERSITY.001

---

## 0) PURPOSE (LAW)
Answer:
**“Does the catalog feel vocally diverse to humans?”**

This QA complements Voice Diversity VAL (token-based).

---

## 1) INPUTS
Required:
- SCOPE_MODE: {GROUP | ALBUM | GLOBAL}
- TRACK_SET: 3–10 tracks (audio) from the same scope
Optional:
- cast/role intent notes (if defined)

---

## 2) PROCEDURE (HOW TO RUN)
1) For each track, sample:
   - 0:10–0:25 (first clear vocal section)
   - main hook/chorus (10–15s)
2) Compare tracks pairwise quickly:
   - do voices feel identical?
   - do deliveries feel identical?
3) Output RESULT and identify “clusters” (same-voice groupings).

---

## 3) AUDIT RUBRIC (HEURISTIC)
### V1 — Timbre similarity
- same brightness/texture? same “person” feeling?

### V2 — Delivery style similarity
- same phrasing, same emphasis, same articulation?

### V3 — Register/role difference
- male/female/androgynous, lead vs contrast, duet splits?

### V4 — Hook-vocal identity
- chorus voice is distinct across tracks?

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- clear vocal variety exists across the set
- no large “same-voice cluster” dominates

WARN when:
- 2–3 tracks sound too similar but fixable with role split

FAIL when:
- most tracks feel like the same singer
- catalog “voice collapse” is obvious

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
- CAST_SPLIT:
  - assign different vocalist roles per track/slot
- DUET_PATTERN:
  - call/response or alternating lines
- VOCAL_CONTRAST:
  - switch delivery style and register
- INSTRUMENTAL_RELEASE:
  - for some slots, release instrumental variants to reduce vocal sameness
- RECYCLE_BLOCK:
  - block the current vocal token for next N tracks (policy to be encoded elsewhere)

---

## 6) OUTPUT TEMPLATE (MANDATORY)
VOICE_DIVERSITY_AUDIT_QA_RESULT:
- SCOPE_MODE:
- TRACK_SET: [uids...]
- RESULT: {PASS | WARN | FAIL}
- CLUSTERS:
  - cluster_id: [track_uids...]
  - note: "sounds like same vocalist"
- NOTES:
  - 3–12 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
Validator context:
- Voice Diversity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md

Catalog memory context:
- Catalog Memory CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
