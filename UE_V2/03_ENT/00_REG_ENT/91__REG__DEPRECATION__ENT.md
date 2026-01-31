FILE: UE_V2/03_ENT/00_REG_ENT/91__REG__DEPRECATION__ENT.md
SCOPE: UE_V2 / 03_ENT / 00_REG_ENT
DOC_TYPE: POLICY+LOG
DOMAIN: REG
UID: UE.V2.REG.DEPRECATION.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — DEPRECATION

PURPOSE:
Единая политика депрекейта:
- фиксирует что устарело,
- объясняет почему,
- указывает редирект (KEY-уровень).

POLICY:
- Устаревшее не удаляется без крайней необходимости.
- Любое удаление = запись тут + запись в CHANGELOG.
- Редирект задаётся через KEY (а не через RAW).

---

## DEPRECATION RECORD
| FIELD | TYPE | NOTES |
|---|---|---|
| OLD_KEY | string | что устарело |
| NEW_KEY | string | куда переехало |
| STATUS | enum | DEPRECATED|REMOVED |
| DATE | date | дата |
| REASON | string | кратко |
| NOTE | string | доп. |

---

## ENTRIES
| OLD_KEY | NEW_KEY | STATUS | DATE | REASON | NOTE |
|---|---|---|---|---|---|
