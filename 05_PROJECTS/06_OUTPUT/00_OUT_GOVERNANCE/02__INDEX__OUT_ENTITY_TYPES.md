# OUT ENTITY TYPES — INDEX
FILE: 06_OUTPUT/00_OUT_GOVERNANCE/02__INDEX__OUT_ENTITY_TYPES.md

SCOPE: Universe Engine / OUT Types
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Типы OUT объектов и их минимальные поля.

---

## STACK (Scene Stack 4TRACK)
Минимум:
- UID
- SCENE_REF
- DURATION
- TRACKS (A/B/C/D)
- ANCHORS

## SCRIPT (Text/Dialogue/Beat Sheet)
Минимум:
- UID
- REF_UID (SCENE/EP)
- CONTENT_REF (или текст внутри)

## AUDIO
Минимум:
- UID
- REF_UID
- CUES (или ссылки на ассеты)

## VIDEO
Минимум:
- UID
- REF_UID
- SOURCE_ASSETS (опционально)
- RENDER_NOTES (опционально)

## IMAGE
Минимум:
- UID
- REF_UID
- PROMPT_REF (опционально)

---
END.
