# Dialogue Engine
## Движок Диалогов Персонажа

---

## 1) Identity / Идентификация

- Engine ID: DE-C7-007
- Class: Character Engine
- Level: C7 (Dialogue Core)
- Status: Active
- Owner: Universe Engine

---

## 2) Purpose / Назначение

### EN
Defines how characters express thoughts through dialogue.
Controls dialogue structure, intent, and interaction logic without generating specific lines.

### RU
Определяет, как персонажи выражают мысли через диалог.
Управляет структурой диалога, намерениями и логикой взаимодействия без генерации конкретных реплик.

---

## 3) Responsibilities / Ответственность

Responsible for:
- Dialogue intent models
- Turn-taking logic
- Speech act classification
- Dialogue flow constraints
- Consistency between dialogue and character state

Отвечает за:
- Модели диалоговых намерений
- Логику очередности реплик
- Классификацию речевых актов
- Ограничения потока диалога
- Согласованность речи с состоянием персонажа

---

## 4) Domains / Entities

- Dialogue Act
- Intent
- Turn
- Response Window
- Interaction Context
- Dialogue State
- Speech Constraint

---

## 5) Inputs / Входные данные

Receives:
- Character psychology state
- Motivation and desire signals
- Relationship dynamics
- Behavioral readiness
- Canon rules

---

## 6) Outputs / Выходные данные

Produces:
- Dialogue intent maps
- Turn-taking rules
- Allowed speech act sets
- Dialogue state transitions
- Consistency validation signals

---

## 7) Operating Logic / Логика работы

1. Read current character state
2. Determine dialogue intent
3. Select allowable speech acts
4. Apply turn-taking constraints
5. Validate dialogue consistency
6. Lock dialogue state

---

## 8) Constraints / Ограничения

This engine must NOT:
- Generate actual dialogue text
- Override character psychology
- Force narrative outcomes
- Ignore relationship context
- Break canon constraints

---

## 9) Integration / Интеграция

Used by:
- Speech Naturalization Engine
- Narrative Engines
- Event Engines
- Relationship Engine

Uses:
- Character Psychology Engine
- Motivation & Desire Engine
- Canon Authority Engine
- Consistency Engine

---

## 10) Canon Status / Канонический статус

- Character Core Engine
- Dialogue logic is canon-bound
- Required for character interaction

---

## 11) Versioning / Версии

- v1.0 — Base dialogue framework

---

## 12) Notes / Заметки

Dialogue is not words.
Dialogue is intent
taking audible form.
