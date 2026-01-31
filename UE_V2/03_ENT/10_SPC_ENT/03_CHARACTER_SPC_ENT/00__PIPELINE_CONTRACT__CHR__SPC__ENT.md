# SPC FAMILY REALM — CHARACTER SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/00__README_CHARACTER_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.CHARACTER.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `03_CHARACTER`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established CHARACTER SPC family realm: purpose, boundaries, interfaces, quality rules, and creation gates."
- REASON: "Need deterministic character layer: stable identities, motivations, relationships, behavioral consistency, and evolution supervision."
- IMPACT: "Characters become coherent systems that stay consistent across scenes, arcs, and writing passes."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.CHARACTER.001

---

## 0) PURPOSE (LAW)
Семейство `03_CHARACTER` отвечает за персонажей как систему:
- ядро персонажа (identity/core)
- личность и поведенческие паттерны
- мотивация, травма, потребности
- отношения и динамики между персонажами
- поведение в диалогах (как проявляется характер)
- контроль эволюции персонажа по арке (чтобы не “ломался”)

Цель семьи — создать **воспроизводимых персонажей**, которые:
- понятны (что ими движет)
- последовательны (не скачут без причины)
- способны меняться (эволюция, а не хаос)

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
**FAMILY NAME:** CHARACTER SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/`

### 2.1 Covered domains (what we DO)
- Character core (identity, values, contradictions)
- Personality modeling (traits, coping, decision style)
- Motivation/trauma/desire (drivers and wounds)
- Relationship dynamics (power, attachment, conflict styles)
- Dialogue behavior (speech patterns as behavior)
- Character evolution supervision (growth consistency across arcs)

### 2.2 Hard boundaries (what we DO NOT do)
- Не владеем структурой истории/сцен (это `02_NARRATIVE`), мы даём ограничения/правдоподобие.
- Не владеем mood/стилем/эстетикой (это `01_CREATIVE`), но учитываем как контекст.
- Не делаем фактчекинг/науку (это `09_RESEARCH` + VAL).
- Не утверждаем лор/канон мира (это `10__LORE_MASTER` + governance).
- Не производим медиа-артефакты (production layer).

---

## 3) DEFAULT OUTPUT PHILOSOPHY
**Default mindset:** DEFINE → TEST IN SCENES → STABILIZE → EVOLVE  
**Primary quality priority:** consistency → motivation clarity → believable change  
**Default outputs:**
- character core sheets
- motivation & trauma drivers
- relationship maps
- dialogue behavior profiles
- evolution checkpoints (what changed and why)

---

## 4) INTERFACES (SYSTEM LINKS)
### 4.1 ENG (Engines) — typical support
- `03_DOMAIN_CHARACTER_ENGINES/*` (core/motivation/psychology/behavior/relationship/dialogue/growth)
- `02_DOMAIN_NARRATIVE_ENGINES/*` (в части “сцены требуют поведения”)
- `05_EXPRESSION_ENGINES/*` (конфликт/повороты как триггеры реакции)

### 4.2 ORC (Orchestrators) — typical usage
ORC вызывает CHARACTER SPC когда нужно:
- создать персонажа/ядро
- проверить мотивационную правдоподобность сцены
- стабилизировать речь/поведение
- спроектировать отношения и конфликтные динамики
- контролировать эволюцию персонажа по арке

### 4.3 VAL / QA (Gates)
Типовые гейты:
- behavioral consistency sanity (персонаж не “ломается”)
- naturalness (если речь/диалоги)
- continuity sanity (если изменения по арке)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- Character Architect: структура персонажа (ядро).
- Personality Psychologist: модель личности и реакции.
- Trauma & Motivation Designer: драйверы желания/страха/раны.
- Relationship Dynamics Designer: динамика “между” персонажами.
- Dialogue Behavior Analyst: речь как поведение (паттерны, манёвры).
- Character Evolution Supervisor: контроль изменений по арке (стабильность эволюции).

### 5.2 Output discipline
- Любая характеристика персонажа должна иметь:
  - наблюдаемые проявления (как это видно в сценах)
  - триггеры (что включает/выключает)
  - цену/последствия (что стоит)

### 5.3 No hidden canon
- Новые факты персонажа/мира не становятся каноном автоматически.
- Если нужно закреплять “истину” — через governance и lоre контроль.

---

## 6) WHEN TO CREATE A NEW CHARACTER SPECIALIST (GATE)
Новый CHARACTER SPC создаётся только если:
- есть устойчивый тип задач, который не закрывается текущими ролями
- требуется отдельный контракт (например “комедийный архетип контроль”)
- роль становится постоянной дырой в пайплайнах

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — CHARACTER ARCHITECT  
02 — PERSONALITY PSYCHOLOGIST  
03 — TRAUMA & MOTIVATION DESIGNER  
04 — RELATIONSHIP DYNAMICS DESIGNER  
05 — DIALOGUE BEHAVIOR ANALYST  
06 — CHARACTER EVOLUTION SUPERVISOR  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `03_CHARACTER`.  
Персонаж — система. Если нет наблюдаемых проявлений, триггеров и причин изменений — персонаж превращается в случайность.

--- END.
