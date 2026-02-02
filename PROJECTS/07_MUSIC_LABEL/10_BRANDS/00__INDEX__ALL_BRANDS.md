# BRANDS INDEX — GLOBAL REGISTRY (CANON)
FILE: 10_BRANDS/00__INDEX__ALL_BRANDS.md

SCOPE: Universe Engine
LAYER: 05_PROJECTS
PROJECT_REALM: 07_MUSIC_LABEL
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_BRAND_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUSIC.IDX.ALL_BRANDS.001
OWNER: USER
ROLE: Single source of truth for existence + navigation of all music brands (groups) in MUSIC_LABEL realm

CHANGE_NOTE:
- DATE: 2026-01-10
- TYPE: MAJOR
- SUMMARY: "Created global brands registry for 07_MUSIC_LABEL."
- REASON: "Need deterministic navigation as multiple brands appear."
- IMPACT: "All brands become discoverable and auditable."

---

## 0) PURPOSE (LAW)
This index is the single source of truth for:
- which brand folders exist in `10_BRANDS/`
- how to navigate to each brand passport and release registry

---

## 1) EXISTENCE RULE (ABSOLUTE)
- If a brand is not registered in this index — it does not exist for MUSIC_LABEL.
- Any folder present in `10_BRANDS/` but missing here is NON-CANON / ignored until registered.

---

## 2) BRAND FOLDER STANDARD (MANDATORY)
Each brand folder must contain:
- `00__BRAND_PASSPORT.md`
- `01__BRAND_DNA.md`
- `02__PROMPT_PRESETS.md`
- `/10_RELEASES/00__INDEX__RELEASES.md`

Optional (recommended):
- `03__REPERTOIRE_PLAN.md`
- `04__VISUAL_IDENTITY.md`

---

## 3) NAMING STANDARD (STRICT)
Brand folder name format:
- `BRD__<BRAND_SLUG>`
Where `<BRAND_SLUG>` is uppercase `A-Z0-9_` only, no spaces.

---

# 4) CANON MAP — BRANDS (ORDERED)

## 01) BRD__SEREBRYANY_VETER
- BRAND PATH:
  `10_BRANDS/BRD__SEREBRYANY_VETER/`

- PASSPORT:
  `10_BRANDS/BRD__SEREBRYANY_VETER/00__BRAND_PASSPORT.md`

- DNA:
  `10_BRANDS/BRD__SEREBRYANY_VETER/01__BRAND_DNA.md`

- PROMPT PRESETS:
  `10_BRANDS/BRD__SEREBRYANY_VETER/02__PROMPT_PRESETS.md`

- RELEASES INDEX:
  `10_BRANDS/BRD__SEREBRYANY_VETER/10_RELEASES/00__INDEX__RELEASES.md`

---

## FINAL RULE (LOCK)
This index is the only canonical registry of brands for MUSIC_LABEL.  
Any new brand must be registered here first, then created.

OWNER: USER  
LOCK: FIXED

--- END.
