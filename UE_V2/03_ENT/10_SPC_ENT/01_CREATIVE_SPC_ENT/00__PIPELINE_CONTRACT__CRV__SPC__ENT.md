# SPC FAMILY REALM — CREATIVE SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/00__README_CREATIVE_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.CREATIVE.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `01_CREATIVE`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established CREATIVE SPC family realm: purpose, boundaries, interfaces, quality rules, and creation gates."
- REASON: "Need deterministic creative layer with clear role separation and non-overlapping responsibilities."
- IMPACT: "Creative work becomes repeatable, auditable, and compatible with canon/standards."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.CREATIVE.001

---

## 0) PURPOSE (LAW)
Семейство `01_CREATIVE` отвечает за **творческое проектирование ощущений и образов**:
- визуальный язык и стиль
- эстетика мира и художественное направление
- концепты и дизайн-идеи
- символизм и метафоры
- настроение/атмосфера
- управляемый художественный риск
- генерацию идей (как источник вариантов)

Это семейство создаёт **варианты и художественные решения**, но обязано сохранять:
- совместимость с каноном (governance)
- воспроизводимость (можно повторить решение)
- ясные границы (кто за что отвечает)

---

## 1) EXISTENCE + NAV RULE (MANDATORY)
- Специалист существует для системы **только если** он:
  1) зарегистрирован в глобальном SPC INDEX:
     `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`
  2) и файл лежит по каноническому пути
- Любые файлы в папке без регистрации — **NON-CANON / ignored**
- Каноническая навигация по семье — через RAW ссылки глобального SPC INDEX

---

## 2) FAMILY SCOPE
**FAMILY NAME:** CREATIVE SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/`  
**WHO THIS FAMILY IS FOR:** художественные решения, стиль, настроение, концепты, символические слои.

### 2.1 Covered domains (what we DO)
- Style direction (визуальный/тональный язык)
- World aesthetic (эстетика мира)
- Concept design (объекты/сцены/силуэты/мотивы)
- Symbolism / metaphor layer (смыслы через образы)
- Mood / atmosphere layer (ощущение и тон)
- Artistic risk (насколько “смело” и зачем)
- Idea generation (варианты, мутации, неожиданные ходы)

### 2.2 Hard boundaries (what we DO NOT do)
- Не утверждаем канон и структуру системы (это TOP Governance).
- Не заменяем сюжетную архитектуру (это Narrative Specialists / Narrative Engines).
- Не делаем психологическую достоверность персонажей (это Character/Psychology).
- Не считаем факты и реальность (это Research/Validation).
- Не производим медиа-артефакты (монтаж/камера/рендер) — это Production/Visual ENG+SPC.

---

## 3) DEFAULT OUTPUT PHILOSOPHY
**Default mindset:** GENERATE → SELECT → COMMIT (с фиксацией причин)  
**Primary quality priority:** clarity → coherence → emotional effect → novelty (в пределах рамок)  
**Default outputs:**
- style notes / art direction rules
- concept briefs / mood boards (текстом)
- motif sets / symbol maps
- tone & atmosphere specs
- variant sets + selection rationale

---

## 4) INTERFACES (SYSTEM LINKS)
### 4.1 ENG (Engines) — typical support
- `06_GENRE_STYLE_ENGINES/*` (tone/mood/atmosphere/symbolism)
- `08_KNOWLEDGE_PRODUCTION_ENGINES/*` (art style / visual composition)
- Частично: `05_EXPRESSION_ENGINES/*` (если нужна выразительная форма события)

### 4.2 ORC (Orchestrators) — typical usage
ORC вызывает CREATIVE SPC когда нужно:
- выбрать художественный язык для проекта/арки/сезона
- создать набор вариантов и выбрать финальный стиль
- усилить смысл через символический слой
- стабилизировать настроение и тон

### 4.3 VAL / QA (Gates)
CREATIVE-выдача обычно требует:
- Consistency gate (не конфликтует с уже принятым стилем/каноном)
- Naturalness (если текст/диалоги затронуты)
- Doc-control (если оформляется как канон-документ)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- Creative Director задаёт “куда и почему”.
- Visual Style Architect задаёт “правила языка”.
- World Aesthetic Designer задаёт “эстетику мира”.
- Concept Designer создаёт “концепты объектов/сцен”.
- Symbolism/Metaphor Designer задаёт “слой смысла”.
- Mood/Atmosphere Curator задаёт “ощущение/тон”.
- Artistic Risk Designer управляет “смелостью”.
- Idea Generator производит “много вариантов”.

### 5.2 Output discipline
- Каждый спец обязан фиксировать:
  - контекст
  - ограничения
  - варианты (если применимо)
  - выбор и WHY (почему выбран этот вариант)

### 5.3 No hidden canon
- Творческая идея не становится каноном сама по себе.
- Если решение должно стать “нормой” — оно проходит governance путь и doc-control.

---

## 6) WHEN TO CREATE A NEW CREATIVE SPECIALIST (GATE)
Новый CREATIVE SPC создаётся только если:
- появился устойчивый тип творческих задач, который не закрывается текущими ролями без размывания границ
- требуется новый режим мышления (например “цветовой сценарист” или “монтаж настроения”), который регулярно нужен
- роль становится “постоянной дырой” в пайплайнах

Создание “на всякий случай” запрещено.

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — CREATIVE DIRECTOR  
02 — VISUAL STYLE ARCHITECT  
03 — WORLD AESTHETIC DESIGNER  
04 — CONCEPT DESIGNER  
05 — SYMBOLISM METAPHOR DESIGNER  
06 — MOOD ATMOSPHERE CURATOR  
07 — ARTISTIC RISK DESIGNER  
08 — IDEA GENERATOR  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `01_CREATIVE`.  
Творчество обязано быть совместимым с каноном и воспроизводимым через контракты и выходные пакеты.

--- END.
