# SPC PRO PACK — TOOL (T10) — DENSITY_RISK_SCAN (R0/R1/R2) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/10__T10__DENSITY_RISK_SCAN.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T10
TOOL_NAME: DENSITY_RISK_SCAN
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T10.DENSITY_RISK_SCAN.001
OWNER: SYSTEM
ROLE: Scans hook/section lyric lines for density and singability risks and outputs a deterministic DENSITY_SCAN with risk levels (R0/R1/R2), flags, and evidence. Does not rewrite lyrics; escalates when R2 indicates no safe breath points.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T10 DENSITY_RISK_SCAN for VOCAL_DIRECTOR."
- REASON: "Density traps cause forced breaths and intelligibility collapse; must be detected early."
- IMPACT: "Deterministic detection and correct escalation routing (T4)."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T10.001

---

## 0) PURPOSE
Generate density/singability risk block:
- DENSITY_SCAN

Supports Gate:
- G6 BREATH / SINGABILITY
Supports Cases:
- T2/T4 (breath split / unsingable density)

---

## 1) INPUTS (REQUIRED)
- section text split into lines (prefer hook/chorus)
- HOOK_SECTION_LABEL
Optional (recommended):
- MUST_HEAR_WORDS.P0 (to mark contains_P0)
- MUST_HEAR_PHRASES.P0 (to mark P0-embedded phrases)
- language label (RU/EN/etc.)

Rules:
- Tool does not infer missing lyrics; if section text missing → GAP.

---

## 2) OUTPUT BLOCK (STABLE NAME)
T10 MUST output:

### DENSITY_SCAN
For each line:
- line_id: <Section>-L#
  - risk_level: R0 | R1 | R2
  - contains_P0: YES/NO (optional but recommended)
  - flags:
    - F_...
  - evidence:
  - fix_hints:
    - 1)
    - 2) (optional)

---

## 3) FLAGS (DETERMINISTIC SET)
Use only this fixed flag set:

- F_LONG_CLAUSE_CHAIN
- F_CONSONANT_CLUSTER_HEAVY
- F_FAST_SYLLABLE_RUN
- F_P0_EMBEDDED
- F_NO_SAFE_BREATH_POINT
- F_MULTIPLE_MEANING_UNITS
- F_LINEBREAK_MISMATCH
- F_UNKNOWN (only if evidence exists but doesn’t fit)

---

## 4) RISK LEVEL DEFINITIONS (STRICT)
### R0 (SAFE)
- line has obvious safe breath points without splitting meaning units
- density moderate; articulation feasible

### R1 (RISK)
- line is dense but feasible with careful breath prep and articulation
- safe breath point exists but is tight

### R2 (UNSINGABLE RISK)
Any of the following triggers R2:
- F_NO_SAFE_BREATH_POINT is true AND line contains a must-hear phrase unit
- breath would have to occur inside a P0 phrase to be performable
- line requires continuous delivery across multiple meaning units with no safe break
- repeated dense clusters likely to cause clarity collapse under hook intensity

Rule:
- If any line is R2, the run must consider escalation (via T14) outside this tool.

---

## 5) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Normalize lines
- Assign line_id sequentially within the hook section:
  - <HOOK>-L1, <HOOK>-L2, ...

Step 2 — Mark contains_P0 (optional)
- If MUST_HEAR_WORDS.P0 provided:
  - contains_P0=YES if any P0 word appears in the line (copy match)
- Else omit contains_P0 field

Step 3 — Apply flag heuristics (simple, deterministic)
- F_LONG_CLAUSE_CHAIN:
  - line has multiple commas/dashes/clauses (>=2 separators) OR multiple conjunction chains
- F_FAST_SYLLABLE_RUN:
  - long uninterrupted word run (many tokens without punctuation/line break)
- F_CONSONANT_CLUSTER_HEAVY:
  - multiple consecutive consonant-heavy words (language-dependent; use conservative judgment and cite evidence)
- F_P0_EMBEDDED:
  - line contains a P0 phrase or multiple P0 words clustered
- F_LINEBREAK_MISMATCH:
  - line break splits an obvious meaning unit (as written)

Step 4 — Decide risk_level
- If F_NO_SAFE_BREATH_POINT applies based on structure (no punctuation/pauses) AND (F_P0_EMBEDDED OR F_MULTIPLE_MEANING_UNITS) → R2
- Else if two or more risk flags exist → R1
- Else → R0

Step 5 — Write evidence
Evidence must be concrete:
- mention the exact substring/line excerpt causing the flag (copy-exact snippet, short)

Step 6 — Write fix_hints (scope-safe)
Allowed fix hints (no lyric rewrite):
- "plan breath before the phrase onset"
- "reduce delivery intensity on this line (performance lever)"
- "avoid stacking on this line"
- "escalate to owner if no safe breath point exists (R2)"

Forbidden:
- rewriting words/lines
- mix/master plugin chains

Step 7 — Output DENSITY_SCAN

---

## 6) STOP / GAP CONDITIONS
Stop and request inputs if:
- hook section lines not provided
- language not specified AND line parsing is ambiguous (do not infer)

---

## 7) TRACE
TRACE:
- TOOL: T10
- OUTPUT: DENSITY_SCAN
- SUPPORTS_GATE: G6

--- END.
