# Rule Hierarchy Engine
FILE: 03__RULE_HIERARCHY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines precedence of laws and documents for ENG; resolves conflicts by determining which rule wins, and enforces canonical override/waiver mechanisms

---

## PURPOSE

Этот движок нужен, чтобы система не спорила сама с собой.

Он фиксирует:
- **иерархию источников** (что сильнее, что слабее)
- **правила конфликта** (как решать противоречия)
- **механизм override/waiver** (как допускаются исключения)
- **правило “локальный vs глобальный”** (что имеет приоритет)

---

## SCOPE (WHAT IT APPLIES TO)

Иерархия распространяется на:
- INDEX (реестр)
- governance движки
- README realm files семейств
- engine files
- любые “производные” артефакты (specs, packs, checklists)
- черновики/чаты (как не-канон)

---

## NON-GOALS

- не утверждает решения (это Canon Authority)
- не проверяет соответствие (это Consistency Engine)
- не управляет изменениями (это Change Control)
- не описывает зависимости (это Dependency Registry)

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- conflicting rules or claims across docs
- family realm files + engine files
- index and governance rules
- waiver proposals (if exception needed)

### PRODUCES
- conflict resolution outcome (winner rule)
- required actions: align / override / waiver / deprecate
- precedence mapping (for auditors and authors)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

### OUTPUT_TARGET
- Used whenever contradictions appear during writing, audits, or integration
- Referenced by Consistency findings and Canon Authority verdicts

---

## HIERARCHY OF TRUTH (CANON PRECEDENCE)

### P0 — Existence & navigation law (highest)
1) `00__INDEX_ALL_ENGINES.md`
- решает: существует ли движок, где он живёт, какой его номер и порядок

### P1 — Governance law
2) `00_GOVERNANCE_ENGINES/*`
- решает: как менять, как проверять, как фиксировать, что считать каноном

### P2 — Family realm law
3) `00__README__<FAMILY>_ENGINES.md`
- решает: термины семьи, границы ответственности, базовые outputs семьи

### P3 — Engine local law
4) `<NN>__<ENGINE>_ENG.md`
- решает: локальная процедура и контракт в рамках границ семьи

### P4 — Derived artifacts (lowest canon)
5) generated specs/checklists/prompt packs/etc
- они обязаны соответствовать P0–P3

### P5 — Non-canon sources (not truth)
6) чаты/черновики/заметки
- не считаются истиной, пока не оформлены как файлы и не зарегистрированы/утверждены

---

## CONFLICT TYPES (STANDARD)

### C1 — Registry conflict (INDEX vs file)
- INDEX всегда побеждает (P0)
- если файл не совпадает с INDEX → файл должен быть приведён к индексу

### C2 — Governance conflict (governance vs anything)
- governance побеждает (P1)
- исключения только через waiver + canon verdict

### C3 — Family realm conflict (README vs engine)
- README побеждает (P2)
- движок обязан подстроиться
- если README устарел — меняем README через Change Control

### C4 — Engine vs engine inside same family
- решается через:
  - boundaries + handoff (Dependency Registry)
  - overlap owner assignment (Canon Authority)

### C5 — Terminology collision
- побеждает определение, зафиксированное в family README
- если термин глобальный — фиксируется в governance/glossary (если появится)
- альтернативы помечаются deprecated

### C6 — Level/Class mismatch (INDEX vs README/engines)
- INDEX заявляет класс/уровень семейства
- README и движки обязаны совпасть
- mismatch = S0 blocker (до фикса)

---

## LOCAL VS GLOBAL RULE (OVERRIDE POLICY)

### Default
Глобальное правило побеждает локальное:
- INDEX (P0) побеждает всё
- Governance (P1) побеждает всё, кроме INDEX

### Allowed local specialization
Локальный движок может уточнять:
- процедуру
- формат outputs
- частные правила

Но НЕ может:
- менять границы семьи (это README)
- менять нумерацию/имена (это INDEX)
- менять governance процесс (это governance)

---

## OVERRIDE / WAIVER MECHANISM (THE ONLY LEGAL EXCEPTION)

Если нужно исключение из более сильного правила:
- оформляется waiver (Canon Authority)
- фиксируется в Audit Log
- имеет scope + expiry + mitigation
- никогда не применяется к S0 blockers (registry, naming, level mismatch)

---

## DEPRECATION RULE (HOW TO RETIRE OLD RULES)

Если правило заменяется новым:
- старое помечается `DEPRECATED`
- указывается `REPLACED_BY: <file/section>`
- указывается дата и причина
- deprecation проходит через Change Control и фиксируется в Audit

---

## PROCEDURE (HOW TO RESOLVE ANY CONFLICT)

1) Identify conflict
- какие документы спорят
- какой тип конфликта (C1–C6)

2) Determine precedence level (P0–P5)
- кто выше — тот и “истина”

3) Decide action
- align: привести низший документ к высшему
- override: только через waiver + verdict
- deprecate: если правило устарело

4) Register decision
- если влияет на канон → через Change Control
- зафиксировать в audit (AUDIT_ID)

---

## VALIDATION CHECKLIST

- RH1: Любой конфликт имеет тип (C1–C6)
- RH2: Решение всегда ссылается на уровень (P0–P5)
- RH3: Исключения только через waiver/verdict
- RH4: Deprecation всегда содержит replaced_by

---

## INTEGRATION NOTES

- Consistency Engine использует эту иерархию как “таблицу истинности”
- Canon Authority использует её при вынесении verdict
- Change Control требует align действий перед LOCK: FIXED

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
