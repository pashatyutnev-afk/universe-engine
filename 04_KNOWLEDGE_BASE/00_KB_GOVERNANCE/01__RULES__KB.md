# KB RULES (GOVERNANCE LAWSET)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULESET
RULESET_SCOPE: KB
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.RULES.001
OWNER: SYSTEM
ROLE: Governs Knowledge Base: canon conditions, existence rule, anti-duplication, tagging, passports, and xref/rel policy inside KB

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "KB ruleset зафиксирован как канон: условия каноничности, anti-dup, структура realm-ов, паспорта, теги и ссылки"
- REASON: "Без жёстких правил KB превращается в свалку и начинает конкурировать со стандартами/законами"
- IMPACT: "Весь слой 04_KNOWLEDGE_BASE и все будущие KB-артефакты"

---

## 0) PURPOSE
Этот ruleset фиксирует **как устроена KB** и что считается корректной KB-единицей.

KB служит для:
- ремесла (как делать)
- практик (чеклисты/паттерны)
- примеров
- справочников KB (tags, entity passports)

KB НЕ служит для:
- законов системы
- дублирования стандартов как SoT

---

## 1) KB CANON CONDITIONS (STRICT)
KB-файл является каноничным только если:

1) Зарегистрирован в master-index KB:
   `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

2) Имеет Doc Control шапку:
   `SCOPE/LAYER/DOC_TYPE/STATUS/LOCK/VERSION/UID/OWNER/ROLE`

3) Имя файла соответствует naming:
   `NN__NAME.md` (realm/системные KB файлы)
   `00__README__...` допустимо только в governance папке

4) Не дублирует SoT смысл (anti-dup)

Нарушение любого пункта => NON-CANON.

---

## 2) ORDER OF AUTHORITY (KB INTERNAL)
Внутри KB приоритет:

1) `00_KB_GOVERNANCE/*` (правила/карты/реестры)
2) `00__INDEX__KNOWLEDGE_BASE.md` (существование/состав)
3) realm-файлы `NN__...` (контент KB)
4) KB entity passports (частные сущности/кейсы/карточки)

---

## 3) REALM RULE (ONE REALM = ONE DOMAIN)
Realm-файл — это “домен знаний” (Narrative/Character/Visual/…).
Правила:
- realm не должен включать чужой домен как основной контент
- пересечения оформляются через XREF, а не копированием

---

## 4) ANTI-DUPLICATION (HARD)
- один смысл → один KB-артефакт
- если контент уже есть в другом realm — делаем ссылку XREF
- если нужен конкретный объект (персонаж/локация/система) — делаем **KB entity passport**, а не размазываем по realm

---

## 5) KB ENTITY PASSPORT (WHEN TO USE)
Используем паспорт, когда:
- нужен объект (entity) с идентичностью (UID)
- нужно версионирование и статус
- нужны связи REL/XREF
- нужен reuse в проектах

Паспорт должен следовать шаблону:
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md`

---

## 6) REL / XREF POLICY (KB)
### 6.1 XREF (doc pointers)
- используем XREF вместо копирования текста
- если есть пересечение между realm-ами — XREF обязателен

### 6.2 REL (entity relationships)
REL применяем для:
- depends_on
- part_of
- related_to
- replaces / deprecates

REL-записи в паспортах должны быть короткими, без “романов”.

---

## 7) TAGGING RULE (KB)
Теги обязательны для KB entity passports и желательны для realm-файлов.

SoT по тегам:
- `04_KNOWLEDGE_BASE/90__KB_TAGS.md`

Запрещено:
- теги, которых нет в словаре
- “случайные” теги ради красоты

---

## 8) CHANGE FLOW (MANDATORY)
Новый KB файл создаётся только так:

1) Проверка anti-dup
2) Регистрация в master-index
3) Создание файла с Doc Control + UID + SemVer
4) Добавление XREF/REL при необходимости
5) Фиксация изменений по правилам системы (через governance)

---

## 9) DEPRECATION RULE (KB)
Если KB-артефакт устарел:
- `STATUS: DEPRECATED`
- `LOCK: FIXED`
- обязателен `REPLACED_BY` (UID/Path)

Удаление допускается только если файл **не был каноном** (не зарегистрирован).

---

## FINAL RULE (LOCK)
Этот ruleset обязателен для всего слоя 04_KNOWLEDGE_BASE.
LOCK: FIXED
--- END.
