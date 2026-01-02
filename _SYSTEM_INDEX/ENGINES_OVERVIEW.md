# Engines Overview
## Обзор Движков

This document defines what an "Engine" is inside Universe Engine,
what types of engines exist, and how they are organized.

Этот документ определяет, что такое «Движок» внутри Universe Engine,
какие бывают классы движков и как они организованы.

---

## 1) Definition / Определение

### Engine (EN)
An Engine is a reusable algorithmic module that produces consistent results
based on rules, inputs and constraints.

### Движок (RU)
Движок — это переиспользуемый алгоритмический модуль,
который выдаёт стабильный результат на основе правил, входных данных и ограничений.

**Key idea / Суть**
- Projects provide DATA (canon, facts, assets)
- Engines provide LOGIC (how to generate / validate / transform)
- Outputs become canon only after approval

Проекты дают ДАННЫЕ (канон, факты, материалы)  
Движки дают ЛОГИКУ (как генерировать / проверять / преобразовывать)  
Результаты становятся каноном только после утверждения

---

## 2) Engine Hierarchy / Иерархия Движков

Universe Engine uses 3 levels:

### L1 — System Engines / Системные движки
Highest-level engines that define global rules and quality gates.

Высший уровень: глобальные правила и контроль качества.

### L2 — Domain Engines / Доменные движки
Engines for specific domains: narrative, worlds, characters, style, production.

Движки по областям: сюжет, миры, персонажи, стиль, производство.

### L3 — Task Engines / Задачные движки
Small specialized engines for a concrete task (scene beats, dialogue polish, etc.).

Малые движки под конкретные задачи (сцены, диалоги, ритм и т.д.).

---

## 3) Core Engine Classes / Основные классы движков

Below are the main engine classes. Each class later becomes a folder tree.

Ниже основные классы движков. Каждый класс позже станет веткой папок.

### A) Governance Engines / Движки управления
- Canon Authority Engine / Авторитет Канона
- Decision & Approval Engine / Утверждение решений
- Consistency Engine / Целостность системы
- Change Control Engine / Контроль изменений

### B) Narrative Engines / Движки повествования
- Plot Architecture Engine / Архитектура сюжета
- Arc Engine / Арки истории
- Conflict Engine / Конфликты
- Pacing Engine / Темп и ритм
- Scene Engine / Сценирование

### C) Character Engines / Движки персонажей
- Character Generator / Генератор персонажей
- Psychology Engine / Психология
- Behavior Engine / Поведение
- Relationship Engine / Отношения
- Dialogue Engine / Диалоги
- Growth Engine / Развитие персонажа

### D) World Engines / Движки миров
- World Builder / Построение мира
- Geography Engine / География
- Society Engine / Социум
- Economy Engine / Экономика (если применяется)
- Timeline Engine / Хронология
- Rules & Physics Engine / Правила и физика мира

### E) Expression Engines / Движки выразительности
- Natural Language Engine / Естественная речь
- Voice & Tone Engine / Голос и тон
- Humor Engine / Юмор
- Symbolism Engine / Символизм
- Atmosphere Engine / Атмосфера

### F) Genre & Format Engines / Движки жанров и форматов
- Genre Switch Engine / Переключение жанров
- Format Engine (Book) / Формат книги
- Format Engine (Series) / Формат сериала
- Format Engine (Shorts) / Формат шортсов
- Format Engine (Game) / Формат игры

### G) Production AI Engines / Движки производства ИИ
- Text Production Pipeline / Пайплайн текста
- Image Production Pipeline / Пайплайн изображений
- Video Production Pipeline / Пайплайн видео
- Audio Production Pipeline / Пайплайн звука
- QC Engine / Контроль качества

### H) Knowledge Engines / Движки знаний
- Research Engine / Исследование
- Source Mapping Engine / Карта источников
- Fact Checking Engine / Проверка фактов
- Synthesis Engine / Синтез знаний

---

## 4) Canonization Rule / Правило канонизации

**Nothing becomes canon automatically.**

Ничто не становится каноном автоматически.

### States / Состояния
- Draft / Черновик
- Candidate / Кандидат
- Approved Canon / Утверждённый Канон
- Deprecated / Устарело (но хранится)

All outputs must declare their state.

Все результаты обязаны иметь статус.

---

## 5) Project Integration / Подключение проектов

Projects never modify engines.
Projects only use engines.

Проекты не меняют движки.
Проекты только используют движки.

### Project provides:
- Canon data
- World facts
- Character sheets
- Constraints and goals

Проект даёт:
- Канон
- Факты мира
- Карточки персонажей
- Ограничения и цели

### Engines provide:
- Generation
- Validation
- Formatting
- Consistency

Движки дают:
- Генерацию
- Проверку
- Форматирование
- Согласованность

---

## 6) Naming Rule / Правило именования

Folders: ENGLISH_ONLY (technical)
Titles inside files: EN + RU

Папки: только АНГЛИЙСКИЙ (технически)
Заголовки в файлах: EN + RU

Example:
- Folder: CHARACTER_ENGINES
- File title:
  # Character Engines
  ## Движки персонажей
