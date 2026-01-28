# SPC PRO PACK — TOOL (T12) — TAKE_PACK_BUILDER (REPEATABLE) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/12__T12__TAKE_PACK_BUILDER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T12
TOOL_NAME: TAKE_PACK_BUILDER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T12.TAKE_PACK_BUILDER.001
OWNER: SYSTEM
ROLE: Builds a repeatable take direction pack for recording/generation: session intent, 2–4 goals per section, risk lines, repeatability rules (>=3), QC hard fails, and comp notes. No lyric edits, no mix/master chains.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T12 TAKE_PACK_BUILDER for VOCAL_DIRECTOR."
- REASON: "Without a disciplined take plan, sessions drift and comps become inconsistent."
- IMPACT: "Higher usable take rate and faster convergence."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T12.001

---

## 0) PURPOSE
Generate stable take/recording artifacts:
- SESSION_INTENT
- TAKE_GOALS_BY_SECTION
- RISK_LINES
- REPEATABILITY_RULES
- QC_HARD_FAILS
- (optional) QC_SOFT_FAILS
- COMP_NOTES

Supports Gate:
- G8 TAKE PACK

---

## 1) INPUTS (REQUIRED)
- section structure (Verse/Chorus/Hook)
- MUST_HEAR_WORDS.P0 (for QC hard fails)
Optional (recommended):
- MUST_HEAR_PHRASES.P0
- arc/levers (from T08)
- breath policy (from T09) and density scan (from T10)
- stacking decision (from T11)

Rules:
- If P0 missing → STOP (cannot define QC hard fails properly).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T12 MUST output:

### SESSION_INTENT
- identity:
- priorities:
- forbidden:

### TAKE_GOALS_BY_SECTION
- Verse:
  - goal:
  - goal:
  - goal: (optional)
  - goal: (optional)
- Chorus:
  - goal:
  - goal:
  - goal: (optional)
  - goal: (optional)

### RISK_LINES
- <Section>-L#:
  - excerpt:
  - risk:

### REPEATABILITY_RULES
- 1)
- 2)
- 3)
- 4) (optional)

### QC_HARD_FAILS
- HF-1:
- HF-2:
- HF-3:
- HF-4 (optional)

### COMP_NOTES
- 1)
- 2)
- 3)

Optional:
### QC_SOFT_FAILS
- SF-1:
- SF-2:

---

## 3) THRESHOLDS (STRICT)
- TAKE_GOALS_BY_SECTION:
  - 2..4 goals per section (hard)
  - chorus must include P0 clarity goal
- REPEATABILITY_RULES:
  - >=3 rules (hard)
  - must include fixed pronunciation for P0 across takes
- QC_HARD_FAILS:
  - must include:
    - HF-1 P0 not understood first listen in hook
    - HF-2 breath split inside P0 phrase (if phrases exist)
    - HF-3 stacking/texture masks P0 attacks (delivery-level)
- COMP_NOTES:
  - must include:
    - no comp across different P0 pronunciations
    - splice only outside P0 phrases
    - avoid mixing different vocal characters in comp

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Write SESSION_INTENT
- identity: 1 line (what this take is)
- priorities: 2–4 bullets (clarity first)
- forbidden: 2–4 bullets (no character switching, no P0 blur)

Step 2 — Build TAKE_GOALS_BY_SECTION
For each section:
- choose 2..4 goals:
  - clarity goal (P0 in hook mandatory)
  - arc goal (if present)
  - breath safety goal (if needed)
  - stacking goal (if used)
Keep goals executable (not vibe-only).

Step 3 — Build RISK_LINES
- mark 1..6 lines that are risky:
  - dense lines (from DENSITY_SCAN)
  - P0 phrase lines
  - stacking entry points
Use copy-exact excerpt (short).

Step 4 — Build REPEATABILITY_RULES (>=3)
Must include:
- keep P0 pronunciation constant across takes
- keep hook articulation policy constant
- keep intensity within a stable band (if intensity lever exists)
Optional:
- keep breath points consistent on risky lines

Step 5 — Build QC_HARD_FAILS
- include HF-1..HF-3 always
- add HF-4 only if needed (e.g., character switching)

Step 6 — Build COMP_NOTES
- include three required rules
- add one optional if needed (e.g., do not splice over consonant attacks)

Step 7 — Output blocks

---

## 5) STOP / GAP CONDITIONS
Stop and request missing inputs if:
- P0 missing
- section structure missing
- hook section unknown

---

## 6) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- rewriting lyrics
- mix/master plugin chains
- claiming “this take will work” without testing

Allowed:
- operational take goals and QC criteria

---

## 7) TRACE
TRACE:
- TOOL: T12
- OUTPUTS: SESSION_INTENT, TAKE_GOALS_BY_SECTION, RISK_LINES, REPEATABILITY_RULES, QC_HARD_FAILS, COMP_NOTES
- SUPPORTS_GATE: G8

--- END.
