# SCOPE IMPACT ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.SCOPE_IMPACT.001>
OWNER: SYSTEM
ROLE: Computes change blast-radius (what breaks/what must be updated across layers, indexes, registries, dependencies, raw-links)
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок отвечает за вопрос:
> “Если мы поменяем X — что ещё обязаны поменять, чтобы система осталась живой?”

What this engine is for:
- оценка влияния изменений (blast-radius)
- классификация влияния: local → cross-family → cross-layer → global
- выявление обязательных вторичных правок (индексы, реестры, raw-links, зависимости)
- выдача Scope Impact Report, который Change Control и Canon Authority используют для решения

Primary outcome:
- перед применением крупной/структурной правки существует Scope Impact Report с полным списком “что затронуто” и “что обновить”.

Non-goals:
- не решает approve/reject (Canon Authority)
- не делает сам изменения (Change Control)
- не логирует вместо Audit Log (но требует audit для канон изменений)

---

## 1) BOUNDARY (ANTI-DUPLICATION)

Owned here:
- анализ радиуса изменений
- mapping “affected → required updates”
- impact classification + required artifacts
- список обязательных задач на фиксы

Not owned here:
- решение (approve)
- применение правки
- глубокая проверка целостности (это Consistency; scope только прогнозирует)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: CHANGE_PROPOSAL>
- <ARTIFACT: CHANGE_NOTE>                 # summary/reason/impact
- <ARTIFACT: AFFECTED_FILES_LIST>
- <ARTIFACT: DEPENDS_ON_DECLARATIONS?>    # if dependencies involved
- <ARTIFACT: INDEX_ENTRYPOINTS?>          # list of canonical indexes/entrypoints
- <ARTIFACT: RAW_LINKS_LIST?>             # extracted raw links (optional)
- <ARTIFACT: STORAGE_MAPS?>               # optional: where outputs live

PRODUCES:
- <ARTIFACT: SCOPE_IMPACT_REPORT>         # main output
- <ARTIFACT: REQUIRED_UPDATES_LIST>       # actionable list
- <ARTIFACT: IMPACT_CLASSIFICATION>       # LOCAL/CROSS_FAMILY/CROSS_LAYER/GLOBAL
- <ARTIFACT: MIGRATION_MAP?>              # for rename/move (OLD→NEW)
- <ARTIFACT: ROLLBACK_HINTS?>             # what rollback must cover

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG]
- [00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG]
- [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG]

OUTPUT_TARGET:
- `99_LOGS/LOG__CHANGES.md` (as part of change package)

---

## 3) IMPACT CLASSIFICATION (STRICT SET)

Allowed IMPACT_CLASS values:
- LOCAL            # inside one file or one family, no index/raw-link updates required
- CROSS_FAMILY     # affects multiple engines within ENG layer families
- CROSS_LAYER      # affects more than one layer (e.g. standards + entities + KB)
- GLOBAL           # affects root entrypoints, global master index, naming/uid rules, or multiple layers + registries

Rule:
- If any fixed index is affected → minimum CROSS_LAYER.
- If global entrypoint index changes → GLOBAL.

---

## 4) IMPACT DOMAINS (WHAT IT LOOKS AT)

### I1 — Index/Registry impact
- Does any canonical index reference a changed path?
- Do we need to update raw-links?
- Does existence rule change what "exists"?

### I2 — Naming/Numbering impact
- Are file names changing?
- Does numbering change break ordering rules?

### I3 — UID impact
- Are UIDs introduced/changed?
- Do UID rules require reformatting across files?

### I4 — Dependency impact
- Does DEPENDS_ON change?
- Does dependency registry need updates?
- Are cycles introduced?

### I5 — Storage/Output impact
- Does OUTPUT_TARGET move?
- Do storage maps need update?

### I6 — Cross-layer entrypoint impact
- Does global master index / layer entrypoint index need update?

---

## 5) HARD GATES (ENFORCEMENT)

- G1: Concrete affected list required  
  If missing → scope report cannot be produced (FAIL)

- G2: Rename/move must produce migration map  
  If CHANGE_TYPE is MOVE/RENAMING and no OLD→NEW mapping → FAIL

- G3: Index touch implies required updates  
  If affected includes any INDEX file and required updates list is empty → FAIL

- G4: Dependency change implies registry update  
  If DEPENDS_ON changes and no dependency updates in required list → FAIL

- G5: Global entrypoints must be listed  
  If impact is CROSS_LAYER/GLOBAL and no entrypoint list included → FAIL

---

## 6) OUTPUT FORMAT (STANDARD)

### 6.1 SCOPE_IMPACT_REPORT (REQUIRED)
FORMAT:

- REPORT_ID: <UE.SCOPE.YYYY-MM-DD.NNN>
- DATE:
- AUTHOR:
- CHANGE_ID: <ref if exists>
- CHANGE_TYPE:
- IMPACT_CLASS: <LOCAL|CROSS_FAMILY|CROSS_LAYER|GLOBAL>

- PRIMARY_AFFECTED:
  - ITEM: <DOC|INDEX|TEMPLATE|ENGINE|REGISTRY|MAP>
    PATH:
    UID: <optional>

- SECONDARY_AFFECTED (predicted):
  - ITEM:
    PATH:
    WHY:

- REQUIRED_UPDATES (actionable):
  - U1: <action> | TARGET:<path or entity> | WHY:<reason> | SEVERITY:<S0..S3>
  - U2: ...
  - U3: ...

- MIGRATION_MAP (if rename/move):
  - OLD_PATH: ...
    NEW_PATH: ...
    NOTES:

- DEPENDENCY_IMPACT:
  - ADDED:
  - REMOVED:
  - CHANGED:
  - REQUIRED_REGISTRY_RECORDS:

- RAW_LINK_IMPACT:
  - LINKS_TO_UPDATE:
  - LINKS_AT_RISK:

- ROLLBACK_HINTS:
  - What must be reversible:
  - What breaks if rollback incomplete:

- NOTES:

### 6.2 REQUIRED_UPDATES_LIST (REQUIRED)
Ordered:
1) S0 blockers first (index/raw link breaks)
2) dependency registry updates
3) UID/naming fixes
4) optional improvements

---

## 7) EXAMPLES (GOOD / BAD)

### 7.1 Good example
Change:
- MOVE: переименовали файл семейства ENG + обновили index.
Scope report shows:
- migration map old→new
- required updates: update raw link in index + update dependency records referencing old name

### 7.2 Bad example
Change:
- DELETE: удалили engine file
Scope report missing:
- which indexes reference it
- rollback hints
Result:
- FAIL (G1/G3), cannot proceed.

---

## 8) REL / XREF (UID-FIRST)

REL:
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.001> | WHY: scope report is required for sensitive changes
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CANON_AUTHORITY.001> | WHY: authority uses blast-radius
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CONSISTENCY.001> | WHY: consistency verifies after apply
- REL: USES | TARGET_UID: <UE.ENG.GOV.DEPENDENCY_REGISTRY.001> | WHY: dependency impacts must be recorded

--- END.
