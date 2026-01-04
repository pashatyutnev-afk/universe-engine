# Mythology & Belief Engine
FILE: 09__MYTHOLOGY_BELIEF_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines belief systems (myths, religions, ideologies, cosmologies) as operational forces shaping norms, legitimacy, taboo, conflict, and meaning; produces Belief Profiles and Myth Maps ensuring consistent cultural logic and narrative causality across civilizations and epochs

---

## PURPOSE

Вера/мифология/идеология — это “двигатель смысла и поведения”.
Движок нужен, чтобы:
- у цивилизаций были объяснимые табу, ритуалы, ценности
- власть имела легитимацию (сакральную/идеологическую/мифологическую)
- конфликты могли быть смысловыми, а не только ресурсными
- “картина мира” была стабильной и воспроизводимой

---

## NON-GOALS

- не заменяет Character Moral/Value (личный уровень)
- не заменяет Geopolitics (договоры/границы)
- не заменяет Economy (ресурсы/потоки)
Он строит **мировой слой верований как систем**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Law Spec (WLS) + Exception Registry (ERX)
- Civilization Profiles (CP) (norms, legitimacy)
- Timeline/Epochs (TM/ER)
- Conflict Ledger (CL) (ideological drivers)
- World Structure (layers/regions) (sacred geography)

### PRODUCES
- BELIEF SYSTEM PROFILE (BSP) — canonical artifact
- MYTH MAP (MM) — gods/forces/places/rituals links
- RITUAL & TABOO REGISTRY (RTR)
- LEGITIMACY NARRATIVE SET (LNS)
- “BELIEF CHANGE” protocol (schisms, reforms)

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md
- 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG.md

### OUTPUT_TARGET
- Feeds:
  - civilization norms & legitimacy
  - geopolitics (holy wars, alliances)
  - conflict escalation (taboo violations)
  - narrative meaning/foreshadowing/symbolism

---

## CANON TERMS

### BELIEF SYSTEM
Устойчивая система объяснений:
- “как устроен мир”
- “что правильно”
- “что будет после смерти”
- “почему власть законна”

### MYTH
История/архетип, который:
- объясняет явления
- задаёт нормы
- легитимизирует решения

### TABOO
Запрет, нарушение которого создаёт:
- социальную санкцию
- сакральный страх
- политический кризис

### RITUAL
Повторяемое действие, которое:
- поддерживает идентичность
- укрепляет власть
- “скрепляет” общество

---

## REQUIRED ARTIFACT A: BELIEF SYSTEM PROFILE (BSP)

### BSP SCHEMA (CANON)

Header:
- BSP_ID:
- CIV_ID / ACTOR_ID:
- NAME:
- EPOCH:
- VERSION:
- STATUS:

Cosmology:
- ORIGIN STORY:
- WORLD MODEL:
  - layers, heavens, underworld, cycles
- AGENCY MODEL:
  - gods | spirits | ancestors | fate | algorithms | none
- AFTERLIFE MODEL:
  - reward/punishment/rebirth/void

Ethics & Norms:
- CORE VIRTUES (3–7):
- CORE SINS (3–7):
- VIOLENCE POLICY:
- STRANGER POLICY:
- PURITY/POLLUTION MODEL (if any):

Institutions:
- PRIESTHOOD/IDEOLOGY APPARATUS:
- RITES OF PASSAGE:
- SACRED TEXTS/ARCHIVES:
- ENFORCEMENT:
  - social | legal | violent | reputational

Legitimacy:
- WHY RULERS ARE LEGIT:
- CORONATION / INITIATION RITUAL:
- SACRED SYMBOLS:
- HERESY/ENEMY DEFINITION:

Everyday Practice:
- DAILY/WEEKLY RITUALS:
- CALENDAR FEASTS:
- OFFERINGS / TITHES / DUTIES (if any):
- SIGNS & OMENS POLICY:

Conflict Hooks:
- TABOOS THAT CAUSE WAR:
- SCHISM TRIGGERS:
- CONVERSION POLICY:
  - aggressive | soft | none
- BLACK/SECRET PRACTICES:
  - cults, forbidden rites

Canon Locks:
- NON-NEGOTIABLES:
- FORBIDDEN KNOWLEDGE:
- SYMBOL LOCKS:
  - colors, icons, phrases that must stay consistent

---

## REQUIRED ARTIFACT B: MYTH MAP (MM)

### MM SCHEMA (CANON)

Nodes:
- DEITY/FORCE/ARCHETYPE node
- SACRED PLACE node
- HERO/SAINT node
- RITUAL node
- TABOO node

Edges:
- “protects”, “demands”, “punishes”, “reveals”, “binds”, “forbids”
- “site of”, “origin of”, “key to legitimacy”

Rule:
- If a symbol/ritual is used repeatedly in canon, it must appear in MM.

---

## REQUIRED ARTIFACT C: RITUAL & TABOO REGISTRY (RTR)

### RTR SCHEMA (CANON)

Entries (repeat):
- RTR_ID:
- NAME:
- TYPE:
  - ritual | taboo
- WHO PRACTICES:
- WHEN/WHERE:
- PURPOSE:
- ENFORCEMENT:
- VIOLATION CONSEQUENCES:
  - social, legal, spiritual, political
- STORY UTILITIES:
  - stakes, foreshadowing, twist, conflict driver

---

## BELIEF RULES (CANON)

### MB1 — Belief affects behavior
Если вера заявлена, она должна:
- менять выбор людей
- менять институты
- менять “что считается возможным”

### MB2 — Legitimacy is tied to belief
Если власть сакральная/идеологическая:
- покажи ритуал
- покажи “ересь”
- покажи цену нарушения

### MB3 — Belief evolves across epochs
Вера меняется:
- реформы, секты, синкретизм
Но это должно быть заякорено в таймлайне.

### MB4 — World Law alignment required
Если вера утверждает “магия/чудеса”:
- либо это реально в WLS/ERX
- либо это миф/пропаганда (и так помечается)

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- belief is described but never affects decisions
- sacred legitimacy exists with no rituals/institutions
- taboo violations have no consequences
- belief claims miracles forbidden by WLS without explanation
- same civilization shows contradictory symbols with no schism/epoch change

Fix options:
- add RTR entries and enforce consequences
- define legitimacy rituals and enforcement apparatus
- mark miracles as propaganda or register ERX exception
- tie changes to epoch events (reform, conquest, revelation)

---

## PROCEDURE (HOW TO RUN)

1) Choose belief type (religion/ideology/cult)
2) Write BSP (cosmology + ethics + legitimacy)
3) Build myth map (nodes/edges)
4) Register rituals and taboos (RTR)
5) Sync with civ norms + conflict drivers
6) Anchor reforms/schisms in timeline
7) Lock symbols and phrases for consistency

---

## QC CHECKLIST (MANDATORY)

- BSP complete (cosmology, ethics, institutions, legitimacy)?
- RTR includes enforceable taboos + rituals?
- MM covers repeated symbols/places?
- alignment with WLS/ERX checked?
- belief impacts at least 2 systems (civ, conflict, geopolitics)?

---

## VALIDATION RULES

- MBV1: Beliefs generate consistent norms and legitimacy.
- MBV2: Taboos/rituals create real consequences and stakes.
- MBV3: Myth map ensures symbol consistency across media and narrative.
- MBV4: Timeline anchoring prevents random belief shifts.

---

OWNER: Universe Engine
LOCK: FIXED
