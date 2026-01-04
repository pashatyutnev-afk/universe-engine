# Randomness & Chaos Engine
FILE: 09__RANDOMNESS_CHAOS_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Introduces controlled randomness and chaos into event/conflict systems without breaking causality or payoff; produces Chaos Injection Specs, Probability Budgets, Uncertainty Maps, Reproducible RNG policies, and Fairness Gates that keep outcomes surprising yet earned

---

## PURPOSE

Случайность нужна, чтобы:
- мир не выглядел “скриптом”
- повышался риск и напряжение
- появлялись неожиданные развилки

Но она опасна:
- ломает причинность
- превращается в deus ex
- убивает payoff (“повезло/не повезло”)

Движок делает случайность:
- **контролируемой**
- **справедливой**
- **воспроизводимой**
- **привязанной к риску и ограничениям**

---

## NON-GOALS

- не заменяет Cause–Effect (логика причин)
- не заменяет System Shock (масштабные каскады)
- не заменяет Scheduling (таймлайн)
Он добавляет **шум и неопределённость** поверх логики.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Event Specs (ES) and dependency graph (DG)
- Conflict Spec (CS), WLC, turning points/climax constraints
- World constraints (WLS) and capability availability
- Resource states (ERX) and environment hazards (HR/SCS)
- Governance rules (no canon break)

### PRODUCES
- CHAOS INJECTION SPEC (CIS) — canonical artifact
- PROBABILITY BUDGET (PB)
- UNCERTAINTY MAP (UM)
- RNG POLICY (RNGP) — reproducibility rules
- FAIRNESS & PAYOFF GATES (FPG)

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md
- 05_EXPRESSION_ENGINES/03__CONFLICT_ENG.md
- 05_EXPRESSION_ENGINES/05__CLIMAX_ENG.md (no deus ex)
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - event scheduling risk notes
  - conflict escalation variability
  - simulation-like world behaviors

---

## CANON TERMS

### CONTROLLED CHAOS
Случайность, которая:
- находится в заранее заданном диапазоне
- влияет на “как”, а не на “что было обещано”

### PROBABILITY BUDGET
Ограничение на то, сколько “рандома” можно вносить в участок истории.

### UNCERTAINTY MAP
Карта того, что именно неизвестно/вариативно и почему.

### RNG POLICY
Политика воспроизводимости:
- как фиксируются “семена” и условия, чтобы результат можно было повторить.

### FAIRNESS
Справедливость:
- исход неожиданен, но объясним ретроспективно
- не нарушает установленные ограничения

---

## RANDOMNESS RULES (CANON)

### RC1 — Randomness cannot decide core payoff alone
Рандом не может **сам** решать исход кульминации или основной WLC.
Он может:
- усложнить
- сместить стоимость
- поменять путь
Но не “выиграл потому что выпало 20”.

### RC2 — Randomness must bind to uncertainty sources
Случайность должна иметь источник:
- погода, трение, усталость, ошибки, шум информации, деградация техники, рынок, толпа

### RC3 — Budgeted and scoped
Рандом задаётся:
- областью влияния (scope)
- бюджетом вероятностей
- диапазоном эффектов

### RC4 — Reproducibility for canonization
Если результат стал каноном:
- он фиксируется (seed/conditions)
- чтобы не “перекидывать кубик” каждый раз

### RC5 — No constraint violations
Рандом не может:
- нарушать world laws
- создавать новые способности/ресурсы из воздуха
- отменять PNR locks

---

## CHAOS TYPES (STANDARD)

- micro-variance (малые отклонения: промах, задержка)
- info-noise (ошибки данных, слухи, дезинфа)
- environment variance (погода, поверхность, сезонные всплески)
- resource variance (поломка, дефицит, скачок цены)
- human variance (паника, ошибка, импульсивность)
- crowd variance (толпа, давка, массовые настроения)
- stochastic encounter (случайная встреча — но в допустимом пуле)

Rule:
- Prefer micro and source-based randomness; avoid “miracle randomness”.

---

## REQUIRED ARTIFACT A: CHAOS INJECTION SPEC (CIS)

### CIS SCHEMA (CANON)

Header:
- CIS_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - event | scene | episode | arc | epoch
- VERSION:
- STATUS:
  - draft | canon | deprecated

Targets:
- TARGET EVENTS / SYSTEMS:
- CHAOS TYPE(S):
- UNCERTAINTY SOURCE:
  - why randomness exists here

Control:
- IMPACT CHANNELS:
  - time | resource | info | injury | social | environment | capability-use
- MAX IMPACT (cap):
  - numeric or categorical
- MIN IMPACT:
- FORBIDDEN OUTCOMES:
  - what cannot happen (payoff breaks, constraint violations)
- COMPENSATION RULE:
  - if randomness harms, what compensates (risk-reward fairness)

Outputs:
- PB_REF
- UM_REF
- RNGP_REF
- FPG_REF

