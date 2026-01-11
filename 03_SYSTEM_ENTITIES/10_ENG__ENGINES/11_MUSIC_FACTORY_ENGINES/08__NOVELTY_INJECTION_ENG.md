# Novelty Injection Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.MF.NOVELTY_INJECTION.001
OWNER: SYSTEM
ROLE: Injects controlled novelty (mutation) to avoid sameness while preserving group identity: modifies limited axes with guardrails and re-validates collisions.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Novelty Injection Engine: mutation menu, guardrails, and re-validation loop."
- REASON: "When collisions persist, we need deliberate novelty without destroying brand sound."
- IMPACT: "Catalog stays fresh while remaining recognizable."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.NOVELTY_INJECTION.001

---

## 0) PURPOSE
This engine is used only when:
- Catalog Collision Engine reports repeated SOFT/HARD collisions, OR
- Outputs feel “samey” even if not strictly colliding, OR
- A group is stagnating and needs “next level” evolution.

It produces a **Mutation Plan** + an updated brief/prompt package and forces re-check.

---

## 1) INPUTS (CONSUMES)
- Group DNA Spec (identity anchors to preserve)
- Artist Roster Spec (who can mutate and who must remain stable)
- Album Blueprint slot or Track Candidate Pack
- Collision Report + Fix Plan (from `07__CATALOG_COLLISION_ENG`)
- Negative Spec library (what must never happen)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- **Novelty Mutation Pack** (mutation plan + updated fingerprint)

Secondary:
- **Updated Track Brief / Album Slot Brief** (with novelty changes)
- **Re-Check Instruction** (must run collision again)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group DNA Spec",
  "Artist Roster Spec",
  "Track/Album Candidate",
  "Collision Report + Fix Plan",
  "Negative Spec Library CTL"
]
PRODUCES: [
  "Novelty Mutation Pack",
  "Updated Brief (track/album)",
  "Updated Style Fingerprint",
  "Re-Validation Request"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/CATALOG/NOVELTY/"

---

## 4) NOVELTY PRINCIPLES (NON-NEGOTIABLE)
1) Preserve **core identity anchors** (2–4) from Group DNA.
2) Mutate only **limited axes** per injection (2–4 axes).
3) Avoid “random weirdness”; every mutation must have a purpose:
   - stronger hook
   - more contrast
   - new timbre color
   - new rhythm language
4) Re-check collisions after mutation.

---

## 5) MUTATION MENU (ALLOWED AXES)
Choose 2–4 axes max per run:

### A) Hook Architecture
- move hook earlier/later
- swap hook type (phrase ↔ rhythm ↔ melody ↔ call-response)
- change repeat grammar (shorter phrase, different spacing)

### B) Intro Signature
- new intro instrument order
- replace opening motif
- change density (minimal → punch)

### C) Groove / Rhythm Language
- straight ↔ half-time ↔ swing-feel
- new percussion texture
- different drum pattern archetype

### D) Timbre Palette
- swap lead texture instrument family (guitar ↔ synth ↔ folk)
- change saturation/cleanliness
- change space (dry ↔ wide)

### E) Vocal Delivery (if vocal track)
- clean ↔ raspy ↔ whispery ↔ chant
- register shift (mid ↔ higher)
- articulation shift (tight ↔ loose)

### F) Fusion Spice (careful)
- add 1 “spice” genre element at 5–10% presence
- must not break core genre identity

### G) Lyric Strategy (PD mode)
- switch to different juice set
- enforce mosaic blend (multi-source)
- avoid famous lines

---

## 6) GUARDRAILS (WHAT MUST NOT CHANGE)
Must remain stable:
- group promise (identity sentence)
- primary genre direction (unless “evolution” explicitly allowed)
- 1–2 signature anchors (e.g., timbre + hook grammar baseline)
- forbidden list from negative specs

If mutation violates guardrails → discard mutation.

---

## 7) WORKFLOW (OPERATIONAL STEPS)
1) Read collision vectors that triggered.
2) Select mutation axes targeting those vectors.
3) Apply guardrails: lock core anchors.
4) Produce updated style fingerprint and updated brief.
5) Output updated prompt guidance (what to change in prompt).
6) Mandatory re-check:
   - run `07__CATALOG_COLLISION_ENG` again
   - run validators/QA light gates

---

## 8) FAILURE MODES & FIXES
1) Mutation breaks identity
- Fix: reduce axes; restore anchors; use only intro/groove changes.

2) Still colliding after mutation
- Fix: change different axes set; if 2 failed attempts → enforce hard mutation (4 axes) or discard.

3) Mutation makes prompt too complex
- Fix: compress instructions; keep tags short; prioritize 3 constraints max.

---

## 9) HANDOFFS (XREF)
NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md` (mandatory re-check)
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` (regenerate variants)
- `11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md` (log injection)

REQUIRED VAL/QA:
- `05__COLLISION_BLOCKER_VAL`
- `03__REPEAT_GUARD_VAL`
- `07__CATALOG_DIFFERENTIATION_QA`

---

## 10) OUTPUT PACK (MANDATORY LIST)
1) Novelty Mutation Pack (axes + changes)
2) Updated Style Fingerprint (anchors preserved + mutated anchors)
3) Updated Brief (track/album)
4) Prompt delta notes (what to replace)
5) Re-Validation Request

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
