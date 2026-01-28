# TOPIC — INSTITUTIONS & POWER SYSTEMS (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/05__WORLD__INSTITUTIONS_POWER_SYSTEMS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.INSTITUTIONS_POWER.001
OWNER: SYSTEM
ROLE: Provide an atomic method to design institutions as power systems with legitimacy, enforcement, incentives, and failure modes; includes an institution card, power map, pass/fail tests, and drift guards

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for institutions/power: power map + legitimacy + enforcement + incentives + failure modes with test cases."
- REASON: "Institutions feel fake when they are just titles; power must be explainable through resources, incentives, and enforcement."
- IMPACT: "Entities can build believable politics and conflict drivers, and audit scenes for institutional mismatch."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.005

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
Институт = система власти, а не “должность”.
Этот модуль даёт процедуру, как описывать институты так, чтобы было ясно:
- кто реально контролирует ресурсы и решения,
- откуда легитимность,
- как исполняются правила,
- какие стимулы/страхи держат систему,
- где система ломается и почему.

---

## 2) WHEN TO USE
- Создаёшь государство/клан/корпорацию/орден/религию/полицию/суд/профсоюз.
- В мире есть “законы”, но непонятно, кто их реально обеспечивает.
- Конфликт про власть, контроль, распределение ресурсов, безопасность.

## 3) WHEN NOT TO USE
- Ты описываешь географию/ресурсы (см. Geo & Resource Causality).
- Ты описываешь технологические возможности (см. Tech Level Impact).
- Ты формализуешь закон мира (см. World Laws & Constraints).

---

## 4) INPUTS (MINIMUM)
- Регион/общество (где действует институт).
- Ресурсы/узлы (chokepoints), которые можно контролировать.
- Угрозы (внешние/внутренние), которые оправдывают власть.

## 5) OUTPUTS (MINIMUM)
- POWER MAP (кто с кем и через что).
- INSTITUTION CARD (легитимность/силы/инструменты/стимулы).
- 2 PASS + 2 FAIL test cases + drift guards.

---

## 6) DEFINITIONS (STRICT)
### Power
Возможность навязать решение (через ресурсы, насилие, доступ, информацию, закон, идеологию).

### Legitimacy
Почему подчиняются “добровольно”:
- традиция, религия, закон, результат (безопасность/еда), страх, харизма.

### Enforcement
Как реально заставляют соблюдать:
- полиция/армия/санкции/контроль доступа/наблюдение/долги/заложники.

### Incentive
Почему участники системы её поддерживают:
- выгода, безопасность, статус, доступ, защита от хаоса.

### Failure mode
Как система ломается:
- коррупция, перегруз, раскол элит, дефицит, потеря легитимности, внешнее поражение.

---

## 7) PROCEDURE (INSTITUTION AS POWER SYSTEM)
### Step 1 — Define the POWER OBJECT (what is controlled)
Выбери 1–3 “объекта власти”:
- chokepoint (перевал/порт/станция)
- ресурс (вода/энергия/еда/металл/данные)
- инфраструктура (связь/транспорт/производство)
- легальный статус (право владения/суд/монополия)
- безопасность (армия/щит/стража)

### Step 2 — Build POWER MAP (actors and flows)
Составь карту из 4–8 акторов:
- A1: институт (центр)
- A2..A8: элиты/силовики/торговцы/жрецы/банкиры/кланы/бунтари/внешние игроки

Для каждой связи укажи:
- что течёт (ресурс/деньги/инфо/защита)
- кто зависит от кого (dependency)
- где точка шантажа (leverage)

### Step 3 — Define LEGITIMACY (2 sources minimum)
Укажи минимум 2 источника легитимности:
- L1: традиция/род/закон
- L2: результат (безопасность/распределение/стабильность)
(Можно добавить страх как отдельную ось, но это слабая легитимность.)

### Step 4 — Define ENFORCEMENT TOOLKIT (3 tools minimum)
Минимум 3 инструмента:
- E1: силовая структура (стража/армия)
- E2: экономические санкции (налоги/пошлины/конфискация)
- E3: контроль доступа (пропуска/реестры/узлы/наблюдение)

