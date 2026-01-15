# SPC PRO PACK — TOOL (T08) — ARC_LEVER_SELECTOR (<=3 LEVERS) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/08__T08__ARC_LEVER_SELECTOR.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T08
TOOL_NAME: ARC_LEVER_SELECTOR
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T08.ARC_LEVER_SELECTOR.001
OWNER: SYSTEM
ROLE: Builds a minimal performance arc map and selects <=3 contrast levers with explicit verse→chorus settings, plus QC checks ensuring lift without sacrificing intelligibility. No mixing advice, no lyric edits.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T08 ARC_LEVER_SELECTOR for VOCAL_DIRECTOR."
- REASON: "Arc drift and lever overload are common causes of flat hooks or chaotic delivery."
- IMPACT: "Controlled lift with minimal performer overload."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T08.001

---

## 0) PURPOSE
Generate arc/contrast blocks:
- PERFORMANCE_ARC_MAP
- CONTRAST_LEVERS
- QC_ARC_CHECKS

Supports Gate:
- G5 ARC / CONTRAST

---

## 1) INPUTS (REQUIRED)
- section structure (at least Verse + Chorus/Hook labels)
Optional:
- delivery profile (VOCAL_STYLE_PROFILE)
- intelligibility constraints (P0 targets / hard fails)
- user intent (mood/genre tags)

Rules:
- If section structure is missing → STOP (needs T01/G1).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T08 MUST output:

### PERFORMANCE_ARC_MAP
- Verse:
- Chorus (HOOK):
- Bridge (optional):
- Final Chorus (optional):

### CONTRAST_LEVERS
- lever: L1
  - verse_setting:
  - chorus_setting:
- lever: L2 (optional)
  - verse_setting:
  - chorus_setting:
- lever: L3 (optional)
  - verse_setting:
  - chorus_setting:

### QC_ARC_CHECKS
- chorus_lift_present: YES/NO
- lever_count_ok (<=3): YES/NO
- intelligibility_preserved: YES/NO
- bridge_contrast_present: YES/NO or N/A

---

## 3) LEVER CANDIDATES (DETERMINISTIC SET)
Choose from this fixed lever set (no new lever invention):
- L1 Intensity band (low→high)
- L2 Texture amount (clean→grit) (must not mask P0 attacks)
- L3 Articulation precision (relaxed→crisp)
- L4 Timing tightness (loose→tight)
- L5 Pitch/melodic lift (flat→more melodic) (if applicable)

Rule:
- Select 1..3 levers only (hard max = 3).
- Prefer levers that preserve P0 clarity.

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Build arc skeleton
- Map Verse baseline
- Map Chorus as lift/release
- Add Bridge/Final chorus only if structure includes them

Step 2 — Select levers (<=3)
Priority:
1) L1 intensity (nearly always)
2) L3 articulation precision (clarity-safe)
3) L2 texture or L4 timing depending on genre intent
Avoid selecting L2 if it risks masking P0.

Step 3 — Define explicit verse→chorus settings
- Use concise, executable settings (no vibe-only)
Example:
- verse_setting: "controlled, medium intensity"
- chorus_setting: "higher intensity but keep consonant attacks clean"

Step 4 — Emit QC_ARC_CHECKS
- chorus_lift_present: YES (if chorus settings increase at least 1 lever vs verse)
- lever_count_ok: YES if <=3
- intelligibility_preserved: default YES only if levers chosen are clarity-safe
  - if L2 texture increased heavily, set to UNCERTAIN via NO and require verify G3 (handled outside tool)

Step 5 — Output blocks

---

## 5) STOP / GAP CONDITIONS
Stop if:
- structure/section labels missing
- hook section unknown

Request:
- Verse/Chorus labels and which section is hook.

---

## 6) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- mix/master chains or plugin recipes
- lyric rewrites
- claiming “intelligibility preserved” as observed fact without test

Allowed:
- defining intended settings and requiring verify G3 after applying arc

---

## 7) TRACE
TRACE:
- TOOL: T08
- OUTPUTS: PERFORMANCE_ARC_MAP, CONTRAST_LEVERS, QC_ARC_CHECKS
- SUPPORTS_GATE: G5

--- END.
