# ENG META EVOLUTION ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
ENGINE_ID: ENG.META.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this meta engine>

---

## 0) PURPOSE (LAW)

Этот движок производит **meta-артефакт** для улучшения Universe Engine:
- обучение / извлечение паттернов / оптимизация / мутация / прогноз
- прозрачная рекомендация действий
- подготовка к governance pipeline при влиянии на канон

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно делает движок в META: learning/patterns/optimization/mutation/forecast>

### DOES NOT OWN
- утверждение канона (это governance)
- переписывание доменных истин (это domain engines)
- скрытые изменения без CR

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] накопились повторяющиеся ошибки/затыки
- [ ] нужно ускорить производство/упростить структуру
- [ ] нужно найти паттерны качества/провалов
- [ ] нужен controlled эксперимент (mutation) с рамками
- [ ] нужен прогноз вариантов развития/рисков

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <WORK_LOGS>
- <ENGINE_RUN_NOTES>
- <QA_REPORTS>
- <ARTIFACT_SET>
- <METRICS_SNAPSHOT>

PRODUCES:
- <SUMMARY/LIBRARY/PROPOSAL/SCENARIOS>
- <CR_DRAFT (if canon impact)>

DEPENDS_ON:
- []  # или перечисли, если этот meta движок требует результатов других meta движков

OUTPUT_TARGET:
- `04_PROJECTS/<project>/99_META/` OR `03_SYSTEM_ENTITIES/.../10_META_EVOLUTION_ENGINES/99__META_OUTPUTS/`

---

## 4) CONTROL SURFACE (PARAMETERS)

- scope_window: last_run | last_week | milestone | full_project
- strictness: low | medium | high
- change_budget: none | small | moderate | aggressive
- risk_tolerance: low | medium | high
- evidence_level: anecdotal | sampled | verified
- output_mode: summary | library | proposal | scenario_set | cr_draft

---

## 5) PROCESS (HOW IT WORKS)

1) Collect inputs (logs/artifacts/metrics)
2) Detect patterns (good/bad)
3) Rank by impact (speed/quality/risk)
4) Generate actions (proposal)
5) Add guardrails + rollback plan (если меняем структуру)
6) If canon impact → produce CR draft + link governance engines
7) Export meta artifacts to OUTPUT_TARGET

---

## 6) OUTPUT FORMAT (STANDARD)

Минимальный формат артефакта:
- Findings (наблюдения)
- Evidence (на чём основано)
- Root causes (паттерн/причины)
- Proposal (что меняем)
- Impact estimate (выгода/цена)
- Risks (что может сломаться)
- Guardrails (что нельзя трогать)
- Rollback plan
- Governance CR link (если нужно)

---

## 7) QUALITY CHECKS

- [ ] есть evidence (не “ощущения”)
- [ ] есть impact estimate
- [ ] есть guardrails
- [ ] есть rollback plan (если вмешательство)
- [ ] прозрачность зависимостей соблюдена
- [ ] при канон-изменениях есть CR draft

---

## 8) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
