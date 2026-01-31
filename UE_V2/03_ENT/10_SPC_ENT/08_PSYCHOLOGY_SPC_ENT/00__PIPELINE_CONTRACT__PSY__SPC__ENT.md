# SPC FAMILY REALM — PSYCHOLOGY SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/00__README_PSYCHOLOGY_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.PSYCHOLOGY.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `08_PSYCHOLOGY`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established PSYCHOLOGY SPC family realm: audience psychology, empathy/identification, emotional impact, nonverbal behavior, and behavioral consistency as deterministic support layer."
- REASON: "Need systematic control of emotional delivery and audience response without random guessing; ensure character behavior remains credible."
- IMPACT: "Narrative becomes more effective and consistent: clearer emotional targets, better empathy mechanics, reduced behavior drift."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.PSYCHOLOGY.001

---

## 0) PURPOSE (LAW)
Семейство `08_PSYCHOLOGY` отвечает за психологическую управляемость контента:
- как аудитория воспринимает события и смысл
- как возникает эмпатия/идентификация
- как проектируется эмоциональный удар и послевкусие
- как невербальное поведение поддерживает правдоподобие
- как удерживается поведенческая консистентность персонажей

Цель семьи — сделать реакции аудитории и поведение персонажей **детерминированными**, а не “на авось”.

---

## 1) EXISTENCE + NAV RULE (MANDATORY)
- Специалист существует для системы **только если**:
  1) зарегистрирован в глобальном SPC INDEX:
     `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`
  2) и файл лежит по каноническому пути
- Любые файлы в папке без регистрации — **NON-CANON / ignored**
- Каноническая навигация по семье — через RAW ссылки глобального SPC INDEX

---

## 2) FAMILY SCOPE
**FAMILY NAME:** PSYCHOLOGY SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/`

### 2.1 Covered domains (what we DO)
- Audience response modeling (Viewer Psychology)
- Empathy & identification mechanisms
- Emotional impact design (setup → hit → aftertaste)
- Nonverbal behavior analysis (body language, micro-signals)
- Behavioral consistency enforcement (no drift)

### 2.2 Hard boundaries (what we DO NOT do)
- Мы не переписываем сюжет вместо `02_NARRATIVE`, а даём психологические требования/гейты.
- Мы не ставим “актерскую режиссуру” (это Director), но даём behavioral signals и risk notes.
- Мы не делаем монтажные решения — только психологические риски/ограничения.
- Мы не утверждаем канон мира/лора — соблюдаем и эскалируем конфликты.

---

## 3) KNOWLEDGE BASE (KB) SCOPE (MANDATORY)
### 3.1 KB INPUTS
- Character Craft realm (психология персонажей)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02__CHARACTER_CRAFT.md
- Narrative Craft realm (эмоциональные арки/смысл)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT.md
- Reference Glossary (термины)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md
- Research & Fact Checking realm (если нужны исследования восприятия)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING.md

### 3.2 KB OUTPUTS
- Чеклисты empathy/impact/consistency как унифицированные “гейты”.
- Типовые “behavior drift patterns” и способы их обнаружения.

### 3.3 KB BOUNDARIES
- Не фиксируем медицинские/клинические утверждения как факты без Research/Validators.
- Не подменяем драматургию: мы задаём психологические constraints, а не сюжет.

---

## 4) INTERFACES (SYSTEM LINKS) — RAW ONLY
### 4.1 ENG (Engines) — typical support
- Emotional resonance engine  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG.md
- Character psychology engine  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG.md
- Character behavior engine  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md

### 4.2 ORC — typical usage
ORC вызывает PSYCHOLOGY SPC когда нужно:
- оценить, что зритель поймёт/почувствует (Viewer Psychology Analyst)
- обеспечить идентификацию/эмпатию (Empathy Identification Specialist)
- спроектировать эмоциональный “удар” (Emotional Impact Designer)
- проверить невербальные сигналы и правдоподобие (Nonverbal Behavior Analyst)
- зафиксировать консистентность поведения (Behavioral Consistency Specialist)

### 4.3 QA / VAL gates
Типовые гейты:
- empathy gate (зритель “сцепился” с персонажем?)
- clarity + impact gate (удар дошёл?)
- behavior drift gate (персонаж не ломается?)
- nonverbal plausibility gate (сигналы не противоречат словам?)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- Viewer Psychology Analyst: модель аудитории и восприятия.
- Empathy Identification Specialist: механики привязки к персонажам.
- Emotional Impact Designer: дизайн удара/послевкусия и эмоциональных “ключей”.
- Nonverbal Behavior Analyst: невербальные сигналы, согласованность тела/голоса.
- Behavioral Consistency Specialist: детектор и фиксер дрейфа поведения.

### 5.2 Evidence law (psychology is testable)
Любое психологическое решение должно быть описано как:
- target emotion / target belief
- triggers (что вызывает)
- fail conditions (как понять что не работает)
- mitigation (как чинить)

### 5.3 Non-editing decision boundary
PSYCHOLOGY не принимает монтажных решений.  
Мы выдаём только:
- психологические риски (если темп/склейки ломают эмоцию)
- требования сохранения ключевых моментов (MUST keep)
- рекомендации на уровне принципов

---

## 6) WHEN TO CREATE A NEW PSYCHOLOGY SPECIALIST (GATE)
Новый PSYCHOLOGY SPC создаётся только если:
- появляется устойчивый тип психологических задач, не закрытый текущими 5 ролями
- нужен отдельный контракт (например “Trauma sensitivity reviewer” при росте требований)
- роль становится постоянной дырой в пайплайне

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — VIEWER PSYCHOLOGY ANALYST  
02 — EMPATHY IDENTIFICATION SPECIALIST  
03 — EMOTIONAL IMPACT DESIGNER  
04 — NONVERBAL BEHAVIOR ANALYST  
05 — BEHAVIORAL CONSISTENCY SPECIALIST  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `08_PSYCHOLOGY`.  
Если нет target emotion, triggers и fail conditions — психологический слой превращается в угадайку и ломает эффективность истории.

--- END.
