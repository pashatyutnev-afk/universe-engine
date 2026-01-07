# KB REALM (GOVERNANCE README)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
REALM: KB_GOVERNANCE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.README.001
OWNER: SYSTEM
ROLE: Governance realm overview for Knowledge Base: boundaries, entrypoints, rules of existence, and how KB is maintained

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "KB governance README приведён к канону: Doc Control + UID + SemVer + жёсткие границы governance vs realms"
- REASON: "Без README-гранниц KB расползается и начинает дублировать стандарты/законы"
- IMPACT: "Вся навигация и дисциплина слоя 04_KNOWLEDGE_BASE"

---

## 0) PURPOSE
Этот файл — **README реальма управления KB** (не контент).

Он объясняет:
- где находится **единственная точка истины** по составу KB
- чем governance отличается от realm-контента
- как добавлять/изменять KB-документы без дублей

---

## 1) CORE PRINCIPLE (KB IS NOT SYSTEM LAW)
KB — это **база знаний и практик**, а не законы системы.

При конфликте:
- System Law (01_SYSTEM_LAW) выше всего
- Standards (02_STANDARDS) задают “как должно быть”
- KB описывает ремесло/подходы/примеры и подчиняется стандартам

---

## 2) ENTRYPOINTS (WHERE TO START)
Единственные официальные входы в KB:

1) MASTER INDEX (existence rule)
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

2) KB governance rules
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`

---

## 3) GOVERNANCE VS REALMS (BOUNDARIES)
### 3.1 Governance (this folder)
`04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/` содержит:
- правила и карты KB
- реестры KB
- storage map KB
- create flow KB
- шаблоны KB-паспортов

Governance **не содержит** “контент-практику” (ремесло).

### 3.2 Realms (content knowledge)
Файлы `04_KNOWLEDGE_BASE/NN__*.md` (Narrative/Character/Visual/...) содержат:
- знания, принципы, примеры, чеклисты
- но не объявляют existence для слоя (это делает master-index)
- и не дублируют стандарты/законы

---

## 4) EXISTENCE RULE (KB)
Для слоя KB действует жёсткое правило:

- если KB-документа нет в `00__INDEX__KNOWLEDGE_BASE.md` → он не существует для KB
- файлы вне реестра считаются NON-CANON

---

## 5) NO-DUPLICATION (KB)
- Один смысл → один KB-артефакт.
- Если нужна детализация:
  - расширяй существующий realm (если это “контент”)
  - или создавай KB Entity Passport + XREF/REL (если это сущность/карточка)

Запрещено:
- копировать один и тот же контент в разные realm-файлы
- создавать “второй главный” документ по теме

---

## 6) CHANGE FLOW (KB MAINTENANCE)
Как добавлять новый KB-документ:

1) Проверить, что смысл не существует (anti-dup).
2) Добавить запись в `00__INDEX__KNOWLEDGE_BASE.md`.
3) Создать файл по naming `NN__...` и Doc Control.
4) Если это сущность — оформить паспорт по шаблону.
5) Зафиксировать изменение по общим правилам изменений системы.

---

## 7) STATUS / LOCK POLICY (KB)
- Governance файлы: обычно `STATUS: ACTIVE`, `LOCK: FIXED`
- Realm-контент: допускается `STATUS: DRAFT`, пока не стабилизирован
- Файл без Doc Control шапки считается неканоничным (ошибка)

---

## FINAL RULE (LOCK)
Этот README закрепляет границы KB и порядок работы.
LOCK: FIXED
--- END.
