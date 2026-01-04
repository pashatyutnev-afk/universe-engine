# Tension & Stakes Engine
FILE: 06__TENSION_STAKES_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines and validates tension mechanics and stakes escalation; produces explicit stakes models per scope and per scene to prevent empty threats, unearned drama, and consequence drift

---

## PURPOSE

Ставки и напряжение — это “цена и давление”.
Движок гарантирует:
- ставки сформулированы ясно (что потеряем/получим)
- давление реально действует (pressure source)
- эскалация честная (earned)
- последствия соразмерны ставкам (без обесценивания)

---

## NON-GOALS

- не задаёт темп (это Pacing)
- не задаёт структуру актов (Story Structure)
- не делает психологию персонажа (Character family)
Он про “механику давления” и “цену провала/успеха” как данные.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Scene Specs (SS)
- Dramatic Arc Spec (DAS)
- Story Structure Spec (SSS)
- World constraints (laws/timeline/resource limits) if known
- Character constraints (values/fears/attachments) if known

### PRODUCES
- STAKES & TENSION SPEC (STS) — canonical artifact
- STAKES LADDER (low->mid->high escalation)
- PRESSURE SOURCES MAP
- CONSEQUENCE MAP (what happens on fail/success)
- EMPTY THREAT FLAGS (if detected)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/03__DRAMATIC_ARC_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md

### OUTPUT_TARGET
- Feeds Continuity (09) and Twist/Reveal (08)
- Informs production editing/sound for “pressure beats” and payoff timing

---

## CANON TERMS

### STAKES
Что поставлено на кон:
- loss (что потеряем)
- gain (что получим)
- identity/moral cost (кем станем)

### TENSION
Ощущение близости последствия:
- time pressure
- uncertainty
- exposure risk
- irreversible choice

### PRESSURE SOURCE
Механизм, который делает ставки “живыми”:
- clock (таймер)
- threat (угроза)
- scarcity (дефицит)
- pursuit (преследование)
- moral trap (моральная ловушка)
- relationship fracture (разрыв связи)

### EMPTY THREAT
Угроза, которая не имеет:
- механизма реализации, или
- последствия, или
- доверия (последствия раньше отменялись)

---

## STAKES TYPES (CANON SET)

- PERSONAL:
  - тело, свобода, отношения, репутация
- SYSTEMIC:
  - власть, порядок, экономика, безопасность
- EXISTENTIAL:
  - смысл, вера, идентичность, выживание мира
- MORAL:
  - цена выбора, вина, предательство принципов
- INFORMATIONAL:
  - правда/тайна, раскрытие, контроль нарратива

Rule:
- stakes must declare type(s).

---

## STAKES LADDER (ESCALATION MODEL)

Эскалация должна быть видна как лестница:

- LOW:
  - локальные потери, обратимые
- MID:
  - потери значимые, частично необратимые
- HIGH:
  - необратимость, фундаментальные потери/изменения

Rule:
- “HIGH” stakes нельзя вводить без подготовки (earned build).

---

## REQUIRED ARTIFACT: STAKES & TENSION SPEC (STS)

### STS SCHEMA (CANON)

Global:
- STS_ID:
- SCOPE:
  - episode | arc | season | book
- PRIMARY STAKES:
  - type + statement
- SECONDARY STAKES:
  - list
- PRESSURE SOURCES (GLOBAL):
  - list with mechanism notes
- STAKES LADDER:
  - low -> mid -> high description
- CONSEQUENCE POLICY:
  - fail consequences must persist? (yes/no + rules)
- TRUST POLICY:
  - do we allow “fakeouts”? (rare/allowed/not allowed)

Per Scene (or per segment):
- SCENE_ID:
- STAKES (explicit):
  - if fail:
  - if succeed:
- PRESSURE SOURCE (in scene):
- TENSION LEVEL (0–10):
- ESCALATION NOTE:
  - how this raises stakes vs previous
- CONSEQUENCE COMMITMENT:
  - what must remain true after scene
- FLAGS:
  - empty threat risk?
  - stakes inflation risk?
  - consequence drift risk?

---

## STAKES RULES (CANON)

### TS1 — Stakes must be explicit
Нельзя “на ощущениях”.
В каждой важной сцене:
- if fail / if success должны быть записаны.

### TS2 — Pressure must be real
Если pressure declared, должен существовать механизм.
Пример:
- таймер: кто/что измеряет, что будет при нуле
- угроза: кто может реализовать, как и почему

### TS3 — Consequences persist
Если high-stakes провал произошёл,
его нельзя отменять без:
- отдельной цены (tradeoff),
- или заранее подготовленного механизма (setup).

### TS4 — No stakes inflation
Если каждый поворот “самый опасный” → обесценивание.
Нужна лестница, и high должно быть редким.

### TS5 — Tension comes from uncertainty + proximity
Без неопределённости и близости последствия напряжение не держится.
Нужно минимум одно:
- uncertainty (“не знаем исход”)
- proximity (“исход близко/таймер”)

### TS6 — Trust is a resource
Слишком много fakeouts ломают доверие.
Если fakeout используется:
- он должен создавать новую цену/правду,
а не “обнулять всё”.

---

## EMPTY THREAT DETECTOR (HEURISTICS)

Флаг EMPTY THREAT если:
- угроза повторяется, но не исполняется 2+ раза
- провалы не имеют последствий
- антагонист “может”, но не делает (без причины)
- таймер “типа идёт”, но ничего не происходит

Fix options:
- реализовать угрозу
- снизить stakes (если не готовы)
- добавить механизм/ограничение, объясняющее задержку
- перенести угрозу в future payoff (но пометить)

---

## PROCEDURE (HOW TO RUN)

1) Define global stakes (primary/secondary)
2) Define global pressure sources
3) Build stakes ladder (low->mid->high)
4) For each scene:
   - write explicit fail/success consequences
   - choose pressure source
   - assign tension level
   - mark commitment (what persists)
5) Run empty threat detector
6) Revise: remove inflation, add persistence
7) Output STS

---

## QC CHECKLIST (MANDATORY)

- are primary stakes explicit?
- is there a stakes ladder?
- are pressure sources mechanistic (not vibes)?
- per-scene fail/success consequences present?
- do consequences persist (especially for high)?
- any empty threat flags unresolved?
- any stakes inflation (too many highs)?
- does tension align with DAS peaks?

---

## VALIDATION RULES

- TSV1: STS exists with global + per-scene entries (or declared scope subset).
- TSV2: Every major scene has explicit fail/success.
- TSV3: Pressure sources are actionable and believable in-world.
- TSV4: Empty threat flags are either fixed or intentionally declared with payoff plan.

---

OWNER: Universe Engine
LOCK: FIXED
