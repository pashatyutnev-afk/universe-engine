FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/01__MUS__PUBLIC_DOMAIN_SOURCE_PICKER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.PUBLIC_DOMAIN_SOURCE_PICKER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PUBLIC_DOMAIN_SOURCE_PICKER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.PUBLIC_DOMAIN_SOURCE_PICKER.001

## [M] PURPOSE
Формирует SOURCE_POLICY_TOKEN: какие источники/референсы допустимы для описаний и анализа.
Цель — снижать риск копирования и держать “референсы” как принципы, а не как воспроизведение.

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF]
- Outputs: [SOURCE_POLICY_TOKEN, FAIL_CODE?]

## [M] CORE_RULES
- Разрешать только общие описания жанра/инструментов/структуры без копирования строк/мелодий.
- Если пользователь просит “сделай как трек X один в один” — помечать как запрет.
- При сомнении — отдавать ограничения и безопасные альтернативы.

## [M] KB SCOPE
- KB Inputs: [правила допустимых ссылок, ограничения копирования]
- KB Outputs: [SOURCE_POLICY_TOKEN]
- KB Boundaries: [не добавлять “факты о правах”, если их нет во входе]

## [M] GATES
- PASS: policy сформирован, запреты ясны
- FAIL: конфликт требований (копирование vs оригинальность)

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: SOURCE_POLICY_TOKEN -> GENRE_STYLE_ROUTER / LYRIC_BRIEF_FACTORY

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
