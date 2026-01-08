# RULE HIERARCHY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.RULE_HIERARCHY.001>
OWNER: SYSTEM
ROLE: Defines rule precedence (who wins conflicts) and publishes canonical hierarchy records used by consistency and change control
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок задаёт **порядок силы правил**: что имеет приоритет при конфликте документов/стандартов/индексов/протоколов.

What this engine is for:
- фиксировать **Rule Precedence Map** (иерархию)
- стандартизировать формат “precedence record”
- дать Consistency Engine и Change Control Engine понятный механизм разрешения конфликтов

Primary outcome:
- существует каноническая иерархия, по которой можно однозначно определить “кто прав”.

Non-goals (hard):
- НЕ принимает решение approve/reject (это Canon Authority)
- НЕ выполняет проверку документов на ошибки (это Consistency Engine)
- НЕ заменяет индексы (не делает existence map слоёв)

---

## 1) BOUNDARY (ANTI-DUPLICATION)

### 1.1 Owned area
- правило: “при конфликте используем hierarchy map”
- структура уровней authority (например: system law > standards > entity registries > KB > projects)
- формат precedence map record

### 1.2 Forbidden overlap
- не владеет audit логированием (Audit Log)
- не владеет процессом изменений (Change Control)
- не владеет оценкой рисков (Risk Safety)

### 1.3 Interfaces
- Inputs: список authoritative entrypoints + их declared roles
- Outputs: precedence map record
- Consumers: Consistency Engine, Change Control, Canon Authority (как reference)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: LAYER_ENTRYPOINTS_LIST>        # список слоёв и их entrypoints (индексы)
- <ARTIFACT: SYSTEM_LAW_PRIORITY>           # приоритет внутри 01_SYSTEM_LAW (если есть)
- <ARTIFACT: STANDARDS_PRIORITY?>           # приоритет стандартов/спеков (если есть)
- <ARTIFACT: EXCEPTION_NOTES?>              # список исключений (если разрешены)

PRODUCES:
- <ARTIFACT: RULE_PRECEDENCE_MAP>           # основной результат: карта приоритетов
- <ARTIFACT: PRECEDENCE_RECORD>             # запись/версия карты (append-style)

DEPENDS_ON:
- []  # минимальная зависимость; может ссылаться на SYSTEM_LAW как источник

