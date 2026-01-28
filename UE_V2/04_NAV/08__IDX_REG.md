# 08__IDX_REG

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / INDEX
UID: UE.V2.NAV.IDX_REG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Вход в REG слой (реестр сущностей и их совместимость).

---

## [M] INTENT
Дать рантайму быстрый доступ к реестрам без просмотра дерева папок и без ROOT_INDEX.

---

## [M] LINKS (PATH)
REG ядро:
- UE_V2/03_ENT/00_REG/01__REG_ENTITY_IDS.md
- UE_V2/03_ENT/00_REG/02__REG_NAMING_RULES.md
- UE_V2/03_ENT/00_REG/03__REG_PATH_MAP.md
- UE_V2/03_ENT/00_REG/04__REG_ENTITY_CATALOG.md
- UE_V2/03_ENT/00_REG/05__REG_CAPABILITIES.md
- UE_V2/03_ENT/00_REG/06__REG_STAGE_RULES.md
- UE_V2/03_ENT/00_REG/07__REG_INCOMPATIBILITY_RULES.md
- UE_V2/03_ENT/00_REG/08__REG_ENTITY_MIN_SET.md
- UE_V2/03_ENT/00_REG/90__REG_CHANGELOG.md

---

## [M] RULES
1) Любой выбор сущностей делается через REG_ENTITY_CATALOG.
2) Любые переезды папок фиксируются в REG_PATH_MAP и CHANGELOG.
3) Если REG отсутствует — STOP на системных задачах, GAP на доменных (по пайпу).

---

## [M] GATES
PASS если:
- REG_ENTITY_CATALOG достижим
GAP если:
- отсутствуют REG файлы 04–08
STOP если:
- отсутствуют 01–03 (идентификация/нейминг/путь)
