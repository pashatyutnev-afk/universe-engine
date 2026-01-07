# DOC REGISTRY — STANDARDS LAYER (SoT)
FILE: 02_STANDARDS/01__DOC_REGISTRY.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: REGISTRY
INDEX_TYPE: DOC_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.REG.STD.DOC_REGISTRY.001
OWNER: SYSTEM
ROLE: Single source of truth registry for canonical documents inside 02_STANDARDS (tracks what exists, status, and pointers)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Создан канонический Doc Registry с Doc Control шапкой + фиксированным порядком; подготовлен для валидации/линтинга"
- REASON: "Устранить коллизию 00__* и получить SoT реестр документов слоя"
- IMPACT: "Стандартизирует контроль состава и статусов документов STANDARDS"

---

## 0) PURPOSE (SoT)
Этот реестр описывает **канонические документы** слоя `02_STANDARDS`.

Он используется для:
- проверки существования (в паре с master-index `00__INDEX__STANDARDS.md`)
- контроля статусов/версий/UID
- миграций (alias-pointer)
- будущей автоматической валидации

NOTE:
- Master-index (`00__INDEX__STANDARDS.md`) — это **entrypoint + existence law**.
- Doc Registry (этот файл) — это **учётная ведомость**: UID/версии/статусы/ссылки.

---

## 1) REGISTRY RULES (HARD)
1) Любая запись здесь обязана иметь: `PATH`, `UID`, `STATUS`, `VERSION`.
2) UID должен соответствовать `01_SYSTEM_LAW/02__UID_RULES.md`.
3) VERSION должен быть SemVer по `01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`.
4) Документы, не прошедшие нормализацию, помечаются `STATUS: DRAFT` и считаются NON-CANON до исправления.

---

## 2) CANON RECORD FORMAT (STANDARD)
Формат записи (одна строка):

`<PATH> | UID:<UID> | STATUS:<STATUS> | VERSION:<X.Y.Z> | RAW:<raw-link>`

Если RAW неизвестен/не нужен, допускается:
`RAW:N/A`

---

## 3) REGISTRY — 02_STANDARDS (CANON SET)

### 3.1 Root entrypoints
- `02_STANDARDS/00__INDEX__STANDARDS.md` | UID:UE.IDX.STD.MASTER.000 | STATUS:ACTIVE | VERSION:1.2.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__INDEX__STANDARDS.md
- `02_STANDARDS/01__DOC_REGISTRY.md` | UID:UE.REG.STD.DOC_REGISTRY.001 | STATUS:ACTIVE | VERSION:1.2.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01__DOC_REGISTRY.md

### 3.2 Canon / Reference
- `02_STANDARDS/00_CANON/ARCHITECTURE_OVERVIEW.md` | UID:UE.STD.CANON.ARCHITECTURE_OVERVIEW.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_CANON/ARCHITECTURE_OVERVIEW.md
- `02_STANDARDS/00_CANON/SYSTEM_CANON.md` | UID:UE.STD.CANON.SYSTEM_CANON.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_CANON/SYSTEM_CANON.md

