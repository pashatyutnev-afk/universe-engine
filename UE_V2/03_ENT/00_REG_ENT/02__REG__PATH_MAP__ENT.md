FILE: UE_V2/03_ENT/00_REG_ENT/02__REG__PATH_MAP__ENT.md
SCOPE: UE_V2 / 03_ENT / 00_REG_ENT
DOC_TYPE: REG_RULES
DOMAIN: REG
UID: UE.V2.REG.PATH_MAP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — PATH MAP

PURPOSE:
Карта смыслов по корням UE_V2 и правила именования папок/слоёв.

---

## UE_V2 ROOT LAYERS (semantic)
| PATH_ROOT | MEANING |
|---|---|
| UE_V2/00_BOOT | старт/рантайм/роутер/протоколы |
| UE_V2/01_SYS | системные шаблоны и тех. каркас |
| UE_V2/02_LAW | законы системы |
| UE_V2/02_STD | стандарты/форматы/шаблоны исполнения |
| UE_V2/03_ENT | сущности и их реестры (включая REG) |
| UE_V2/04_NAV | навигационные индексы и карты доступа |
| UE_V2/05_KB | базы знаний и их контуры |
| UE_V2/06_PIPE | пайпы исполнения (общие) |
| UE_V2/07_DOM_AUD | домен аудио/музыка/звук |
| UE_V2/08_DOM_VIS | домен визуал/графика |
| UE_V2/09_DOM_LOR | домен лор/сюжет/мир |
| UE_V2/10_REL | релизы/сборки/пакеты |
| UE_V2/11_LEX | терминология/лексикон |
| UE_V2/14_LOG | логи/архив токенов/решения |

---

## FOLDER NUMBERING (rule)
- 00__ reserved for hub-files in folder (INDEX_MANIFEST + PIPELINE_CONTRACT).
- 01..89 reserved for active docs.
- 90..99 reserved for logs/policies (CHANGELOG/DEPRECATION etc.).

---

## PATH STABILITY (rule)
- Переименования допустимы, но должны сопровождаться:
  - записью в CHANGELOG
  - редиректом/пометкой в DEPRECATION
  - обновлением RAW в INDEX_MANIFEST соответствующих папок
