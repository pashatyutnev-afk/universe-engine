# DOMAIN NARRATIVE ENGINES — Realm
FILE: 00__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Realm file for narrative-domain engines (story logic and structure mechanics)

---

## WHAT THIS FAMILY IS

**DOMAIN NARRATIVE ENGINES** — это движки доменной логики повествования.
Они отвечают за то, чтобы история была:
- причинно-следственной
- структурированной
- драматически работающей
- понятной на уровне сцен
- управляемой по темпу и напряжению
- непрерывной по фактам и состояниям
- несущей тему/смысл

Это НЕ “стиль” и НЕ “продакшн-формат”.
Стиль живёт в GENRE_STYLE_ENGINES, формат — в PRODUCTION_FORMAT_ENGINES.

---

## WHY IT EXISTS

Чтобы из сырых событий получить работающий нарратив:
- события → сцены
- сцены → дуги
- дуги → сезон/книга
- сезон → каноническая история

---

## INPUT / OUTPUT (CANON)

### Inputs
- Event list (что происходит)
- Character intents (кто чего хочет)
- World constraints (что возможно)
- Target audience/format constraints (если есть)

### Outputs
- Story skeleton (acts / beats / arcs)
- Scene list (с целями и поворотами)
- Stakes & tension map
- Continuity constraints
- Theme statement + throughlines

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

## DOMAIN INVARIANTS (NARRATIVE LAW)

- N0: У каждого события есть причина или оно маркировано как “внешний удар”.
- N1: Любая сцена обязана менять состояние (инфо/отношения/положение/риск).
- N2: Любая дуга имеет старт → напряжение → точку перелома → выход.
- N3: Темп управляется осознанно, а не случайно.
- N4: Ставки либо растут, либо меняют природу угрозы.
- N5: Твисты не противоречат канону и подготовлены (явно или скрыто).
- N6: Непрерывность важнее “красивой идеи”. Сначала консистентность.
- N7: Тема проявляется через выборы и последствия, а не декларации.

---

## INTEGRATION

- With CORE (Identity/State/Lifecycle): сцены и арки тоже сущности с состояниями.
- With CHARACTER engines: мотивации/психология — топливо нарратива.
- With WORLD engines: законы мира ограничивают решения.
- With ORC Orchestrators: пайплайн “events → scenes → arcs → canon”.
- With VAL/QA: проверка логики, непрерывности, качества.

---
OWNER: Universe Engine
STATUS: FIXED
