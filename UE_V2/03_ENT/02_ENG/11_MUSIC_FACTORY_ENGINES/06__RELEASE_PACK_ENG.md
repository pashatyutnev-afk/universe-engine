# Release Pack Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.2
UID: UE.ENG.MF.RELEASE_PACK.001
OWNER: SYSTEM
ROLE: Produces a complete release pack (variants + metadata + credits + QA/VAL snapshot + platform-ready titles) for track or album.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; preserved original rules and dependencies."
- REASON: "Compressed formatting is error-prone during edits."
- IMPACT: "Release packaging becomes deterministic and easy to execute."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.RELEASE_PACK.003

---

## 0) PURPOSE (LAW)
This engine turns approved tracks/albums into a **Release Pack**:
- approved versions (main/short/alt/extended/instrumental etc.)
- title variants per platform format
- metadata (genre tags, mood, language, descriptors)
- credits/rights note (policy controlled)
- QA/VAL results snapshot
- export checklist (upload-ready)

It does not generate audio itself — it packages what exists.

---

## 1) INPUTS (CONSUMES)
- Group DNA Spec
- Album Blueprint Spec (if album release)
- Track Winner Pack (approved track + final prompt)
- Duration Map (from `05__DURATION_STRATEGY_ENG`)
- Release variants CTL:
  - `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md`
- Credits/metadata policy CTL:
  - `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md`
- Platform title format engine (naming family)

---

## 2) OUTPUTS (PRODUCES)

### Primary
- **Release Pack (Track)** OR **Release Pack (Album)**

### Secondary
- **Variant Manifest** (list of files/versions + target durations)
- **Metadata Sheet** (tags + descriptors)
- **Credits & Rights Note** (PD compliance note if used)
- **Export Checklist** (what to upload where)
- **Readiness Snapshot** (VAL/QA pass list)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group DNA Spec",
  "Album Blueprint Spec (optional)",
  "Approved Track Winner Pack (one or many)",
  "Duration Map",
  "Release Variants CTL",
  "Credits/Metadata Policy CTL"
]
PRODUCES: [
  "Release Pack (Track/Album)",
  "Variant Manifest",
  "Metadata Sheet",
  "Credits & Rights Note",
  "Readiness Snapshot (VAL/QA)"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS//GROUPS//RELEASES/"

---

## 4) RELEASE PACK CONTENTS (STANDARD)

### 4.1 Track Release Pack must include
1) **Release Passport**
   - RELEASE_ID, track ID, version, date, status

2) **Variant Manifest**
   - MAIN, SHORT_CUT, ALT, INSTRUMENTAL, EXTENDED (as applicable)

3) **Titles (per platform)**
   - Spotify/Apple style title
   - YouTube title
   - TikTok/Reels caption title

4) **Metadata Sheet**
   - genre tags, mood, energy, language, themes, descriptors

5) **Credits & Rights Note**
   - PD usage statement if used
   - “no claim of authorship of original poet text”

6) **QA/VAL Snapshot**
   - which validators passed, which QA notes included

7) **Export Checklist**
   - upload-ready list + filename conventions

### 4.2 Album Release Pack must include (in addition)
- album story/promise
- track list + roles
- per-track variant summary
- album-level metadata + naming set

---

## 5) VARIANTS RULES (BASED ON CTL)
Variant types (controlled):
- MAIN RELEASE (required)
- SHORT CUT (UGC) (recommended)
- ALT MIX / ALT ARRANGEMENT (optional)
- INSTRUMENTAL (optional)
- EXTENDED (rare; only if genre benefits)

Hard rules:
- Each variant must have:
  - target duration range
  - purpose
  - naming suffix policy
  - QA/VAL readiness note

---

## 6) TITLES & NAMING INTEGRATION
Release Pack must produce:
- WORKING TITLE (internal)
- PUBLIC TITLE (platform)
- SAFE TITLE (if collisions detected)

Use naming engines:
- naming brief → naming generation → naming collision check → platform formatting

---

## 7) RIGHTS / PD HANDLING (IMPORTANT)
If lyrics use PD fragments:
- Mark: `LYRICS_SOURCE_MODE: PD_ONLY` or `PD_PLUS_PATCHES`
- Keep a “source note” explaining:
  - fragments used (short list)
  - transformation notes (paraphrase/reorder/blend)
- Never present as “original poem by us”.

(Policy and wording controlled by CTL.)

---

## 8) READINESS GATES (MUST PASS)
Before a release pack is marked READY:
- `RELEASE_PACK_READY_VAL` must PASS
- `CREDITS_RIGHTS_VAL` must PASS (if used)
- UGC-ready validators must pass for short cut variant
- Collision blocker must pass (names + fingerprint)

---

## 9) FAILURE MODES & FIXES
1) Missing variants  
- Fix: re-run variants plan; produce missing files.

2) Metadata inconsistent  
- Fix: regenerate metadata sheet from blueprint + group DNA.

3) Title collision  
- Fix: naming collision engine; produce safe title.

4) Rights ambiguity  
- Fix: strengthen PD note; remove risky claims.

---

## 10) HANDOFFS (XREF)
NEXT ORC:
- `20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md`

REQUIRED CTL:
- `04__RELEASE_VARIANTS_CTL`
- `13__CREDITS_METADATA_POLICY_CTL`

REQUIRED VAL:
- `06__RELEASE_PACK_READY_VAL`
- `07__NAMING_COLLISION_VAL`
- `09__CREDITS_RIGHTS_VAL`

REQUIRED QA:
- `04__CREATOR_PANEL_QA` (human check)
- `09__REGRESSION_GUARD_QA` (if updating existing release)

---

## 11) OUTPUT PACK (MANDATORY LIST)
1) Release Passport
2) Variant Manifest
3) Titles per platform
4) Metadata Sheet
5) Credits & Rights Note
6) QA/VAL Snapshot
7) Export Checklist

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
