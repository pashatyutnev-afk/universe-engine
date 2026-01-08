# RISK SAFETY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.RISK_SAFETY.001>
OWNER: SYSTEM
ROLE: Safety gates + risk scoring for changes (what is forbidden to break, stop conditions, allowed risk envelopes, mitigation requirements)
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок отвечает за вопрос:
> “Насколько опасно изменение, что именно оно может сломать, и какие условия обязательны, чтобы допустить его?”

Он фиксирует:
- строгие safety правила (что запрещено ломать)
- классификацию риска и воздействия
- стоп-факторы (S0 blockers)
- обязательные mitigation действия (что сделать ДО/ВО ВРЕМЯ/ПОСЛЕ)
- решение типа: SAFE / CONDITIONAL / UNSAFE (без final approve; это рекомендация для Canon Authority)

Non-goals:
- не применяет изменения (Change Control)
- не определяет каноническую истину (Canon Authority)
- не занимается “полной проверкой консистентности” после изменений (Consistency)

---

## 1) CORE SAFETY PRINCIPLES (HARD)

### P1 — Existence rule supremacy
Если сущность/файл отсутствует в каноническом INDEX — он не существует.  
Любое изменение, нарушающее это правило (двойные источники истины), — UNSAFE.

### P2 — Entrypoint integrity
Канонические entrypoint индексы должны оставаться открываемыми и рабочими всегда.
Если правка ломает навигацию (битые raw-links / неверные пути) — S0.

### P3 — Lock discipline
LOCK: FIXED — нельзя менять без governance pipeline.
Попытка правки FIXED без протокола — S0.

### P4 — UID stability
Если UID уже выдан и объект остается тем же объектом — UID не меняется.
UID change допускается только при REPLACE/DEPRECATION с явной причиной.

### P5 — No silent dependency change
Любое изменение DEPENDS_ON обязано отражаться в Dependency Registry.
Иначе — S0.

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: CHANGE_PROPOSAL>
- <ARTIFACT: SCOPE_IMPACT_REPORT>
- <ARTIFACT: AFFECTED_FILES_LIST>
- <ARTIFACT: DEPENDENCY_DIFF?>            # before/after
- <ARTIFACT: UID_DIFF?>                   # before/after if any
- <ARTIFACT: LOCK_STATUS_DIFF?>           # fixed/open touched?

PRODUCES:
- <ARTIFACT: RISK_SAFETY_REPORT>
- <ARTIFACT: SAFETY_GATE_DECISION>        # SAFE | CONDITIONAL | UNSAFE
- <ARTIFACT: BLOCKERS_LIST>               # S0 issues (if any)
- <ARTIFACT: MITIGATION_PLAN>             # required actions
- <ARTIFACT: RISK_SCORE_CARD>             # scoring table

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG]
- [00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG]
- [00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG]
- [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG]

OUTPUT_TARGET:
- `99_LOGS/LOG__CHANGES.md` (as part of change package)

---

## 3) RISK TYPES (STRICT SET)

Allowed RISK_TYPE values:
- NAV_BREAK          # broken indexes/raw-links/entrypoints
- UID_CORRUPTION     # UID instability, duplicates, invalid formats
- AUTHORITY_CONFLICT # two “truth sources”, conflicting indexes
- DEPENDENCY_DRIFT   # hidden or unrecorded dependency change
- LOCK_VIOLATION     # fixed changed without pipeline
- DATA_MODEL_DRIFT   # DB/entity types drift without registry
- MIGRATION_GAP      # rename/move without mapping + link updates
- BACKWARD_BREAK     # deprecations without replacement path
- HUMAN_ERROR_RISK   # unclear steps / ambiguous instructions

---

## 4) RISK LEVELS + DECISION

### 4.1 Risk level (L0..L4)
- L0: trivial, local, no cross-effects
- L1: low, contained, easy rollback
- L2: medium, cross-family or touches templates/standards
- L3: high, touches indexes/registries/UID rules
- L4: critical, touches core laws/entrypoints/multiple layers

