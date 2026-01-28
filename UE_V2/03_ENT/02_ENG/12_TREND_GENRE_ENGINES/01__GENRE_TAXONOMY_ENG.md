# Genre Taxonomy Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 12_TREND_GENRE_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: TREND_GENRE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.TG.GENRE_TAXONOMY.001
OWNER: SYSTEM
ROLE: Maintains a compact genre taxonomy used by the Music Factory: defines genre families,
their audio DNA (tempo/groove/instrument palette/vocal delivery/structure/mix), and a compatibility graph for fusion.

Provides deterministic tags for Prompt Compiler.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created genre taxonomy engine: genre DNA schema, tag sets, compatibility graph, and selection workflow."
- REASON: "Without taxonomy, genre selection and blending becomes chaotic and inconsistent."
- IMPACT: "Faster planning, better compatibility, fewer prompt contradictions."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.GENRE.TAX.001
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; no semantic changes."
- REASON: "Compressed formatting is error-prone during edits."
- IMPACT: "Safer edits and easier audits."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.TG.GENRE.TAX.002

---

## 0) PURPOSE (LAW)
This engine defines **how the system talks about genres**.

It provides:
- a standard schema to describe any genre
- a controlled set of genre families and substyles
- compatibility rules for fusion
- deterministic tags for platforms (Suno/Udio)

---

## 1) INPUTS (CONSUMES)
- Trend signals / audience segments (what is demanded)
- Catalog memory (what we already did)
- Platform constraints (Suno/Udio behavior)
- Internal decisions (what genres we plan to cover)

---

## 2) OUTPUTS (PRODUCES)
### GENRE TAXONOMY (GTX)
- Genre Family list (stable)
- Genre DNA schema (mandatory fields)
- Default tag packs per family
- Compatibility Graph (A↔B pairing guidance)
- Anti-compatibility (bad mixes)

### GENRE SELECTION OUTPUT (on request)
- best-fit genre family for a group/album/track brief
- recommended fusion candidates (B/C)

### PROMPT TAGS DICTIONARY
- platform-ready tags and short instruction lines

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Trend / Audience signals (optional)",
  "Catalog Memory (optional)",
  "Platform constraints"
]
PRODUCES: [
  "Genre Taxonomy (GTX)",
  "Compatibility Graph",
  "Prompt Tags Dictionary",
  "Genre Selection Output (when requested)"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS//GENRE_TAXONOMY/"

---

## 4) GENRE DNA SCHEMA (MANDATORY)
Every genre entry must be described with the same fields:

- FAMILY_ID: (short code)
- NAME: (human name)
- CORE_TEMPO_BAND: (slow/medium/fast + approximate range)
- GROOVE_FEEL: (straight/half-time/swing/bounce/etc.)
- DRUM_SIGNATURE: (pattern character)
- BASS_SIGNATURE: (movement + pocket)
- HARMONY_COLOR: (simple/bright/dark/modal/etc.)
- MELODY_HOOK_STYLE: (chant/motif/anthemic/etc.)
- VOCAL_STYLE: (if used; delivery + articulation)
- STRUCTURE_DEFAULT: (fast hook / long build / verse-chorus, etc.)
- MIX_AESTHETIC: (dry/wide/lofi/clean/punchy)
- COMMON_INSTRUMENT_PALETTE: (short list)
- UGC_STRENGTH: (high/med/low)
- SAFE_FUSIONS: (recommended B genres)
- RISKY_FUSIONS: (allowed only with strict recipe)
- FORBIDDENS: (things that break identity)

---

## 5) DEFAULT GENRE FAMILIES (BASE SET)
Base set is intentionally compact. We expand later via governed updates.

- GTX-01: POP / MAINSTREAM  
  Hook-forward, clear vocals, simple structure, high UGC strength.

- GTX-02: TRAP / HIP-HOP  
  808 pocket, hats, rhythmic vocal phrasing, high UGC.

- GTX-03: PHONK / DRIFT  
  Aggressive bass, cowbell/lead motifs, high energy edits.

- GTX-04: EDM / DANCE  
  Drops, build-ups, club energy, strong loop potential.

- GTX-05: ROCK / ALT / POST-PUNK  
  Guitars, live-feel drums, anthemic or dark hooks.

- GTX-06: METAL / HARD  
  Heavy riffs, fast energy, niche but intense loyalty.

- GTX-07: FOLK / ETHNO  
  Acoustic/ethnic palette, storytelling, cultural vibe.

- GTX-08: CINEMATIC / EPIC  
  Big drums, orchestral elements, trailer-like tension.

- GTX-09: LOFI / CHILL  
  Soft textures, relaxed groove, study vibe.

- GTX-10: R&B / SOUL  
  Smooth vocals, groove pocket, emotional hooks.

- GTX-11: DNB / BREAKBEAT  
  Fast break grooves, high kinetic energy.

- GTX-12: HOUSE / TECH  
  Steady groove, dancefloor loopability.

Rule:
- A group/album chooses one **primary family** (A).
- Fusion Recipe handles secondary flavors (B/C).

---

## 6) COMPATIBILITY GRAPH (GUIDELINES)
Compatibility = “what axis can be borrowed safely”.

### High compatibility (generally safe)
- POP ↔ EDM (structure + drop)
- TRAP ↔ POP (hook clarity + 808 pocket)
- ROCK ↔ CINEMATIC (drama + guitars)
- PHONK ↔ EDM (energy + motifs)
- HOUSE ↔ POP (dance hook)

### Medium compatibility (needs recipe)
- TRAP ↔ ROCK (axis-limited: drums OR guitar)
- CINEMATIC ↔ TRAP (use in drop/bridge only)
- DNB ↔ POP (tempo and groove risk; use fragments)

### Low compatibility (usually avoid unless experimental)
- LOFI ↔ METAL
- FOLK ↔ PHONK
- R&B ↔ PHONK

This graph is guidance; Fusion Recipe makes final allowed plan.

---

## 7) GENRE SELECTION WORKFLOW (HOW TO USE)
1) Input: group foundation + target audience segment.
2) Choose primary family by:
   - hook preference
   - groove comfort
   - UGC strength requirement
3) Choose secondary B candidate:
   - must improve novelty or trend appeal
   - must respect fingerprint anchors
4) Output:
   - Primary A
   - 2–3 possible B options ranked
   - “forbiddens” list that Prompt Compiler will enforce

---

## 8) PLATFORM TAG DICTIONARY (OUTPUT)
For each family, engine must provide:
- SUNO_TAG_PACK (6–12 tags)
- UDIO_TAG_PACK (8–15 tags)
- 1–2 short instruction lines (what tags can’t express)

No long essays.
Tags must be consistent and reusable.

---

## 9) UPDATE POLICY (GOVERNED)
Taxonomy updates must be:
- additive or controlled edits
- logged and versioned
- compatible with existing catalog memory

No uncontrolled genre explosion.

---

## 10) HANDOFFS (XREF)
Used by:
- `12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md`
- `12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md`
- `12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
