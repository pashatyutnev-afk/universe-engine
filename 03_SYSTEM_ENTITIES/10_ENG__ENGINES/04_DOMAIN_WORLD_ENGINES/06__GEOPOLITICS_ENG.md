# Geopolitics Engine
FILE: 06__GEOPOLITICS_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines geopolitical structure (borders, sovereignty, treaties, alliances, influence, diplomacy, control over routes and choke points); produces Control Maps and Treaty Ledgers ensuring consistent political constraints and plausible state/faction behavior across narrative and world systems

---

## PURPOSE

Геополитика отвечает:
- кто где хозяин
- где спорные земли
- какие союзы и почему
- какие договоры держат мир
- какие интересы пересекаются на карте

Движок нужен, чтобы:
- “карта власти” была стабильной
- действия государств/фракций были логичны
- дипломатия имела механику (а не декорацию)
- границы и контроль совпадали с логистикой/ресурсами

---

## NON-GOALS

- не заменяет Conflict & Power (источники силы/эскалация)
- не заменяет Civilization (внутренняя система общества)
- не заменяет Economy & Resource (учет потоков)
Он делает **карту контроля + договорную реальность**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Structure Spec (WSS) + Map Index (WMI)
- Timeline/Epochs (TM/ER)
- Civilization Profiles + Network Maps (CP/CNM)
- Conflict Ledger + Power Map (CL/PM)
- World Law (WLS) (border/zone constraints if any)

### PRODUCES
- CONTROL MAP (CM) — canonical artifact
- TREATY & AGREEMENT LEDGER (TAL)
- INFLUENCE GRAPH (IG)
- BORDER TYPES + DISPUTE MODEL (BDM)
- DIPLOMACY PLAYBOOK (DP) (rules of state behavior)
- “POLITICAL CHANGE” protocol (handoff to governance/continuity)

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/05__CONFLICT_POWER_ENG.md
- 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG.md
- 04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md

### OUTPUT_TARGET
- Feeds:
  - Economy & Resource engine (taxes/tolls, route control)
  - Narrative engines (stakes, constraints, espionage)
  - Continuity (border shifts, treaties, regime changes)

---

## CANON TERMS

### SOVEREIGNTY
Право принимать решения на территории.

### CONTROL
Фактическая власть:
- военная
- административная
- инфраструктурная (контроль дорог/портов/ворот)

### INFLUENCE
Мягкая власть:
- идеология, религия, медиа, торговля, кредиты/долги (если есть), технологии

### BORDER TYPE
Тип границы:
- natural
- fortified
- administrative
- contested
- frontier
- no-go zone

### DISPUTE
Спор:
- о земле, ресурсе, народе, святыне, маршруте, статусе

---

## GEOPOLITICAL UNITS (STANDARD)

Actors:
- states/empires
- city-states
- federations
- protectorates
- occupied zones
- autonomous regions
- non-state actors (factions/cults/corps) controlling territory/routes

---

## REQUIRED ARTIFACT A: CONTROL MAP (CM)

### CM SCHEMA (CANON)

Header:
- CM_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Territory Claims (repeat):
- CLAIM_ID:
- REGION_ID / NODE_ID:
- CLAIMED BY:
  - ACTOR_ID
- CONTROL TYPE:
  - full | partial | nominal | none
- ADMIN MODEL:
  - direct | vassal | proxy | occupation
- BORDER TYPE:
- ENFORCEMENT:
  - army | police | militia | bureaucracy | tech system
- KEY ASSETS:
  - choke points, ports, gates, archives
- POPULATION STATUS:
  - loyal | mixed | hostile | unknown
- DISPUTE FLAG:
  - yes/no
- NOTES:
  - what makes it stable/unstable

Choke Points Control (mandatory section):
- BOTTLENECK_ID:
- LOCATION LINK (WMI LINK/NODE):
- CONTROLLER:
- TOLL/TAX POLICY (optional):
- CONFLICT RISK:
- WHY IT MATTERS:

Rule:
- If the world uses gates/corridors, every major gate/corridor must be in this section.

---

## REQUIRED ARTIFACT B: TREATY & AGREEMENT LEDGER (TAL)

### TAL SCHEMA (CANON)

Header:
- TAL_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Treaties (repeat):
- TREATY_ID:
- NAME:
- PARTIES:
- DATE:
  - anchor-based or absolute (TM)
