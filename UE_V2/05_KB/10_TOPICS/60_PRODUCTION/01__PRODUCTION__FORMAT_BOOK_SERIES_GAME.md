# TOPIC — FORMAT: BOOK vs SERIES vs GAME (PRODUCTION / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/01__PRODUCTION__FORMAT_BOOK_SERIES_GAME.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.PROD.FORMAT.BSG.001
OWNER: SYSTEM
ROLE: Atomic method to choose and enforce a production format (book/series/game) as a structural contract: units, pacing rules, turning points, deliverables, and constraints; includes Format Contract Cards and pass/fail tests

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for production format selection: format contracts for book/series/game with unit structure, pacing expectations, and deliverables."
- REASON: "Stories fail when format expectations are ignored; each medium demands different unit design, pacing, and payoff cadence."
- IMPACT: "Entities can adapt the same story core to multiple formats deterministically without losing coherence."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.PROD.001

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_production
- type_topic
- format_contract
- adaptation
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Формат — это контракт:
- какие “единицы” контента (глава/серия/квест),
- какой темп и частота поворотов,
- как выдаётся информация,
- какой deliverables pack должен быть на выходе.

---

## 2) WHEN TO USE
- Нужно выбрать: писать как книгу, как сериал, как игру (или адаптировать).
- История “не работает” в выбранном формате (темп/повороты/клиффхэнгеры).
- Требуется план производства: что сдаём и в каком виде.

## 3) WHEN NOT TO USE
- Ты пишешь одну сцену (это narrative topics).
- Ты проектируешь мир (world topics).

---

## 4) INPUTS (MINIMUM)
- Story core (конфликт/герой/ставки/финал).
- Целевая платформа/формат (book/series/game).
- Ограничения: длительность, бюджет, интерактивность, аудитория.

## 5) OUTPUTS (MINIMUM)
- Format Contract Card (для выбранного формата).
- Unit blueprint (структура единицы).
- Pacing & payoff cadence (частота крючков/поворотов/payoff).
- PASS/REWORK/FAIL по совместимости истории и формата.

---

## 6) DEFINITIONS (STRICT)
### Unit
Минимальная “поставляемая единица”:
- Book: глава
- Series: эпизод (и сезон)
- Game: миссия/квест/глава кампании

### Cadence
Ритм появления:
- целей, препятствий, поворотов, раскрытий, payoff.

### Format contract
Набор правил: “если формат X — то обязаны Y”.

---

## 7) FORMAT CONTRACTS (CORE)
### 7.1 BOOK CONTRACT (novel)
**Strengths:**
- глубина внутреннего мира, нюансы, длинные дуги  
**Constraints:**
- нельзя держать читателя “без крючка” слишком долго  
- экспозиция должна быть встроена (см. Exposition Integration)  
**Unit rules (chapter):**
- цель → конфликт → микроповорот → мини-итог  
**Cadence:**
- микро-интерес каждые 1–3 страницы (наблюдение/вопрос)  
- заметный поворот каждые 1–3 главы  
**Deliverables:**
- outline по главам, сцены, voice/POV, theme thread  

### 7.2 SERIES CONTRACT (episodic)
**Strengths:**
- клиффхэнгеры, параллельные линии, частые payoff  
**Constraints:**
- каждый эпизод обязан иметь собственную дугу и крючок конца  
**Unit rules (episode):**
- hook → setup → escalation → turn → cliff/payoff  
**Cadence:**
- смена “статуса” каждые 3–7 минут (beat density)  
- клиффхэнгер/крючок в конце почти всегда  
**Deliverables:**
- season bible, episode beats, cliff map, arc map  

### 7.3 GAME CONTRACT (interactive)
**Strengths:**
- агентность игрока, выборы, повторяемые циклы  
**Constraints:**
- история должна быть совместима с циклом “делаю → получаю → улучшаю”  
- экспозиция дозируется во время действия  
**Unit rules (quest/mission):**
- objective → play loop → obstacle → reward → new objective  
**Cadence:**
- reward/feedback каждые 2–5 минут  
- значимый выбор/развилка регулярно (по жанру)  
**Deliverables:**
- core loop doc, quest list, reward table, fail states, narrative beats  

---

## 8) PROCEDURE (CHOOSE & ADAPT FORMAT)
### Step 1 — Identify STORY CORE
- protagonist goal
- antagonist pressure
- stakes ladder
- ending type (win/lose/pyrrhic)

### Step 2 — Pick FORMAT TARGET
- book / series / game

### Step 3 — Create FORMAT CONTRACT CARD
Заполни контракт выбранного формата (см. §9).

### Step 4 — Map STORY to UNITS
- Book: 10–40 глав (по задаче)
- Series: 6–12 эпизодов/сезон (по задаче)
- Game: 8–30 миссий (по задаче)

### Step 5 — Define CADENCE RULES
- где крючки
- где turning points
- как часто payoff

### Step 6 — Run MISMATCH CHECK
Проверить:
- book: нет ли “пустых глав” без цели/конфликта
- series: есть ли клиффы/эпизодные дуги
- game: есть ли reward loop и выборы

### Step 7 — Fix with adaptation levers
- split/merge units
- move reveals earlier/later
- add playable objectives (game)
- add cliff map (series)
- deepen internal POV (book)

---

## 9) FORMAT CONTRACT CARD (COPY)
FORMAT CONTRACT CARD:
- FORMAT: BOOK | SERIES | GAME
- UNIT TYPE:
- UNIT BLUEPRINT (must include):
- CADENCE (hooks/turns/payoffs):
- EXPOSITION RULE:
- AGENCY RULE:
- DELIVERABLES PACK (required outputs):
- MISMATCH RISKS (top 3):
- PASS/FAIL NOTES:

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] выбран формат и единица
- [ ] есть blueprint единицы (что обязательно внутри)
- [ ] задан cadence (частота крючков/поворотов/payoff)
- [ ] определён deliverables pack
- [ ] mismatch check пройден
- [ ] есть levers исправления

PASS IF:
- всё соблюдено и история “ложится” в формат

REWORK IF:
- формат выбран, но cadence/units не определены

FAIL IF:
- формат требует того, чего история не предоставляет (например, game без агентности)

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (same core, different formats)
Story core: “герой хочет доступ в сектор, мир контролирует узлы”
- Series: закончить эпизод клиффом “метка наблюдения”
- Book: усилить внутренний POV и сделать микроповорот в конце главы
- Game: превратить доступ в миссию + награда “ключ-канал”, ввести fail state “тревога”
WHY PASS:
- один core, но разные unit contracts.

### 11.2 FAIL EXAMPLE
Game:
- нет выборов, нет reward loop, только “сцены разговора”
WHY FAIL:
- формат mismatch: интерактивность не обслужена.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/10__NARRATIVE__CHARACTER_AGENCY_DECISIONS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/12__NARRATIVE__EXPOSITION_INTEGRATION.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/13__NARRATIVE__CLIMAX_RESOLUTION_PAYOFF.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/06__NARRATIVE__PACING_RHYTHM.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (format = contract; must define units + cadence + deliverables)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
