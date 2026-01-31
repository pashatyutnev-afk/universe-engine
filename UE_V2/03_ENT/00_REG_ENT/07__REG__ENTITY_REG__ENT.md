FILE: UE_V2/03_ENT/00_REG_ENT/07__REG__ENTITY_REG__ENT.md
SCOPE: UE_V2 / 03_ENT / 00_REG_ENT
DOC_TYPE: REGISTRY
DOMAIN: REG
UID: UE.V2.REG.ENTITY_REGISTRY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — ENTITY REGISTRY

PURPOSE:
Канонический реестр сущностей UE_V2 (SPC/ENG/ORC/CTL/VAL/QA/XREF/PIPE/KB/NAV/REG/SYS).

POLICY:
- append-only
- запись должна иметь UID и TYPE
- адрес (RAW) хранится не здесь, а в INDEX_MANIFEST соответствующих папок

---

## RECORD SCHEMA
| FIELD | TYPE | NOTES |
|---|---|---|
| UID | string | уникальный UID сущности |
| TYPE | enum | SPC|ENG|ORC|CTL|VAL|QA|XREF|PIPE|KB|NAV|REG|SYS |
| KEY | string | ключ для навигации (не адрес) |
| NAME | string | человекочитаемое имя |
| STATUS | enum | ACTIVE|DRAFT|DEPRECATED |
| VERSION | string | semver |
| OWNER | string | владелец |
| NOTE | string | кратко |

---

## REGISTRY (entries)
> Пока можно держать только REG-уровень, затем добавлять остальные сущности по мере канонизации.

| UID | TYPE | KEY | NAME | STATUS | VERSION | OWNER | NOTE |
|---|---|---|---|---|---|---|---|
| UE.V2.REG.INDEX_MANIFEST.001 | REG | REG.INDEX_MANIFEST | INDEX_MANIFEST — REG | ACTIVE | 1.0.0 | SYS | init |
| UE.V2.REG.PIPELINE_CONTRACT.001 | REG | REG.PIPELINE_CONTRACT | PIPELINE_CONTRACT — REG | ACTIVE | 1.0.0 | SYS | init |
