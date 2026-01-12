# Series Naming Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/05__SERIES_NAMING_ENG.md

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
UID: UE.ENG.NAMING.SERIES_NAMING.001
OWNER: SYSTEM
ROLE: Defines deterministic naming rules for series-based catalogs (seasons/episodes/volumes):
marker formats, sequencing, and platform representation.

Produces a Series Rules Pack (SRP) used by Naming Brief and Platform Titles formatting.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Series Naming engine: series markers, sequencing rules, and platform formatting guidance."
- REASON: "Series releases require consistent markers to avoid chaos and collisions."
- IMPACT: "Clean season/episode cataloging and safer platform titles."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.NAMING.SERIES.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Как мы называем серии, чтобы всё было ровно и без коллизий?”**

It must define:
- series marker syntax (Vol/Ep/Season/etc.)
- numbering rules (zero padding or not)
- how markers appear on each platform
- collision-safe formatting
- optional subtitle rules inside series

---

## 1) INPUTS (CONSUMES)
- Series context:
  - SERIES_ID / SERIES_NAME (optional)
  - series type: {SEASON_EPISODE | VOLUME | COLLECTION | CHAPTERS}
  - current index (season/episode/vol)
- Naming Brief constraints (language/length)
- Platform list
- Catalog memory (existing series markers and titles)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- SERIES_RULES_PACK (SRP)

Secondary:
- SERIES_MARKER_FORMATS:
  - streaming marker
  - YouTube marker
  - short-form marker
- VALIDATION RULES:
  - allowed ranges
  - required presence (yes/no)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Series context (type + index)",
  "Naming brief constraints",
  "Platform list",
  "Catalog memory (optional)"
]
PRODUCES: [
  "Series Rules Pack (SRP)",
  "Series marker formats",
  "Validation rules"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS//NAMING/SERIES/"

---

## 4) SERIES TYPES (STANDARD)
S1 — SEASON_EPISODE
- Season 1 Episode 01, etc.

S2 — VOLUME
- Vol. 1, Vol. 2

S3 — COLLECTION
- Collection 01, 02 (for packs)

S4 — CHAPTERS
- Chapter 01, 02 (book-like)

---

## 5) MARKER FORMATS (DEFAULTS)
Choose minimal consistent syntax.

### Streaming (clean)
- S1: "S<season> E<episode>" (optional, only if brief allows)
- S2: "Vol. <n>"
- S3: "Collection <nn>"
- S4: "Chapter <nn>"

### YouTube (context-friendly)
- "S<season>E<episode> — <CORE_TITLE>"
- or "<CORE_TITLE> | S<season>E<episode>"

### Short-form (minimal)
- "#<episode>" or "Ep <n>" (optional)
- avoid long markers

Padding rule (default):
- use 2-digit padding for episode/collection/chapter: 01..99

---

## 6) PROCEDURE (DETERMINISTIC)
1) Identify series type (S1..S4).
2) Read current indices (season/episode/vol).
3) Produce marker format fields for each platform.
4) Validate against catalog memory:
   - no duplicate marker + title combos.
5) Output SRP.

---

## 7) OUTPUT SCHEMA (MANDATORY)

### SERIES_RULES_PACK (SRP)
- SERIES_ID:
- SERIES_TYPE:
- INDEX:
  - season: (optional)
  - episode: (optional)
  - vol: (optional)
  - chapter: (optional)
  - collection: (optional)
- PADDING_RULE:
- STREAMING_MARKER:
- YOUTUBE_MARKER:
- SHORTFORM_MARKER:
- REQUIRED: YES/NO
- NOTES:
  - how to apply markers in Naming Brief and Platform Titles

---

## 8) FAILURE MODES & FIXES
1) Markers make titles too long
- Fix: make markers optional for streaming; keep for YouTube only.

2) Confusing ordering
- Fix: enforce numeric padding; enforce one marker style globally.

3) Collisions inside series
- Fix: add safe subtitle; add year marker if allowed.

---

## 9) HANDOFFS (XREF)
Used by:
- `14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md`
- `14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md`
- `14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
