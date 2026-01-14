# TOPIC — QA GATES & RUBRICS (PRODUCTION / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.PROD.QA_GATES.001
OWNER: SYSTEM
ROLE: Atomic method to evaluate artifacts with deterministic QA gates and rubrics: criteria, thresholds, defect taxonomy, and pass/rework/fail decisions; includes QA Scorecard templates for narrative and music outputs

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created QA gates/rubrics: deterministic criteria, thresholds, defect taxonomy, and scorecards for production outputs."
- REASON: "Quality drifts when decisions are purely subjective; rubrics make QA repeatable and enforceable."
- IMPACT: "Entities can audit outputs consistently, reduce regressions, and enforce release readiness."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.PROD.006

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_production
- type_topic
- qa
- gates
- rubrics
- defect_taxonomy
- maturity_seed

---

## 1) PURPOSE
Сделать оценку качества повторяемой:
- критерии и пороги,
- типовые дефекты,
- решение PASS/REWORK/FAIL,
- единые scorecards для разных типов артефактов (текст/сцена/эпизод/трек).

---

## 2) WHEN TO USE
- Нужно выпускать регулярно без падения качества.
- Споры “нравится/не нравится” тормозят процесс.
- Нужно найти, что именно сломано, и как чинить.
- Нужны автоматизируемые гейты на релиз.

## 3) WHEN NOT TO USE
- Очень ранние черновики (но можно использовать облегченную версию).

---

## 4) DEFINITIONS (STRICT)
### Gate
Пороговое решение:
- PASS: готово для следующего шага/релиза
- REWORK: нужно исправление по списку дефектов
- FAIL: пересобрать/переписать фундаментально

### Rubric
Набор критериев + шкала оценки.

### Defect
Конкретная ошибка, которую можно назвать и исправить.

---

## 5) UNIVERSAL GATES (ALL ARTIFACTS)
Минимальные гейты для любого результата:

G1 — STRUCTURE GATE  
- есть цель/контракт формы, нет “пустых” частей

G2 — CLARITY GATE  
- понятность: что происходит/что требуется/что изменилось

G3 — CONSISTENCY GATE  
- нет противоречий (логику/правила/тон)

G4 — QUALITY SIGNAL GATE  
- есть “хук” или сильный сигнал качества (первые секунды/первые строки)

G5 — RELEASE READINESS (если релиз)  
- метадата/кредиты/права/версии/пак собраны

---

## 6) DEFECT TAXONOMY (COMMON)
- D1: No hook (нет крючка)
- D2: No state change (ничего не изменилось)
- D3: Exposition dump (лекция)
- D4: Motivation gap (герой делает без причины)
- D5: Stakes unclear (ставки не ясны)
- D6: Repetition (повторы без роста)
- D7: Rule break / deus-ex (слом правил)
- D8: Tone drift (тон уехал)
- D9: Technical issue (формат/уровни/шумы/артефакты)
- D10: Missing metadata/credits/rights (релиз риск)

---

## 7) THRESHOLDS (DECISION RULES)
### PASS
- нет дефектов D7/D10
- ≤ 2 дефекта уровня “minor”
- все обязательные гейты G1–G4 = PASS
- если релиз: G5 = PASS

### REWORK
- есть 1–3 дефекта среднего уровня (например D2, D3, D5)
- структура не сломана, но нужны правки
- G1/G2/G4 могут быть PARTIAL

### FAIL
- есть D7 (deus-ex/слом правил) или системная несостыковка
- или 4+ дефектов среднего/критического уровня
- или нет основы (G1 FAIL)

---

## 8) QA SCORECARD — NARRATIVE (COPY)
NARRATIVE QA SCORECARD:
- Artifact type: scene|chapter|episode|outline
- G1 Structure: PASS/REWORK/FAIL
- G2 Clarity: PASS/REWORK/FAIL
- G3 Consistency: PASS/REWORK/FAIL
- G4 Hook/Signal: PASS/REWORK/FAIL
- Defects (from D1..D10):
  - D?:
- Fix list (ordered):
  1)
  2)
- Decision: PASS | REWORK | FAIL
- Notes:

### Narrative quick checks
- [ ] есть objective + obstacle
- [ ] есть escalation / turn
- [ ] есть state change
- [ ] экспозиция оплачена (если есть)
- [ ] нет повтора без роста
- [ ] нет deus-ex

---

## 9) QA SCORECARD — MUSIC (COPY)
MUSIC QA SCORECARD:
- Artifact type: track|hook|verse|mix
- G1 Structure: PASS/REWORK/FAIL
- G2 Clarity (hook/readability): PASS/REWORK/FAIL
- G3 Consistency (style/voice): PASS/REWORK/FAIL
- G4 Hook/Signal (first 10s): PASS/REWORK/FAIL
- G5 Release readiness (if release): PASS/REWORK/FAIL
- Defects (from D1..D10):
  - D?:
- Fix list (ordered):
  1)
  2)
- Decision: PASS | REWORK | FAIL
- Notes:

### Music quick checks
- [ ] хук ≤ 10–15 секунд
- [ ] вокал читается (rap + chorus)
- [ ] низ плотный, не мажет
- [ ] нет лишней грязи/артефактов
- [ ] стиль цельный (industrial/nu metal/glitch)
- [ ] концовка/аутро не провисает

---

## 10) PROCEDURE (RUN QA)
### Step 1 — Choose scorecard
- narrative или music

### Step 2 — Evaluate gates G1–G5
Заполни PASS/REWORK/FAIL по каждому.

### Step 3 — List defects
Назвать дефекты по D1..D10.

### Step 4 — Create fix list (ordered)
Порядок:
1) чинить структуру (G1)
2) чинить ясность/ставки (G2)
3) чинить консистентность/правила (G3)
4) чинить хук (G4)
5) чинить релиз-пак (G5)

### Step 5 — Decide PASS/REWORK/FAIL by thresholds
Применить пороги §7.

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS example (narrative)
- G1 PASS, G2 PASS, G3 PASS, G4 PASS
- defects: D6 minor
Decision: PASS

### 11.2 REWORK example (music)
- G4 REWORK (hook late), G2 REWORK (vocal masked)
- defects: D1, D9
Decision: REWORK

### 11.3 FAIL example
- defect: D7 (deus-ex), G1 FAIL
Decision: FAIL

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/05__PRODUCTION__WORKFLOW_ROLES_HANDOFFS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/04__PRODUCTION__VERSIONING_DELIVERY_NAMING.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/12__NARRATIVE__EXPOSITION_INTEGRATION.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (use rubrics; no subjective-only decisions; defects must be named)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
