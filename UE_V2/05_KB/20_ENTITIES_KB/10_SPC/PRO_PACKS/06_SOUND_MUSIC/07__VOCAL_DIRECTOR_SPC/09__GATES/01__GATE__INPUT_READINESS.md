# SPC PRO PACK — GATE (G1) — INPUT READINESS (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/01__GATE__INPUT_READINESS.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
OWNER: SYSTEM
ROLE: Gate G1 verifies minimum input readiness for VOCAL_DIRECTOR work: lyrics exist, structure exists, language is known, and hook section is identifiable. This is a hard-stop gate.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G1 INPUT READINESS for VOCAL_DIRECTOR."
- REASON: "Without minimum inputs, any direction becomes guessing and non-auditable."
- IMPACT: "Forces intake discipline and deterministic downstream tooling."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G1.001

---

## 0) PURPOSE
Determine if the run may proceed beyond intake.

If FAIL:
- STOP RUN (no further gates/tools).

---

## 1) REQUIRED INPUTS (MINIMUM)
- Lyrics: at least HOOK/CHORUS lines (minimum viable)
- Structure: section list OR loop profile that identifies hook moment
- Language label (RU/EN/etc.)
- Hook section identifiable

Optional (not required for PASS):
- tempo/groove notes
- vocal mode
- arrangement notes

---

## 2) REQUIRED ARTIFACTS (FROM TOOLS)
G1 requires these artifact blocks to exist (stable names):
- MIN_INPUTS_CHECK
- HOOK_SECTION_LABEL
- GAP_REPORT
- NEXT_STEP

Origin tool:
- T01 INTAKE_NORMALIZER

---

## 3) PASS / REWORK / FAIL (THRESHOLDS)
### PASS if ALL are true:
- LYRIC_DRAFT_PRESENT = YES
- SECTION_STRUCTURE_PRESENT = YES
- LANGUAGE_PRESENT = YES
- HOOK_SECTION_IDENTIFIABLE = YES

### REWORK (rare) if:
- all minimum fields exist BUT hook identification is ambiguous in naming only
- and can be resolved by a trivial relabel (no new data needed)
Rule:
- REWORK must still output a concrete HOOK_SECTION_LABEL candidate list (max 2).

### FAIL if ANY is true:
- any minimum field is missing (lyrics/structure/language)
- hook cannot be identified from provided structure
- intake is “vibe request” with no lyrics/structure (STOP/GAP)

Hard stop rule:
- If FAIL → do not proceed to G2..G9.

---

## 4) OUTPUT (G1 VERDICT BLOCK)
Gate output must be expressed as:

G1_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G2 MUST-HEAR (T02/T03)"
  - if REWORK: "Resolve hook label ambiguity; rerun T01; then proceed"
  - if FAIL: "Request missing fields; rerun T01"

---

## 5) FIX ROUTE
Primary fix tool:
- T01 INTAKE_NORMALIZER

If FAIL:
- request missing fields using T01 GAP_REPORT.REQUEST_TEXT format
- rerun T01 and re-evaluate G1

---

## 6) VIOLATIONS / ANTI-GUESSING
Forbidden at G1:
- guessing the hook without structure
- inventing language or lyrics
- proceeding to later gates on incomplete intake

---

## 7) TRACE
TRACE:
- GATE: G1
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- TOOL: T01

--- END.
