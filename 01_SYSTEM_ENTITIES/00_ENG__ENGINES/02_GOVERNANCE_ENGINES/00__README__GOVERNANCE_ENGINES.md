# GOVERNANCE ENGINES

CLASS_ID: GOVERNANCE_ENGINES
LEVEL: L1–L2
ROLE: System Governance

## PURPOSE
Governance Engines управляют решениями, изменениями и влиянием
на систему, не нарушая канон.

## SCOPE (ALLOWED)
- Управление изменениями
- Оценка рисков
- Контроль зависимостей
- Принятие и отклонение решений

## FORBIDDEN
- Изменение канона напрямую
- Генерация контента
- Нарративная логика

## ALLOWED CALLERS
- System
- Core Engines

## TYPICAL ENGINES
- Change Control Engine
- Decision Approval Engine
- Dependency Registry Engine
- Scope Impact Engine
- Risk Safety Engine

## COMMON MISTAKES
- Смешивание с валидаторами
- Использование для проверки фактов

## CREATION RULE
Создаётся только для управления системой,
а не для проверки или генерации.
