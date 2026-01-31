 FILE: UE_V2/03_ENT/00_REG_ENT/01__REG__ENTITY_IDS__ENT.md`
`SCOPE: UE_V2 / 03_ENT / 00_REG_ENT`
DOC_TYPE: REG_RULES
DOMAIN: REG
UID: UE.V2.REG.ENTITY_IDS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — ENTITY IDS

PURPOSE:
Единый список кодов/семейств сущностей UE_V2, чтобы:
- не плодить несовместимые названия,
- обеспечить предсказуемую маршрутизацию,
- поддержать UID/KEYSPACE.

---

## CANON ENTITY FAMILIES (CODES)

| CODE | FAMILY | ROLE_BRIEF |
|---|---|---|
| SYS | System | системные управляющие документы/шаблоны |
| LAW | Law | законы/политики/инварианты |
| STD | Standard | стандарты/шаблоны исполнения/форматы |
| NAV | Navigation | навигационные хабы (index_manifest/pipe_contract) |
| REG | Registry | реестры UID/сущностей/артефактов |
| KB | Knowledge Base | базы знаний и их правила |
| PIPE | Pipeline | доменные пайпы и контракты исполнения |
| LOG | Logs | логи прогона/решений/токенов |
| ENT | Entities | сущности рантайма (SPC/ENG/ORC/...) |
| SPC | Specialist | постановка/критерии/контроль смысла |
| ENG | Engine | генерация/сборка/преобразование |
| ORC | Orchestrator | управление шагами и стыковка сущностей |
| CTL | Controller | ограничения/допуски/политики исполнения |
| VAL | Validator | проверки/валидация/гейты |
| QA | Quality | тесты/дефекты/регресс |
| XREF | Cross-refs | перекрёстные соответствия/карты связей |
| DOM_* | Domain | домены (DOM_AUD, DOM_VIS, DOM_LOR, DOM_MUSIC и др.) |

---

## FILE NAMING RULE (folder-scoped)
CANON:
- 00__INDEX_MANIFEST__<FOLDER>.md
- 00__PIPELINE_CONTRACT__<FOLDER>.md
- NN__<FOLDER>_<SUBJECT>.md

NOTES:
- "00__" reserved for folder hubs only.
- Файлы реестров/правил не обязаны содержать ссылки. Адреса — только в INDEX_MANIFEST папки.

---

## KEY CONVENTION (recommended)
KEY_FORMAT:
- <FAMILY>.<OBJECT>
Examples:
- REG.UID_REGISTRY
- KB.SPC.OVERVIEW
- PIPE.DOM_MUSIC.DEFAULT
