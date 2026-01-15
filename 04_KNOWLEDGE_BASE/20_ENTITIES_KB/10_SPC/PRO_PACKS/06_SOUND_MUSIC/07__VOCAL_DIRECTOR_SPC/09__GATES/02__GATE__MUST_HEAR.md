# SPC PRO PACK — GATE (G2) — MUST-HEAR TARGETS (P0/P1/P2 + PHRASES) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/02__GATE__MUST_HEAR.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
OWNER: SYSTEM
ROLE: Gate G2 defines and validates MUST-HEAR targets: prioritized words (P0/P1/P2), required phrases, and clarity targets. Establishes thresholds and anti-bloat rules so intelligibility becomes testable.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G2 MUST-HEAR for VOCAL_DIRECTOR."
- REASON: "If must-hear targets are missing/bloated, all clarity work becomes subjective and un-auditable."
- IMPACT: "Creates deterministic priorities for G3..G8."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G2.001

---

## 0) PURPOSE
Define and validate what MUST be understood in the hook.

PASS of G2 is required before G3.

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G2 requires these artifact blocks:
- MUST_HEAR_WORDS
- CLARITY_TARGETS
- (recommended) MUST_HEAR_PHRASES

Origin tools:
- T02 MUST_HEAR_BUILDER
- T03 PHRASE_PROMOTION_HELPER

---

## 2) THRESHOLDS (STRICT)
### P0 (must land first listen)
- count: 3..8
- fillers in P0: NO
- must include identity/meaning carriers

Exception:
- If hook is extremely short, P0 may be 2 with explicit note and strong phrases.

### P1 (should land by second listen)
- count: 0..12 OR explicit N/A with reason

### P2 (nice-to-hear)
- optional

### P0 PHRASES
- count: 1..4 (prefer 1..2)
- copy-exact from lyrics (no paraphrase)
- required if meaning depends on multi-word units (negative constructions, signature line)

### CLARITY_TARGETS
- Target A is mandatory:
  - "P0 understood on first listen in HOOK"
- Target B optional:
  - "No breath split inside P0 phrases" (if phrases exist)

---

## 3) PASS / REWORK / FAIL
### PASS if ALL are true:
- P0_COUNT_OK = YES (3..8 or allowed exception)
- P1_COUNT_OK = YES (<=12 or N/A)
- FILLER_IN_P0 = NO
- Target A present
- If phrases are required: MUST_HEAR_PHRASES present and copy-exact

### REWORK if:
- artifacts exist but thresholds are violated:
  - P0 bloated (>8) OR fillers included
  - P1 bloated (>12)
  - phrases are present but too many / misaligned / not copy-exact
  - clarity targets missing beyond Target A
(These are fixable by pruning without new inputs.)

### FAIL if ANY is true:
- MUST_HEAR_WORDS missing
- P0 missing entirely
- no clarity targets at all
- phrases required but not provided and meaning depends on them

Hard rule:
- If FAIL → stop before G3 and apply fixes.

---

## 4) OUTPUT (G2 VERDICT BLOCK)
G2_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G3 INTELLIGIBILITY (T04/T05)"
  - if REWORK: "Prune/re-rank targets via T02/T03; rerun G2"
  - if FAIL: "Rebuild targets via PB-02; rerun G2"

---

## 5) FIX ROUTE
Primary tools:
- T02 MUST_HEAR_BUILDER
- T03 PHRASE_PROMOTION_HELPER

Playbook:
- PB-02 MUST-HEAR REBUILD (A1)

After fix:
- rerun G2, then proceed to G3.

---

## 6) ANTI-GUESSING / ANTI-DRIFT
Forbidden:
- inventing phrases not in lyrics
- keeping contradictory duplicates in P0
- treating fillers as P0 targets
- using >8 P0 items “just in case”

---

## 7) TRACE
TRACE:
- GATE: G2
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- TOOLS: T02, T03
- PLAYBOOK: PB-02

--- END.
