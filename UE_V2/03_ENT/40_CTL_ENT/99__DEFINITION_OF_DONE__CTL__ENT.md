FILE: UE_V2/03_ENT/40_CTL_ENT/99__DEFINITION_OF_DONE__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT
DOC_TYPE: STD
DOMAIN: CTL_ENT
UID: UE.V2.ENT.CTL.DOD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT

---

## [M] DEFINITION OF DONE (40_CTL_ENT)

PASS когда выполнено всё ниже:

### [M] ROOT COMPLETE
- `00__INDEX_MANIFEST__CTL__ENT.md` содержит:
  - SELF
  - REQUIRED (INDEX_MANIFEST, PIPELINE_CONTRACT, DOD)
  - REALM keys: REALM.TPL_CTL, REALM.MUS_CTL, REALM.VID_CTL, REALM.WEB_CTL, REALM.LIB_CTL
  - корректные RAW ссылки на индекс каждого реалма
- `00__PIPELINE_CONTRACT__CTL__ENT.md`:
  - не содержит RAW
  - роутит по доменам и артефакт-хинтам
  - возвращает KEYS only

### [M] REALMS COMPLETE
Для каждого реалма (00_TEMPLATES / 10_MUSIC / 20_VIDEO / 30_WEB / 90_SHARED_LIB):
- существует INDEX_MANIFEST реалма и он содержит SELF + PIPELINE_CONTRACT + контентные KEY
- существует PIPELINE_CONTRACT реалма и он без RAW
- все CTL_ENTITY/CTL_BLOCKER документы реалма не содержат RAW
- любые RAW ссылки находятся только в INDEX_MANIFEST соответствующего реалма

### [M] POLICY INVARIANTS
- Никаких RAW вне INDEX_MANIFEST.
- Контракты не содержат RAW и не делают repo edits.
- Любая новая библиотека/контроллер добавляется:
  - новым файлом в соответствующем реалме
  - новой записью KEY в INDEX_MANIFEST реалма
  - (опционально) добавлением realm в root manifest, только если это новый реалм, а не новый файл

### [M] NAV DETERMINISM
- Любой маршрут CTL начинается с root `PIPELINE_CONTRACT` или напрямую с realm `PIPELINE_CONTRACT`, но везде через KEY.
- PATH используется только как справка.

FAIL если:
- RAW встречается не в INDEX_MANIFEST
- нет SELF в любом INDEX_MANIFEST
- PIPELINE_CONTRACT содержит RAW или не может вернуть KEY для запуска
