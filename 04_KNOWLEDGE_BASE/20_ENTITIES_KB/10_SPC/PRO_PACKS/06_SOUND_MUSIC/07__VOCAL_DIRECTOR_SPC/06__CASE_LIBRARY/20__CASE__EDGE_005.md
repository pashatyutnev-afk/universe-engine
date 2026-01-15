# SPC PRO PACK — CASE (EDGE-005) — ARRANGEMENT SEAT CONFLICT MASKS P0 (ESCALATE) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/20__CASE__EDGE_005.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE.005.DRAFT.001
OWNER: SYSTEM
ROLE: EDGE case calibrating seat/space conflicts: P0 intelligibility fails because arrangement density masks the must-hear words. VOCAL_DIRECTOR must not prescribe mix chains; only principle-level seat requests and escalation to Arranger/Producer are allowed.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created EDGE-005: arrangement seat conflict masks P0; requires escalation (no mix-chain prescriptions)."
- REASON: "Some intelligibility failures are not performance issues; they are seat conflicts that must be handled by arrangement/production owners."
- IMPACT: "Prevents out-of-scope mixing advice; preserves ownership while still enabling fixes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.EDGE005.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: EDGE-005
- TYPE: EDGE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: clean-aggressive hook
  - tempo_feel: mid-tempo
  - note: Edge is arrangement density masking must-hear words.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook)
[Chorus / Hook]
Я вижу маршрут — меня не согнут.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут
MUST_HEAR_PHRASES:
- P0: "вижу маршрут", "не согнут"

CLARITY_TARGETS:
- Target A: P0 understood on first listen in chorus/hook

---

## 2) BASELINE_DIRECTION_PACK (PERFORMANCE IS FINE)
Delivery intent:
- consonant-forward on P0
- no breath splits
- stacking_used: NO (N/A for this case)

Observed issue:
- Even with clean articulation, P0 is hard to understand due to dense instrumental layers in the same moment as the hook.

---

## 3) FAILURE OBSERVATION + ROOT CAUSE (T7)
FAILURE OBSERVATION:
- Listener hears hook as “...рут ...нут” blur, even when vocal take is clean.

ROOT_CAUSE_CLASSIFICATION:
- T7 — ARRANGEMENT SEAT CONFLICT:
  - competing elements (e.g., dense guitars/synth lead/drums hits) occupy the same perceptual space during P0 attacks
  - intelligibility fails without changing performance

Note:
- VOCAL_DIRECTOR cannot prescribe EQ/compression chains. Must escalate.

---

## 4) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> REWORK (via escalation / seat request)
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001 -> PASS (if no mix-chain advice is present)

---

## 5) CORRECT ACTION (ESCALATION — PRINCIPLES ONLY)
ESCALATION_NOTES (anchor):
- owner: Arranger/Producer
- section: Chorus (HOOK)
- problem: "P0 intelligibility fails due to arrangement density during hook attacks."
- request (principles only):
  - "Leave perceptual space on P0 attacks (маршрут/согнут)."
  - "Reduce competing lead elements during those exact words."
  - "Avoid adding new layers on hook word attacks."
- must_keep:
  - P0 words/phrase timing points (hook attacks)
- forbidden:
  - plugin chains, EQ/compressor settings, DAW recipes (out of scope)

---

## 6) FIX ROUTE
- Primary: Escalate to Arranger/Producer (seat/space changes).
- Secondary (after seat change): rerun intelligibility checks (G3).

---

## 7) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
