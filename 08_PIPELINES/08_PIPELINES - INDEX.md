# 08_PIPELINES
## System Pipelines Layer

---

## Назначение

Папка 08_PIPELINES содержит описания всех рабочих процессов
(Pipelines), определяющих порядок действий системы Universe Engine.

Pipelines описывают **как именно** система работает,
а не **что** она создаёт.

---

## Роль в архитектуре

Pipelines:
- соединяют Engines и Specialists
- управляют последовательностью действий
- обеспечивают повторяемость результата
- предотвращают хаос и импровизацию

---

## Канонический поток

ENGINES → SPECIALISTS → PIPELINES → PROJECTS → ENTITIES

---

## Что хранится здесь

- Core Pipelines (базовые процессы)
- Content Pipelines (книги, сериалы, видео, игры)
- AI Production Pipelines
- Quality Control Pipelines
- Governance Pipelines

---

## Что НЕ хранится здесь

- идеи
- сущности
- канон
- персонажи
- описания мира

---

## Статус

- Тип: Process Layer
- Уровень: System Control
- Изменяемость: Контролируемая
