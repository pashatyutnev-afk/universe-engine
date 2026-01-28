# 28__SCOPE_GATE_PATTERN

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.SCOPE_GATE_PATTERN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единый паттерн "SCOPE-GATE": турникет доступа к знаниям/модулям/сущностям через KB_SCOPE и индексы.

---

## [M] INTENT
Гарантировать, что сущности не блуждают и не тащат мусор:
каждая сущность проходит через scope-гейт и берёт только разрешённые модули/источники в ограниченном объёме.

---

## [M] DEFINITIONS
- SCOPE-GATE: правило-турникет, ограничивающее доступ (что можно брать и сколько).
- KB_SCOPE_ID: идентификатор профиля знаний (что разрешено знать/использовать).
- DOMAIN_SCOPE: ограничение по домену (MUSIC/VIS/LOR/REL/CORE).
- MODULE: KB-модуль (карточка знаний).
- PICKSET: выбранный набор модулей (3–7).

---

## [M] CANON FLOW (SCOPE-GATE)
S0) Identify scope:
- получить KB_SCOPE_ID (из REG или из ROUTE/PLAN)

S1) Load scope profile:
- открыть KB_SCOPE_PROFILES и найти профиль

S2) Pick modules via IDX:
- открыть KB_NAV_ROOT
- затем IDX_KB_MODULES_BY_DOMAIN или IDX_KB_MODULES_BY_TOPIC
- выбрать PICKSET (3–7 модулей)

S3) Extract token:
- извлечь из PICKSET краткий KB_TOKEN (5–15 пунктов)
- закрыть KB (не держать модули в контексте)

S4) Use token:
- дальше работать только по KB_TOKEN + ограничениям do_not

---

## [M] LIMITS (DEFAULT)
- PICKSET_MAX_MODULES: 7
- KB_TOKEN_MAX_ITEMS: 15
- KB_TOKEN_MAX_DO_NOT: 5
- KB_SOURCES_MAX: 5
- Если нужно больше — делаем дополнительный STEP (STEP-RUN), а не расширяем один шаг

---

## [M] SCOPE RULES
1) Сущность не имеет права использовать знания вне своего KB_SCOPE_ID.
2) Несовпадение DOMAIN задачи и DOMAIN_ALLOWED scope-профиля -> REWORK или GAP.
3) Если scope отсутствует -> GAP (создать профиль или назначить KB_SCOPE_ID в REG).
4) Любой “большой текст” должен быть превращён в токен (KB_TOKEN / CONTRIBUTION_TOKEN).

---

## [M] OUTPUTS (REQUIRED)
- KB_TOKEN (обязателен при обращении к KB)
- TRACE запись: какие модули были выбраны (через ссылки/ID, без копирования)

---

## [M] GATES
PASS если:
- KB_TOKEN создан из 3–7 модулей и в пределах лимитов
GAP если:
- нет KB_SCOPE профиля или нет IDX_KB навигации
REWORK если:
- тянут знания вне scope или превышают лимиты
STOP если:
- систематическое нарушение scope (ломает весь anti-noise режим)
