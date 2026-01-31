FILE: UE_V2/03_ENT/00_REG/00__INDEX_MANIFEST__REG.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: INDEX_MANIFEST
DOMAIN: REG
UID: UE.V2.REG.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: RAW-ONLY
CREATED: 2026-01-30
OWNER: SYS

---

# INDEX_MANIFEST — REG

PURPOSE:
Единая адресная таблица папки REG. Содержит RAW для всех документов REG и сам используется как единственный источник адресов для PIPELINE_CONTRACT и рантайма.

ANTI_NOISE:
- RAW хранится только здесь.
- Любая навигация по REG выполняется через KEY → RAW.
- Запрещено дублировать RAW в других файлах REG.

---

## KEYSPACE (REG)

KEY_FORMAT:
REG.<OBJECT>

RESOLUTION_RULE:
KEY → RAW берётся только из TABLE ниже.

---

## TABLE (ADDRESS BOOK)

> Заполни колонку RAW, когда будешь вставлять реальные RAW-ссылки.

| KEY | FILE | DOC_TYPE | PURPOSE_BRIEF | STATUS | RAW |
|---|---|---|---|---|---|
| REG.INDEX_MANIFEST | 00__INDEX_MANIFEST__REG.md | INDEX_MANIFEST | Адресная таблица REG | ACTIVE | <PASTE_RAW> |
| REG.PIPELINE_CONTRACT | 00__PIPELINE_CONTRACT__REG.md | PIPELINE_CONTRACT | Навигатор работы с REG | ACTIVE | <PASTE_RAW> |
| REG.ENTITY_IDS | 01__REG_ENTITY_IDS.md | REG_RULES | Коды/ID сущностей, префиксы, семейства | ACTIVE | <PASTE_RAW> |
| REG.PATH_MAP | 02__REG_PATH_MAP.md | REG_RULES | Карта путей UE_V2, смысл корней/папок | ACTIVE | <PASTE_RAW> |
| REG.ENTITY_CATALOG | 03__REG_ENTITY_CATALOG.md | REG_CATALOG | Каталог обязательных сущностей UE_V2 | ACTIVE | <PASTE_RAW> |
| REG.ENTITY_TYPES | 04__REG_ENTITY_TYPES.md | REG_SCHEMA | Типы сущностей и их обязательные поля | ACTIVE | <PASTE_RAW> |
| REG.ENTITY_MIN_SET | 05__REG_ENTITY_MIN_SET.md | REG_RULES | Минимальные наборы для рантайма/доменов | ACTIVE | <PASTE_RAW> |
| REG.UID_REGISTRY | 06__REG_UID_REG.md | REGISTRY | Реестр UID, коллизии, резервы | ACTIVE | <PASTE_RAW> |
| REG.ENTITY_REGISTRY | 07__REG_ENTITY_REG.md | REGISTRY | Реестр сущностей (канон) | ACTIVE | <PASTE_RAW> |
| REG.ARTIFACT_REGISTRY | 08__REG_ARTIFACT_REG.md | REGISTRY | Реестр артефактов/выходов | ACTIVE | <PASTE_RAW> |
| REG.CHANGELOG | 90__REG_CHANGELOG.md | LOG | История изменений REG | ACTIVE | <PASTE_RAW> |
| REG.DEPRECATION | 91__REG_DEPRECATION.md | POLICY+LOG | Депрекейт и редиректы | ACTIVE | <PASTE_RAW> |

---

## LOAD_HINTS (MUST_LOAD for REG)
MIN_SET_KEYS:
- REG.INDEX_MANIFEST
- REG.PIPELINE_CONTRACT
- REG.ENTITY_IDS
- REG.PATH_MAP
- REG.UID_REGISTRY

OPTIONAL_KEYS:
- REG.ENTITY_TYPES
- REG.ENTITY_MIN_SET
- REG.ENTITY_REGISTRY
- REG.ARTIFACT_REGISTRY

---

## GUARDS
STOP_IF:
- INDEX_MANIFEST RAW missing for any MIN_SET_KEYS

GAP_IF:
- отсутствует KEY в TABLE для запрошенного объекта
