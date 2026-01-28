# TEMPLATE — SPC PRO PACK (SUPER-PROFESSIONAL STANDARD)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/22__TEMPLATE__SPC_PRO_PACK.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
INDEX_TYPE: SPC_PRO_PACK_TEMPLATE
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO.001
OWNER: SYSTEM
ROLE: Copy standard for Specialist (SPC) Pro Pack: required file set, proficiency requirements, gates, and evidence rules to ensure each specialist is "super pro" and KB-driven

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created SPC Pro Pack template: mandatory file set + proficiency matrix hooks + evidence requirements (KB_SOURCES/KB_GATES)."
- REASON: "Specialists must know their craft inside-out; KB is the quality driver."
- IMPACT: "SPC KB becomes measurable, auditable, and scalable across all specialists."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.SPC.001

---

## 0) PURPOSE (WHAT SPC PRO PACK IS)
SPC PRO PACK — это KB-пакет профессиональных знаний специалиста:
- что он должен уметь (skill tree),
- лучшие принципы профессии (golden principles),
- процедуры/алгоритмы (playbooks),
- контроль качества (checklists + evaluation rubric),
- паттерны/анти-паттерны и кейсы,
- доказательства: на какие KB-модули он опирается (KB_SOURCES) и какие гейты применяет (KB_GATES).

SPC PRO PACK не заменяет сущность SPC в `03_SYSTEM_ENTITIES`.
Это KB-слой: “что SPC знает и как применяет”.

---

## 1) REQUIRED FOLDER + FILE SET (MANDATORY)
Каждый SPC обязан иметь папку:

`04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__<SPC_NAME>/`

И внутри ОБЯЗАТЕЛЬНО следующие файлы:

1) `00__KB_PASSPORT.md`
2) `01__SKILL_TREE.md`
3) `02__GOLDEN_PRINCIPLES.md`
4) `03__PLAYBOOKS.md`
5) `04__CHECKLISTS.md`
6) `05__PATTERNS_ANTI_PATTERNS.md`
7) `06__CASE_LIBRARY.md`
8) `07__EVALUATION_RUBRIC.md`
9) `90__KB_SOURCES.md`
10) `91__KB_GATES.md`

Запрещено удалять/переименовывать эти файлы без change control.

---

## 2) CONTENT REQUIREMENTS (WHAT MUST BE INSIDE)
### 2.1 00__KB_PASSPORT.md (mandatory fields)
- Purpose (миссия SPC)
- When to use / When not to use
- Scope / Boundaries (что входит / что не входит)
- Inputs / Outputs (контракт)
- Typical tasks (3–10)
- Stop conditions (когда стоп)
- Links to key KB modules (PATH)

### 2.2 01__SKILL_TREE.md (inside-out mastery)
Skill tree должен быть уровневым:
- CORE (must-have)
- ADVANCED
- ELITE

Минимум:
- CORE: ≥ 10 навыков
- ADVANCED: ≥ 5 навыков
- ELITE: ≥ 3 навыка

Каждый навык должен иметь:
- short description
- associated procedures (PATH to topics/libraries)
- evaluation method (rubric/checklist path)

### 2.3 02__GOLDEN_PRINCIPLES.md (best of profession)
Минимум:
- 20 принципов (коротко, чётко, без воды)
Каждый принцип:
- формулировка
- “why it matters”
- “how to apply”
- (если нужно) ссылка PATH на источник/пример

### 2.4 03__PLAYBOOKS.md (procedures)
Минимум:
- 5 playbooks (для CORE задач)

Каждый playbook содержит:
- trigger (когда запускать)
- inputs (что нужно)
- steps (1..N)
- outputs (что получить)
- gates (какие проверки применить)
- failover (что делать если не получилось)

### 2.5 04__CHECKLISTS.md (decision & quality control)
Минимум:
- 3 чеклиста:
  - decision checklist
  - quality checklist
  - regression checklist (если применимо)

Чеклист должен иметь PASS/FAIL criteria.

### 2.6 05__PATTERNS_ANTI_PATTERNS.md
Минимум:
- 5 patterns
- 5 anti-patterns
Каждый:
- симптомы
- последствия
- исправление
- профилактика
- ссылка на примеры/рубрики (PATH)

### 2.7 06__CASE_LIBRARY.md
Минимум:
- 10 кейсов (можно смешивать PASS/FAIL/EDGE)

Каждый кейс содержит:
- context / input
- decision / действия
- output
- why pass/fail
- ссылки на используемые модули (PATH)

### 2.8 07__EVALUATION_RUBRIC.md
Рубрика оценки работы SPC:
- PASS criteria
- REWORK criteria
- FAIL criteria
- шкала (optional)
- типовые причины FAIL и что делать

---

## 3) EVIDENCE BLOCKS (MANDATORY)
### 3.1 90__KB_SOURCES.md (sources)
Обязательный формат:

KB_SOURCES:
- REQUIRED:
  - PATH: ...
  - PATH: ...
- OPTIONAL:
  - PATH: ...

Правило:
- REQUIRED источники должны покрывать CORE skill tree и playbooks.
- Нельзя ссылаться на файлы вне master-index.

### 3.2 91__KB_GATES.md (checks)
Обязательный формат:

KB_GATES:
- Gate:
  - NAME: ...
  - PATH: ...
  - APPLIES_TO: <skill/playbook/case>
  - RESULT: <PASS/FAIL/REWORK>  # при аудите/проверке

---

## 4) PROFICIENCY GATES (SUPER-PRO MODE)
SPC считается “super pro”, если выполнены условия:

### Gate A — Coverage
- заполнены все 10 обязательных файлов
- SKILL_TREE имеет CORE/ADVANCED/ELITE уровни

### Gate B — Actionability
- минимум 5 playbooks
- минимум 3 чеклиста
- рубрика оценки присутствует и применима

### Gate C — Proof
- минимум 10 кейсов
- есть ссылки на KB modules (PATH) и привязка к gates

### Gate D — No Fantasy
- все утверждения либо source-locked, либо Memory-OK (VERIFIED) без искажений

---

## 5) STATE / MATURITY (RECOMMENDED)
Рекомендуемые состояния:
- сначала: UNREAD / maturity_seed
- затем: READ_ONCE / maturity_working
- после применения и отсутствия конфликтов: VERIFIED / maturity_verified

Изменение VERIFIED требует revalidation (см. KB module state system).

---

## 6) QUICK START (HOW TO CREATE NEW SPC PRO PACK)
1) Создай папку `SPC__<SPC_NAME>/`
2) Создай 10 обязательных файлов
3) Заполни в порядке:
   - 00 паспорт
   - 01 skill tree
   - 03 playbooks
   - 91 gates
   - 90 sources
   - 07 rubric
   - 04 checklists
   - 06 case library
   - 05 patterns
   - 02 golden principles
4) Зарегистрируй новые файлы в KB master-index (CANON MAP)

--- END.
