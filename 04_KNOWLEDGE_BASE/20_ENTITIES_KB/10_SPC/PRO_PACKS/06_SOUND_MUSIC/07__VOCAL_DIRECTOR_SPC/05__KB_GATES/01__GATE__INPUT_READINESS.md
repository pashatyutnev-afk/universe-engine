# SPC PRO PACK — GATE (G1) — INPUT READINESS (STOP/GAP) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/01__GATE__INPUT_READINESS.md

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
ROLE: Gate G1 checks that minimum required inputs exist before any vocal direction is produced. This gate is STOP/GAP: it prevents guessing and prohibits “vibe-only” direction when lyrics/structure/language are missing.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G1: Input Readiness (STOP/GAP) for VOCAL_DIRECTOR Pro Pack."
- REASON: "VOCAL_DIRECTOR output must be anchored to lyrics + structure + language; otherwise it becomes non-deterministic and violates no-guessing."
- IMPACT: "Prevents invalid runs; forces explicit intake and missing-field reporting."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.INPUT.001

---

## 0) PURPOSE
This gate answers:
- Do we have enough inputs to run VOCAL_DIRECTOR responsibly?

If not:
- STOP and mark GAP (do not proceed to other gates).

---

## 1) REQUIRED INPUTS (MINIMUM)
MINIMUM_INPUTS (must exist):
- I1: LYRIC_DRAFT
  - at least chorus/hook lines (or the main message lines)
  - verse placeholders acceptable for first pass
- I2: SECTION STRUCTURE
  - explicit section list (Intro/Verse/Chorus/Bridge/Outro) OR a LOOP PROFILE
- I3: LANGUAGE
  - language label + any known pronunciation/stress risks (if known)

Recommended inputs (not required for PASS):
- R1: Lyrics variants
- R2: Topline constraints / accent points
- R3: Tempo/groove notes
- R4: Arrangement seat map (density/space)
- R5: Sonic identity ruleset (from Music Supervisor)

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if:
- I1, I2, I3 are present AND
- LYRIC_DRAFT is not empty AND
- SECTION STRUCTURE is unambiguous (hook section identifiable)

### REWORK
REWORK if:
- minimum inputs exist, but structure is weak/ambiguous, such that hook section cannot be confidently identified
Example:
- structure provided as a paragraph without section list; hook location unclear
Fix:
- request a minimal section list (no ownership change; just clarification)

### FAIL (STOP/GAP)
FAIL if ANY minimum input is missing:
- missing LYRIC_DRAFT OR
- missing SECTION STRUCTURE/LOOP PROFILE OR
- missing LANGUAGE

FAIL must be treated as:
- STOP/GAP (no further gates are run)

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN IN OUTPUT)
To claim PASS, the run must show evidence fields:
EVIDENCE_BLOCK:
- LYRIC_DRAFT_PRESENT: YES/NO
- SECTION_STRUCTURE_PRESENT: YES/NO
- LANGUAGE_PRESENT: YES/NO
- HOOK_SECTION_IDENTIFIABLE: YES/NO
- MISSING_FIELDS (if any): list

If FAIL:
- must list exact missing fields (I1/I2/I3).

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If FAIL (STOP/GAP):
- Apply: PB-01 (Intake & GAP check step)
- Action: request missing inputs (explicit list)

If REWORK:
- Apply: PB-01 (Intake normalization)
- Action: convert structure into minimal section list; clarify hook section label

No other playbooks may run until G1 PASS.

---

## 5) COMMON FAIL MODES (WHAT TO CATCH)
- “Write vocal direction” but no lyrics provided (impossible)
- “Make chorus bigger” but no structure/hook specified
- Unknown language → pronunciation/stress work becomes guessing
- Vague structure (“there’s a drop later”) without section map

---

## 6) OUTPUT FORMAT (MANDATORY)
G1_RESULT:
- VERDICT: PASS | REWORK | FAIL(STOP/GAP)
- EVIDENCE_BLOCK:
  - LYRIC_DRAFT_PRESENT:
  - SECTION_STRUCTURE_PRESENT:
  - LANGUAGE_PRESENT:
  - HOOK_SECTION_IDENTIFIABLE:
  - MISSING_FIELDS:
- NEXT_STEP:
  - if PASS: "Proceed to G2 MUST-HEAR TARGETS"
  - if REWORK: "Request clarified section list / hook section"
  - if FAIL: "Request missing minimum inputs"

--- END.