### 3.3 Specifications (SoT)
- `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md` | UID:UE.STD.UID_MARKING.SOT.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md
- `02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md` | UID:UE.STD.STORAGE_MAP.SOT.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md
- `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md` | UID:UE.STD.DOC_CONTROL.SOT.001 | STATUS:ACTIVE | VERSION:1.2.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md` | UID:UE.STD.REL_XREF.SOT.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
- `02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md` | UID:UE.STD.SCENE_STACK_4TRACK.SOT.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md
- `02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md` | UID:UE.TPL.STD.SCENE_PACK.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md
- `02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md` | UID:UE.TPL.STD.TRACK_EVENT.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md
- `02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md` | UID:UE.STD.NAT_GATES.SOT.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md
- `02_STANDARDS/01_SPECIFICATIONS/06A__TEMPLATE__NAT_PROFILE.md` | UID:UE.TPL.STD.NAT_PROFILE.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/06A__TEMPLATE__NAT_PROFILE.md
- `02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md` | UID:UE.STD.DOC_REGISTRY.SOT.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md

### 3.4 Legacy / To normalize (tracked but NON-CANON until fixed)
- `02_STANDARDS/01_SPECIFICATIONS/ENTITY_MODEL_SPEC.md` | UID:UE.STD.ENTITY_MODEL.LEGACY.001 | STATUS:DRAFT | VERSION:0.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/ENTITY_MODEL_SPEC.md
- `02_STANDARDS/01_SPECIFICATIONS/INDEX_STRUCTURE_SPEC.md` | UID:UE.STD.INDEX_STRUCTURE.LEGACY.001 | STATUS:DRAFT | VERSION:0.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/INDEX_STRUCTURE_SPEC.md

### 3.5 Protocols (to normalize naming)
- `02_STANDARDS/02_PROTOCOLS/CHANGE_MANAGEMENT_PROTOCOL.md` | UID:UE.PROTO.STD.CHANGE_MANAGEMENT.001 | STATUS:DRAFT | VERSION:0.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/CHANGE_MANAGEMENT_PROTOCOL.md
- `02_STANDARDS/02_PROTOCOLS/CHAT_PROTOCOL.md` | UID:UE.PROTO.STD.CHAT.001 | STATUS:DRAFT | VERSION:0.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/CHAT_PROTOCOL.md

### 3.6 Technical templates (to normalize naming)
- `02_STANDARDS/03_TECHNICAL/ENTITY_PASSPORT_TEMPLATE.md` | UID:UE.TPL.STD.ENTITY_PASSPORT.LEGACY.001 | STATUS:DRAFT | VERSION:0.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/03_TECHNICAL/ENTITY_PASSPORT_TEMPLATE.md
- `02_STANDARDS/03_TECHNICAL/INDEX_TEMPLATE.md` | UID:UE.TPL.STD.INDEX_TEMPLATE.LEGACY.001 | STATUS:DRAFT | VERSION:0.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/03_TECHNICAL/INDEX_TEMPLATE.md

### 3.7 Terms / Glossary (to normalize naming)
- `02_STANDARDS/04_TERMS_DEFINITIONS/GLOSSARY.md` | UID:UE.STD.TERMS.GLOSSARY.LEGACY.001 | STATUS:DRAFT | VERSION:0.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/04_TERMS_DEFINITIONS/GLOSSARY.md

### 3.8 Requirements
- `02_STANDARDS/05_REQUIREMENTS_TZ/00__INDEX.md` | UID:UE.IDX.STD.REQ.MASTER.000 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/05_REQUIREMENTS_TZ/00__INDEX.md

### 3.9 Marking Modules
- `02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md` | UID:UE.STD.MODULE.ID_STANDARD.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md
- `02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md` | UID:UE.STD.MODULE.STORAGE_MAP.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md
- `02_STANDARDS/06_MARKING_STANDARDS/03__STATUS_LOCK_VERSION.md` | UID:UE.STD.MODULE.STATUS_LOCK_VERSION.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/03__STATUS_LOCK_VERSION.md
- `02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md` | UID:UE.STD.MODULE.PRIORITY_S0_S3.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md
- `02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md` | UID:UE.STD.MODULE.REL_POLICY_XREF.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md
- `02_STANDARDS/06_MARKING_STANDARDS/06__SCENE_STACK_4TRACK.md` | UID:UE.STD.MODULE.SCENE_STACK_4TRACK.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/06__SCENE_STACK_4TRACK.md
- `02_STANDARDS/06_MARKING_STANDARDS/07__NATURALNESS_GATES.md` | UID:UE.STD.MODULE.NATURALNESS_GATES.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/07__NATURALNESS_GATES.md
- `02_STANDARDS/06_MARKING_STANDARDS/08__DOC_CONTROL.md` | UID:UE.STD.MODULE.DOC_CONTROL.001 | STATUS:ACTIVE | VERSION:1.0.0 | RAW:https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/06_MARKING_STANDARDS/08__DOC_CONTROL.md

---

## 4) NEXT NORMALIZATION QUEUE (TRACKED)
Очередь нормализации (в порядке пользы для системы):
1) `02_PROTOCOLS/*` → привести к `NN__...md` + Doc Control шапки + SemVer + UID
2) `03_TECHNICAL/*` → привести к `NN__...md` + Doc Control
3) `04_TERMS_DEFINITIONS/*` → привести к `NN__...md` + Doc Control
4) Legacy specs (`ENTITY_MODEL_SPEC`, `INDEX_STRUCTURE_SPEC`) → либо нормализовать, либо явно задепрекейтить

---

## FINAL RULE (LOCK)
LOCK: FIXED
--- END.
