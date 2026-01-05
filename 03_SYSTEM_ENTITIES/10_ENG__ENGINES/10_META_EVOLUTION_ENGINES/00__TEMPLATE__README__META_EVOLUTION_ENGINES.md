# ENG META EVOLUTION ENGINES — REALM (FAMILY README)
FILE: 00__README__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for meta-evolution of the whole system (learning → extraction → optimization → mutation → forecasting)

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY отвечает за **мета-эволюцию** Universe Engine:
- учёба системы на опыте (learning loops)
- извлечение паттернов из артефактов и работы движков
- оптимизация процессов/пайплайнов/структур
- креативная мутация (controlled innovation) без разрушения канона
- прогнозирование будущих веток/рисков/выгод

Задача FAMILY — улучшать систему **поверх всех слоёв**, не подменяя собой доменные движки.

---

## 1) OWNERSHIP (BOUNDARIES)

### THIS FAMILY OWNS
- meta-learning & feedback loops (что мы узнали из работы)
- pattern mining (повторяющиеся решения/ошибки/структуры)
- optimization proposals (ускорение, упрощение, стандарты)
- controlled mutation (эксперименты с охранными рамками)
- future projections (сценарии развития, roadmap options)
- метрики качества процесса (не доменные метрики истории/музыки и т.п.)

### THIS FAMILY DOES NOT OWN
- Доменные решения по истории/персонажам/миру/стилю
  → `02_DOMAIN_NARRATIVE_ENGINES/*`, `03_DOMAIN_CHARACTER_ENGINES/*`, `04_DOMAIN_WORLD_ENGINES/*`, `06_GENRE_STYLE_ENGINES/*`
- Производственные артефакты визуала/монтажа/звук-производства
  → `08_KNOWLEDGE_PRODUCTION_ENGINES/*`
- Governance “закон и разрешение”
  → `00_GOVERNANCE_ENGINES/*`

META может предлагать изменения, но **не утверждает** и **не вводит в канон** самостоятельно.

---

## 2) HARD RULE: META ≠ GOVERNANCE

- META = генератор улучшений, паттернов, вариантов, прогнозов.
- GOVERNANCE = authority + change control + фиксация канона.

Любая мутация/оптимизация, затрагивающая канон:
→ проходит pipeline:
- `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- `00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md`
- `00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md`
- `00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md`

---

## 3) CANON ORDER (MANDATORY)

01 — Learning Engine  
02 — Pattern Extraction Engine  
03 — Optimization Engine  
04 — Creative Mutation Engine  
05 — Future Projection Engine  

---

## 4) META INPUT/OUTPUT INTERFACES

### INPUT TYPES (typical)
- WORK_LOGS: audit logs / change logs / decisions
- ARTIFACT_SET: пак артефактов проекта (docs, outlines, cues, renders, etc.)
- ENGINE_RUN_NOTES: заметки/результаты прогонов движков
- QA_REPORTS: ошибки, провалы, спорные места
- METRICS_SNAPSHOT: скорость, качество, стабильность, повторяемость
- CONSTRAINTS: сроки/ограничения/порог рисков

### OUTPUT TYPES (typical)
- LEARNING_SUMMARY: что узнали / чему научились
- PATTERN_LIBRARY: паттерны (good/bad), антипаттерны
- OPTIMIZATION_PROPOSALS: предложения улучшений (с оценкой эффекта)
- MUTATION_PROPOSALS: экспериментальные варианты (с guardrails)
- ROADMAP_SCENARIOS: 2–5 сценариев будущего развития
- RISK_MAP: риски/цена/выгоды/точки контроля
- CHANGE_REQUEST_DRAFTS: черновики на governance pipeline

OUTPUT_TARGET (recommended):
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/`
  - `99__META_OUTPUTS/` (если выносите результаты)
или
- `04_PROJECTS/<project>/99_META/`

---

## 5) META QUALITY STANDARD

Минимальные критерии качества для любого результата META:
- есть **наблюдение** (что происходит)
- есть **причина/паттерн** (почему)
- есть **предложение действия** (что менять)
- есть **оценка эффекта** (скорость/качество/риск)
- есть **guardrails** (что нельзя ломать)
- при затрагивании канона — есть ссылка на governance CR

---

## 6) SAFETY RAILS (ANTI-CHAOS)

- Запрещены изменения “втихую”.
- Запрещена мутация без rollback plan.
- Любая оптимизация должна сохранять:
  - canonical naming/numbering
  - link rules (raw links)
  - mini-contract standard
  - dependency/xref transparency

---

## 7) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Change Control: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- Audit Log: `../00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md`
- Versioning & Memory: `../00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md`

---

## 8) AUTHOR RULES (MANDATORY)

- Каждый движок обязан иметь mini-contract.
- Каждый движок должен выдавать воспроизводимый артефакт (summary/library/proposal/scenario).
- Любая рекомендация, влияющая на канон, должна формировать CR-черновик.

---

OWNER: Universe Engine
LOCK: OPEN