- TYPE:
  - alliance | non-aggression | trade | border | ceasefire | access-rights | vassalage
- TERMS (bullets):
- ENFORCEMENT MECHANISM:
  - hostages, mutual deterrence, monitors, sacred oath, tech lock, etc
- BENEFICIARIES:
  - who gains
- LOSERS:
  - who is constrained
- LOOPHOLES:
  - known weak spots
- VIOLATION TRIGGERS:
  - what breaks it
- CONSEQUENCES:
  - retaliation, sanctions, war escalation
- STATUS:
  - active | strained | violated | obsolete
- CONTINUITY LOCK:
  - must be remembered in scenes

Rule:
- A treaty without enforcement mechanism is a decorative treaty (invalid).

---

## REQUIRED ARTIFACT C: INFLUENCE GRAPH (IG)

### IG SCHEMA (CANON)

Header:
- IG_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Influence Channels (global list):
- ideology
- religion
- information/media
- trade access
- tech dependency
- security guarantees
- migration/refugees
- elite capture

Edges (repeat):
- EDGE_ID:
- FROM_ACTOR:
- TO_ACTOR/REGION:
- CHANNEL:
- STRENGTH:
  - low/med/high or 0–5
- DEPENDENCY:
  - what TO needs
- RESENTMENT:
  - low/med/high
- COUNTER-INFLUENCE:
  - who opposes it and how
- BREAK CONDITIONS:
  - what breaks the influence

Rule:
- Influence without dependency is weak; define what is “held”.

---

## BORDER & DISPUTE MODEL (BDM)

Dispute Types:
- resource dispute
- ethnic/religious
- strategic chokepoint
- historical claim
- ideology “liberation”
- regime legitimacy dispute

Resolution Modes:
- treaty
- arbitration
- war
- autonomy
- partition
- frozen conflict

Rule:
- Every contested border must declare:
  - dispute type
  - why it persists
  - what would resolve it (even if unlikely)

---

## GEOPOLITICS RULES (CANON)

### G1 — Control is not claim
Если они “заявляют”, но не контролируют — это отдельный статус.
Сцены обязаны различать:
- номинальное владение
- фактический контроль

### G2 — Borders follow structure and power
Границы должны быть объяснимы:
- реками/горами/пустынями
- choke points
- логистикой
- силой и институтами

### G3 — Treaties need enforcement
Любой договор обязан иметь “почему он держится”.
Без механизма принуждения — он не реальный.

### G4 — Influence creates backlash
Мягкая власть всегда рождает:
- сопротивление
- контр-нарратив
- подполье
Это нужно учитывать в стабильности.

### G5 — Political change has consequences
Смена власти/границ:
- меняет маршруты, ресурсы, безопасность, отношения
И должна фиксироваться в continuity.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- borders ignore geography/logistics entirely
- empire controls far territory with no supply routes
- treaties exist with no enforcement and never break
- influence is claimed but no dependency defined
- contested regions never produce incidents
- control map not synced with conflict ledger

Fix options:
- add chokepoint control + routes (WMI/CNM hooks)
- downgrade claim vs control status
- define enforcement (hostages, monitors, deterrence)
- add dependency and backlash edges
- add incidents or escalation triggers
- crosslink CM <-> CL <-> TAL

---

## PROCEDURE (HOW TO RUN)

1) Choose epoch scope
2) Build Control Map:
   - claims + control types + borders
3) Register chokepoints and controllers
4) Draft Treaty Ledger with enforcement mechanisms
5) Build Influence Graph (channels + dependencies)
6) Mark disputed borders with persistence logic
7) Sync with conflict ledger and economy routes
8) Lock changes via governance pipeline if canon

---

## QC CHECKLIST (MANDATORY)

- CM includes control type vs claim?
- chokepoints section filled?
- TAL treaties have enforcement + violation triggers?
- IG edges include dependency + break conditions?
- disputed borders have persistence + resolution mode?
- CM/CL/TAL synchronized?

---

## VALIDATION RULES

- GPV1: CM exists and matches geography/logistics/power.
- GPV2: TAL exists with enforceable treaties (not decorative).
- GPV3: IG explains soft power and dependencies.
- GPV4: Border disputes and incidents remain consistent across scenes.

---

OWNER: Universe Engine
LOCK: FIXED
