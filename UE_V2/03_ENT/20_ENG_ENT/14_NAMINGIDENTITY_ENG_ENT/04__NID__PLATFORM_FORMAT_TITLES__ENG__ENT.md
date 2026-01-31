# Platform Format Titles Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md

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
UID: UE.ENG.NAMING.PLATFORM_FORMAT_TITLES.001
OWNER: SYSTEM
ROLE: Converts approved name candidates into platform-specific titles (Spotify/Apple/YouTube/TikTok/etc.),
with deterministic formatting rules, safe suffixes, and release-pack compatibility.

Outputs a Platform Titles Pack (PTP) for Release Pack.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Platform Format Titles engine: platform rules, formatting patterns, and output schema."
- REASON: "Each platform has different title conventions; we need deterministic formatting and safe variants."
- IMPACT: "Cleaner uploads, better discovery, fewer rejections, consistent catalog titles."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.NAMING.PLATFORM_TITLES.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Как оформить название под каждую платформу?”**

It must:
- take approved shortlist from Naming Collision
- output platform-ready titles for:
  - streaming (Spotify/Apple/…)
  - YouTube
  - short-form (TikTok/Reels)
- include safe fallbacks (if a platform title collides)
- keep titles within length and clarity constraints

---

## 1) INPUTS (CONSUMES)
- Naming Brief (NB) (platform list + constraints)
- Naming Collision Report (approved shortlist + safe fallbacks)
- Optional: Release context:
  - target type (group/album/track/release)
  - episode/series markers (if used)
  - hook quote line (optional; for TikTok captions)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- PLATFORM_TITLES_PACK (PTP)

Secondary:
- CORE_TITLE (selected “default”)
- ALT_TITLES (platform alternates)
- FILENAME_SAFE_TITLES (sanitized strings for file naming)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Naming Brief (NB)",
  "Naming Collision Report (approved shortlist + safe fallbacks)",
  "Release context (optional)"
]
PRODUCES: [
  "Platform Titles Pack (PTP)",
  "Core title selection",
  "Alternate titles",
  "Filename-safe titles"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS//NAMING/PLATFORM_TITLES/"

---

## 4) PLATFORM RULES (STANDARD)
These are formatting patterns, not creative generation.

### P1 — STREAMING (Spotify/Apple/etc.)
Goal: clean, short, readable.
- Use CORE_TITLE only.
- Avoid extra descriptors unless required.
- No hashtags.
- Prefer: 1–5 words (or per NB length rule).

Pattern:
- STREAMING_TITLE = CORE_TITLE

Optional (if allowed by brief):
- STREAMING_TITLE_ALT = CORE_TITLE (Subtitle)

### P2 — YOUTUBE (longform)
Goal: clickable + searchable + context.
Allowed additions:
- group name (if target is track)
- genre/mood hint (short)
- episode marker (if series)

Patterns (choose 1):
- YT: "<CORE_TITLE> — <GROUP_NAME>"
- YT: "<CORE_TITLE> | <GENRE_HINT> | <GROUP_NAME>"
- YT: "<CORE_TITLE> — <GROUP_NAME> (Official Audio)"
(“Official Audio” only if policy allows.)

### P3 — SHORT-FORM (TikTok/Reels)
Goal: caption-friendly, memetic, short.
Allowed additions:
- quote line snippet (very short)
- emoji (optional, minimal)
- hashtag set (optional, controlled by policy)

Patterns:
- TT: "<CORE_TITLE> — <QUOTE_SNIPPET>"
- TT: "<CORE_TITLE> | <MOOD_WORD>"
- TT: "<CORE_TITLE> 🔁" (loop signal) (optional)

Never:
- long sentences
- too many hashtags

---

## 5) SAFE SUFFIXES / PREFIXES (FOR COLLISIONS)
If a platform title collides:
- add a safe differentiator:
  - year marker (if allowed)
  - “Vol. 1/2” (series only)
  - short subtitle (2–3 words max)
  - group tag (for track titles)

Do not add:
- random numbers without meaning
- huge bracket tails

---

## 6) FILENAME-SAFE NORMALIZATION
Also output file-safe versions:
- lower-case optional
- replace spaces with underscores
- remove punctuation
- collapse underscores
- keep RU letters if filesystem allows; otherwise transliteration policy (if defined)

---

## 7) PROCEDURE (DETERMINISTIC)
1) Select CORE_TITLE:
   - take top approved shortlist item unless a platform requires different.
2) Read NB platform list and constraints.
3) Generate titles per platform using patterns:
   - streaming
   - youtube
   - short-form
4) If conflicts detected inside PTP:
   - apply safe suffix rule and output ALT title.
5) Produce filename-safe versions.
6) Output PTP.

---

## 8) OUTPUT SCHEMA (MANDATORY)

### PLATFORM_TITLES_PACK (PTP)
- TARGET_TYPE:
- TARGET_UID:
- DATE:
- CORE_TITLE:
- STREAMING:
  - TITLE:
  - ALT (optional):
- YOUTUBE:
  - TITLE:
  - ALT (optional):
- SHORTFORM:
  - TITLE:
  - ALT (optional):
- FALLBACKS:
  - list of safe titles (1–5)
- FILENAME_SAFE:
  - STREAMING:
  - YOUTUBE:
  - SHORTFORM:

---

## 9) FAILURE MODES & FIXES
1) Titles too long
- Fix: remove descriptors; use core title only; shorten subtitle.

2) Titles look spammy
- Fix: remove hashtags and extra “promo” words; keep clean.

3) YouTube title lacks context
- Fix: add group name + genre hint, but keep short.

4) TikTok caption not memetic
- Fix: use quote snippet or one mood word.

---

## 10) HANDOFFS (XREF)
Used by:
- `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
