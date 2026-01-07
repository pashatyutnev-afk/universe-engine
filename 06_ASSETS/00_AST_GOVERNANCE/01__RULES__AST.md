# ASSETS (AST) — RULES
FILE: 07_ASSETS/00_AST_GOVERNANCE/01__RULES__AST.md

SCOPE: Universe Engine / Assets Rules
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила для AST: UID, регистрация, связи, версии, анти-дубли.

---

## 0) CORE LAW
- UID обязателен и единственный ID.
- Ассет существует только после регистрации в AST Global Registry.
- Дубли ассетов запрещены (S0), кроме явно разрешённых серий (кадры, вариации).

---

## 1) UID FORMAT (AST)
`UE.<GLOBAL>.<CATEGORY>.<FAMILY>.<NAME>`

Для AST:
- GLOBAL = AST
- CATEGORY = IMG | AUD | VID | PRM | REF
- FAMILY = VIS | SND | GEN | NAR | ... (по смыслу)
- NAME = UPPER_SNAKE_CASE

Примеры:
- `UE.AST.IMG.VIS.SCENE_EP01_SCN_003_REF_01`
- `UE.AST.AUD.SND.SFX_DOOR_METAL_01`
- `UE.AST.PRM.VIS.IMG_PROMPT_SCENE_EP01_SCN_003_V1`

---

## 2) REQUIRED PASSPORT FIELDS
- UID
- STATUS / LOCK / VERSION
- ASSET_KIND (что именно: photo/render/sfx/voice/music/prompt/reference)
- SOURCE (manual|gen|external|mixed)
- REF_UID (SCENE/STACK/OUT optional)
- STORAGE_PATH

---

## 3) SERIES POLICY (ALLOWED)
Разрешены серии:
- IMG_001..IMG_999 (кадры/вариации)
- AUD_001.. (слои)
- VID_001.. (шоты)

Серии должны иметь единый базовый NAME и суффиксы.

---

## 4) LINK POLICY
- Ассеты могут ссылаться на PRJ (SCENE) и на OUT (STACK/VIDEO/AUDIO)
- OUT может ссылаться на AST всегда

---
END.
