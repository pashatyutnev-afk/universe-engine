# KB TAGS (SYSTEM REFERENCE) (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REGISTRY
REGISTRY_TYPE: KB_TAGS
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.TAGS.090
OWNER: SYSTEM
ROLE: Canonical registry of KB tags used for classification and filtering across KB entities and realm knowledge. Tags do not define essence (TYPE does), tags are metadata.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "KB tags вынесены в governance (90+ namespace) для устранения коллизии с realm 02_CHARACTER_CRAFT; введён controlled tag registry"
- REASON: "Убрать номерную коллизию и стандартизировать теги"
- IMPACT: "KB entities tagging + realm tagging + registries"

---

## XREF (UID-first)
XREF: UE.KB.GOV.STORAGE_MAP.014 | governs | KB system refs live in 90+ namespace | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md
XREF: UE.KB.GOV.RULES.011 | governs | tags are metadata, no-dup, typing | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 0) PURPOSE
Этот файл — единый справочник тегов KB.

Теги используются:
- в паспортах сущностей (поле TAGS)
- в реестре сущностей (колонка TAGS)
- в realm-знаниях (как метки секций/примеров)

---

## 1) PRIME RULES (ABSOLUTE)
- TAG ≠ TYPE  
  TYPE определяет “что это” (CHARACTER/LOCATION/…), TAG — метаданные.
- Один смысл → один TAG_KEY (no-dup)
- Тег не должен конфликтовать по смыслу с ENTITY_TYPE.
- Если тег не в этом реестре — он считается **non-standard** (разрешено временно, но нежелательно).

---

## 2) TAG FORMAT (CONTROLLED)
Каждый тег имеет:
- TAG_KEY: UpperCamelCase или UPPER_SNAKE_CASE (выбери один стиль и держи)
- TAG_NAME: человекочитаемое имя
- DOMAIN: WORLD|NARRATIVE|CHARACTER|VISUAL|SOUND|PRODUCTION|MARKETING|RESEARCH|SYSTEM
- DESCRIPTION: кратко “что помечает”
- ALIASES: optional

Рекомендация (для чистоты): TAG_KEY = UpperCamelCase.

---

## 3) CONTROLLED DOMAINS
- WORLD
- NARRATIVE
- CHARACTER
- VISUAL
- SOUND
- PRODUCTION
- MARKETING
- RESEARCH
- SYSTEM

---

## 4) TAG REGISTRY TABLE (CANON)
| TAG_KEY | TAG_NAME | DOMAIN | DESCRIPTION | ALIASES |
|---|---|---|---|---|
| Season_1 | Season 1 | WORLD | Относится к материалам/сущностям 1 сезона | S1 |
| Season_2 | Season 2 | WORLD | Относится к материалам/сущностям 2 сезона | S2 |
| Arc_Main | Main Arc | NARRATIVE | Главная сюжетная дуга | MainArc |
| Arc_Side | Side Arc | NARRATIVE | Побочная дуга | SideArc |
| Tone_Dark | Dark Tone | NARRATIVE | Мрачный тон | Dark |
| Tone_Light | Light Tone | NARRATIVE | Лёгкий тон | Light |
| Style_Realistic | Realistic Style | VISUAL | Реалистичная стилистика | Realism |
| Style_Stylized | Stylized Style | VISUAL | Стилизованная подача | Stylized |
| Canon_Core | Core Canon | SYSTEM | Ядро канона (нельзя менять без протокола) | Core |
| Canon_Legacy | Legacy | SYSTEM | Устаревшее/историческое, сохранено как legacy | Legacy |

> Заполни дальше под свои нужды. Главное — не плодить синонимы.

---

## 5) TAG USAGE PATTERNS
### 5.1 In entity passports
TAGS: [Season_1, Arc_Main, Tone_Dark]

### 5.2 In Global Registry
TAGS: Season_1; Arc_Main; Tone_Dark

---

## 6) CHANGE POLICY
- PATCH: описание/alias исправления
- MINOR: добавлен новый тег
- MAJOR: переименование/удаление тега (breaking)

---

## FINAL RULE (LOCK)
Этот реестр — SoT по стандартным тегам KB.
--- END.