OUTPUT_TARGET:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md` (this doc)
- + optional shared storage for maps (if you have one): `99_LOGS/LOG__CHANGES.md` or registry area

---

## 3) PRECEDENCE MODEL (CORE)

### 3.1 Precedence levels (default L0..L5)
- L0: SYSTEM LAW (core laws / UID rules / canon protocol)
- L1: STANDARDS (doc control, marking, index structure, protocols)
- L2: SYSTEM ENTITIES REGISTRIES (ENG/ORC/SPC/CTL/VAL/QA registries)
- L3: KNOWLEDGE BASE (methods/knowledge; non-binding unless elevated by law)
- L4: PROJECTS (production usage; local overrides must be declared)
- L5: OUTPUT/ASSETS (deliverables; must comply with upstream constraints)

Rule:
- Higher level overrides lower on conflict.
- Same level conflicts must be resolved by “within-level order” (see 3.2).

### 3.2 Within-level order (default)
Each level must define internal order. Examples:
- L0 (System Law): index / core law / canon protocol / versioning policy / uid rules / constraints / schema registry / pipeline registry
- L1 (Standards): doc control standard > index structure spec > rel/xref policy > templates
- L2 (Registries): global registries > family registries > instance docs

If internal order is unknown:
- produce PRECEDENCE_RECORD with a “GAP” and require Change Control decision.

### 3.3 Exception policy (strict)
Exceptions are allowed only if:
- explicitly listed in EXCEPTION_NOTES
- have WHY and SCOPE
- have an expiry condition (optional)
- are audited when used in canon decisions

---

## 4) OPERATION MODEL (HOW IT WORKS)

### 4.1 Trigger
Run when:
- a new layer index is introduced or renamed
- authority definitions change (system law or standards)
- exception policy changes
- major restructure occurs

### 4.2 Steps
1) Collect entrypoints + their declared roles
2) Normalize them into L0..L5 levels
3) Define internal order within each level
4) Validate for contradictions (hard gates)
5) Publish RULE_PRECEDENCE_MAP + PRECEDENCE_RECORD (versioned)

---

## 5) HARD GATES (ENFORCEMENT)

- G1: No ambiguous top authority  
  CHECK: L0 exists and has at least one core law entrypoint  
  FAIL: no top authority → STOP (cannot build map)

- G2: Each level must have at least one anchor (or marked empty)  
  CHECK: L1..L5 either have entries or explicit EMPTY marker  
  FAIL: implicit missing → require change control

- G3: Internal order must be explicit OR declared GAP  
  CHECK: within-level precedence is defined  
  FAIL: silent ambiguity → mark GAP + require decision

- G4: Exception list must be explicit and justified  
  CHECK: every exception has WHY + SCOPE  
  FAIL: exceptions without why → reject exceptions from map

- G5: Map determinism  
  CHECK: given two conflicting docs, map can always tell which wins (or yields GAP explicitly)  
  FAIL: silent nondeterminism → not allowed

---

## 6) OUTPUT ARTIFACTS (STANDARD FORMS)

### 6.1 RULE_PRECEDENCE_MAP (REQUIRED)
FORMAT (Markdown):

- MAP_ID: <UE.RULEMAP.YYYY-MM-DD.NNN>
- DATE:
- AUTHOR:
- LEVELS:
  - L0: [<entrypoints>]
  - L1: [<entrypoints>]
  - L2: [<entrypoints>]
  - L3: [<entrypoints>]
  - L4: [<entrypoints>]
  - L5: [<entrypoints>]
- WITHIN_LEVEL_ORDER:
  - L0: <ordered list or GAP>
  - L1: <ordered list or GAP>
  - ...
- EXCEPTIONS:
  - EXC: <name> | SCOPE:<...> | WHY:<...> | RULE:<what overrides what>
- NOTES:
- STATUS: ACTIVE

### 6.2 PRECEDENCE_RECORD (APPEND STYLE)
- RECORD_ID:
- MAP_ID:
- CHANGE_TYPE:
- SUMMARY:
- REASON:
- IMPACT:

---

## 7) EXAMPLES (GOOD / BAD)

### 7.1 Good example
Conflict:
- A KB doc says “X is allowed”
- System Law says “X is forbidden”
Result:
- L0 overrides L3 → System Law wins, KB statement becomes non-binding.

### 7.2 Bad example
Conflict:
- Two standards both claim “highest priority”
- No within-level order given
Result:
- Must produce GAP + require Change Control decision; cannot silently pick.

---

## 8) FAILURE MODES & EDGE CASES

- Layer temporarily missing (in progress)  
  → allowed only if explicitly marked EMPTY in map and treated as non-authoritative.

- Historical docs in repo  
  → treated as non-authoritative unless indexed as canon.

- “One-folder/one-index law” per layer  
  → belongs to layer indexes; precedence engine only says which index beats which if conflict.

---

## 9) REL / XREF (UID-FIRST)

REL:
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CONSISTENCY.###> | WHY: consistency needs precedence rules to resolve conflicts
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.###> | WHY: change control uses hierarchy to plan conflict resolution
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CANON_AUTHORITY.001> | WHY: authority decisions reference precedence map
- REL: COORDINATES | TARGET_UID: <UE.ENG.GOV.AUDIT_LOG.001> | WHY: precedence map changes should be audited (externally)

XREF:
- XREF_UID: <01_SYSTEM_LAW/00__SYSTEM_LAW.md> | WHY: top authority content source
- XREF_UID: <01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md> | WHY: law registry order reference

RULE:
- RAW links — in registries/indexes.
- This engine doc is UID-first and publishes map format only.

--- END.
