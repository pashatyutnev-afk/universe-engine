# 09__IDX_XREF

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / INDEX
UID: UE.V2.NAV.IDX_XREF.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Вход в XREF реалм (карты связности и обязательности) — UE_V2/03_ENT/08_XREF.

---

## [M] INTENT
Дать рантайму быстрый доступ к картам:
- какой PIPE/ORC использовать
- какие CTL/VAL/QA обязательны
- как стыкуются IO и KB scopes
- как обеспечивать покрытие Pillars

---

## [M] LINKS (PATH)
XREF REALM:
- UE_V2/03_ENT/90_XREF_ENT/00__INDEX__CROSSREF.md
- UE_V2/03_ENT/90_XREF_ENT/00__README__CROSSREF.md

MAPS:
- UE_V2/03_ENT/90_XREF_ENT/01__MAP_ENG_to_ORC.md
- UE_V2/03_ENT/90_XREF_ENT/02__MAP_ORC_to_SPC.md
- UE_V2/03_ENT/90_XREF_ENT/03__MAP__VALIDATION_MATRIX.md
- UE_V2/03_ENT/90_XREF_ENT/04__MAP__PIPELINES.md
- UE_V2/03_ENT/90_XREF_ENT/05__MAP__ENTITY_IO_TYPES.md
- UE_V2/03_ENT/90_XREF_ENT/06__MAP__KB_SCOPE_BINDINGS.md
- UE_V2/03_ENT/90_XREF_ENT/07__MAP__COVERAGE_TO_ENTITIES.md
- UE_V2/03_ENT/90_XREF_ENT/08__MAP__DEFAULT_CHAIN.md

---

## [M] GATES
PASS если:
- доступны 03__MAP__VALIDATION_MATRIX и 04__MAP__PIPELINES
GAP если:
- отсутствуют карты 05–08
STOP если:
- отсутствует 03 или 04 (валидация/пайпы)