### 4.2 Decision (strict)
- SAFE:
  - no S0 blockers
  - risk <= L1 OR L2 with full mitigation
- CONDITIONAL:
  - no S0 blockers
  - risk L2..L3 BUT mitigation mandatory + explicit checklist
- UNSAFE:
  - any S0 blocker present
  - OR risk L4 without staged migration & rollback strategy

---

## 5) S0 BLOCKERS (ABSOLUTE STOP)

If any is true → UNSAFE (cannot proceed):

S0-1: Any canonical entrypoint/index has broken path or broken raw-link
S0-2: Fixed (LOCK: FIXED) file changed outside governance pipeline package
S0-3: UID duplication detected or UID format violated for existing canon entities
S0-4: Dependency changed but no dependency registry record is planned
S0-5: Rename/Move/Delete without MIGRATION_MAP + required updates list
S0-6: Authority conflict: two indexes claim different existence for same entity
S0-7: Deletion of canon entity without DEPRECATED replacement route

---

## 6) RISK SCORING (STANDARD)

Score dimensions (0..3 each):
- D1: Scope size (how many files/layers)
- D2: Entrypoint touch (indexes/registries)
- D3: UID impact
- D4: Dependency impact
- D5: Lock sensitivity (fixed touched)
- D6: Migration complexity (rename/move/delete)

Total risk score:
- 0–4  => L0
- 5–7  => L1
- 8–11 => L2
- 12–15 => L3
- 16–18 => L4

Rule:
- If any S0 blocker exists → ignore scoring → UNSAFE.

---

## 7) REQUIRED MITIGATION ACTIONS (CHECKLIST)

### M1 — Pre-change snapshot
- list of affected files + copy/commit id (or equivalent)

### M2 — Migration map if structure changes
- OLD_PATH → NEW_PATH mapping
- link update list

### M3 — Registry/index updates
- ensure all referenced indexes updated
- ensure existence rule satisfied

### M4 — Dependency registry updates
- add required registry records in standard format

### M5 — Rollback plan
- what to revert
- what breaks if partial rollback

### M6 — Post-change validation
- run Consistency Engine
- verify entrypoints open and raw-links resolve

---

## 8) OUTPUT FORMAT (STANDARD)

### 8.1 RISK_SAFETY_REPORT (REQUIRED)
FORMAT:

- REPORT_ID: <UE.RISK.YYYY-MM-DD.NNN>
- DATE:
- AUTHOR:
- CHANGE_ID:
- IMPACT_CLASS: <from scope report>
- DECISION: <SAFE|CONDITIONAL|UNSAFE>
- RISK_LEVEL: <L0..L4>

- BLOCKERS (S0):
  - (if none) []

- RISK_SCORE_CARD:
  - D1:
  - D2:
  - D3:
  - D4:
  - D5:
  - D6:
  - TOTAL:

- RISK_TYPES:
  - - NAV_BREAK
    - DEPENDENCY_DRIFT
    ...

- MITIGATION_PLAN (required):
  - M1: ...
  - M2: ...
  - M3: ...
  - M4: ...
  - M5: ...
  - M6: ...

- NOTES:

### 8.2 SAFETY_GATE_DECISION (REQUIRED)
One line:
`DECISION: SAFE|CONDITIONAL|UNSAFE`

---

## 9) REL / XREF (UID-FIRST)

REL:
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.001> | WHY: safety gates define required mitigation before apply
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CANON_AUTHORITY.001> | WHY: authority uses safety decision recommendation
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CONSISTENCY.001> | WHY: post-change validation is required mitigation
- REL: USES | TARGET_UID: <UE.ENG.GOV.DEPENDENCY_REGISTRY.001> | WHY: dependency drift is S0 blocker

--- END.
