# SPC PRO PACK — TOOL (T07) — CONTRADICTION_DETECTOR (COHERENCE_CHECK) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/07__T07__CONTRADICTION_DETECTOR.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T07
TOOL_NAME: CONTRADICTION_DETECTOR
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T07.CONTRADICTION_DETECTOR.001
OWNER: SYSTEM
ROLE: Detects contradictions and non-executable instructions in the delivery profile and related constraints. Outputs a compact COHERENCE_CHECK verdict and a contradiction list without prescribing production/mixing solutions. Supports Gate G4.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T07 CONTRADICTION_DETECTOR for VOCAL_DIRECTOR."
- REASON: "Profiles often contain conflicting constraints; must be flagged deterministically."
- IMPACT: "Cleaner profiles and fewer drift regressions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T07.001

---

## 0) PURPOSE
Evaluate internal coherence of direction constraints and output:
- COHERENCE_CHECK
- CONTRADICTIONS_LIST (helper)

Supports Gate:
- G4 DELIVERY COHERENCE

---

## 1) INPUTS (REQUIRED)
- VOCAL_STYLE_PROFILE (from T06) OR any profile draft text
Optional:
- FORBIDDEN_STYLES
- arc notes (if present)

Rules:
- This tool does not “fix”; it flags contradictions and executability risks.
- No invented constraints.

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T07 MUST output:

### COHERENCE_CHECK
- contradictions_found: YES/NO
- executability_ok: YES/NO
- reasons:
  - 1)
  - 2) (optional)
  - 3) (optional)

Optional helper block (recommended, not mandatory in output packs):
- CONTRADICTIONS_LIST:
  - C-1:
  - C-2:

---

## 3) CONTRADICTION TYPES (DETERMINISTIC)
Flag as contradictions if any pair implies mutually exclusive execution without an explicit section split:

- Texture contradiction:
  - “very clean” AND “constant heavy grit” (same section)
- Intensity contradiction:
  - “soft intimate” AND “full shout” (same section)
- Timing contradiction:
  - “tight staccato” AND “lazy behind-the-beat” (same phrase)
- Character contradiction:
  - “single stable persona” AND “multiple characters every line”
- Clarity contradiction:
  - “words must be crystal clear” AND “bury consonants / slur as style”

Executability risks (not strict contradictions):
- >6 principles (overload)
- vibe-only items with no action (non-actionable)
- multiple goals assigned to the same micro-moment (over-constrained)

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Extract claims
- Turn each principle into a normalized “claim” (texture/intensity/timing/character/clarity)

Step 2 — Pairwise check for contradictions
- Compare claims within same implied scope (hook/verse/overall)
- If no section split is specified, assume same scope

Step 3 — Evaluate executability
- executability_ok=YES only if:
  - principles <=6
  - no contradictions that require split
  - constraints are actionable enough to execute

Step 4 — Emit COHERENCE_CHECK
- contradictions_found YES if any contradiction flagged
- reasons must be 1–3 concise bullets

Step 5 — Emit CONTRADICTIONS_LIST (optional helper)
- list each contradiction with type + involved principles

---

## 5) STOP / GAP CONDITIONS
Stop (GAP) if:
- no profile input exists at all (VOCAL_STYLE_PROFILE missing and no draft)
Request:
- “Provide style profile draft or tags to build one (T06).”

---

## 6) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- prescribing mix/master chains as a “fix”
- rewriting lyrics
- inventing missing principles

Allowed:
- stating that a contradiction exists
- recommending routing to PB-01 for pruning (without implementing inside T07)

---

## 7) TRACE
TRACE:
- TOOL: T07
- OUTPUT: COHERENCE_CHECK (optional CONTRADICTIONS_LIST)
- SUPPORTS_GATE: G4

--- END.
