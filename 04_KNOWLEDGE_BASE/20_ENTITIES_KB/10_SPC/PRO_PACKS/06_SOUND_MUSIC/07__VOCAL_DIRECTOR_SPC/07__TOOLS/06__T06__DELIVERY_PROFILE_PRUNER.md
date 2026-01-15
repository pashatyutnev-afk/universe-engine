# SPC PRO PACK — TOOL (T06) — DELIVERY_PROFILE_PRUNER (<=6 PRINCIPLES) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/06__T06__DELIVERY_PROFILE_PRUNER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T06
TOOL_NAME: DELIVERY_PROFILE_PRUNER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T06.DELIVERY_PROFILE_PRUNER.001
OWNER: SYSTEM
ROLE: Builds a minimal, executable delivery profile (<=6 principles) and a short forbidden styles list (2–5). Prunes vague or contradictory instructions. Produces stable blocks for Gate G4.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T06 DELIVERY_PROFILE_PRUNER for VOCAL_DIRECTOR."
- REASON: "Bloated or vibe-only profiles cause drift and invalidate downstream gates."
- IMPACT: "Coherent, repeatable vocal identity and faster sessions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T06.001

---

## 0) PURPOSE
Generate stable profile blocks:
- VOCAL_STYLE_PROFILE
- FORBIDDEN_STYLES

Supports Gate:
- G4 DELIVERY COHERENCE

---

## 1) INPUTS (REQUIRED)
- language label (RU/EN/etc.)
Optional:
- genre/style tags provided by user
- vocal mode (rap/sing/mixed)
- any existing draft profile notes

Rules:
- If no style notes exist, T06 produces a safe minimal default profile based on input tags ONLY (no invented micro-details).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T06 MUST output:

### VOCAL_STYLE_PROFILE
- delivery_principles:
  1)
  2)
  3)
  4)
  5) (optional)
  6) (optional)

### FORBIDDEN_STYLES
- 1)
- 2)
- 3) (optional)
- 4) (optional)
- 5) (optional)

---

## 3) THRESHOLDS (STRICT)
- delivery_principles count: 4..6 (hard max = 6)
- forbidden styles count: 2..5
- principles must be performer-actionable (not “more vibe”)
- no mix/master chains or DAW recipes

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Collect candidate principles (from user notes/tags)
- Convert tags into actionable constraints:
  - articulation
  - intensity band
  - texture usage window
  - timing feel
  - character consistency

Step 2 — Prune for executability
- Remove duplicates
- Remove vague items (“be cool”, “more energy”)
- Keep strongest 4..6

Step 3 — Enforce non-contradiction (basic)
- If a principle conflicts (e.g., “very clean” + “very lo-fi”):
  - keep the one aligned with user intent OR
  - rewrite into section-conditional note ONLY if section split exists (otherwise drop)

Step 4 — Build forbidden styles list (2..5)
Must include at least:
- intelligibility protection:
  - "do not swallow consonant attacks on P0"
- drift protection:
  - "do not switch vocal character between takes"
Then add 0–3 genre-specific forbids if provided.

Step 5 — Emit stable blocks

---

## 5) DEFAULT SAFE PROFILE (IF INPUTS MINIMAL)
If only language + generic genre tags exist:
- output 4 principles:
  1) clear consonant-forward delivery
  2) stable intensity band in hook
  3) texture (grit) only as accent, not on P0 attacks
  4) consistent character across takes
Forbidden styles:
  - swallow consonants
  - character switching
(+ optional genre forbids if given)

---

## 6) STOP / GAP CONDITIONS
Stop (GAP) if:
- language not provided (do not infer; affects word class and articulation context)
Otherwise proceed with defaults.

---

## 7) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- plugin chains or mixing instructions
- rewriting lyrics
- inventing complex story context for the singer

Allowed:
- minimal performer constraints based on provided tags

---

## 8) TRACE
TRACE:
- TOOL: T06
- OUTPUTS: VOCAL_STYLE_PROFILE, FORBIDDEN_STYLES
- SUPPORTS_GATE: G4

--- END.
