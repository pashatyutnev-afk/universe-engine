# TOPIC — LORE CONSISTENCY RULES (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/02__WORLD__LORE_CONSISTENCY_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.LORE_CONSISTENCY.001
OWNER: SYSTEM
ROLE: Provide an atomic, actionable method to keep lore consistent by mapping claims to world laws, detecting contradiction types, and applying a resolution protocol with drift guards; includes pass/fail examples and a checklist

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for lore consistency: claim-to-law mapping, contradiction taxonomy, resolution protocol, and drift guard checklist."
- REASON: "Lore drift destroys credibility; consistency must be enforced through explicit checks and resolution steps."
- IMPACT: "Entities can prevent contradictions, audit new scenes, and handle conflicts deterministically."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.002

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_world
- type_topic
- skill_procedure
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Согласованность лора = способность любого нового утверждения (claim) “вписаться” в законы мира без скрытых исключений.
Этот модуль даёт процедуру:
- как формулировать claim,
- к каким законам/ограничениям его привязать,
- как находить противоречия,
- как детерминированно разрешать конфликт,
- как ставить drift guard (защита от дрейфа).

---

## 2) WHEN TO USE
- Добавляешь новый факт/правило/способность/артефакт/событие.
- Появилось чувство “раньше было иначе”.
- В мире много элементов и легко “сломать” причинность.

## 3) WHEN NOT TO USE
- Ты только формируешь закон мира (используй topic про laws/constraints).
- Ты делаешь терминологию/глоссарий (reference realm).
- Ты пишешь чисто метафорическую аллегорию, где правила не важны (если таков стиль — отдельный закон жанра).

---

## 4) INPUTS (MINIMUM)
- Новый claim (утверждение) в 1–2 предложениях.
- Список релевантных world laws (PATH).
- Контекст: где claim будет использован (сцена/эпизод/арка).

## 5) OUTPUTS (MINIMUM)
- Claim Card (statement + law mapping + status).
- Результат проверки: PASS / REWORK / FAIL.
- Если конфликт: план разрешения (resolution plan) + drift guard.

---

## 6) DEFINITIONS (STRICT)
### Claim
Новое утверждение о мире:
- “Х может делать Y”, “в секторе Z действует правило Q”, “артефакт R даёт эффект”.

### Law mapping
Привязка claim к существующим законам/ограничениям:
- какие laws разрешают/ограничивают claim.

### Contradiction
Несовместимость claim с ранее заданным:
- фактом, законом, ограничением, стоимостью, доступом, хронологией.

---

## 7) CONTRADICTION TYPES (TAXONOMY)
- T1: Capability drift — добавили новую способность без закона/цены
- T2: Cost drift — убрали/уменьшили цену
- T3: Access drift — расширили доступ (“теперь могут все”)
- T4: Rule conflict — прямое противоречие законам
- T5: Timeline conflict — события/порядок не сходятся
- T6: Artifact teleport — объект/ресурс “появился” без источника
- T7: Exception creep — появилось скрытое исключение без фиксации/цены

---

## 8) PROCEDURE (CLAIM → LAW MAPPING → DECISION)
### Step 1 — Write CLAIM (one sentence, testable)
Формат:
- “Сущность/система X может Y при условиях Z.”

Запрещено:
- размыто: “иногда”, “как правило”, “может быть”.

### Step 2 — Identify the AFFECTED LAW SURFACE
Отметь, что затронуто:
- law/capability
- constraints (resource/access/side effect)
- exceptions
- costs
- timeline

### Step 3 — Map CLAIM to existing LAWS (PATH list)
Список:
- LAW SUPPORT (что разрешает)
- LAW LIMITS (что ограничивает)
Если нет поддерживающего закона — claim не может быть VERIFIED (минимум REWORK).

### Step 4 — Run DRIFT CHECK (3 questions)
1) Добавляет ли claim новую способность? (T1)
2) Уменьшает ли claim цену/риск? (T2)
3) Расширяет ли claim доступ? (T3)

