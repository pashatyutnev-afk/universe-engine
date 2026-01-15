# SPC PRO PACK — TOOL (T04) — INTELLIGIBILITY_CHECKLIST_BUILDER (A..E) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/04__T04__INTELLIGIBILITY_CHECKLIST_BUILDER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T04
TOOL_NAME: INTELLIGIBILITY_CHECKLIST_BUILDER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T04.INTELLIGIBILITY_CHECKLIST_BUILDER.001
OWNER: SYSTEM
ROLE: Builds a deterministic intelligibility checklist (Gates A..E) and hard-fail triggers for clarity QA. Does not invent lyrics or audio facts; expresses checks as pass criteria and fail triggers tied to MUST_HEAR targets.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T04 INTELLIGIBILITY_CHECKLIST_BUILDER for VOCAL_DIRECTOR."
- REASON: "Intelligibility must be testable; checklist + hard fails stabilize G3 verdicts."
- IMPACT: "Consistent clarity QA and repair routing."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T04.001

---

## 0) PURPOSE
Generate stable QA blocks for intelligibility:
- INTELLIGIBILITY_GATES_CHECKLIST (A..E)
- HARD_FAIL_TRIGGERS

Supports Gate:
- G3 INTELLIGIBILITY

---

## 1) INPUTS (REQUIRED)
- MUST_HEAR_WORDS (P0/P1) (from T02)
- HOOK_SECTION_LABEL (from T01)
Optional (recommended):
- MUST_HEAR_PHRASES (from T03)
- any existing attack notes (from T05) (if already made)

Rules:
- This tool does not claim audio results; it defines what must be tested.
- If MUST_HEAR_WORDS missing → STOP (GAP).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T04 MUST output:

### INTELLIGIBILITY_GATES_CHECKLIST
Must include exactly these checklist items:
- Gate A (P0 first listen):
- Gate B (P1 second listen):
- Gate C (no breath split inside P0 phrases):
- Gate D (consonant attacks protected):
- Gate E (hook clarity >= verse baseline):

### HARD_FAIL_TRIGGERS
Must include:
- HF-1:
- HF-2:
- HF-3:
Optional:
- HF-4:
- HF-5:

Optional helper block (recommended, not mandatory in output packs):
- MASKING_RISKS

---

## 3) CHECKLIST DEFINITIONS (DETERMINISTIC)
### Gate A (P0 first listen)
Definition:
- All P0 words are understood on first listen in the HOOK section.

### Gate B (P1 second listen)
Definition:
- P1 words are understood by second listen OR explicitly set to N/A.

### Gate C (no breath split inside P0 phrases)
Definition:
- If MUST_HEAR_PHRASES.P0 exists: no breath split occurs inside those phrases.
- If no phrases exist: Gate C = N/A with reason.

### Gate D (consonant attacks protected)
Definition:
- Onsets and final consonants of P0 words remain distinct (not swallowed).

### Gate E (hook clarity >= verse baseline)
Definition:
- Hook is at least as intelligible as verse baseline.
- If verse baseline not provided: Gate E = N/A with reason.

---

## 4) HARD FAILS (MANDATORY)
T04 must emit hard fails as binary triggers:
- HF-1: Any P0 word not understood on first listen in hook
- HF-2: Any breath split inside any P0 phrase (if phrases exist)
- HF-3: Any P0 consonant attack swallowed/masked (onset or tail)

Optional:
- HF-4: Hook clarity drops vs verse baseline
- HF-5: Stacking reduces P0 clarity (if stacking_used=YES)

Rule:
- If any hard fail is true → G3 cannot be PASS.

---

## 5) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Validate required inputs
- Confirm MUST_HEAR_WORDS exists
- Confirm HOOK_SECTION_LABEL exists
If missing → GAP.

Step 2 — Populate checklist A..E
- Fill each gate line with:
  - a short test statement
  - allowed N/A rule (only for B/C/E when applicable)

Step 3 — Populate hard fails HF-1..HF-3
- Tie them directly to P0 words/phrases (reference P0 list)

Step 4 — Add optional masking risks (if useful)
- If user provided notes about density/stacking/aggression:
  - list risk headings only (no mix advice)

Step 5 — Output blocks with stable names
- Ensure both blocks exist even if some gates are N/A.

---

## 6) STOP / GAP CONDITIONS
Stop and output GAP request if:
- MUST_HEAR_WORDS missing
- HOOK_SECTION_LABEL missing
- language not specified (do not infer; affects filler/phrase handling)

GAP request should ask only for missing fields.

---

## 7) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- claiming “it is intelligible” without an explicit test context
- rewriting lyrics to fix clarity
- giving plugin chains or mix/master recipes

Allowed:
- defining tests and fail triggers
- referencing P0/P1 lists and copy-exact phrases (if provided)

---

## 8) TRACE
TRACE:
- TOOL: T04
- OUTPUTS: INTELLIGIBILITY_GATES_CHECKLIST, HARD_FAIL_TRIGGERS (optional MASKING_RISKS)
- SUPPORTS_GATE: G3

--- END.
