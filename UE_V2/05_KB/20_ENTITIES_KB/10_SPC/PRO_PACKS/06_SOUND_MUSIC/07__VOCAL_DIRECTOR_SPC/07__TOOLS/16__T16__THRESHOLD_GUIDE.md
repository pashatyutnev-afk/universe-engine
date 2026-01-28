# SPC PRO PACK — TOOL (T16) — THRESHOLD_GUIDE (PASS/REWORK/FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/16__T16__THRESHOLD_GUIDE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T16
TOOL_NAME: THRESHOLD_GUIDE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T16.THRESHOLD_GUIDE.001
OWNER: SYSTEM
ROLE: Provides deterministic thresholds to classify outcomes as PASS/REWORK/FAIL for common VOCAL_DIRECTOR artifacts and gates. Outputs BORDERLINE_CLASSIFICATION with rationale and required rerun gates. Non-creative: does not propose lyric rewrites or mix chains.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T16 THRESHOLD_GUIDE for VOCAL_DIRECTOR."
- REASON: "Borderline decisions cause inconsistent verdicts; thresholds stabilize the workflow."
- IMPACT: "More consistent PASS/REWORK/FAIL decisions and fewer subjective loops."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T16.001

---

## 0) PURPOSE
Classify borderline cases consistently across gates and artifacts.

Outputs:
- BORDERLINE_CLASSIFICATION

Used in:
- POST-RUN READY review
- Any “is this good enough?” decision point

---

## 1) INPUTS (REQUIRED)
- gate_or_artifact: (G1..G9 or artifact block name)
- observed_status: (PASS/REWORK/FAIL candidate)
- evidence: short bullets (what was observed)

Optional:
- stacking_used YES/NO
- phrases_present YES/NO

Rule:
- Tool does not claim observation by itself; it classifies based on provided evidence.

---

## 2) OUTPUT BLOCK (STABLE NAME)
T16 MUST output:

### BORDERLINE_CLASSIFICATION
- gate_or_artifact:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- rerun_gates:
  - G? (optional)
- stop_until_fixed: YES/NO

---

## 3) THRESHOLDS (DETERMINISTIC)
### G1 INPUT READINESS
PASS:
- all min inputs YES (lyrics + structure + language + hook identifiable)
REWORK:
- minor ambiguity (e.g., 2 hook candidates) but usable with explicit selection
FAIL:
- any missing min input

stop_until_fixed:
- YES for FAIL

---

### G2 MUST-HEAR (Targets)
PASS:
- P0 exists AND count 3..8 (or 2 with explicit short-hook note)
- fillers not in P0
REWORK:
- P0 count 9..10 OR includes 1–2 filler items OR phrases missing where meaning is phrase-based
FAIL:
- P0 missing OR wildly bloated (>10) OR targets include invented words

rerun:
- G2 (then verify G3)

stop_until_fixed:
- YES for FAIL

---

### G3 INTELLIGIBILITY
PASS:
- HF-1/HF-2/HF-3 are all cleared (no hard fails)
REWORK:
- minor, localized clarity issue not affecting P0 first-listen consistently (requires small patch)
FAIL:
- any hard fail true:
  - HF-1 P0 not understood first listen
  - HF-2 breath split inside P0 phrase (if phrases exist)
  - HF-3 consonant attacks swallowed

rerun:
- G3 (and G6 or G7 if those axes changed)

stop_until_fixed:
- YES for FAIL

---

### G4 DELIVERY COHERENCE
PASS:
- contradictions_found=NO AND executability_ok=YES
- profile principles <=6 and actionable
REWORK:
- 1 contradiction or 1 vibe-only principle can be pruned
FAIL:
- multiple contradictions OR profile overload (>>6) OR non-executable

rerun:
- G4 (verify G3 if delivery changes affect clarity)

stop_until_fixed:
- YES for FAIL

---

### G5 ARC / CONTRAST
PASS:
- chorus lift present AND levers <=3 AND QC checks satisfied
REWORK:
- lever count = 3 but settings vague, or lift too subtle/too harsh (needs tighten)
FAIL:
- lever overload (>3) OR flat arc (no lift) OR contradictions with clarity

rerun:
- G5 (verify G3 if intensity/texture levers change)

stop_until_fixed:
- YES for FAIL

---

### G6 BREATH / SINGABILITY
PASS:
- forbidden splits defined AND no breath split inside P0 phrases
- no R2 “no safe breath point” unresolved
REWORK:
- breath policy exists but missing one explicit forbidden split OR R1 dense line needs tighter guidance
FAIL:
- any R2 with no escalation OR breath splits inside P0 phrases

rerun:
- G6 → G3

stop_until_fixed:
- YES for FAIL

---

### G7 STACKING SAFE
PASS:
- if stacking_used=NO: explicit N_A decision exists
- if stacking_used=YES: protected zones + QC rules exist and P0 clarity preserved
REWORK:
- stacking_used=YES but plan is too broad and needs pruning (still has protected zones)
FAIL:
- stacking_used=YES but protected zones/QC missing OR stacking masks P0 (hard)

rerun:
- G7 → G3

stop_until_fixed:
- YES for FAIL

---

### G8 TAKE PACK
PASS:
- goals per section 2..4
- repeatability rules >=3
- QC hard fails include HF-1..HF-3
- comp notes include “no comp across pronunciations”
REWORK:
- one element missing (e.g., rules count 2, or one hard fail missing)
FAIL:
- take pack missing OR QC hard fails missing OR goals are vibe-only

rerun:
- G8

stop_until_fixed:
- YES for FAIL

---

### G9 SCOPE COMPLIANCE
PASS:
- F1..F5 all NO
REWORK:
- F2/F3 ownership language present but can be converted to escalation
FAIL (HARD):
- F1 YES (lyric rewrite present)
- F4 YES (mix/master chain present)
- F5 YES (guessing) that affects decisions

rerun:
- G9

stop_until_fixed:
- YES for FAIL

---

## 4) NOTE ON “ONE-AXIS”
If STATUS is REWORK:
- recommend a single-axis repair route via T15 (do not stack fixes).

---

## 5) TRACE
TRACE:
- TOOL: T16
- OUTPUT: BORDERLINE_CLASSIFICATION
- USED_IN: POST_RUN + borderline decisions

--- END.
