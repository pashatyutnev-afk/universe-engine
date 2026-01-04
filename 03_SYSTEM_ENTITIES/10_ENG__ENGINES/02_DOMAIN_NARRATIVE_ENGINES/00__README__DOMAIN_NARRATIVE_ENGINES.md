# DOMAIN NARRATIVE ENGINES — Realm
FILE: 00__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm file for narrative domain engines; defines canonical narrative terms, boundaries, outputs, and how narrative specs flow into character/world and production families

---

## WHAT THIS FAMILY IS

**DOMAIN_NARRATIVE_ENGINES** — это движки, которые превращают “идею” в **сценарную систему**:
- логика нарратива
- структура истории
- драматическая дуга
- сцены и биты
- темп/ритм
- ставки/напряжение
- предвосхищение и раскрытия
- непрерывность
- тема/смысл

Это слой L2: фундамент домена “история”.

---

## WHY IT EXISTS

Если нарратив не системный:
- события не следуют причинности
- сцены не держат смысловую дугу
- персонажи выглядят случайно
- монтаж/визуал не имеют опоры

Этот family делает **Narrative Spec** — то, на что могут опираться:
- Character engines
- World engines
- Production engines

---

## FAMILY BOUNDARY (IMPORTANT)

Narrative family НЕ делает:
- психологию персонажей (это 03_DOMAIN_CHARACTER_ENGINES)
- устройство мира/законы/экономику (это 04_DOMAIN_WORLD_ENGINES)
- камеру/свет/монтаж (это production families)

Narrative family делает:
- **смысловую структуру** истории и сцены
- **требования** к персонажам/миру как to-be constraints
- **scene spec** как главный output

---

## FAMILY-WIDE CANON TERMS

### NARRATIVE SPEC
Структурированное описание истории/сцены, достаточное для воспроизведения:
- цель сцены
- биты
- конфликт
- ставки
- поворот/кульминация/разрешение
- последствия

### BEAT
Мини-событие/шаг, который меняет состояние сцены.

### TURN
Сдвиг направления: персонаж/ситуация “переворачивается”.

### STAKES
Цена, которую платит герой.

### CONTINUITY
Непрерывность логики и фактов между сценами.

---

## PRIMARY OUTPUTS (WHAT DOWNSTREAM EXPECTS)

### Scene Spec (canonical payload)
- SCENE_ID
- GOAL (what must land)
- SETUP
- BEATS (ordered)
- CONFLICT
- STAKES
- TURNING POINT
- CLIMAX
- RESOLUTION
- CONSEQUENCES
- CONTINUITY NOTES
- THEME HOOK (meaning anchor)

### Story Skeleton (optional)
- acts/episodes structure
- major turns and reveals

---

## PIPELINE LINKS (HANDOFF)

Narrative outputs feed:
- Character family: motivations, trauma, evolution, dialogue intent
- World family: location constraints, law constraints, timeline anchors
- Production families: shot lists, visuals, editing rhythm, sound sync hooks

---

## FAMILY CONTENTS

01 — Narrative Logic Engine  
02 — Story Structure Engine  
03 — Dramatic Arc Engine  
04 — Scene Construction Engine  
05 — Pacing & Rhythm Engine  
06 — Tension & Stakes Engine  
07 — Foreshadowing Engine  
08 — Twist & Reveal Engine  
09 — Narrative Continuity Engine  
10 — Theme & Meaning Engine  

---

## FAMILY-WIDE VALIDATION

- N1: Любая сцена имеет цель и измеримый “сдвиг состояния”.
- N2: Причинность не нарушена (если не заявлено intentional).
- N3: Continuity notes существуют всегда (минимум 1–3 пункта).
- N4: Сцена имеет связь с темой (theme hook), даже если тонкая.

---

OWNER: Universe Engine
LOCK: FIXED
