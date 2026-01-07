# PRODUCTION PIPELINE (KB REALM)
FILE: 04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_REALM
REALM: PRODUCTION
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.REALM.PRODUCTION.001
OWNER: SYSTEM
ROLE: Canonical knowledge realm for production pipeline: from narrative assets to media outputs, pipeline stages, handoffs, QA gates, and pointers to production engines

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Realm Production Pipeline канонизирован: этапы, handoff контракты, QA гейты, границы и XREF"
- REASON: "Без пайплайна даже хорошие идеи не превращаются в артефакты; нужен общий язык этапов"
- IMPACT: "Связка KB → ENG production engines → outputs"

---

## 0) PURPOSE
Этот realm — база знаний “как доводить идею до артефакта”.

Он содержит:
- этапы пайплайна (идея → план → производство → QA → выпуск)
- правила передачи (handoff) между этапами
- гейты качества (минимальные)
- XREF на ENG движки производства и форматные движки

---

## 1) BOUNDARIES (HARD)
### 1.1 This realm IS
- стадии производства (pipeline stages)
- контракты вход/выход (что нужно на входе и что получить)
- гейты качества (минимум для перехода)
- дисциплина версий/папок как практика (но не стандарт)

### 1.2 This realm IS NOT
- нарративные правила сцен (это narrative realm)
- психология персонажей (character realm)
- законы канона/UID/версий (system law + standards)

---

## 2) PRIMARY XREF (WHERE THE TRUTH LIVES)
### 2.1 Production engines (execution)
- `08_KNOWLEDGE_PRODUCTION_ENGINES/*` (visual/audio/media generation, editing)
- `07_PRODUCTION_FORMAT_ENGINES/*` (book/series/youtube/short/game)

### 2.2 Governance engines (changes)
- `00_GOVERNANCE_ENGINES/*` (audit/change control/consistency/dependencies)

---

## 3) PIPELINE STAGES (CANON PRACTICE MAP)
> Это “практическая карта”. Точные форматы — в standards/templates.

### Stage 0 — Intake (сырьё)
Вход:
- идея, заметки, референсы, требования
Выход:
- краткое описание цели, аудитории, формата
Гейт:
- понятна цель и формат

### Stage 1 — Plan (структура)
Вход:
- Stage 0 output
Выход:
- структура (главы/эпизоды/сцены), список сущностей, риски
Гейт:
- есть план и “что делаем дальше”

### Stage 2 — Build (производство)
Вход:
- план + материалы
Выход:
- черновые артефакты (черновик текста / черновой монтаж / черновые кадры)
Гейт:
- артефакт существует и повторяемо собирается

### Stage 3 — QA (проверка)
Вход:
- черновые артефакты
Выход:
- список исправлений + правки
Гейт:
- нет критических дыр (логика/читабельность/качество)

### Stage 4 — Release (выпуск)
Вход:
- QA passed
Выход:
- финальные артефакты + метаданные (описания, упаковка)
Гейт:
- артефакт готов для потребления

---

## 4) HANDOFF CONTRACT (MINIMUM)
Любая передача между этапами обязана иметь:
- WHAT: что передаём (артефакты)
- WHY: зачем (цель)
- DONE: критерий “готово”
- NEXT: кто следующий и что делает

Если хоть одного пункта нет — передача считается “туманной”.

---

## 5) QA GATES (MINIMUM)
### 5.1 Narrative gate (если есть история)
- причинность не рвётся
- ставки понятны
- есть повороты/изменения

### 5.2 Visual gate (если есть визуал)
- читаемость кадра
- стиль не прыгает
- continuity выдержан

### 5.3 Sound gate (если есть звук)
- слышно главное
- музыка не мешает смыслу

### 5.4 Packaging gate
- метаданные есть (название/описание/версия)
- структура хранения соответствует storage map

---

## 6) COMMON FAILURE MODES (WHAT TO WATCH)
- “делаем всё сразу” без плана → распад сроков
- “нет handoff контракта” → передали воздух
- “QA нет” → на релиз вылезают дыры
- “плодим версии без смысла” → невозможно понять, что актуально

---

## 7) OUTPUT POINTERS
Этот realm обычно “производит”:
- чеклист пайплайна на проект
- handoff notes
- список артефактов на выпуск (release pack)

---

## 8) XREF (MANDATORY POINTERS)
XREF_DOC: 04_KNOWLEDGE_BASE/03__VISUAL_CINEMA.md | WHY:визуальные решения должны быть встроены в пайплайн
XREF_DOC: 04_KNOWLEDGE_BASE/04__SOUND_MUSIC.md | WHY:звук/музыка должны проходить production гейт
XREF_DOC: 04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION.md | WHY:упаковка и выпуск требуют маркетинга/дистрибуции

---

## 9) NEXT EXTENSIONS (CONTROLLED)
Добавлять сюда можно:
- конкретные handoff шаблоны (как KB entities/templates)
- чеклисты QA как сущности
- ссылки на “output layer” (когда он формализован)

--- END.
