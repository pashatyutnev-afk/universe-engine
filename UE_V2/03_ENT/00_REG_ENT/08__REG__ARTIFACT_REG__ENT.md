FILE: UE_V2/03_ENT/00_REG_ENT/08__REG__ARTIFACT_REG__ENT.md
SCOPE: UE_V2 / 03_ENT / 00_REG_ENT
DOC_TYPE: REGISTRY
DOMAIN: REG
UID: UE.V2.REG.ARTIFACT_REGISTRY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — ARTIFACT REGISTRY

PURPOSE:
Канонический реестр выходных артефактов (OUTPUT_PACK/релизы/промпты/тексты/схемы), чтобы:
- фиксировать выпуск,
- отслеживать версии,
- избегать потери результатов.

POLICY:
- append-only
- адреса (RAW) не храним тут
- linkage идёт через UID/KEY и через INDEX_MANIFEST домена/релиза

---

## RECORD SCHEMA
| FIELD | TYPE | NOTES |
|---|---|---|
| UID | string | UID артефакта |
| ARTIFACT_TYPE | string | например OUTPUT_PACK / SUNO_TRACK / SPEC / MAP |
| DOMAIN | string | DOM_MUSIC / DOM_VIS / ... |
| TITLE | string | название артефакта |
| STATUS | enum | DRAFT|ACTIVE|DEPRECATED |
| VERSION | string | semver |
| CREATED | date | дата |
| OWNER | string | владелец |
| SOURCE_NOTE | string | краткий источник/прогон |

---

## REGISTRY (entries)
| UID | ARTIFACT_TYPE | DOMAIN | TITLE | STATUS | VERSION | CREATED | OWNER | SOURCE_NOTE |
|---|---|---|---|---|---|---|---|---|
