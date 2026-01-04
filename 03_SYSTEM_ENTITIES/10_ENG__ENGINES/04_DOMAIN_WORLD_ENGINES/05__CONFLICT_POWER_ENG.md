# Conflict & Power Engine
FILE: 05__CONFLICT_POWER_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines power sources, power balances, deterrence, and conflict dynamics (drivers, escalation ladders, win conditions, persistent tensions); produces Power Maps and Conflict Ledgers that keep wars, rivalries, and faction struggles logically stable and narratively usable

---

## PURPOSE

Конфликт — это двигатель мира. Власть — топливо.
Движок нужен, чтобы:
- конфликты имели причины и устойчивость
- сила не была “по желанию автора”
- были понятны: кто сильнее, почему, и где слаб
- эскалация была логична (лестница)
- победы/поражения имели цену и последствия

---

## NON-GOALS

- не заменяет Narrative conflict engine (внутри сцен)
- не заменяет Geopolitics (карта границ/договоров)
- не заменяет Economy (учет ресурсов/логистики)
Он строит **общемировую механику силы и конфликта**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Structure Spec (WSS) (terrain, bottlenecks)
- World Law Spec (WLS) (limits, exceptions)
- Timeline/Epochs (TM/ER)
- Civilization Profiles (CP) + Network Maps (CNM)
- Tech/Magic notes (if available)

### PRODUCES
- POWER MAP (PM) — canonical artifact
- CONFLICT LEDGER (CL) — active/latent conflicts
- DETERRENCE & ESCALATION RULESET (DER)
- WIN CONDITIONS MATRIX (WCM)
- “POWER UPDATE” protocol after major events

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG.md
- 04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md

### OUTPUT_TARGET
- Feeds:
  - Geopolitics engine (treaties/borders)
  - Economy & Resource engine (war economy, chokepoints)
  - Narrative engines (stakes, tension)
  - Continuity (state changes post-conflict)

---

## CANON TERMS

### POWER SOURCE
Источник силы:
- military
- economic/logistics
- information
- legitimacy/ideology
- technology/magic
- geography/bottlenecks
- alliances
- internal cohesion

### DETERRENCE
Сдерживание: “почему они ещё не начали войну”.

### ESCALATION LADDER
Лестница эскалации:
- от давления → к войне → к тотальному уничтожению

### STABILITY LOOP
Петля устойчивости конфликта:
- причина + выгода + страх + ограничение → конфликт держится

---

## REQUIRED ARTIFACT A: POWER MAP (PM)

### PM SCHEMA (CANON)

Header:
- PM_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Actors (repeat):
- ACTOR_ID:
- TYPE:
  - state | faction | corporation | cult | network | AI | warlord
- HOME REGION/LAYER:
- POWER PROFILE:
  - MILITARY:
  - LOGISTICS:
  - INFO:
  - LEGITIMACY:
  - TECH/MAGIC:
  - ALLIANCES:
  - INTERNAL COHESION:
- KEY ASSETS:
  - choke points, fleets, archives, gates
- KEY VULNERABILITIES:
  - supply, legitimacy, succession, tech limits
- RED LINES:
  - what triggers escalation
- DETERRENCE LEVERS:
  - what prevents war with them
- “POWER SIGNATURE”:
  - how they project power (fear, charm, trade, ideology)

Scoring (optional but recommended):
- 0–5 or low/med/high per dimension
Rule:
- scoring must be consistent within epoch, not absolute “universe strength”.

---

## REQUIRED ARTIFACT B: CONFLICT LEDGER (CL)

### CL SCHEMA (CANON)

Header:
- CL_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Conflicts (repeat):
- CONFLICT_ID:
- TYPE:
  - cold | hot | insurgency | proxy | economic | ideological | resource | succession
- ACTORS:
  - primary/secondary
- ROOT CAUSE:
  - what started it
- CURRENT DRIVER:
  - what keeps it going now
- STAKES:
  - what can be lost/won
- BALANCE STATE:
  - stable | shifting | collapsing
- DETERRENCE:
  - why it isn’t total war (or why it is)
- ESCALATION STATUS:
  - step on ladder (DER link)
