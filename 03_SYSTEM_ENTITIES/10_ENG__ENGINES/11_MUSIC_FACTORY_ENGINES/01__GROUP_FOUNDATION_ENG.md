# Group Foundation Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.MF.GROUP_FOUNDATION.001
OWNER: SYSTEM
ROLE: Builds a deterministic “Group DNA” foundation (identity + style + cast + constraints) that all albums/tracks must obey.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; no semantic changes."
- REASON: "Compressed single-line formatting is error-prone during edits."
- IMPACT: "Safer copy/paste; easier review."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.GROUP_FOUNDATION.002

---

## 0) PURPOSE
This engine creates the **single source of truth** for a music group:
- identity + naming brief baseline
- genre/style direction and allowed fusion space
- **cast roster** (vocalists + instrumentalists + producer persona roles)
- signature “style fingerprint” anchors (to stay consistent)
- constraints (language, topic boundaries, tempo/mood ranges, taboo/negative specs)
- readiness for album blueprint + track factory

Output is meant to be used by:
- `11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`
- naming engines for group/album/track names

---

## 1) INPUTS (CONSUMES)
- Audience segment target (from CTL):
  `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md`
- Viral / UGC rules baseline (from CTL):
  `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md`
- Prompt contract constraints (from CTL):
  `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md`
- Catalog memory snapshot (from CTL):
  `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md`
- Optional: poet corpus preferences (PD-only policy):
  `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md`

---

## 2) OUTPUTS (PRODUCES)
Primary:
- **Group DNA Spec** (canonical group foundation document)

Secondary:
- **Cast Roster** (members list with style responsibilities)
- **Style Fingerprint** (anchors + forbidden overlaps)
- **Group Constraints Pack** (negative specs, language, content boundaries)
- **Take Log Entry** (registry record for decisions)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Audience Segments CTL",
  "UGC Viral Ruleset CTL",
  "Prompt Contract CTL",
  "Catalog Memory Snapshot",
  "PD Policy (optional)"
]
PRODUCES: [
  "Group DNA Spec",
  "Cast Roster",
  "Style Fingerprint",
  "Group Constraints Pack",
  "Take Log Entry"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS//GROUPS//"

---

## 4) BOUNDARIES (ANTI-DUPLICATION)

### In scope
- Group identity rules, cast composition, signature anchors, constraints.
- Defining “what makes this group unique” in a deterministic way.
- Preventing internal duplication (too-similar groups) using catalog memory.

### Out of scope
- Full album narrative and track ordering (handled by `03__ALBUM_BLUEPRINT_ENG`).
- Track-level prompts and generation variants (handled by `04__TRACK_FACTORY_ENG` + prompt compiler).
- Deep music theory composition decisions (handled by `09_SOUND_MUSIC_ENGINES/*`).
- Platform-specific packaging (handled by `06__RELEASE_PACK_ENG`).

---

## 5) WORKFLOW (OPERATIONAL STEPS)
1) **Audience Target Lock**
   - Choose primary segment + secondary segment(s) from `AUDIENCE_SEGMENTS_CTL`.
   - Output: segment ID(s) + why.

2) **Genre Direction**
   - Choose 1 core genre + 1 support genre.
   - Define allowable fusion radius (what may mix, what must not).
   - Use `GENRE_TAXONOMY_ENG` and `FUSION_RECIPE_ENG` if needed.

3) **Cast Construction (Members)**
   - Define required roles:
     - Vocals (lead, backing/duo, optional rap/chant)
     - Instruments (guitar/synth/bass/drums/folk instruments etc.)
     - Producer persona (mix aesthetic + arrangement taste)
   - Each member gets:
     - role, signature style, do/don’t, signature tricks, register/range (if vocals)

4) **Style Fingerprint Anchors**
   - Define 5–12 anchors:
     - tempo window(s), groove type, harmonic mood, timbre palette, “hook grammar”
   - Define forbidden overlaps (avoid sounding like previous catalog takes).

5) **Language + Content Constraints**
   - Language mode: RU by default.
   - PD-only lyric mode if enabled.
   - Negative specs library applied (ban-list / avoid-list).

6) **Collision Pre-Check (Group Level)**
   - Compare to catalog memory:
     - names similarity
     - style fingerprint similarity
     - cast similarity
   - If too close: mutate at least 2 anchors + 1 role.

7) **Package & Log**
   - Emit Group DNA Spec + Cast Roster + Constraints Pack.
   - Create Take Log record for traceability.

---

## 6) DECISION RULES (FACTORY LOGIC)
Hard rules:
- A group must have **one core identity sentence** (“who we are”) and **one sonic identity sentence** (“how we sound”).
- Minimum cast:
  - 1 vocal identity (even if instrumental project: “lead instrument” becomes voice-equivalent)
  - 1 rhythm identity (drums/groove driver)
  - 1 texture identity (pads/guitars/strings/folk timbre)
- Fingerprint anchors must include:
  - tempo window OR “energy curve”
  - hook grammar rule (repeat length / placement)
  - timbre palette
  - “no-go” list (negative specs)
- If PD-only lyrics enabled:
  - output must declare: `LYRICS_SOURCE_MODE: PD_ONLY` or `PD_PLUS_PATCHES`
- Must pass “group differentiation” threshold vs catalog memory.

---

## 7) FAILURE MODES & FIXES
1) **Group feels generic / no identity**
- Symptom: cannot describe group in 1–2 sentences; style tags are broad.
- Fix: add 2 unique anchors (instrument/timbre + hook grammar), add a “signature technique”.

2) **Too similar to an existing group**
- Symptom: collision pre-check triggers.
- Fix: mutate cast + change core genre support + change 3 anchors.

3) **Cast roles overlap / messy**
- Symptom: members doing same thing; no contrast.
- Fix: enforce role boundaries: lead vs texture vs rhythm.

4) **Prompt drift risk (AI improvises too much)**
- Symptom: model adds random genre elements.
- Fix: tighten constraints pack + stronger negative specs + shorter style tags.

Escalate to:
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md`

---

## 8) HANDOFFS (XREF)
NEXT ORC:
- `20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md`

NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/02__ARTIST_FACTORY_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md`

REQUIRED CTL:
- `08__AUDIENCE_SEGMENTS_CTL`
- `02__UGC_VIRAL_RULESET_CTL`
- `01__PROMPT_CONTRACT_CTL`
- `07__CATALOG_MEMORY_CTL`
- `12__NEGATIVE_SPEC_LIBRARY_CTL`

REQUIRED VAL:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md`

REQUIRED QA:
- `60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md`

---

## 9) OUTPUT PACK (MANDATORY LIST)
1) Primary artifact: **Group DNA Spec**
2) Secondary artifact: **Cast Roster**
3) Log record: **Take Log Entry**
4) Validation report: **Group Differentiation / Collision Pre-Check Report**

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
