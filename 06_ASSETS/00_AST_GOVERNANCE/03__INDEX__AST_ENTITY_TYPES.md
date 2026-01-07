# AST ENTITY TYPES — INDEX
FILE: 07_ASSETS/00_AST_GOVERNANCE/03__INDEX__AST_ENTITY_TYPES.md

SCOPE: Universe Engine / Assets Types
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Типы ассетов и минимальные поля.

---

## IMG — Image Asset
Минимум:
- UID
- ASSET_KIND (photo/render/frame/reference)
- RESOLUTION/FORMAT (optional)
- REF_UID (optional)
- STORAGE_PATH

## AUD — Audio Asset
Минимум:
- UID
- ASSET_KIND (sfx/voice/music/stem)
- DURATION (optional)
- REF_UID (optional)
- STORAGE_PATH

## VID — Video Asset
Минимум:
- UID
- ASSET_KIND (shot/broll/render)
- DURATION/FORMAT (optional)
- REF_UID (optional)
- STORAGE_PATH

## PRM — Prompt Asset
Минимум:
- UID
- TARGET (IMG|VID|AUD)
- PROMPT_TEXT (or ref)
- REF_UID (optional)

## REF — Reference Asset
Минимум:
- UID
- SOURCE (link/book/note)
- SUMMARY
- REF_UID (optional)

---
END.
