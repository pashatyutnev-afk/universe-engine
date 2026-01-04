# Risk Safety Engine
FILE: 09__RISK_SAFETY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Establishes risk taxonomy and safety rails for ENG; prevents destructive canon drift, hidden coupling, unsafe cycles, and unapproved breaking changes by enforcing risk assessment and mitigation artifacts

---

## PURPOSE

Этот движок — “страховка системы”.

Он нужен, чтобы:
- мы не ломали систему незаметно
- не создавали скрытых зависимостей
- не вводили циклы без контроля
- не теряли навигацию и единый язык

---

## SCOPE (WHAT IT COVERS)

Risk Safety покрывает:
- риски при изменениях движков, README, INDEX
- риски при изменениях контрактов/выходов/входов
- риски при перестройке уровней (L1–L4)
- риски при добавлении новых семейств
- риски при разрешении dependency cycles

---

## NON-GOALS

- не утверждает канон (Canon Authority)
- не делает аудит целостности (Consistency)
- не строит dependency graph (Dependency Registry)
- не заменяет scope impact (Scope Impact)
Он задаёт “safety rules” и форму управления рисками.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Impact Reports (IR)
- Change packets (CHG)
- Consistency Reports (CR)
- Dependency graphs / cycle reports (DG/CY)
- any proposal that modifies canon

### PRODUCES
- RISK REGISTER entry (RR) — mandatory artifact when risk is non-trivial
- SAFETY RAILS decisions (what is forbidden / requires approvals)
- MITIGATION PLAN checklist
- STOP/GO safety verdict (as recommendation to Canon Authority)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

### OUTPUT_TARGET
- Used at Change Control gates G2 (impact) and before G4 (approve)
- Required before approving D3 decisions or any change with I2/I3 blast radius

---

## RISK TAXONOMY (CANON)

### R1 — Registry Risk
- INDEX drift
- broken links
- naming/number mismatch
Impact: navigation becomes false → system cannot orient.

### R2 — Contract Risk
- consumes/provides mismatch
- missing handoff
Impact: engines cannot interoperate.

### R3 — Dependency Risk
- hidden coupling
- cycle creation
Impact: unpredictable feedback loops; governance failure.

### R4 — Role Overlap Risk
- two engines claim same responsibility
Impact: agents choose different truths; canon forks.

### R5 — Level/Class Drift Risk
- L3 doing L4 behavior
- META competes with production
Impact: layer boundaries collapse.

### R6 — Terminology Risk
- same term, different meanings
- new term duplicates old
Impact: misunderstandings; inconsistent specs.

### R7 — Process Risk
- changes without CHG/CV/AUDIT
Impact: loss of traceability; “shadow canon”.

### R8 — Safety / Content Risk (system policy)
- outputs that violate safety constraints in downstream usage
Impact: unsafe generation; compliance problems.
(Для ENG это обычно “rails” про то, что не делать автоматически.)

---

## RISK LEVELS (STANDARD)

- LOW: unlikely + low impact
- MEDIUM: plausible + moderate impact
- HIGH: likely or high impact
- CRITICAL: system-wide break or irrecoverable confusion

---

## SAFETY RAILS (MANDATORY RULES)

### Rail 1 — No index drift
Запрещено:
- добавлять файл без регистрации в INDEX
- держать в INDEX ссылку на отсутствующий файл

### Rail 2 — No breaking renumber without propagation
Любая смена нумерации/переезд:
- считается MAJOR (D3)
- требует IR + CR + audit + verdict

### Rail 3 — No cycles by default
Циклы запрещены.
Разрешение только через:
- Cycle report (CY)
- governance break mechanism
- Canon Authority explicit approve

### Rail 4 — No contract changes without DG snapshot
Если меняется contract/handoff:
- обязательно обновить edges
- выдать DG snapshot
- указать consumers

### Rail 5 — No unresolved role overlap
Если overlap есть:
- назначить OWNER_OVERLAP
- прописать boundary в обоих движках
- иначе: stop condition

### Rail 6 — Waivers are temporary
Waiver:
- должен иметь expiry
- не может закрывать S0 blockers

### Rail 7 — Locked canon must be auditable
LOCK: FIXED ставится только если:
- audit запись есть
- verdict есть
- CR PASS

---

## CANON ARTIFACT: RISK REGISTER ENTRY (RR)

### RISK_REGISTER_ENTRY SCHEMA (CANON)

- RR_ID: RR-ENG-0001
- DATE:
- TRIGGER:
  - CHG_ID / IR_ID / conflict id
- SCOPE:
  - families/engines affected
- RISK_TYPE:
  - R1–R8
- RISK_LEVEL:
  - LOW | MEDIUM | HIGH | CRITICAL
- DESCRIPTION:
  - what could go wrong
- LIKELIHOOD:
  - low/med/high
- IMPACT:
  - low/med/high
- DETECTION:
  - how we will detect failure (CR/DG checks)
- MITIGATION:
  - what we will do to prevent/limit it
- OWNER:
- STATUS:
  - OPEN | MITIGATED | ACCEPTED | CLOSED
- EXPIRY (optional):
  - for accepted risks / waivers
- REFERENCES:
  - IR/CR/DG/CY/CV/AL ids as applicable

---

## WHEN RR IS REQUIRED (RULE)

Risk Register entry обязателен, если:
- IR impact level is I2 or I3
- decision level is D2 or D3
- any cycle is proposed
- any role overlap exists
- any index restructure is planned

---

## PROCEDURE (HOW TO USE RISK SAFETY)

1) Read IR (Impact Report)
2) Identify applicable risk types (R1–R8)
3) Assign risk level
4) Write RR entry if required
5) Define mitigation checklist
6) Provide STOP/GO recommendation to Canon Authority
7) Ensure Change Control gates include mitigation steps

---

## MITIGATION CHECKLIST (DEFAULT)

- M1: run registry scan (index vs files)
- M2: run contract scan (produces/consumes)
- M3: generate DG snapshot
- M4: check for cycles + write CY if needed
- M5: resolve overlaps (owner + boundary)
- M6: run terminology scan (README terms)
- M7: update audit with RR ref
- M8: lock only after PASS

---

## STOP CONDITIONS (SAFETY)

Immediate STOP (recommend REJECT/RETURN):
- index drift exists
- naming mismatch exists
- level mismatch exists
- unapproved cycle exists
- unresolved role overlap exists
- no audit/verdict for a canon change

---

## INTEGRATION NOTES

- Scope Impact produces IR → Risk Safety translates it into RR + mitigation
- Change Control requires mitigation steps before approval gate
- Consistency validates mitigations after changes
- Dependency Registry provides DG/CY support
- Canon Authority uses RR for final verdict and waivers

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
