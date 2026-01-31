FILE: UE_V2/03_ENT/00_REG/06__REG_UID_REG.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REGISTRY
DOMAIN: REG
UID: UE.V2.REG.UID_REGISTRY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — UID REGISTRY

PURPOSE:
Реестр UID для предотвращения коллизий и фиксации канона.

POLICY:
- append-only (добавляем записи, не переписываем историю)
- collision-first (при совпадении UID — это COLLISION)
- reserved блокирует использование UID до снятия резерва

---

## UID FORMAT (rule)
RECOMMENDED:
UE.V2.<LAYER>.<DOMAIN>.<OBJECT>.<NNN>

EXAMPLES:
- UE.V2.REG.UID_REGISTRY.001
- UE.V2.NAV.INDEX_MANIFEST.010
- UE.V2.DOM_MUSIC.PIPE.DEFAULT.001

---

## RECORD SCHEMA
| FIELD | TYPE | NOTES |
|---|---|---|
| UID | string | уникальный идентификатор |
| STATUS | enum | ACTIVE|DRAFT|RESERVED|DEPRECATED |
| SCOPE | string | область системы |
| DOC_TYPE | string | тип документа |
| FILE_NAME | string | имя файла |
| VERSION | string | semver |
| CREATED | date | дата создания |
| OWNER | string | владелец |
| NOTE | string | краткая причина/коммент |

---

## REGISTRY (entries)
> Добавляй сюда по мере фиксации канона.

| UID | STATUS | SCOPE | DOC_TYPE | FILE_NAME | VERSION | CREATED | OWNER | NOTE |
|---|---|---|---|---|---|---|---|---|
| UE.V2.REG.INDEX_MANIFEST.001 | ACTIVE | UE_V2/03_ENT/00_REG | INDEX_MANIFEST | 00__INDEX_MANIFEST__REG.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.PIPELINE_CONTRACT.001 | ACTIVE | UE_V2/03_ENT/00_REG | PIPELINE_CONTRACT | 00__PIPELINE_CONTRACT__REG.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.ENTITY_IDS.001 | ACTIVE | UE_V2/03_ENT/00_REG | REG_RULES | 01__REG_ENTITY_IDS.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.PATH_MAP.001 | ACTIVE | UE_V2/03_ENT/00_REG | REG_RULES | 02__REG_PATH_MAP.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.ENTITY_CATALOG.001 | ACTIVE | UE_V2/03_ENT/00_REG | REG_CATALOG | 03__REG_ENTITY_CATALOG.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.ENTITY_TYPES.001 | ACTIVE | UE_V2/03_ENT/00_REG | REG_SCHEMA | 04__REG_ENTITY_TYPES.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.ENTITY_MIN_SET.001 | ACTIVE | UE_V2/03_ENT/00_REG | REG_RULES | 05__REG_ENTITY_MIN_SET.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.UID_REGISTRY.001 | ACTIVE | UE_V2/03_ENT/00_REG | REGISTRY | 06__REG_UID_REG.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.ENTITY_REGISTRY.001 | ACTIVE | UE_V2/03_ENT/00_REG | REGISTRY | 07__REG_ENTITY_REG.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.ARTIFACT_REGISTRY.001 | ACTIVE | UE_V2/03_ENT/00_REG | REGISTRY | 08__REG_ARTIFACT_REG.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.CHANGELOG.001 | ACTIVE | UE_V2/03_ENT/00_REG | LOG | 90__REG_CHANGELOG.md | 1.0.0 | 2026-01-30 | SYS | init |
| UE.V2.REG.DEPRECATION.001 | ACTIVE | UE_V2/03_ENT/00_REG | POLICY+LOG | 91__REG_DEPRECATION.md | 1.0.0 | 2026-01-30 | SYS | init |
