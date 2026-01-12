# Naming Brief Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md

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
UID: UE.ENG.NAMING.NAMING_BRIEF.001
OWNER: SYSTEM
ROLE: Produces a deterministic Naming Brief (NB) for group/album/track/release:
what the name must signal, constraints, forbidden patterns, and platform requirements.

This brief is the contract for Name Generation and Collision control.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Naming Brief engine: brief schema, constraints, forbidden patterns, and platform needs."
- REASON: "Without a brief, names drift, collide, and lose identity consistency."
- IMPACT: "Higher naming quality, lower collisions, consistent catalog identity."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.NAMING.BRIEF.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Каким должен быть нейминг именно для этого объекта?”**

It must:
- define the naming target type (GROUP/ALBUM/TRACK/RELEASE)
- encode identity signals (genre, mood, mythos, vibe, audience)
- define constraints (language, length, style)
- define forbiddens (overused words, banned patterns)
- define platform needs (YouTube style vs Spotify style vs TikTok captions)

---

## 1) INPUTS (CONSUMES)
- Group DNA Spec (identity + anchors)
- Album Blueprint (if album/track)
- Track Intent Brief (if track)
- Style Fingerprint (tone and identity anchors)
- Catalog Memory (existing names used)
- Audience Segment target (what resonates)
- Platform list (where it will be published)
- Optional: Series rules (if part of a series)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- NAMING_BRIEF (NB) — single source of truth

Secondary:
- KEYWORDS PACK (KP):
  - must-use words/themes
  - avoid words/themes
- NORMALIZATION RULES:
  - how to compare names for collisions

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group DNA Spec",
  "Album Blueprint (optional)",
  "Track Intent Brief (optional)",
  "Style Fingerprint",
  "Catalog Memory (existing names)",
  "Audience Segment target",
  "Platform list",
  "Series rules (optional)"
]
PRODUCES: [
  "Naming Brief (NB)",
  "Keywords Pack (KP)",
  "Normalization Rules"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS//NAMING/BRIEFS/"

---

## 4) NAMING BRIEF SCHEMA (MANDATORY)
NB must contain:

### A) Target
- TARGET_TYPE: {GROUP | ALBUM | TRACK | RELEASE}
- TARGET_UID:
- GROUP_UID:
- ALBUM_UID: (optional)
- TRACK_UID: (optional)

### B) Identity Signals (what name must convey)
- GENRE_CORE:
- MOOD_TONE:
- AESTHETIC: (dark/romantic/retro/industrial/etc.)
- THEMES: (3–7)
- SYMBOLS / IMAGERY: (optional)
- AUDIENCE: (segment)

### C) Style Constraints
- LANGUAGE: {RU | EN | MIX}
- LENGTH_RULE:
  - max words
  - max characters (optional)
- FORM: {one-word | two-word | phrase | code-name | subtitle style}
- SOUND: (harsh/soft/sharp; optional)
- PROFANITY: {NO | ALLOW} (default NO)

### D) Forbidden Patterns (anti-cheap naming)
- banned clichés (list)
- banned structures (e.g., “<word> (feat…)” if not used)
- banned duplicates of existing catalog names

### E) Must-have / Avoid keywords
- MUST_USE (0–3)
- SHOULD_USE (3–10)
- AVOID (5–20)

### F) Platform requirements
- PLATFORMS: [YouTube, Spotify, TikTok, etc.]
- PLATFORM_NOTES:
  - YouTube: can include context words / episode markers
  - Spotify: cleaner, shorter
  - TikTok: caption-friendly

### G) Collision sensitivity
- STRICTNESS: {LOW | MED | HIGH}
- NORMALIZATION_RULES:
  - lower-case
  - remove punctuation
  - remove stop-words (optional)
  - collapse repeated spaces
  - transliteration notes (optional)

---

## 5) PROCEDURE (DETERMINISTIC)
1) Determine TARGET_TYPE and primary platform.
2) Extract identity anchors from Group DNA + Fingerprint.
3) Extract theme/role signals from Album/Track intent (if applicable).
4) Pull existing names from catalog memory for “avoid list”.
5) Define constraints: language + length + form.
6) Define forbiddens (clichés + duplicates).
7) Produce NB + Keywords Pack + Normalization Rules.

---

## 6) FAILURE MODES & FIXES
1) Brief too vague → names generic
- Fix: add 3 concrete themes + 3 imagery tokens + a form rule.

2) Too strict → no candidates
- Fix: relax must-use; widen allowed forms; keep collisions strict.

3) Platform mismatch (YouTube title too short / Spotify too long)
- Fix: split into “core name” + “platform formatting” (engine 04 handles this).

---

## 7) HANDOFFS (XREF)
Feeds into:
- `14_NAMING_IDENTITY_ENGINES/02__NAMING_GENERATION_ENG.md`
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