---

## REQUIRED ARTIFACT B: PROBABILITY BUDGET (PB)

### PB SCHEMA (CANON)

- PB_ID:
- CIS_ID:

Budget table (repeat):
- OUTCOME CLASS:
  - minor | moderate | severe | catastrophic
- PROBABILITY RANGE:
  - e.g. 60–80% minor, 15–30% moderate, 1–5% severe
- EFFECTS ALLOWED:
  - what it can change
- EFFECTS FORBIDDEN:
  - what it cannot change

Rule:
- Severe/catastrophic probabilities must be rare and justified by high-risk context.

---

## REQUIRED ARTIFACT C: UNCERTAINTY MAP (UM)

### UM SCHEMA (CANON)

- UM_ID:
- CIS_ID:

Uncertainties (repeat):
- UNKNOWN:
  - what is uncertain
- WHY UNKNOWN:
  - sensor limits, fog of war, chaos, market opacity
- WHO KNOWS WHAT:
  - knowledge distribution
- UPDATE MECHANISM:
  - how uncertainty resolves (time, scout, test, rumor)
- CONSEQUENCE OF WRONG ASSUMPTION:

Rule:
- If uncertainty impacts decisions, knowledge distribution must be stated.

---

## REQUIRED ARTIFACT D: RNG POLICY (RNGP)

### RNGP SCHEMA (CANON)

- RNGP_ID:
- CIS_ID:
- RNG MODE:
  - none | narrative_rng | simulation_rng
- SEED POLICY:
  - fixed seed for canon
  - variable seed for drafts
- WHEN TO ROLL:
  - only at declared injection points
- REROLL POLICY:
  - prohibited for canon
  - allowed for exploration drafts
- LOGGING:
  - where rolls are logged (Audit Log)
- TRACEABILITY:
  - conditions -> roll -> outcome recorded

Rule:
- Canon outcomes require fixed seed + logged conditions.

---

## REQUIRED ARTIFACT E: FAIRNESS & PAYOFF GATES (FPG)

### FPG SCHEMA (CANON)

- FPG_ID:
- CIS_ID:

Gates:
1) PAYOFF SAFE:
   - randomness does not decide core WLC alone
2) CONSTRAINT SAFE:
   - no world-law/capability violations
3) COST CONSISTENT:
   - any “lucky break” has a tradeoff or future cost
4) TELEGRAPHING:
   - risk was visible beforehand (setup)
5) POST EXPLAINABILITY:
   - can be explained retrospectively via sources and budgets

Rule:
- If any gate fails → CIS cannot be canonized.

---

## CANONIZATION POLICY

### Draft mode
- randomness can be explored to find interesting branches
- rerolls allowed
- logs must still exist for learning

### Canon mode
- choose one branch
- fix seed and conditions
- register outcome deltas + scars if significant

---

## “CHAOS WITHOUT CHEATING” PATTERNS

### Pattern 1: Randomness shifts cost, not result
- win still possible, but becomes more expensive

### Pattern 2: Randomness shifts path
- same destination, different route (delay, detour, new ally)

### Pattern 3: Randomness creates opportunity AND risk
- lucky opening appears, but brings exposure or debt

### Pattern 4: Uncertainty is the enemy
- not random miracles, but fog-of-war and wrong assumptions

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- randomness decides climax outcome directly
- catastrophic random event appears with no risk telegraphing
- new capability/ally appears via “luck”
- rerolls happen silently
- randomness violates time locks/PNR locks
- no PB/UM exists (“it just happens”)

Fix options:
- reduce randomness scope to micro-variance
- add risk telegraphing and setup
- cap impact ranges and move severe events into System Shock engine
- log RNG and fix seed for canon
- convert “lucky rescue” into pre-seeded dependency (ally existed earlier)

---

## PROCEDURE (HOW TO RUN)

1) Identify where unpredictability is needed (tension realism)
2) Choose chaos type and uncertainty source
3) Define PB (budget) + caps (max impact)
4) Map uncertainty (UM) and knowledge distribution
5) Set RNG policy (RNGP) for draft vs canon
6) Define fairness gates (FPG)
7) Inject at declared points only
8) If canon: lock seed + log + register deltas/scars

---

## QC CHECKLIST (MANDATORY)

- CIS declares source, scope, caps?
- PB exists and catastrophic odds are justified/rare?
- UM exists and who-knows-what is explicit?
- RNG policy defines roll points + logging?
- fairness/payoff gates pass?
- no deus ex outcomes?
- canon seed fixed and logged?

---

## VALIDATION RULES

- RCV1: Randomness is scoped, sourced, and budgeted.
- RCV2: Core payoff is protected; no random-only wins.
- RCV3: Outcomes are reproducible for canonization.
- RCV4: Surprise remains fair and explainable.

---

OWNER: Universe Engine
LOCK: FIXED