- WIN CONDITIONS:
  - link to WCM
- OFF-RAMPS:
  - how it could end (peace, exhaustion, collapse)
- TRIGGERS:
  - what can spike it
- CANON CONSEQUENCES:
  - if escalated, what must change

---

## REQUIRED ARTIFACT C: DETERRENCE & ESCALATION RULESET (DER)

### DER SCHEMA (CANON)

- ESCALATION LADDER (global):
  0) soft pressure (propaganda, tariffs, sabotage)
  1) coercion (raids, assassinations, sanctions)
  2) limited conflict (border war, proxy)
  3) open war (campaigns)
  4) total war (societal mobilization)
  5) existential (collapse/annihilation)

For each step:
- ENTRY CONDITIONS:
- COMMON TOOLS:
- COSTS:
- STOP CONDITIONS:
- VISIBILITY (how public it becomes)

Deterrence Model (per actor pair):
- MUTUAL COST:
- KEY RED LINES:
- RETALIATION CAPABILITY:
- ESCALATION CONTROL:
  - who can stop escalation (institutions/leaders)

Rule:
- If a conflict sits at level 3+, it must show logistics and societal cost.

---

## REQUIRED ARTIFACT D: WIN CONDITIONS MATRIX (WCM)

### WCM SCHEMA (CANON)

For each conflict type/actor:
- “WIN” definition:
  - territory | regime change | resource access | narrative legitimacy | annihilation | autonomy
- “LOSS” definition:
- ACCEPTABLE COST:
- UNACCEPTABLE COST:
- TIME HORIZON:
- THIRD-PARTY EFFECTS:
  - who benefits from prolonging

Rule:
- Win condition must be compatible with actor’s legitimacy + values (from CP).

---

## CONFLICT/POWER RULES (CANON)

### CP1 — Power is multidimensional
Нельзя “у них армия сильнее — значит выиграли”.
Всегда проверять:
- логистику
- информацию
- легитимность
- внутреннюю сплоченность
- географию

### CP2 — Conflicts persist via stability loop
Каждый долгий конфликт должен иметь:
- выгоду (хотя бы для кого-то)
- страх (deterrence)
- ограничение (law/terrain/logistics)

### CP3 — Escalation has cost and visibility
Чем выше ступень, тем:
- дороже
- заметнее
- сложнее остановить

### CP4 — Red lines must be credible
Красные линии должны:
- быть известны
- иметь ответные меры
Иначе они декоративные.

### CP5 — Off-ramps exist unless world is doom-locked
Если мир не “вечная война по закону”,
у конфликтов должны быть пути завершения.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- actor wins repeatedly without logistics
- wars start with no deterrence failure explanation
- escalation jumps from 0 to 4 with no intermediate triggers
- conflict continues with no benefit to anyone
- red lines declared but violated with no response
- win conditions contradict legitimacy/values

Fix options:
- add logistics constraints and supply lines (CNM/Economy hooks)
- define deterrence failure trigger (assassination, collapse, revelation)
- enforce ladder steps and show transition events
- assign “war profiteers” or ideological drivers
- add retaliation and consequences
- align win goals with civilization legitimacy

---

## PROCEDURE (HOW TO RUN)

1) Build Power Map for key actors
2) Define deterrence levers and red lines
3) Register conflicts in ledger with causes + drivers
4) Assign escalation ladder level + triggers
5) Define win conditions + off-ramps
6) Sync with geopolitics/economy/continuity
7) Update PM/CL after major events

---

## QC CHECKLIST (MANDATORY)

- power profiles cover at least 5 dimensions?
- deterrence exists for each major rival pair?
- each conflict has root cause + current driver?
- escalation level + triggers defined?
- win conditions compatible with legitimacy/values?
- off-ramps defined (or doom-locked declared)?

---

## VALIDATION RULES

- CPV1: PM exists and prevents “author fiat power”.
- CPV2: CL exists and explains persistence and escalation.
- CPV3: DER prevents implausible war jumps.
- CPV4: WCM makes outcomes meaningful and consistent.

---

OWNER: Universe Engine
LOCK: FIXED
