# ENG DOMAIN NARRATIVE ENGINES — REALM (FAMILY README)
FILE: 00__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for Narrative domain engines

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY владеет **логикой истории**: как строится смысл, сцены, арки, темп, напряжение,
как удерживается непротиворечивость и “движение истории”.

Domain Narrative отвечает за:
- причинно-смысловую структуру истории (что ведёт к чему и почему)
- формы сюжетной архитектуры (структуры, арки, сцены)
- темп и ритм в рамках **story-time** (а не монтажа)
- управление напряжением/ставками
- continuity (согласованность фактов и событий)
- темы и значения (why it matters)

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)

### THIS FAMILY OWNS
- Story logic (causality, motives, consequences)
- Story structure (acts, beats, arcs)
- Dramatic arc shaping
- Scene construction (story-level)
- Pacing & rhythm (story-time)
- Tension & stakes modeling
- Foreshadowing / setup-payoff
- Twists / reveals mechanics
- Narrative continuity (canon coherence in story layer)
- Theme & meaning extraction/encoding

### THIS FAMILY DOES NOT OWN
- Editing rhythm / montage rhythm (это `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`)
- Production-level storytelling for specific formats (это `07_PRODUCTION_FORMAT_ENGINES`)
- Character internals (это `03_DOMAIN_CHARACTER_ENGINES`)
- World laws/economy/tech (это `04_DOMAIN_WORLD_ENGINES`)
- Governance pipeline/locks (это `00_GOVERNANCE_ENGINES`)

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### Narrative Rhythm vs Editing Rhythm
- Story-time rhythm принадлежит:
  `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md`
- Screen-time rhythm принадлежит:
  `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`

---

## 3) CANON ORDER (MANDATORY)

Порядок внутри `02_DOMAIN_NARRATIVE_ENGINES` строгий:

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

## 4) INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- STORY_SEED
- CORE_IDENTITY_PROFILE (from CORE)
- WORLD_RULES_SNAPSHOT (from WORLD)
- CHARACTER_PROFILE (from CHARACTER)
- CANON_FACTS / CANON_EVENTS
- SCENE_REQUIREMENTS
- THEME_TARGETS

### OUTPUT TYPES (typical)
- STORY_STRUCTURE_MAP
- ARC_BLUEPRINT
- SCENE_BLUEPRINT
- PACING_PLAN (story-time)
- TENSION_CURVE
- FORESHADOWING_MAP
- TWIST_REVEAL_PLAN
- CONTINUITY_MATRIX
- THEME_STATEMENT_PACK

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/02_NARRATIVE/`
- `04_PROJECTS/<project>/03_SCRIPT/`
- `04_PROJECTS/<project>/CANON/`

---

## 5) DEPENDENCY RULES

- Narrative engines могут зависеть от:
  - CORE (identity/state)
  - WORLD (законы/эпохи/ограничения)
  - CHARACTER (мотивации/арки персонажей)
  - GOVERNANCE (если нужен pipeline/решения)
- Запрещено: Narrative engines зависят от Production layer (монтаж/камера/генерация)

---

## 6) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Governance pipeline: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- Boundary: `../08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`

---

## 7) AUTHOR RULES (MANDATORY)

- Каждый движок обязан иметь mini-contract.
- В каждом движке должна быть секция “Boundaries / Not owned”.
- Любые зависимости указывать явно (DEPENDS_ON).

---

OWNER: Universe Engine
LOCK: OPEN
