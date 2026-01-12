# NAMING / IDENTITY ENGINES — REALM (README)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/00__README__NAMING_IDENTITY_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 14_NAMING_IDENTITY_ENGINES
DOC_TYPE: README
README_TYPE: REALM
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.REALM.NAMING_IDENTITY.001
OWNER: SYSTEM
ROLE: Operational entrypoint for naming and identity: naming brief, name generation, collision control,
and platform-format titles for group/album/track/release.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created realm README for 14_NAMING_IDENTITY_ENGINES: scope, pipeline order, and RAW-only navigation."
- REASON: "Without naming system, releases collide and platforms become inconsistent."
- IMPACT: "Deterministic titles + safer releases + higher catalog clarity."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.REALM.NAMING_IDENTITY.001

---

## 0) PURPOSE (LAW)
This realm standardizes naming so that:
- names are consistent with Group DNA / Album Blueprint / Track Intent
- names do not collide inside catalog memory
- titles comply with platform formatting rules (YouTube / Spotify / TikTok etc.)
- the system can produce “safe fallback titles” when collisions occur

---

## 1) SCOPE & BOUNDARIES

### In scope
- Naming briefs (what the name must signal)
- Name generation (candidate lists)
- Collision checking (within group + global optional)
- Platform formatting (title patterns per platform)

### Out of scope
- Genre theory and hook engineering → `12_TREND_GENRE_ENGINES`
- Release packaging (variants, metadata) → `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG`
- Enforcement thresholds/laws → CTL/VAL/QA (naming collision validator exists there)

---

## 2) PIPELINE ORDER (LAW)
Engines must be applied in this order unless a controller overrides:

01 — Naming Brief Engine  
02 — Naming Generation Engine  
03 — Naming Collision Engine  
04 — Platform Format Titles Engine  
05 — Series Naming Engine (optional, if you run series)

---

## 3) OUTPUT TYPES
- NAMING_BRIEF (NB)
- NAME_CANDIDATES (NC)
- COLLISION_REPORT (NCR)
- PLATFORM_TITLES_PACK (PTP)
- SERIES_RULES_PACK (SRP)

---

## 4) NAV (RAW LINKS)

01 — Naming Brief Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md

02 — Naming Generation Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/02__NAMING_GENERATION_ENG.md

03 — Naming Collision Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md

04 — Platform Format Titles Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md

05 — Series Naming Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/05__SERIES_NAMING_ENG.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
