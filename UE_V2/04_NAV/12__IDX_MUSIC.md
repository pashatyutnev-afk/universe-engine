# 12__IDX_MUSIC

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / INDEX
UID: UE.V2.NAV.IDX_MUSIC.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Доменный индекс MUSIC: быстрый вход в пайпы + реалмы сущностей (ORC/CTL/VAL/QA) + KB навигацию.

---

## [M] INTENT
Дать рантайму один короткий вход в музыку, чтобы:
- ROUTER выбирал музыку через IDX, а не через дерево папок
- ORC/CTL/VAL/QA находились через индексы реалмов
- KB подключалась через KB_NAV_ROOT и scope-профили

---

## [M] MUSIC ENTRY (PIPES)
- UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md
- UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
- UE_V2/06_PIPE/22__PIPE_MUSIC_IDENTITY.md
- UE_V2/06_PIPE/14__PIPE_REL.md (handoff для релиза)

---

## [M] MUSIC ORC (REALM INDEX)
- UE_V2/03_ENT/30_ORC_ENT/10_MUSIC_ORCHESTRATORS/00__INDEX_MUSIC_ORCHESTRATORS.md

---

## [M] MUSIC CTL (REALM INDEX)
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS/00__INDEX__MUSIC_CONTROLLERS.md

---

## [M] MUSIC VAL (REALM INDEX)
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VALIDATORS/00__INDEX__MUSIC_VALIDATORS.md

---

## [M] MUSIC QA (REALM INDEX)
- UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__INDEX__MUSIC_QA.md

---

## [M] KB (ENTRYPOINT)
- UE_V2/05_KB/10__KB_NAV_ROOT.md
- UE_V2/05_KB/09__KB_SCOPE_PROFILES.md
- UE_V2/05_KB/08__KB_SOURCES.md

---

## [M] ROUTER REQUIREMENT
- If DOMAIN=MUSIC -> REQUIRED_IDX must include this file: UE_V2/04_NAV/12__IDX_MUSIC.md

---

## [M] GATES
PASS если:
- доступны пайпы и индексы реалмов ORC/CTL/VAL/QA
GAP если:
- отсутствует любой из реалм-индексов (создать/добавить)
STOP если:
- IDX_MUSIC недоступен при music-задаче