### Step 5 — Define INCENTIVE STRUCTURE (why people comply)
Опиши стимулы для 3 групп:
- элиты
- обычные
- силовики/админ

Формат:
- “Группа X поддерживает институт потому что получает ___ и боится ___.”

### Step 6 — Define CORRUPTION & LEAKS (realism)
Укажи 2–3 “утечки” системы:
- где взятки
- где контрабанда
- где саботаж
Если утечек нет — система выглядит фальшиво.

### Step 7 — Define FAILURE MODES (3 modes minimum)
Минимум 3:
- F1: потеря ресурса/chokepoint
- F2: раскол элит/силовиков
- F3: потеря легитимности из-за голода/поражения/скандала

### Step 8 — Test cases (2 PASS + 2 FAIL)
PASS: сцены, где власть работает по правилам карты.
FAIL: сцены, где власть “не может так работать” без объяснения (mismatch).

### Step 9 — Drift guards (2+)
Проверки на будущее:
- “если меняется ресурс/техуровень — пересчитать enforcement и incentives”
- “если добавляется новый актор — обновить power map”

---

## 8) INSTITUTION CARD FORMAT (COPY)
INSTITUTION CARD:
- NAME:
- REGION:
- POWER OBJECTS (1–3):
  - P1:
- POWER MAP (actors + flows):
  - A1:
  - A2:
  - LINK: A1 -> A2 (flow / dependency / leverage)
- LEGITIMACY (2+):
  - L1:
  - L2:
- ENFORCEMENT TOOLKIT (3+):
  - E1:
  - E2:
  - E3:
- INCENTIVES (3 groups):
  - Elites:
  - People:
  - Enforcement:
- CORRUPTION/LEAKS (2–3):
  - C1:
  - C2:
- FAILURE MODES (3+):
  - F1:
  - F2:
  - F3:
- TEST CASES:
  - PASS 1:
  - PASS 2:
  - FAIL 1:
  - FAIL 2:
- DRIFT GUARDS (2+):
  - Guard 1:
  - Guard 2:

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] Определены power objects (что контролируется)
- [ ] Есть power map (4–8 акторов + потоки/зависимости)
- [ ] Есть 2+ источника легитимности
- [ ] Есть 3+ инструментов enforcement
- [ ] Прописаны incentives для 3 групп
- [ ] Есть 2–3 утечки (коррупция/контрабанда)
- [ ] Есть 3+ failure modes
- [ ] Есть 2 PASS + 2 FAIL теста
- [ ] Есть drift guards

PASS IF:
- все пункты true

REWORK IF:
- есть титулы/структура, но нет потоков и механизмов

FAIL IF:
- институт “на словах” без enforcement/incentives

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (chokepoint clan)
INSTITUTION CARD (fragment):
- POWER OBJECT: горный перевал (chokepoint) + вода
- LEGITIMACY: “мы защищаем караваны” + “традиционный род”
- ENFORCEMENT: стража перевала, пошлина, пропуска
- INCENTIVES:
  - элиты: богатеют на пошлине
  - люди: получают стабильные поставки и защиту
  - стража: статус + доля пошлины
- LEAKS: контрабанда ночью по тропе, взятки за быстрый проход
- FAILURE: если перевал перекрыт лавиной или стража раскололась — город голодает, власть падает
WHY PASS:
- власть объяснима ресурсом, контролем и стимулами.

### 10.2 FAIL EXAMPLE (institution mismatch)
Заявлено:
- нет армии/контроля доступа/санкций
В сцене:
- “институт мгновенно заставляет весь регион подчиниться приказу”
WHY FAIL:
- нет enforcement toolkit → власть не может исполняться так быстро.

---

## 11) COMMON FAILURE MODES
- Failure: “король сказал — все сделали”
  Fix: показать enforcement и incentives (кто заставляет и почему).
- Failure: нет утечек
  Fix: добавить коррупцию/контрабанду/саботаж.
- Failure: власть не связана с ресурсом
  Fix: привязать к chokepoint/resource/infrastructure.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/04__WORLD__GEOGRAPHY_RESOURCE_CAUSALITY.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/01__WORLD__WORLD_LAWS_CONSTRAINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/02__WORLD__LORE_CONSISTENCY_RULES.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines checkable cards/maps)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
