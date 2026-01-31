# Naming Generation Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/02__NAMING_GENERATION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 14_NAMING_IDENTITY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: NAMING_IDENTITY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.NAMING.NAMING_GENERATION.001
OWNER: SYSTEM
ROLE: Generates a structured set of name candidates from a Naming Brief:
core names, alternates, and style-bucketed variants (one-word, phrase, codename, subtitle).

Outputs a Name Candidates Pack (NC) for collision checking and platform formatting.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Naming Generation: candidate buckets, deterministic procedure, and output schema."
- REASON: "We need consistent, scalable naming generation that follows a brief and avoids cheap clichés."
- IMPACT: "More high-quality names, easier collision filtering, better platform titles."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.NAMING.GENERATION.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Дай список сильных названий, которые соответствуют Naming Brief.”**

It must:
- generate candidates in multiple “buckets” (formats)
- obey constraints (language/length/form/forbiddens)
- include a “core name” subset (top picks)
- include alternates for A/B tests and safe fallbacks

---

## 1) INPUTS (CONSUMES)
- Naming Brief (NB)
- Keywords Pack (must/should/avoid)
- Catalog used names (optional snapshot for soft avoidance)
- Optional: Series rules (if naming series)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- NAME_CANDIDATES_PACK (NC)

Secondary:
- CORE_SHORTLIST (top 5–15)
- THEME TAGS per candidate (for later organization)
- “Generation Notes” (what strategies were used)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Naming Brief (NB)",
  "Keywords Pack",
  "Catalog used names (optional)",
  "Series rules (optional)"
]
PRODUCES: [
  "Name Candidates Pack (NC)",
  "Core Shortlist",
  "Theme tags per candidate",
  "Generation notes"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS//NAMING/CANDIDATES/"

---

## 4) CANDIDATE BUCKETS (STANDARD SET)
Generate candidates in buckets to avoid “samey” outputs:

B1 — ONE-WORD (1 word, strong stamp)
B2 — TWO-WORD (compact phrase)
B3 — PHRASE (3–6 words, lyrical)
B4 — CODE-NAME (short codename / industrial / numeric)
B5 — SYMBOLIC (metaphor / imagery)
B6 — SUBTITLE FORM (Core: Subtitle) (optional)
B7 — RU / EN variants (if language=MIX)

Each bucket should output 5–20 candidates depending on needs.

---

## 5) GENERATION RULES (MUST OBEY)
- obey LANGUAGE constraint
- obey LENGTH_RULE (max words)
- obey FORM constraint (if strict)
- respect MUST_USE and AVOID lists
- no profanity unless explicitly allowed
- avoid cheap cliché patterns (from forbiddens)
- avoid duplicates and near-duplicates of existing names when possible (soft)

---

## 6) PROCEDURE (DETERMINISTIC)
1) Load Naming Brief NB.
2) Extract:
   - TARGET_TYPE, tone, themes, aesthetics
   - constraints: language/length/form
   - MUST_USE / SHOULD_USE / AVOID
3) Choose active buckets:
   - always include B1..B3
   - include B4..B6 if brief allows
4) Generate candidates per bucket:
   - use themes + imagery + genre/mood signals
   - produce variations by:
     - synonym swap
     - imagery swap
     - word order swap
     - “sharp vs soft” style variant
5) Filter:
   - remove forbidden patterns
   - remove candidates violating length/form
   - remove exact duplicates
6) Rank roughly:
   - assign “strength score” 0–10 based on:
     - memorability
     - clarity
     - uniqueness
     - fit with tone
7) Output NC Pack + Core shortlist.

---

## 7) OUTPUT SCHEMA (MANDATORY)

### NAME_CANDIDATES_PACK (NC)
- TARGET_TYPE:
- TARGET_UID:
- LANGUAGE:
- DATE:
- BUCKETS:
  - B1_ONE_WORD:
    - candidate: {name, score_0_10, theme_tags, notes}
  - B2_TWO_WORD:
    - ...
  - B3_PHRASE:
    - ...
  - B4_CODE_NAME:
    - ...
  - B5_SYMBOLIC:
    - ...
  - B6_SUBTITLE (optional):
    - ...
- CORE_SHORTLIST:
  - list of 5–15 best candidates (name + why 1 line)
- GENERATION_NOTES:
  - what strategies were used
  - what was avoided

---

## 8) FAILURE MODES & FIXES
1) Names generic
- Fix: add stronger imagery tokens; tighten “must signal” identity; add codename bucket.

2) Too many similar names
- Fix: increase bucket diversity; enforce uniqueness tags; add code-name bucket.

3) All names violate constraints
- Fix: relax length or form in the brief (engine 01), not here.

4) Names don’t fit platform style
- Fix: platform formatting is engine 04; keep NC as “core names”.

---

## 9) HANDOFFS (XREF)
Feeds into:
- `14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md`
- `14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md`

Used by:
- `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
