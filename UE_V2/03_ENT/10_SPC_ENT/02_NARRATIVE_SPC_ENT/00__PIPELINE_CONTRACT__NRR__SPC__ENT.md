# SPC FAMILY REALM — NARRATIVE SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/00__README_NARRATIVE_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.NARRATIVE.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `02_NARRATIVE`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established NARRATIVE SPC family realm: purpose, boundaries, interfaces, quality rules, and creation gates."
- REASON: "Need deterministic narrative layer with clear role separation, repeatable story outputs, and no overlap with creative/style ownership."
- IMPACT: "Narrative work becomes structured, auditable, and compatible with engines/orchestration."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.NARRATIVE.001

---

## 0) PURPOSE (LAW)
Семейство `02_NARRATIVE` отвечает за **построение истории**:
- логика повествования
- структура (сюжетные каркасы)
- драматические дуги
- сцены и их функция
- темп/ритм
- ставки/напряжение
- foreshadowing / twists / continuity
- темы и смысл
- диалоги (как часть повествования)
- лор (каноническая связность мира в рассказе)
- романизация (перевод структуры в прозу)

Цель семьи — делать историю **понятной, сильной и повторяемой**, а не “на вдохновении без схемы”.

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
**FAMILY NAME:** NARRATIVE SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/`  
**WHO THIS FAMILY IS FOR:** архитектура истории, сцены, драматургия, смысл, диалоги, лор и перевод в текст.

### 2.1 Covered domains (what we DO)
- Story architecture and structure
- Scene design and scene function
- Dramatic arc, stakes, tension
- Pacing and rhythm (story-time)
- Foreshadowing, twist/reveal mechanics
- Continuity control (narrative coherence)
- Theme/meaning (смысловая рамка истории)
- Dialogue as narrative tool
- Lore integration (канон-совместимый лор внутри истории)
- Novelization (структура → проза)

### 2.2 Hard boundaries (what we DO NOT do)
- Не владеем визуальным стилем/эстетикой/атмосферой как художественными правилами (это `01_CREATIVE`).
- Не владеем психологической моделью персонажей как системой (это `03_CHARACTER` + `08_PSYCHOLOGY`).
- Не владеем фактчекингом и научной проверкой (это `09_RESEARCH` + VAL).
- Не делаем продакшн артефактов (монтаж/камера/звук) — это `07_PRODUCTION` / `05_VISUAL` / `06_SOUND_MUSIC`.
- Не утверждаем канон и структуру системы (TOP Governance).

---

## 3) DEFAULT OUTPUT PHILOSOPHY
**Default mindset:** STRUCTURE → TEST → ITERATE → COMMIT  
**Primary quality priority:** coherence → causality → emotional impact → clarity  
**Default outputs:**
- story structure docs
- arc maps and scene maps
- tension/stakes plans
- continuity notes
- theme/meaning statements
- dialogue briefs and scene dialogue passes
- lore integration notes
- novelization drafts (chapter-based)

---

## 4) INTERFACES (SYSTEM LINKS)
### 4.1 ENG (Engines) — typical support
- `02_DOMAIN_NARRATIVE_ENGINES/*` (логика/структура/арка/сцены/темп/континуити/тема)
- `05_EXPRESSION_ENGINES/*` (event/cause-effect/conflict/climax/resolution)
- `03_DOMAIN_CHARACTER_ENGINES/*` (когда сцена зависит от мотивации/роста)
- `04_DOMAIN_WORLD_ENGINES/*` (когда сцена завязана на законы мира/эпохи)

### 4.2 ORC (Orchestrators) — typical usage
ORC вызывает NARRATIVE SPC когда нужно:
- превратить идею/события в структуру
- построить сцены и их функцию
- сделать арку персонажа/истории понятной
- удержать континуити и лор
- выдать текстовую форму (скрипт/проза)

### 4.3 VAL / QA (Gates)
Типовые гейты для нарратива:
- Consistency / continuity sanity
- Naturalness (язык/диалог)
- Fact plausibility (если история опирается на реальные факты)
- Doc-control (если фиксация в каноне/индексах)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- Episode Showrunner: цель эпизода, сквозной контроль драматургии эпизода.
- Head Writer: владелец писательского контура и единого голоса.
- Story Architect: каркас структуры истории.
- Dramaturg: драматургические функции/эффект/работоспособность сцен.
- Screenwriter: сценарная форма (сценарные единицы, действия/сцены).
- Dialogue Writer: диалоги как инструмент сцены.
- Cliffhanger Specialist: “крючки” и удержание.
- Emotional Arc Designer: эмоции по арке/эпизоду.
- Theme & Meaning Curator: смысловые оси и тезисы.
- Lore Master: канон-совместимый лор внутри повествования.
- Novelist: проза, главы, литературная форма.

### 5.2 Output discipline
- Каждый вывод должен включать:
  - контекст + ограничения
  - структуру/каркас (если применимо)
  - тест на причинно-следственность (почему это работает)
  - последствия и риски
  - что дальше делать (handoff)

### 5.3 No hidden canon
- Никакая история не меняет канон “по умолчанию”.
- Если повествование требует канон-правки → governance путь.

---

## 6) WHEN TO CREATE A NEW NARRATIVE SPECIALIST (GATE)
Новый NARRATIVE SPC создаётся только если:
- есть повторяющийся тип задач, который не закрывается текущими ролями без размывания границ
- нужен отдельный режим мышления/контракт (например “комедия-ритм”, “детектив-логика”)
- роль появляется постоянно как “дырка” в пайплайнах

Создание “на всякий случай” запрещено.

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — EPISODE SHOWRUNNER  
02 — HEAD WRITER  
03 — STORY ARCHITECT  
04 — DRAMATURG  
05 — SCREENWRITER  
06 — DIALOGUE WRITER  
07 — CLIFFHANGER SPECIALIST  
08 — EMOTIONAL ARC DESIGNER  
09 — THEME MEANING CURATOR  
10 — LORE MASTER  
11 — NOVELIST  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `02_NARRATIVE`.  
Нарратив обязан быть структурным, проверяемым и совместимым с каноном; иначе это дрейф и хаос.

--- END.
