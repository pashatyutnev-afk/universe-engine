# CREDITS & METADATA POLICY — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: CREDITS_METADATA_POLICY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.CREDITS_METADATA_POLICY.001
OWNER: SYSTEM
ROLE: Defines minimum required metadata + credits for every documented track and every Release Pack,
including PD-only lyric attribution fields and “text mode” labeling rules.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Rebuilt Credits & Metadata Policy: normalized field sets, PD text-mode labeling, platform sheets, and required outputs."
- REASON: "Previous content was a compressed stub; release packaging needs operational schemas and consistent fields."
- IMPACT: "Consistent releases, searchable catalog, rights-safe documentation."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.CREDITS.METADATA.001

---

## 0) PURPOSE (LAW)
Ensure every track that passes TEST→DOC and every Release Pack is:
- consistent (same minimal fields everywhere)
- searchable (stable ids, genre/mood stacks)
- rights-safe (clear text mode + attribution rules, especially for PD workflows)

CTL defines fields and labeling rules only (no creative content).

---

## 1) REQUIRED METADATA — CORE (MANDATORY)
These fields MUST exist in:
- Track Card (DOC_PACK)
- Release Pack (passport/metadata sheet)

### Identity
- GROUP_NAME
- GROUP_UID (if available)
- ALBUM_NAME (or SINGLE)
- ALBUM_UID (optional if single)
- TRACK_TITLE
- TRACK_UID
- RELEASE_VERSION (e.g., v1.0, v1.1)
- DATE_CREATED
- DATE_RELEASE_TARGET (optional)

### Content descriptors (compact)
- LANGUAGE_PRIMARY (RU/EN/MIX)
- GENRE_STACK (3–8 tags max)
- MOOD_STACK (3–8 tags max)
- TEMPO_BAND (optional)
- HOOK_TYPE (optional: chant/slogan/motif)
- DURATION_MODE (SHORT/FULL/ALT_INTRO)
- UGC_MODE (YES/NO)

### Platform targets
- PLATFORM_TARGETS: (TikTok, Shorts, Reels, Spotify, Apple, YouTube, etc.)
- PLATFORM_TITLES_PACK_REF (pointer/id when produced)

### Production traceability
- WINNER_TAKE_ID
- PROMPT_PACK_FROZEN_REF (pointer/id)
- QA_VAL_SNAPSHOT_REF (pointer/id)
- CATALOG_MEMORY_TOKEN_UPDATE_REF (pointer/id)

---

## 2) REQUIRED CREDITS — CORE (MANDATORY)
Credits must exist in two levels:
- Track Card: minimal
- Release Pack: full block

### Core music credits
- MUSIC_CREDIT: "AI-assisted / system" (default label; may be overridden by project policy later)
- ARRANGEMENT_CREDIT: (role or system)
- MIX_CREDIT: (role or system)
- MASTER_CREDIT: (role or system)

### Vocals / roles (if applicable)
- LEAD_VOCAL:
- CONTRAST_VOCAL: (optional)
- HOOK_CARRIER:
- CHOIR_STACK: (optional)

### Production roles (optional but recommended)
- PRODUCER:
- PROMPT_ARCHITECT:
- UGC_DIRECTOR:
- EARWORM_DIRECTOR:

(If the project does not track human names, store role labels and/or system markers.)

---

## 3) TEXT / LYRICS ATTRIBUTION (MANDATORY WHEN LYRICAL)
If lyrics exist, must declare **TEXT_MODE** and related fields.

### TEXT_MODE (one of)
- ORIGINAL (generated lyrics, not sourced)
- PD_VERBATIM (verbatim use of PD text fragments)
- PD_MOSAIC (mosaic from PD fragments)
- ADAPTATION (adapted from a source; not verbatim)
- INSPIRED (inspired by a source; no direct copying)

Rule:
- For PD workflows, prefer PD_MOSAIC; PD_VERBATIM is allowed only when PD is confirmed and policy allows fragments.

### Required fields when TEXT_MODE ≠ ORIGINAL
- TEXT_SOURCE_TYPE: {PD_CORPUS | OTHER}
- AUTHOR:
- WORK:
- SOURCE_REF:
  - internal pointer to PD corpus record / eligibility report
- ATTRIBUTION_LINE:
  - how to credit (short, platform-safe)

### PD compliance fields (if PD corpus involved)
- PD_POLICY_MODE: {STRICT | STANDARD | LENIENT}
- PD_ELIGIBILITY_REPORT_REF:
- EXCERPT_COLLISION_REPORT_REF:

---

## 4) RIGHTS RULES (HARD)
R1 — If PD eligibility is NOT confirmed:
- TEXT_MODE MUST NOT be PD_VERBATIM or PD_MOSAIC.
- Allowed only: ADAPTATION or INSPIRED.
- Must record why (short note).

R2 — If PD eligibility IS confirmed:
- PD_MOSAIC is allowed.
- PD_VERBATIM is allowed only under fragment limits and policy.

R3 — No full poem dump in docs:
- docs may store only structured lyrics / mosaic, never whole PD works.

Dependency:
- Poet PD Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

Validator alignment:
- Credits/Rights VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

---

## 5) WHERE THIS MUST APPEAR (OUTPUT STANDARD)
### Track Card (DOC_PACK) — MINIMUM
Must include:
- core metadata (Section 1)
- minimal credits (Section 2)
- TEXT_MODE + source fields if lyrical (Section 3)

### Release Pack — FULL
Must include:
- full metadata sheet
- full credits block (core + vocals + production roles if tracked)
- platform titles pack reference
- variants manifest reference

---

## 6) FILE-NAME SAFE STRINGS (REQUIRED FOR EXPORT)
Release Pack must provide filename-safe strings:
- GROUP_NAME_SAFE
- TRACK_TITLE_SAFE
- VARIANT_LABEL_SAFE
- PLATFORM_TITLE_SAFE (per platform)

Rules:
- strip punctuation
- collapse spaces
- keep within reasonable length
(Exact mechanics defined by tooling, not by this CTL.)

---

## 7) DEPENDENCIES (RAW)
Used by:
- Release Pack ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
- Release Pack ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

Naming integration:
- Platform Format Titles ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
