# Economy & Resource Engine
FILE: 07__ECONOMY_RESOURCE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Models resources, production, scarcity, logistics, incentives (optional economy/no-currency mode supported)

---

## PURPOSE

Моделирует ресурсы и стимулы.
ВАЖНО: движок поддерживает режимы:
- **NO-CURRENCY** (у вас канон: великие цивилизации без валюты)
- LIMITED-CURRENCY (локально)
- FULL ECONOMY (если когда-то надо)

---

## INPUTS

- Civilization profiles
- Environment constraints
- Tech/magic rules
- World structure (routes)

---

## OUTPUTS

- Resource Map (что где)
- Production & logistics model
- Scarcity pressure list
- Incentive model per actor
- Vulnerable supply chains

---

## CANONICAL RESOURCE MODEL

Resources:
- energy / food / materials / labor / info / tech / magic reagents / territory

For each:
- source
- extraction/production cost
- transport/logistics constraints
- substitution options
- chokepoints
- conflict potential

---

## NO-CURRENCY MODE (CANON)

Instead of money:
- ALLOCATION RIGHTS (кто распределяет)
- QUOTAS / CREDITS (не валюта, а лимит доступа)
- DEBT OF SERVICE (обязательства)
- STATUS ACCESS (ранг → доступ)
- CONTRACTS OF TRUST (социальные гарантии)

---

## PROCEDURE

1) List key resources (5–15)
2) Map production and flow (routes)
3) Identify chokepoints + dependencies
4) Determine scarcity pressures
5) Define incentive logic by civilization:
   - what they maximize (security, growth, stability, faith, control)
6) Output conflict hooks (resource wars / sabotage / embargo)

---

## VALIDATION RULES

- ER1: Дефицит создаёт поведение.
- ER2: Логистика — король (если что-то далеко, это цена).
- ER3: В no-currency режиме стимулы всё равно есть (доступ/власть/обязательства).
- ER4: Ресурсы должны влиять на геополитику.

---

## FAILURE MODES

- ресурсы не влияют ни на что
- “всё есть везде”
- экономика ломает канон no-currency

---

## INTEGRATION

- With GEOPOLITICS_ENG: зависимости и рычаги
- With CONFLICT_POWER_ENG: ресурс → эскалация
- With TECHNOLOGY_MAGIC_ENG: ресурсы как топливо технологий/магии

---
OWNER: Universe Engine
STATUS: FIXED
