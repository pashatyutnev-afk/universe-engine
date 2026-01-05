# ENG DOMAIN CHARACTER ENGINES — REALM (FAMILY README)
FILE: 00__README__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for Character domain engines

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY владеет **персонажной системой**: кто персонаж, чего он хочет, что им движет,
как он думает/чувствует/действует, как строит отношения, как звучит его речь,
как он растёт или ломается, и как его изменения фиксируются в каноне.

Character domain отвечает за:
- ядро персонажа (идентичность/ценности/границы)
- мотивации, желания, страхи, цели
- мораль, ценностные конфликты, внутренние запреты
- психологию и поведенческие паттерны
- отношения и динамику между персонажами
- диалоги, речь, “натуральность” голоса
- травмы, рост, деградацию, трансформацию
- эволюцию персонажа во времени

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)

### THIS FAMILY OWNS
- Character identity model (who they are)
- Motivation & desire (what they want / why)
- Values / morals / principles (what they won’t do)
- Psychology & behavior (how they operate)
- Relationship dynamics (how they attach / conflict / bond)
- Dialogue + voice consistency (how they speak)
- Trauma / growth (why they change)
- Character evolution tracking (how change is recorded)

### THIS FAMILY DOES NOT OWN
- Сюжетная архитектура сцен/арок/ритма истории (это `02_DOMAIN_NARRATIVE_ENGINES`)
- Мир/экономика/технологии/эпохи как внешние законы (это `04_DOMAIN_WORLD_ENGINES`)
- Формат выпуска (книга/сериал/игра) (это `07_PRODUCTION_FORMAT_ENGINES`)
- Монтаж/камера/арт/продакшн (это `08_KNOWLEDGE_PRODUCTION_ENGINES`)
- Governance pipeline (это `00_GOVERNANCE_ENGINES`)

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### Character Motivation vs Story Causality
- Мотивации/внутренние причины принадлежат Character domain
- Причинно-сюжетные связи сцен/событий принадлежат Narrative domain

### Dialogue vs Editing / Performance
- Текст и структура реплик — Character domain
- Актёрская подача / монтаж / тайминги — Production layer

---

## 3) CANON ORDER (MANDATORY)

Порядок внутри `03_DOMAIN_CHARACTER_ENGINES` строгий:

01 — Character Core Engine  
02 — Motivation & Desire Engine  
03 — Moral & Value Engine  
04 — Character Psychology Engine  
05 — Character Behavior Engine  
06 — Relationship Engine  
07 — Dialogue Engine  
08 — Speech Naturalization Engine  
09 — Growth & Trauma Engine  
10 — Character Evolution Engine  

---

## 4) INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- CHARACTER_SEED
- ROLE_IN_STORY (from Narrative)
- WORLD_CONSTRAINTS_SNAPSHOT (from World)
- CANON_FACTS (existing)
- SCENE_CONTEXT (optional)
- THEME_TARGETS (optional)

### OUTPUT TYPES (typical)
- CHARACTER_PROFILE
- MOTIVATION_MAP
- VALUES_MORAL_MATRIX
- PSYCHOLOGICAL_MODEL
- BEHAVIOR_RULESET
- RELATIONSHIP_MAP
- DIALOGUE_VOICE_GUIDE
- SPEECH_STYLE_PACK
- TRAUMA_GROWTH_ARC
- CHARACTER_EVOLUTION_LOG

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/01_CHARACTERS/`
- `04_PROJECTS/<project>/CANON/CHARACTERS/`

---

## 5) DEPENDENCY RULES

- Character engines могут зависеть от:
  - CORE (identity/state layer)
  - WORLD (законы/ограничения среды)
  - NARRATIVE (роль в истории как входной контекст)
- Запрещено:
  - зависеть от Production layer (монтаж/камера/генерация)
  - “тайно” менять факты канона без фиксации в governance

---

## 6) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Narrative family: `../02_DOMAIN_NARRATIVE_ENGINES/`
- World family: `../04_DOMAIN_WORLD_ENGINES/`
- Governance pipeline: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`

---

## 7) AUTHOR RULES (MANDATORY)

- Каждый движок обязан иметь mini-contract.
- В каждом движке должна быть секция “Boundaries / Not owned”.
- Любые зависимости указывать явно (DEPENDS_ON).
- Результаты Character domain не переписывают канон “молча”.

---

OWNER: Universe Engine
LOCK: OPEN
