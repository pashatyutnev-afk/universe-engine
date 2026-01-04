# Risk & Safety Engine
FILE: 09__RISK_SAFETY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Identifies risks, defines safety constraints, and sets mitigation requirements for system changes

---

## PURPOSE

Описывает **риск-модель** и **страховочные правила**:
- какие риски бывают в документационной машине
- какие зоны считаются “опасными”
- какие меры обязательны для предотвращения распада канона

---

## DEFINITIONS

- Risk — вероятность * ущерб.
- Hazard Zone — зона повышенного риска (например, индексы/законы/переезды).
- Mitigation — мера снижения риска.
- Safety Constraint — ограничение, которое нельзя нарушать.
- Rollback — способ отката.

---

## INPUTS

- change package
- impact classification
- dependency blast radius
- audit context
- decision record (если есть)

---

## OUTPUTS

- Risk Profile (низкий/средний/высокий/критический)
- Required Mitigations
- Safety Constraints Checklist
- Rollback Plan requirement

---

## RISK TYPES (CANONICAL)

- R1: Navigation Collapse
  - битые индексы, несоответствие путей, сироты/фантомы
- R2: Authority Drift
  - конфликт правил, неясная власть, локальные правила ломают глобальные
- R3: Semantic Contract Break
  - движок поменял смысл, а downstream продолжает старое понимание
- R4: Reference Break
  - битые raw/github ссылки, отсутствие XREF
- R5: Duplicate Canon
  - два “источника истины” на одно
- R6: Untraceable Changes
  - нет audit/decision → нельзя восстановить историю

---

## SAFETY CONSTRAINTS (MUST HOLD)

- S1: Не допускаются фантомы/сироты.
- S2: Нельзя менять protected zones без approval.
- S3: Любой переезд обязан иметь mapping + проверку ссылок.
- S4: Формат индексов/правил нельзя ломать без migration plan.
- S5: История (audit/decision) не переписывается.

---

## MECHANICS (HOW IT WORKS)

1) По impact и типам изменений определяем risk profile.
2) Если есть move/rename/index/law changes → risk минимум HIGH.
3) Назначаем mitigation:
   - backup before
   - mapping file (xref)
   - consistency validation
   - staged rollout (если много файлов)
4) Требуем rollback plan для high/critical.

---

## MITIGATIONS (DEFAULT SET)

- M1: XREF mapping “from → to”
- M2: Consistency pass (invariants)
- M3: Link validation (raw paths)
- M4: Audit event completeness check
- M5: Decision record (если требуется)
- M6: Rollback plan:
  - что откатываем
  - как вернуть индексы/ссылки

---

## FAILURE MODES

- F1: Переезд без страховки → массовые поломки.
- F2: Правка правил без approval → authority drift.
- F3: Смена смысла без фикса downstream → неверная “машина”.

---

## INTEGRATION

- With SCOPE_IMPACT_ENG: impact → риск.
- With CHANGE_CONTROL_ENG: риск → блокировки и gates.
- With CONSISTENCY_ENG: safety constraints проверяются как инварианты.
- With VERSIONING_MEMORY_ENG: rollback и релизы.

---
OWNER: Universe Engine
STATUS: FIXED
