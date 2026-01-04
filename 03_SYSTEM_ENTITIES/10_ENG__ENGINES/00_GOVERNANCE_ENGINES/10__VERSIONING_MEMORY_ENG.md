# Versioning & Memory Engine
FILE: 10__VERSIONING_MEMORY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines versioning strategy, release snapshots, and long-term memory of canonical states

---

## PURPOSE

Делает систему **воспроизводимой во времени**:
- вводит понятие версий/релизов канона
- фиксирует “снимки” состояния (milestones)
- хранит память решений и изменений (audit + decision linkage)
- позволяет откатиться или понять “как было на версии X”

---

## DEFINITIONS

- Canon Version — версия канона (структура + индексы + ключевые правила).
- Release Snapshot — фиксированный снимок состояния.
- Milestone — значимый этап (например, закончена структура ENG).
- Compatibility — совместимость форматов/правил между версиями.
- Changelog — список изменений между версиями.

---

## INPUTS

- audit events
- decision records
- index states
- standards/law changes
- change packages

---

## OUTPUTS

- Release Note (what changed + why)
- Snapshot Reference (commit/tag/ref)
- Compatibility Notes
- Migration Notes (если breaking)

---

## VERSIONING STRATEGY (CANONICAL)

Рекомендуемая модель:

- MAJOR: ломаем форматы/пути/иерархии (breaking)
- MINOR: добавляем новые сущности/семейства без ломки старого
- PATCH: правки без изменения контрактов

Пример: 1.2.3

---

## MECHANICS (HOW IT WORKS)

1) Любой релиз фиксируется:
   - версия
   - snapshot ref (commit/tag)
   - список ключевых индексов/законов, которые определяют релиз
2) Релиз обязан ссылаться на:
   - все DR, которые вошли
   - summary audit за период
3) Если релиз MAJOR:
   - обязателен migration guide
   - обязателен rollback plan
4) “Память” — это связность:
   - change → audit → decision → release

---

## RULES

- V1: Нельзя выпускать MAJOR без migration plan.
- V2: Релиз должен фиксировать “точки истины”:
  - какие индексы определяют состав сущностей
  - какие standards действуют
- V3: Любые изменения форматов должны иметь compatibility note.
- V4: Нельзя стирать историю: supersede, но не delete.

---

## FAILURE MODES

- F1: Версия есть, а что в ней — непонятно → невозможна воспроизводимость.
- F2: Breaking без миграции → пользователи системы “падают”.
- F3: Нет связи между audit/decision/release → память рвётся.

---

## INTEGRATION

- With AUDIT_LOG_ENG: audit — источник правды о фактах изменения.
- With DECISION_APPROVAL_ENG: решения — источник правды о причинах.
- With RISK_SAFETY_ENG: релизы high/critical требуют страховок.
- With CONSISTENCY_ENG: релиз невозможен при нарушении инвариантов.

---

## CHANGE POLICY

- Менять стратегию версионирования можно только через Decision Approval.
- Ввод новых типов релизов/милстоунов требует обновления стандартов.

---
OWNER: Universe Engine
STATUS: FIXED
