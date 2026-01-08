# GOVERNANCE ENGINES — REALM README (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: REALM_README
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.GOV.REALM.001
OWNER: SYSTEM
ROLE: Family scope law + boundaries + mandatory governance workflow + quality bar

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "Normalized governance realm: UID assigned, header standardized, RAW-only references, removed footer duplicates."
- REASON: "Align governance docs with marking standards + raw-only navigation rule."
- IMPACT: "Governance family becomes fully compliant with Doc Control + navigation rules."
- CHANGE_ID: UE.CHG.2026-01-08.001

---

## 0) PURPOSE (LAW)

Это REALM README семейства `00_GOVERNANCE_ENGINES`.

Он фиксирует:
- границы семейства governance (что делает / чего не делает)
- обязательный пайплайн для изменений канона
- обязательные стандарты качества для движков family
- правило: канонический состав/порядок движков хранится только в `02__INDEX_ALL_ENGINES.md`

IMPORTANT:
- Canon roster/order живёт в `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md` (raw-link в REFERENCES).
- Здесь любые списки — только reference и не создают “существование”.

---

## 1) SCOPE — WHAT THIS FAMILY OWNS

Governance family owns:
- Audit logging (фиксировать факт изменений)
- Canon authority (решение accept/reject)
- Rule hierarchy (кто побеждает при конфликте правил)
- Change control (пайплайн изменения)
- Consistency inspection (диагностика конфликтов/битых ссылок/нарушений стандартов)
- Dependency registry (реестр зависимостей)
- Decision approval (процедуры апрувов)
- Scope impact (blast-radius анализа)
- Risk safety (safety gates / blockers)
- Versioning & memory (версионирование + память изменений)

Governance family strictly does NOT own:
- доменный контент (сюжет/персонажи/мир)
- production outputs (визуал/видео/монтаж/звук как медиа)
- deep music composition (это семейство 09)

---

## 2) FAMILY BOUNDARIES (ANTI-DUP)

### 2.1 Governance stops here
Governance определяет правила, контроль, записи, решения и проверку целостности — но не создаёт “контент вселенной”.

### 2.2 Overlaps to avoid
- QA/VAL не дублируем: governance может требовать отчёты, но не подменяет валидаторы.
- PRJ слой не дублируем: governance задаёт рамки, но не ведёт проектные сущности вместо PRJ.

### 2.3 Conflict resolution (mandatory)
Если 2 документа/движка конфликтуют:
1) применяем Rule Hierarchy (03)
2) фиксируем Change Package (04)
3) принимаем решение (02 + при необходимости 07)
4) обязательно Audit (01)
5) проверка Consistency (05)
6) фиксируем Versioning/Memory (10)

---

## 3) MANDATORY GOVERNANCE WORKFLOW (CANON CHANGE)

Default pipeline:
1) S0 PROPOSE (Change Control)
2) S1 PRE-CHECK (Change Control + Consistency checks as needed)
3) S2 DECISION (Canon Authority + Decision Approval if required)
4) S3 APPLY (Change Control records application)
5) S4 AUDIT (Audit Log mandatory)
6) S5 POST-VERIFY (Consistency mandatory)
7) S6 CLOSE + MEMORY (Versioning & Memory)

Hard rule:
- No canon change is considered complete without DECISION + AUDIT + POST-VERIFY PASS.

---

## 4) TEMPLATES (MANDATORY)

- Engine template:
  `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md`
- README template:
  `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__README__GOVERNANCE_ENGINES.md`

---

## 5) FAMILY QUALITY BAR (WHAT “DONE” MEANS)

Governance engine считается “готовым”, только если:
- header: полный Doc Control + CHANGE_NOTE
- mini-contract: CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET
- минимум 5 hard gates
- есть good/bad examples
- есть failure modes / edge cases
- зависимости прозрачны + отражаются в dependency registry при изменениях
- изменения канона → Audit record обязательно

---

## 6) REFERENCES (RAW ONLY)

ENG INDEX (canon roster/order):
- UE.ENG.INDEX.ALL_ENGINES — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

GOVERNANCE engines:
- UE.ENG.GOV.AUDIT_LOG.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- UE.ENG.GOV.CANON_AUTHORITY.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- UE.ENG.GOV.RULE_HIERARCHY.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
- UE.ENG.GOV.CHANGE_CONTROL.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- UE.ENG.GOV.CONSISTENCY.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- UE.ENG.GOV.DEPENDENCY_REGISTRY.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- UE.ENG.GOV.DECISION_APPROVAL.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md
- UE.ENG.GOV.SCOPE_IMPACT.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md
- UE.ENG.GOV.RISK_SAFETY.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md
- UE.ENG.GOV.VERSIONING_MEMORY.001 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

--- END.
