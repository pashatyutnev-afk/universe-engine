# NARRATIVE CRAFT (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/01_NARRATIVE_CRAFT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: NARRATIVE_CRAFT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.NARRATIVE.101
OWNER: SYSTEM
ROLE: Knowledge realm for narrative craft: story structure, arcs, pacing, themes, scene logic, continuity, and narrative constraints. Provides methods and rules; does not replace entity passports.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован realm Narrative: добавлен Doc Control header + каркас разделов + правила no-dup и UID-first"
- REASON: "Realm должен быть каноническим документом и читаться как методология"
- IMPACT: "All narrative knowledge placement"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | KB entity vs knowledge rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.SPEC.SCENE_4TRACK.105 | references | scene structure standard | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md

---

## 0) PURPOSE
Этот realm хранит **методики и правила повествования**:
- структура истории и арок
- причинно-следственная логика
- темп/пейсинг
- драматургические инструменты
- continuity и ограничения мира

Realm НЕ хранит паспорта сущностей.
Все сущности описываются паспортами в `04_KNOWLEDGE_BASE/10_ENTITIES/*` и связываются UID-first.

---

## 1) CORE PRINCIPLES (SoT внутри realm)
- Причина → следствие важнее “красивых сцен”
- Каждая сцена меняет состояние (мира/персонажа/отношений)
- Конфликт должен быть проверяемым (видимым в действиях)
- Темп строится управлением “плотности событий” и “информационного давления”

---

## 2) STORY STRUCTURE (MODELS)
### 2.1 Arc / Season / Episode models
- Model list (expand):
  - 3-act
  - 5-act
  - hero’s journey
  - mystery spiral
  - escalation ladder

### 2.2 Beats (beat sheets)
- Beat definition
- Beat types
- Beat density rules

---

## 3) SCENE LOGIC (CAUSE/EFFECT)
### 3.1 Scene purpose contract
Каждая сцена должна иметь:
- цель (goal)
- препятствие (obstacle)
- действие (action)
- изменение (delta)

### 3.2 Scene delta types
- information delta
- relationship delta
- power delta
- location delta
- capability delta

---

## 4) PACING (TEMPO CONTROL)
- compression vs expansion
- tension waves
- micro-beats inside scenes
- silence as tool (negative space)

---

## 5) THEME & MEANING
- theme statement
- motif system
- symbol economy (no-overuse)

---

## 6) CONTINUITY & CONSISTENCY
### 6.1 Continuity checklist
- timeline coherence
- geography consistency
- tech/rules consistency
- character intent consistency

### 6.2 Retcon policy (within narrative)
- when retcon allowed
- how to mark retcon as knowledge (XREF to affected entities/scenes)

---

## 7) WORLD CONSTRAINTS (NARRATIVE-LEVEL)
- hard constraints from system/world laws
- “forbidden moves” (things that break the world contract)

---

## 8) LINKING TO ENTITIES (UID-FIRST)
Если правило ссылается на конкретную сущность/событие/локацию:
- использовать XREF на ENTITY_UID (или SCENE_UID, если сцена вынесена как объект)

Pattern:
XREF:
- XREF: <ENTITY_UID> | references | "example / usage" | <passport-path(optional)>

---

## 9) EXAMPLES (OPTIONAL)
> Здесь храним примеры применения методов.
> Каждый пример должен ссылаться UID-first на сущности/сцены, если они внутренние.

---

## 10) OPEN QUESTIONS / TODO (OPTIONAL)
- (list)

--- END.
