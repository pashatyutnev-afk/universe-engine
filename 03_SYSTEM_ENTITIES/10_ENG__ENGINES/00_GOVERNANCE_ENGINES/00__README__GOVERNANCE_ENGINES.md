# GOVERNANCE ENGINES — REALM FILE (ENG FAMILY)
FILE: 00__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm boundary + navigation + rules for all governance engines (ENG layer)

---

## 0) PURPOSE (REALM LAW)

Этот REALM-файл определяет **границы и смысл** семейства `00_GOVERNANCE_ENGINES`.

GOVERNANCE-движки нужны, чтобы:
- держать **канон** в целостности (one source of truth)
- управлять **изменениями** (pipeline) и не допускать “теневой канон”
- фиксировать **историю решений** (audit/decision/memory)
- держать **инварианты** (consistency) и **граф зависимостей** (dependency registry)
- обеспечивать **безопасность изменений** (risk/scope)

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)

Семейство владеет:
- governance pipeline (как вносить изменения в канон)
- правилами согласования решений (decision levels)
- аудитом (что изменили), авторитетом (что правда), иерархией правил (что главнее)
- проверкой целостности (consistency invariants)
- реестром зависимостей (dependency graph + cycles policy)
- оценкой воздействия изменений (impact / blast radius)
- риск-рамками (safety rails)
- версионированием и памятью (release snapshots / compatibility)

---

## 2) NON-GOALS (BOUNDARIES)

GOVERNANCE НЕ делает:
- доменный контент (сцены, персонажи, мир) — это DOMAIN families
- продакшен-артефакты (видео/арт/звук) — это PRODUCTION families
- “творческое развитие системы” — это META family

GOVERNANCE только задаёт **правила игры**, порядок изменений и контроль целостности.

---

## 3) HOW TO USE (NAVIGATION)

1) Если ты хочешь **поменять канон** → начни с `04__CHANGE_CONTROL_ENG.md`.
2) Если нужно понять **кто решает** → `02__CANON_AUTHORITY_ENG.md` + `07__DECISION_APPROVAL_ENG.md`.
3) Если нужно понять **что важнее** → `03__RULE_HIERARCHY_ENG.md`.
4) Если нужно проверить **не сломали ли систему** → `05__CONSISTENCY_ENG.md`.
5) Если нужно понять **что заденет правка** → `08__SCOPE_IMPACT_ENG.md`.
6) Если нужно понять **риски и запреты** → `09__RISK_SAFETY_ENG.md`.
7) Если нужно зафиксировать **память/версии** → `10__VERSIONING_MEMORY_ENG.md`.
8) Если упёрлись в “скрытые связи” → `06__DEPENDENCY_REGISTRY_ENG.md`.
9) Любое существенное действие должно оставлять след в `01__AUDIT_LOG_ENG.md`.

---

## 4) FAMILY INDEX (CANON ORDER)

**Family Path:** `00_GOVERNANCE_ENGINES/`

01 — Audit Log Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md  
02 — Canon Authority Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md  
03 — Rule Hierarchy Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md  
04 — Change Control Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md  
05 — Consistency Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md  
06 — Dependency Registry Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md  
07 — Decision Approval Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md  
08 — Scope Impact Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md  
09 — Risk Safety Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md  
10 — Versioning & Memory Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md  

---

## 5) FAMILY INVARIANTS (CANON RULES)

- Любая канон-правка должна проходить governance pipeline (Change Control → Impact/Risk → Approve → Audit → Lock).
- Любые зависимости должны отражаться в Dependency Registry.
- Любой движок без mini-contract считается incomplete.
- Любой `LOCK: FIXED` требует audit-след и согласование.

---

## FINAL (LOCK)

OWNER: Universe Engine  
LOCK: FIXED
