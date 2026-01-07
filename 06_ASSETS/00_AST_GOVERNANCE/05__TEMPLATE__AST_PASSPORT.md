# AST PASSPORT — TEMPLATE (UNIVERSAL)
FILE: 07_ASSETS/00_AST_GOVERNANCE/05__TEMPLATE__AST_PASSPORT.md

SCOPE: Universe Engine / Assets
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Универсальный паспорт ассета (IMG/AUD/VID/PRM/REF).

SOURCE OF TRUTH:
- UID: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- AST Rules: `07_ASSETS/00_AST_GOVERNANCE/01__RULES__AST.md`

---

## 0) HEADER (REQUIRED)
UID: <UE.AST.<CATEGORY>.<FAMILY>.<NAME>>
CATEGORY: <IMG|AUD|VID|PRM|REF>
FAMILY: <VIS|SND|GEN|NAR|...>
STATUS: <DRAFT|ACTIVE|ARCHIVED|DEPRECATED>
LOCK: <OPEN|FIXED>
VERSION: <1.0>
OWNER: <SYSTEM|YOU>

---

## 1) SUMMARY (REQUIRED)
1–3 строки: что это за ассет.

---

## 2) ASSET META (REQUIRED)
ASSET_KIND: <photo|render|frame|reference|sfx|voice|music|stem|shot|broll|prompt|link|note>
SOURCE: <manual|gen|external|mixed>

REF_UID: <UE.PRJ.SCENE... | UE.OUT.STACK... | UE.OUT.VIDEO... | NONE>

STORAGE_PATH:
- passport: <this file path>
- media: <relative or absolute path or NONE>

---

## 3) TECH META (OPTIONAL)
FORMAT: <png|jpg|wav|mp3|mp4|...>
RESOLUTION: <w×h> (for IMG)
DURATION: <MM:SS.mmm> (for AUD/VID)

---

## 4) LINKS (OPTIONAL)
XREFS: []
DEPENDS_ON: []

---

## 5) NOTES (OPTIONAL)
- любые примечания

---
END.
