# Core State Engine
FILE: 02__CORE_STATE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines canonical states and allowed transitions for any entity

---

## PURPOSE

Вводит **единый State Machine** для сущностей:
- какие статусы существуют
- что означает каждый статус
- какие переходы разрешены
- какие gates/проверки нужны для переходов

---

## CANONICAL STATES

- DRAFT  
  Сущность создаётся/черновик. Может быть неполной. Не является “боевой истиной”.

- ACTIVE  
  Сущность утверждена и действует. На неё можно ссылаться как на истину.

- DEPRECATED  
  Сущность устаревает. Использование допускается, но рекомендуется миграция.

- ARCHIVED  
  Сущность выведена из активного использования, но хранится как история.

- BROKEN  
  Сущность обнаружена как неконсистентная/ошибочная (битые ссылки, конфликт правил, неверный контракт). Требует ремонта.

Опционально (если захочешь расширить позже, но не обязательно сейчас):
- EXPERIMENTAL (для лаборатории)
- PROPOSED (для решений/планов)

---

## STATE MEANINGS (STRICT)

- ACTIVE = можно ссылаться в индексах/правилах/проектах.
- DRAFT = можно хранить, но ссылки в канон запрещены (кроме intake/workshop зон).
- DEPRECATED = можно ссылаться только с пометкой миграции.
- ARCHIVED = ссылки только исторические.
- BROKEN = ссылки запрещены, пока не исправлено.

---

## ALLOWED TRANSITIONS

- DRAFT → ACTIVE (через validation gates)
- ACTIVE → DEPRECATED (если появился replacement или сменился контракт)
- DEPRECATED → ARCHIVED (когда миграция завершена)
- ACTIVE → ARCHIVED (если удалено из использования без фазы deprecated — редко, только по решению)
- ANY → BROKEN (если выявлена критическая ошибка)
- BROKEN → DRAFT (в ремонт)
- BROKEN → ACTIVE (после ремонта и валидации)

Запрещено:
- ARCHIVED → ACTIVE (только через новый объект или через supersede decision)
- DRAFT → ARCHIVED (без причины/истории)

---

## GATES (REQUIRED CHECKS)

### Gate A: Identity Valid
- ID, PATH, OWNER, FAMILY, VERSION корректны.

### Gate B: Index Consistency
- если сущность индексируемая — присутствует в нужном INDEX.

### Gate C: Reference Integrity
- нет битых ссылок на неё и от неё (если проверяется сейчас).

### Gate D: Contract Completeness
- документ соответствует минимальному формату (STANDARDS).

---

## MECHANICS (HOW IT WORKS)

1) Сущность создаётся в DRAFT.
2) При подготовке к публикации запускаются gates.
3) Если gates пройдены → ACTIVE.
4) При появлении новой версии или замены:
   - старая становится DEPRECATED
   - указывается replacement (через xref / index note)
5) После миграции старая уходит в ARCHIVED.

---

## FAILURE MODES

- F1: DRAFT сущности используются как истина → хаос.
- F2: Нет deprecated фазы → ломается обратная совместимость.
- F3: BROKEN не выделяется → ошибки размазываются по системе.
- F4: ARCHIVED реактивируют без контроля → история переписывается.

---

## INTEGRATION

- With CHANGE_CONTROL_ENG: блокирует переходы при нарушениях.
- With CONSISTENCY_ENG: обнаружение BROKEN.
- With DECISION_APPROVAL_ENG: required для критических переходов (например ACTIVE→ARCHIVED массово).
- With VERSIONING_MEMORY_ENG: релизы фиксируют состояния ключевых сущностей.
- With QA_QUALITY: качество = gate перед ACTIVE.

---
OWNER: Universe Engine
STATUS: FIXED
