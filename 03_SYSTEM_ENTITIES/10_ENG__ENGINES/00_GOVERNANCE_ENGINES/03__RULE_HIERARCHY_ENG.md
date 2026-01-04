# Rule Hierarchy Engine
FILE: 03__RULE_HIERARCHY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines strict hierarchy of rules, precedence order, and conflict resolution across the system

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- Conflicting statements (rules, contracts, readmes, indexes)
- Change proposals touching rules/structure
- Registry/index references for affected scope
- Audit entries / decision IDs (if exist)

PRODUCES:
- Canon precedence verdict (which rule wins)
- Required rewrite targets (what must be fixed)
- Conflict classification (type + severity)
- Enforcement checklist for maintainers
- Anti-duplication boundary map (when needed)

DEPENDS_ON:
- 02__CANON_AUTHORITY_ENG
- 04__CHANGE_CONTROL_ENG
- 01__AUDIT_LOG_ENG

OUTPUT_TARGET:
- Rule enforcement across all ENG files and registries
- Governance resolutions used by indexes/owners

---

## 0) PURPOSE (LAW)
Rule Hierarchy Engine гарантирует, что система всегда может ответить:

1) **Какая формулировка является истиной**, если тексты конфликтуют?
2) **Что сильнее**: INDEX, RULES, README, Engine contract, notes?
3) **Что делать**, когда найдено противоречие?

### ABSOLUTE RULE
> При конфликте выигрывает правило **более высокого уровня**.  
> Проигравший текст обязан быть исправлен или помечен как non-canon.

---

## 1) RULE LAYERS (SYSTEM MAP)
Система состоит из слоёв правил (от более сильных к более слабым):

- **L0 — CORE LAW**: базовые законы репозитория (если существуют)
- **L1 — LAYER LAW (ENG)**: правила слоя ENG (realm + ruleset + index)
- **L2 — FAMILY LAW**: правила семейства (README family + family rules)
- **L3 — ENGINE LAW**: правила конкретного движка (mini-contract + boundaries)
- **L4 — ARTIFACTS**: любые результаты, заметки, черновики (non-law)

---

## 2) PRECEDENCE ORDER (STRICT)
Если есть конфликт, применяй порядок ниже (1 = сильнее):

1) **GLOBAL INDEX / REGISTRIES** (состав/порядок/существование)
2) **LAYER RULESET** (например `01__RULES__ENGINES.md`)
3) **CANON AUTHORITY DECISION** (если есть явное решение с audit)
4) **FAMILY README / REALM** (границы, термины, правила семейства)
5) **ENGINE MINI-CONTRACT** (consumes/produces/depends/output_target)
6) **ENGINE BODY TEXT** (описания, процессы, примеры)
7) **NOTES / DRAFTS / IDEAS** (всё остальное)

### NOTE
Решение Canon Authority (п.3) работает как “временный/финальный арбитр”, но не отменяет обязанность привести документы в порядок по иерархии.

---

## 3) EXISTENCE & REGISTRY LAW (NON-NEGOTIABLE)
### 3.1 Existence rule
> Если объект не зарегистрирован в INDEX/REGISTRY — он не существует в каноне.

### 3.2 Canon path rule
Любая ссылка/путь обязаны быть каноническими и повторяемыми.

### 3.3 Ordering rule
Порядок в INDEX — обязательный, не “рекомендация”.

---

## 4) CONFLICT TYPES (CLASSIFIER)
### T1 — Text Conflict
Два текста утверждают разные факты/правила.

### T2 — Scope Conflict
Два документа пытаются владеть одной областью (дублирование).

### T3 — Contract Conflict
CONSUMES/PRODUCES/DEPENDS_ON противоречат другим контрактам/реестрам.

### T4 — Registry Conflict
INDEX говорит одно, а файлы/папки — другое.

### T5 — Authority Conflict
Два владельца/решения конфликтуют по правам.

---

## 5) RESOLUTION PROTOCOL (MANDATORY)
Когда найден конфликт:

1) **Определи scope**: Layer / Family / Engine
2) **Определи тип конфликта** (T1–T5)
3) **Применяй precedence order** (раздел 2)
4) **Зафиксируй вывод**:
   - что победило
   - что проиграло
   - какие файлы переписать
5) **Запусти governance pipeline**, если затронут канон:
   - Change Control → Canon Authority → Audit Log → Versioning (если надо)
6) **Обнови реестры**, если изменился состав/порядок/зависимости

### FAST RULE
> Нельзя “оставить как есть”. Любой конфликт должен завершиться либо переписыванием, либо явным решением/пометкой non-canon.

---

## 6) ANTI-DUPLICATION LAW (BOUNDARY ENFORCEMENT)
Дублирование запрещено на уровне “владения смыслом”.

### Boundary rule
Если два файла описывают одно и то же:
- один становится владельцем области
- второй должен:
  - либо стать ссылкой/указателем (xref),
  - либо сузить scope,
  - либо быть удалён/перенесён в non-canon (по решению)

---

## 7) “WHERE RULES LIVE” (CANON PLACEMENT)
Чтобы не было хаоса:

- **Состав/порядок** — только в INDEX/registries
- **Правила слоя** — в layer ruleset
- **Границы семейства** — в README family
- **Контракты движков** — только в engine файлах (mini-contract)
- **Примеры/пайплайны** — в engine body / artifacts (но не выше правил)

---

## 8) ENFORCEMENT CHECKLIST (QUICK)
Перед тем как считать область “чистой”:

- [ ] Есть INDEX запись (существование подтверждено)
- [ ] Есть правила слоя/семейства (realm/readme)
- [ ] У движка есть mini-contract
- [ ] Нет конфликтов с соседними движками (boundaries)
- [ ] Зависимости отражены в DEPENDS_ON и dependency registry
- [ ] Изменения прошли governance pipeline (если канон тронут)

---

## 9) FINAL LAW (LOCK)
> Rule Hierarchy — механизм, который не даёт канону расползтись.  
> Любое противоречие обязано быть разрешено по этой иерархии.

OWNER: Universe Engine  
LOCK: FIXED