Если “да” → требуется обновление/создание world law (через law topic) или отказ.

### Step 5 — Run CONTRADICTION SCAN
Проверь:
- конфликт с rule statement
- конфликт с constraints
- конфликт с timeline
- конфликт с ранее заданными исключениями/ценой

Классифицируй тип (T1..T7).

### Step 6 — Resolution protocol (choose one)
Если конфликт найден, выбери решение:

- R1: REJECT CLAIM (удалить/заменить)
- R2: NARROW CLAIM (сузить условия/эффект)
- R3: ADD COST/CONSTRAINT (добавить цену/ограничение)
- R4: CREATE NEW LAW (создать отдельный закон мира с тестами)
- R5: FORMAL EXCEPTION (добавить исключение с exception cost)

Правило:
- “скрытое исключение” запрещено. Любое исключение должно быть формализовано и иметь цену.

### Step 7 — Set CLAIM STATUS
- VERIFIED: полностью соответствует laws и constraints
- REWORK: можно исправить через R2/R3/R5
- FAIL: противоречит и не ремонтируется без разрушения мира

### Step 8 — Drift guard (mandatory on VERIFIED)
Добавь 2–3 guard проверки:
- “Если в будущем появится Y, проверить constraint C1”
- “Нельзя использовать claim для решения Z без цены”
- “Доступ не расширять без новой версии закона”

---

## 9) CLAIM CARD FORMAT (COPY)
CLAIM CARD:
- CLAIM:
- CONTEXT:
- LAW SUPPORT (PATH):
  - PATH: ...
- LAW LIMITS (PATH):
  - PATH: ...
- DRIFT CHECK:
  - capability drift: YES/NO
  - cost drift: YES/NO
  - access drift: YES/NO
- CONTRADICTION TYPE (if any): <T1..T7 or NONE>
- RESOLUTION: <R1..R5 or NONE>
- STATUS: VERIFIED|REWORK|FAIL
- DRIFT GUARD:
  - Guard 1:
  - Guard 2:

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] Claim сформулирован тестируемо (X может Y при Z)
- [ ] Есть law mapping (support + limits)
- [ ] Drift check пройден (или зафиксировано изменение через закон)
- [ ] Contradiction scan выполнен и классифицирован
- [ ] При конфликте выбрано формальное решение (R1..R5)
- [ ] Есть drift guard (2+ пункта)

PASS IF:
- STATUS = VERIFIED и guard есть

REWORK IF:
- STATUS = REWORK и есть план исправления

FAIL IF:
- claim ломает law/constraints или скрыто расширяет возможности без цены

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (narrow + cost)
CLAIM:
- “Устройство X открывает один шлюз на 10 секунд, если подключено к ядру станции.”
LAW MAPPING:
- support: (law about device)
- limits: (constraints about access + alarm)
DRIFT CHECK:
- capability drift: NO (уже предусмотрено законом)
- cost drift: NO
- access drift: NO
STATUS:
- VERIFIED
DRIFT GUARD:
- “Нельзя открывать более одного шлюза без ключа”
- “Любое открытие поднимает тревогу”

### 11.2 FAIL EXAMPLE (capability drift)
CLAIM:
- “Теперь устройство X может открывать любые двери где угодно и бесшумно.”
DRIFT CHECK:
- capability drift: YES
- cost drift: YES
- access drift: YES
WHY FAIL:
- ломает constraints и превращает инструмент в deus-ex.

---

## 12) COMMON FAILURE MODES
- Failure: claim без закона
  Fix: создать/обновить law card или сузить claim.
- Failure: “маленькое” расширение доступа
  Fix: зафиксировать как новый закон/версию или запретить.
- Failure: исключение без цены
  Fix: формализовать exception cost или удалить исключение.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/01__WORLD__WORLD_LAWS_CONSTRAINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/04__WORLD__GEOGRAPHY_RESOURCE_CAUSALITY.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
