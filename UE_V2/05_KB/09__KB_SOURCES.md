# 08__KB_SOURCES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: KB / SOURCES
UID: UE.V2.KB.SOURCES.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Реестр разрешённых источников KB (модулей/доков/доменных баз). Анти-хаос и анти-выдумки.

---

## [M] INTENT
Определить, какие KB-источники разрешено использовать для задач, чтобы система не опиралась на случайные или неканоничные данные.

---

## [M] RULES
1) Любая ссылка на “знание” должна указывать SOURCE_ID (если оно не является очевидным вводом пользователя).
2) Источник может быть:
   - внутренний документ UE_V2 (STD/LAW/PIPE/DOMAIN KB)
   - доменный модуль TOPICS
   - внешняя ссылка, если явно разрешена
3) Любое добавление/изменение источника фиксируется в CHANGE_LOG.
4) Источники привязываются к DOMAIN и KB_SCOPE профилям.

---

## [M] SOURCE_ENTRY_TEMPLATE
KB_SOURCE:
- SOURCE_ID:
- DOMAIN:
- TYPE: (INTERNAL_DOC|TOPIC_MODULE|EXTERNAL_REF)
- PATH_REF_OR_URL:
- SUMMARY (1–3 строки):
- ALLOWED_SCOPES: (csv KB_SCOPE_ID)
- STATUS: (ACTIVE|DEPRECATED)

---

## [M] SOURCES (STARTER)
| SOURCE_ID | DOMAIN | TYPE | PATH_REF_OR_URL | SUMMARY | ALLOWED_SCOPES | STATUS |
|---|---|---|---|---|---|---|
| KB.SRC.CORE.STD | CORE | INTERNAL_DOC | UE_V2/02_STD/* | Стандарты формата/гейтов/шума | KB.SCOPE.CORE.* | ACTIVE |
| KB.SRC.CORE.LAW | CORE | INTERNAL_DOC | UE_V2/01_LAW/* | Законы системы | KB.SCOPE.CORE.GOV | ACTIVE |
| KB.SRC.CORE.XREF | CORE | INTERNAL_DOC | UE_V2/03_ENT/08_XREF/* | Карты совместимости/обязательности | KB.SCOPE.CORE.GOV,KB.SCOPE.CORE.QA | ACTIVE |
| KB.SRC.MUSIC.TOPICS | MUSIC | TOPIC_MODULE | UE_V2/10_TOPICS/03_SOUND_MUSIC/* | Музыкальные темы/модули | KB.SCOPE.MUSIC.* | ACTIVE |

---

## [M] GATES
PASS если:
- KB_TOKEN ссылается на разрешённые SOURCE_ID
REWORK если:
- используются источники вне списка
GAP если:
- нужен новый источник (добавить SOURCE_ENTRY)
