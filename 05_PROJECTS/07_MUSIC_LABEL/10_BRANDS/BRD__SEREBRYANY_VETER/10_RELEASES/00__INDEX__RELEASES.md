# RELEASES INDEX — "СЕРЕБРЯНЫЙ ВЕТЕР" (CANON)
FILE: 10_BRANDS/BRD__SEREBRYANY_VETER/10_RELEASES/00__INDEX__RELEASES.md

SCOPE: Universe Engine
LAYER: 05_PROJECTS
PROJECT_REALM: 07_MUSIC_LABEL
BRAND: BRD__SEREBRYANY_VETER
DOC_TYPE: INDEX
INDEX_TYPE: RELEASE_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUSIC.BRD.SEREBRYANY_VETER.IDX.RELEASES.001
OWNER: USER
ROLE: Single source of truth for releases of the brand "Серебряный Ветер" (existence + navigation)

CHANGE_NOTE:
- DATE: 2026-01-10
- TYPE: MAJOR
- SUMMARY: "Created brand release registry index."
- REASON: "Need deterministic navigation and existence rule for all releases."
- IMPACT: "Releases become trackable, repeatable, and auditable."

---

## 0) PURPOSE (LAW)
This index is the single source of truth for:
- what releases exist for this brand
- where release artifacts are stored
- how to navigate release output packs

---

## 1) EXISTENCE RULE (ABSOLUTE)
- If a release is not registered in this index — it does not exist for the brand.
- Any stray files in `/10_RELEASES/` that are not listed here are NON-CANON / ignored.

---

## 2) STORAGE MAP (BRAND RELEASES)
### 2.1 Output pack records (SoT)
- `10_RELEASES/YYYY-MM-DD__TRK__<TRACK_SLUG>__OUTPUT_PACK.md`

### 2.2 Artifacts folders (storage only)
- `_AUDIO/` — exports (wav/mp3), stems if any
- `_COVERS/` — cover images, thumbnails
- `_SHORTS/` — short clips plan, timestamps, rendered shorts

NOTE: folders do not define existence. Only this index defines existence.

---

## 3) NAMING STANDARD (STRICT)
- Date: `YYYY-MM-DD`
- Track slug: `A-Z0-9_` only, uppercase, no spaces
- Output pack filename:
  `YYYY-MM-DD__TRK__<TRACK_SLUG>__OUTPUT_PACK.md`

---

# 4) CANON MAP — RELEASES (ORDERED)

## 2026
### 2026-01-10 — Серебряный путь (PILOT)
- OUTPUT PACK:
  `2026-01-10__TRK__SEREBRYANY_PUT__OUTPUT_PACK.md`
- AUDIO:
  `_AUDIO/` (place exports here)
- COVERS:
  `_COVERS/` (place cover here)
- SHORTS:
  `_SHORTS/` (place shorts plan here)

---

## FINAL RULE (LOCK)
This index is the only canonical registry of releases for this brand.  
Any new release must be registered here first, then created.

OWNER: USER  
LOCK: FIXED

--- END.
