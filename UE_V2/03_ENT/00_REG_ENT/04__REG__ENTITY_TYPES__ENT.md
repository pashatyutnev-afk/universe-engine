FILE: UE_V2/03_ENT/00_REG/04__REG_ENTITY_TYPES.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REG_SCHEMA
DOMAIN: REG
UID: UE.V2.REG.ENTITY_TYPES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — ENTITY TYPES (Schema)

PURPOSE:
Определяет типы сущностей и минимальные поля, чтобы любая сущность была машиночитаемой и совместимой.

---

## CANON ENTITY PASSPORT (fields)

REQUIRED:
- UID
- NAME
- TYPE (SPC|ENG|ORC|CTL|VAL|QA|XREF|SYS|PIPE|KB|NAV|REG)
- SCOPE
- STATUS
- VERSION
- MODE (USAGE-ONLY|EDIT-ALLOWED)
- INPUTS (list)
- OUTPUTS (list)
- RULES (constraints)
- GATES (PASS/STOP/GAP)
- KB_SCOPE (inputs/outputs/boundaries)

OPTIONAL:
- DEFAULTS
- FAILURE_MODES
- EXAMPLES
- NOTES

---

## TYPE PROFILES (minimal intent)

| TYPE | CORE ROLE | MUST INCLUDE |
|---|---|---|
| SPC | постановка и критерии | success criteria, constraints, acceptance gates |
| ENG | генерация/преобразование | transformation rules, output format guarantees |
| ORC | оркестрация шагов | step plan, handoff rules, merge strategy |
| CTL | ограничения/политики | forbidden actions, guardrails, compliance checks |
| VAL | проверка | validation checklist, fail codes |
| QA | качество | test scenarios, defect taxonomy |
| XREF | связи | mapping rules, cross-reference format |
| PIPE | маршрут исполнения | step-run contract, required keys, orchestration rules |
| KB | знания | scope/boundaries, update policy |
| REG | реестры | append-only rules, collision policy |
| NAV | навигация | index manifest rules, keyspace |

---

## COMPATIBILITY RULE
- Любая сущность должна быть понятна без ссылок внутри неё.
- Адреса и навигация — задача NAV/REG через INDEX_MANIFEST.
