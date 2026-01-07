# VISUAL CINEMA (KB REALM)
FILE: 04_KNOWLEDGE_BASE/03__VISUAL_CINEMA.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_REALM
REALM: VISUAL
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.REALM.VISUAL.001
OWNER: SYSTEM
ROLE: Canonical knowledge realm for visual & cinema craft: composition, framing, camera language, lighting intent, art direction basics, readability, continuity (practices + checklists + pointers)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Realm Visual Cinema канонизирован: Doc Control + границы + практики + чеклисты + XREF"
- REASON: "Без визуального ремесла сцены не читаются и распадаются по стилю"
- IMPACT: "Визуальные практики, связка с production pipeline и image/video engines"

---

## 0) PURPOSE
Этот realm — база знаний “как сделать визуал читаемым и кинематографичным”.

Он содержит:
- практики композиции, кадра, визуального языка
- чеклисты читаемости и последовательности
- XREF на ENG-производственные движки (camera/lighting/art style/image/video)

---

## 1) BOUNDARIES (HARD)
### 1.1 This realm IS
- композиция, баланс, акценты
- кадрирование, планы, визуальная грамматика
- движение/статичность камеры как смысл
- свет как намерение (не как физический симулятор)
- читаемость (силуэт, контраст, иерархия)
- визуальная непротиворечивость сцен (continuity)

### 1.2 This realm IS NOT
- сюжетная структура/повороты (narrative realm)
- глубокая музыка/аранж/вокал (sound/music engines)
- правила канона/версий/UID (system law + standards)

---

## 2) PRIMARY XREF (WHERE THE TRUTH LIVES)
### 2.1 Engines (production execution)
- Knowledge Production Engines (ENG): visual composition, art style, camera/cinematography, lighting, image generation, video generation, editing/montage

### 2.2 Standards
- Doc control + UID/naming (оформление артефактов)
- если используются scene packs / track events — они живут в стандартах

---

## 3) CORE VISUAL MODEL (MINIMUM)
Если надо быстро собрать “рабочий кадр”, минимум такой:

1) SUBJECT (что главное)
2) CONTEXT (где/когда/что вокруг)
3) DEPTH (передний/средний/задний планы)
4) LIGHT INTENT (что подсвечиваем и зачем)
5) READABILITY (силуэт/контраст/иерархия)

---

## 4) COMPOSITION (PRACTICES)
### 4.1 Hierarchy rule (главное видно сразу)
- один главный акцент
- максимум 2 вторичных акцента
- остальное — фон/ритм

### 4.2 Silhouette test
Если главный объект не читается в чёрном силуэте — кадр слабый.

### 4.3 Lines & flow
Используй линии/массы, чтобы вести взгляд:
- к герою
- к действию
- к важной детали

---

## 5) FRAMING & SHOT LANGUAGE
### 5.1 Shot purpose rule
Каждый план должен иметь цель:
- показать действие
- показать реакцию
- показать информацию (пространство/угрозу/ресурс)

### 5.2 Common shots (utility)
- wide: география/контекст
- medium: действие/диалог
- close: эмоция/деталь
- insert: важная информация

---

## 6) CAMERA (MEANING, NOT ONLY STYLE)
### 6.1 Camera movement rule
Движение камеры должно объясняться:
- вниманием (мы “подсматриваем”)
- напряжением (мы “поджимаем”)
- раскрытием (мы “открываем” информацию)

Если движение “просто красиво” — часто мешает.

### 6.2 Stability vs chaos
- статичная камера = контроль/ясность
- дрожь/хаос = опасность/неустойчивость
Не смешивай без причины.

---

## 7) LIGHTING (INTENT)
### 7.1 3 questions
- что подсветить?
- что скрыть?
- какое чувство дать?

### 7.2 Value separation
Главный объект должен отделяться по “value”:
- светлее или темнее фона
- не одинаковый тон с окружением

---

## 8) ART STYLE CONSISTENCY (BASICS)
Стиль держится на стабильных решениях:
- палитра (в общем)
- материалы/фактуры
- форма (углы/мягкость)
- детализация (сколько шума)

Если стиль “прыгает”, зритель перестаёт верить.

---

## 9) VISUAL CONTINUITY (ANTI-JUMP)
Проверяй:
- положение персонажей/объектов
- направление движения/взгляда
- источник света (логика)
- реквизит (не исчезает)

---

## 10) CHECKLISTS (KB)
### 10.1 Frame readability (pass/fail)
- [ ] главный объект читается силуэтом
- [ ] есть один главный акцент
- [ ] глубина присутствует (слои)
- [ ] свет имеет намерение
- [ ] фон не спорит с главным

### 10.2 Scene visual continuity
- [ ] позиции/направления стабильны
- [ ] стиль/палитра не прыгают
- [ ] реквизит консистентен

---

## 11) OUTPUT POINTERS
Этот realm обычно “производит”:
- визуальные гайды для сцен
- список кадров/планов
- style notes (минимальные)
- lighting intent notes

---

## 12) XREF (MANDATORY POINTERS)
XREF_DOC: 04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md | WHY:переход от визуальных решений к производству/пайплайну
XREF_DOC: 04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT.md | WHY:визуал обслуживает повороты/ставки/раскрытия сцены

---

## 13) NEXT EXTENSIONS (CONTROLLED)
Добавлять сюда можно:
- практики/чеклисты
- ссылки на KB entity passports (методы/чеклисты как объекты)

Если правило становится “универсальным модулем” → делаем паспорт `KB_PRACTICE`/`KB_CHECKLIST`.

--- END.
