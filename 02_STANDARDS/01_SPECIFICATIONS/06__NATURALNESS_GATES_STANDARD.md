# NATURALNESS GATES STANDARD (SoT) (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.NAT_GATES.106
OWNER: SYSTEM
ROLE: Source-of-Truth specification for Naturalness Gates: defines quality gates for plausibility, consistency, and immersion. Provides controlled gate set, scoring rules, and the interface to NAT Profile template.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован Naturalness Gates SoT: набор гейтов, уровни строгости, правила оценивания, интерфейс к NAT Profile"
- REASON: "Нужен единый механизм контроля 'естественности' без субъективного хаоса"
- IMPACT: "Narrative/Character/Visual/Sound authoring, pipeline validation"

---

## 0) PURPOSE (LAW)
Этот документ — SoT-спека о том:
- что такое Naturalness Gates,
- какие гейты существуют (контролируемый список),
- как задаётся строгость и оценка,
- как оформлять NAT Profile (шаблон),
- как внедрять гейты в процессы (pipelines).

---

## 1) AUTHORITY & XREF (UID-first)
Primary authority:
- `01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md` (pipelines concept)
- `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md` (doc structure)
- `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md` (xrefs)

XREF:
- XREF: UE.REG.PIPELINE.MASTER.007 | references | pipelines can embed NAT gates | 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md
- XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header/compliance | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
- XREF: UE.STD.TPL.NAT_PROFILE.106A | implements | NAT Profile template interface | 02_STANDARDS/01_SPECIFICATIONS/06A__TEMPLATE__NAT_PROFILE.md

---

## 2) DEFINITIONS
- **Naturalness** — ощущение естественности: причинность, мотивации, консистентность мира, отсутствие “пластика/склейки”.
- **Gate** — проверка (правило), которую можно применить к сцене/персонажу/эпизоду/дизайну.
- **NAT Profile** — конфигурация включённых гейтов и их строгости для конкретного проекта/реалма/пайплайна.
- **Gate Result** — результат применения гейта: PASS/WARN/FAIL + комментарий.

---

## 3) NAT GATES MODEL (CONTRACT)
### 3.1 Gate record (minimum)
Каждый гейт описывается как:
- `GATE_ID` (stable key)
- `NAME`
- `APPLIES_TO` (Narrative/Character/Visual/Sound/Any)
- `INTENT` (что предотвращает)
- `CHECK` (как проверять, кратко)
- `OUTPUT` (PASS/WARN/FAIL)

### 3.2 Strictness levels
Уровни строгости:
- `S0` — мягко (warn-heavy)
- `S1` — стандарт
- `S2` — строго
- `S3` — ультра строго (fail-heavy)

(Это НЕ приоритет задач S0-S3 из других модулей; здесь это “strictness”.)

---

## 4) CONTROLLED GATE SET (CANONICAL)
Ниже — контролируемый список гейтов. Добавление нового — через Canon Protocol.

### G-01 CAUSALITY
- GATE_ID: G-01
- NAME: Causality & Consequences
- APPLIES_TO: Any
- INTENT: Исключить “магические” события без причин/последствий
- CHECK: есть причина → действие → результат → последствия (хотя бы тезисно)
- OUTPUT: PASS/WARN/FAIL

### G-02 MOTIVATION
- GATE_ID: G-02
- NAME: Agent Motivation Coherence
- APPLIES_TO: Character/Narrative
- INTENT: Убрать “персонаж делает потому что надо”
- CHECK: действие персонажа объясняется мотивацией/контекстом/ставками
- OUTPUT: PASS/WARN/FAIL

### G-03 WORLD CONSISTENCY
- GATE_ID: G-03
- NAME: World Rules Consistency
- APPLIES_TO: Any
- INTENT: Не нарушать правила мира
- CHECK: событие не противоречит установленным правилам/ограничениям
- OUTPUT: PASS/WARN/FAIL

### G-04 STAKES CLARITY
- GATE_ID: G-04
- NAME: Stakes Clarity
- APPLIES_TO: Narrative
- INTENT: Избежать “всё происходит без риска”
- CHECK: ставки обозначены (явно или имплицитно)
- OUTPUT: PASS/WARN/FAIL

### G-05 EMOTIONAL CONTINUITY
- GATE_ID: G-05
- NAME: Emotional Continuity
- APPLIES_TO: Character
- INTENT: Убрать резкие эмоциональные скачки без мостов
- CHECK: эмоциональные переходы имеют мост/причину
- OUTPUT: PASS/WARN/FAIL

### G-06 VISUAL READABILITY
- GATE_ID: G-06
- NAME: Visual Readability & Blocking
- APPLIES_TO: Visual
- INTENT: Избежать нечитаемой сцены
- CHECK: зрителю понятно кто где/что делает, логичная мизансцена
- OUTPUT: PASS/WARN/FAIL

### G-07 SOUND LOGIC
- GATE_ID: G-07
- NAME: Sound Logic & Continuity
- APPLIES_TO: Sound
- INTENT: Убрать “звук ради звука”, разрывы атмосферы
- CHECK: звук/музыка поддерживают событие и не ломают тон
- OUTPUT: PASS/WARN/FAIL

### G-08 INFORMATION FLOW
- GATE_ID: G-08
- NAME: Information Flow (No Teleport Info)
- APPLIES_TO: Narrative/Character
- INTENT: Персонажи не должны знать то, чего не могли узнать
- CHECK: знания/информация имеют источник/путь
- OUTPUT: PASS/WARN/FAIL

### G-09 TIME/SPACE PLAUSIBILITY
- GATE_ID: G-09
- NAME: Time & Space Plausibility
- APPLIES_TO: Any
- INTENT: Исключить невозможные перемещения/тайминги
- CHECK: таймлайн и география не ломаются
- OUTPUT: PASS/WARN/FAIL

---

## 5) SCORING & OUTCOMES (STANDARD)
### 5.1 Gate outputs
- PASS — ок
- WARN — допустимо, но отметить
- FAIL — блокер (в зависимости от strictness)

### 5.2 Strictness rule
В NAT Profile для каждого гейта задаётся strictness:
- S0: FAIL применяется редко (только явные провалы), чаще WARN
- S1: баланс
- S2: FAIL чаще, WARN меньше
- S3: почти всё важное превращается в FAIL, пока не исправлено

### 5.3 Overall NAT score (optional)
Если нужно считать общий итог:
- `NAT_SCORE = 100 - (FAIL*20 + WARN*5)` (минимум 0)
Это опционально и не является обязательным контрактом.

---

## 6) NAT PROFILE INTERFACE (TEMPLATE 06A)
NAT Profile обязан задавать:
- список включённых гейтов
- strictness по каждому
- apply scope (к чему применяется)
- policy: “что делать при FAIL/WARN” (block/allow/flag)

Шаблон:
- `06A__TEMPLATE__NAT_PROFILE.md`

---

## 7) PIPELINE INTEGRATION (HOW TO USE)
Пайплайны могут включать NAT gates как gate set.
Минимальный режим:
- применить 3–5 гейтов к сцене/арке
- записать результат (PASS/WARN/FAIL) и комментарии

---

## 8) MIGRATION NOTES
S0:
- создать NAT Profile для каждого realm/потока, где нужен контроль естественности
S1:
- если появятся новые типы гейтов, расширять controlled set через Canon Protocol

---

## FINAL RULE (LOCK)
Naturalness Gates — SoT по контролю естественности.
Добавление/изменение базового набора гейтов = изменение канона (Canon Protocol).
--- END.
