# GATE — VOICE DIVERSITY INTENT (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/05__KB_GATES/02__GATE__VOICE_DIVERSITY_INTENT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: KB_GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001
OWNER: SYSTEM
ROLE: Gate for PROMPT_ARCHITECT: checks whether the prompt specifies sufficient vocal role separation and contrast intent to reduce “same singer syndrome”. Outputs PASS/REWORK/FAIL with fix mapping and recheck plan.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created voice diversity intent gate: role ownership + contrast levers + targeted negatives checks."
- REASON: "Voice sameness is a frequent failure mode; this gate makes vocal intent explicit before generation."
- IMPACT: "More distinct vocal parts and fewer same-voice outputs."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.GATE.VOICE.001

---

## 0) TARGET OUTPUT
TARGET_OUTPUT:
- VOCAL_INTENT_BLOCK (and/or VOCAL_CONTRAST_BLOCK)
- STRUCTURE_BLOCK (for section role ownership)
- NEGATIVE_SPEC_BLOCK (voice-related negatives)

This gate evaluates intent specification (prompt-level), not audio output.

---

## 1) TEST METHOD (DETERMINISTIC)
Run checks:

V1 — Role map exists (if multi-section song)
- If “full song”:
  - prompt defines who leads verse vs chorus (role ownership)
- If “single voice only”:
  - prompt defines at least 2 delivery modes across sections (e.g., verse vs chorus delivery)

V2 — Contrast levers present (2–4 max)
At least two of:
- delivery mode contrast (rap percussive vs melodic sustained)
- range separation (principle)
- timbre contrast (principle)
- call/response or adlibs plan (optional)
Rule:
- If levers > 4 → overload risk (REWORK).

V3 — Chorus vs verse differentiation explicitly stated
- Prompt explicitly says:
  - chorus lead differs from verse lead OR chorus delivery differs from verse delivery

V4 — Targeted voice negatives present (recommended)
At least one of:
- “avoid identical vocal timbre across sections”
- “avoid same delivery mode for verse and chorus”
- “avoid chorus sounding like verse”

If V4 missing:
- still possible PASS if V1–V3 strong; otherwise REWORK.

V5 — No contradictions in vocal plan
Examples:
- “single vocalist only” AND “two distinct singers A/B”
- “rap only track” AND “melodic chorus required” without structure
If contradictions exist → REWORK/FAIL depending on severity.

---

## 2) PASS / REWORK / FAIL CRITERIA
PASS:
- V1 PASS
- V2 PASS
- V3 PASS
- V5 PASS
- V4 present OR (V1–V3 are very explicit and compact)

REWORK:
- missing one element (e.g., V4) OR
- levers overloaded (>4) OR
- role map too vague (“different voices” with no mechanics)

FAIL:
- no role ownership / no section-based vocal plan for full song
- no contrast levers (vocal plan is vibes-only)
- vocal plan contradictory and cannot be resolved by pruning
- chorus vs verse differentiation absent

---

## 3) OUTPUT RECORD (COPY)
GATE_RESULT_RECORD:
- GATE_UID: UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- RESULT: PASS/REWORK/FAIL
- FAILED_CHECKS:
  - <V#>
- EVIDENCE (short):
  - <snippet>
- FIX DIRECTIONS:
  - <action>
- RECHECK:
  - rerun this gate after fix

---

## 4) FIX MAPPING (WHAT TO DO IF FAILS)
If V1 missing role map:
- Fix: add explicit section role ownership (A verses, B chorus) OR define two delivery modes for single voice.

If V2 missing levers:
- Fix: add 2 contrast levers:
  - delivery mode + (range OR timbre)
- Keep compact.

If V3 missing:
- Fix: add explicit sentence:
  - “Chorus lead must clearly differ from verse lead.”

If V4 missing:
- Fix: add 1–3 targeted negatives from voice library.

If contradictions exist (V5):
- Fix: prune to one coherent plan:
  - either single voice with delivery contrast
  - or A/B roles with ownership

Playbook mapping:
- Use PB-05 VOCAL DIVERSITY BOOST for full fix.
- Use PB-04 PATCH MIN for minimal edits.

---

## 5) EXAMPLES (PLACEHOLDER)
EXAMPLES:
- PASS example:
  - <to be filled>
- FAIL example:
  - <to be filled>
- BORDERLINE example:
  - <to be filled>

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- gate result is claimed without evidence snippet
- fixes are not actionable
- gate is skipped in a pipeline that requires vocal diversity intent

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.VOCAL_DIVERSITY.001 | WHY: primary fix method
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal fixes
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 | WHY: contract completeness gate precedes vocal gate

--- END.
