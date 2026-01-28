# FORESHADOWING ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/07__FORESHADOWING_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 07__FORESHADOWING_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.FORESHADOW.001
OWNER: SYSTEM
ROLE: Plan foreshadowing: seed signals early, track promises, and ensure payoffs are earned without leaking or over-telegraphing.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Foreshadowing Engine created: seed plan, promise tracking, concealment rules, and foreshadow-to-payoff mapping."
- REASON: "Needed deterministic system for planting future revelations/payoffs across structure and scenes."
- IMPACT: "Twists/reveals/payoffs become controllable and verifiable."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.FORESHADOW.001

---

## 0) PURPOSE (LAW)
Этот движок планирует **предвестники (foreshadowing)**:
- какие “семена” (seeds) посадить заранее
- где и как их показывать (без прямого спойлера)
- какие обещания (promises) создаются у аудитории
- как семена закрываются (payoffs) и где
- как избежать двух провалов:
  - “из ниоткуда” (unearned)
  - “слишком очевидно” (over-telegraph)

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- генерацию твистов/раскрытий (это `08__TWIST_REVEAL_ENG`)
- проектирование сцен целиком (это `04__SCENE_CONSTRUCTION_ENG`)
- монтажные приёмы сокрытия/намёков (production) → `08_*`
- атмосферные/жанровые “намёки” как стиль (если это про тон/символизм) → `06_GENRE_STYLE_ENGINES/*`

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–10)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `SCENE_BLUEPRINT_SET` (optional but recommended)
- `DRAMATIC_ARC_SPEC` (optional)
- `TENSION_STAKES_MAP` (optional but recommended)
- `PAYOFF_OBLIGATIONS` (optional but recommended)
- `PLAUSIBILITY_RULESET` (optional)

### PRODUCES (1–7)
- `FORESHADOW_PLAN`
- `SEED_CATALOG`
- `PROMISE_PAYOFF_MAP`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG, 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG, 02_DOMAIN_NARRATIVE_ENGINES/06__TENSION_STAKES_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/FORESHADOW/`

---

## 3) DEFINITIONS (LOCAL)
- **Seed** — ранний сигнал/деталь, который станет значимым позже.
- **Promise** — ожидание аудитории, сформированное seed’ом.
- **Payoff** — момент, где promise “оплачивается” (объяснение/последствие/использование).
- **Telegraphing** — избыточная очевидность, когда аудитория угадывает раньше времени.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- система семян/обещаний/оплат
- размещение семян по структуре (акт/сегмент) и сценам (если есть)
- правила сокрытия (concealment rules) на уровне story logic (не монтаж)
- метрики очевидности/плотности (warning system)

### OUT OF SCOPE (HARD)
- создание самого твиста/раскрытия
- художественная стилизация намёка (визуальные/звуковые приёмы)
- полное переписывание сцен

### COLLISION RULE (ROUTING)
- Если речь про “сам твист/раскрытие” → `08__TWIST_REVEAL_ENG`
- Если речь про “как показать визуально/звуком” → `08_KNOWLEDGE_PRODUCTION_ENGINES/*`
- Если речь про символизм как смысловой слой → `06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG` или `05__METAPHOR_ENG`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `SEED_CATALOG`
**MUST (fields):**
- `catalog_id`
- `version`
- `seeds[]`
- `anti_patterns[]`
- `validation_checks[]`

**Seed (minimum):**
- `seed_id`
- `seed_type` (enum: `OBJECT|DETAIL|RULE|HABIT|RELATIONSHIP|RUMOR|EVIDENCE|SCAR|LOCATION|SYSTEM_GLITCH|WARNING`)
- `seed_content` (what it is)
- `purpose` (what it will enable later)
- `promise_type` (enum: `ANSWER_LATER|PAY_LATER|REVEAL_LATER|USE_LATER|COST_LATER`)
- `strength` (`SOFT|HARD`)
- `visibility` (enum: `SUBTLE|MEDIUM|LOUD`)
- `risk_of_telegraph` (`LOW|MEDIUM|HIGH`)
- `logic_refs[]` (atoms/constraints it relies on)
- `notes`

**VALIDATION:**
- every seed must have a `purpose` and a `promise_type`
- if `strength=HARD`, it must map to a payoff obligation or future reveal (else open_unknown)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/FORESHADOW/SEED_CATALOG.md`

---

### B) `FORESHADOW_PLAN`
**MUST (fields):**
- `plan_id`
- `version`
- `placements[]` (seed placements)
- `density_by_act[]`
- `concealment_rules[]`
- `telegraph_controls[]`
- `open_unknowns[]`
- `scope_notes`

**Placement (minimum):**
- `placement_id`
- `seed_id`
- `ref_type` (enum: `ACT|SEQUENCE|SCENE|BEAT`)
- `ref_id`
- `placement_mode` (enum: `MENTION|SHOW|CONSEQUENCE|ABSENCE|CONTRAST|MISDIRECT`)
- `intensity` (enum: `LIGHT|NORMAL|HEAVY`)
- `expected_audience_read` (short)
- `do_not_explain_yet` (bool; default true)
- `notes`

**Concealment rule (minimum):**
- `id`
- `rule_text`
- `scope` (enum: `GLOBAL|ACT|SCENE`)
- `strength` (`HARD|SOFT`)

**Telegraph control (minimum):**
- `id`
- `control_text`
- `trigger` (e.g., “too many loud seeds in a row”)
- `action` (e.g., “convert to subtle”, “delay placement”, “add misdirect seed”)

**VALIDATION:**
- placements must not violate pacing (too many loud seeds in high-intensity cluster without reason)
- concealment rules must not contradict logic constraints (no impossible misdirection)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/FORESHADOW/FORESHADOW_PLAN.md`

---

### C) `PROMISE_PAYOFF_MAP`
**MUST (fields):**
- `map_id`
- `promises[]`
- `payoffs[]`
- `links[]` (promise -> payoff)
- `unpaid_promises[]` (promises without payoff yet)

**Promise (minimum):**
- `promise_id`
- `seed_ids[]`
- `what_audience_expects`
- `severity_if_unpaid` (`S0|S1|S2|S3`)
- `due_by_ref` (act/segment id or `UNKNOWN`)

**Payoff (minimum):**
- `payoff_id`
- `type` (enum: `ANSWER|CONSEQUENCE|USE|REVEAL|COST|REVERSAL`)
- `ref_type` (enum: `ACT|SEQUENCE|SCENE|BEAT`)
- `ref_id`
- `what_it_pays`

**Link (minimum):**
- `promise_id`
- `payoff_id`
- `quality` (enum: `CLEAN|OK|WEAK|MISALIGNED`)
- `notes`

**VALIDATION:**
- any `S0` promise must not remain in `unpaid_promises`
- payoff location must be compatible with structure/arc (no payoff before seed unless deliberate misdirect noted)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/FORESHADOW/PROMISE_PAYOFF_MAP.md`

---

## 6) PROCESS (PIPELINE)
1) Identify payoff needs:
   - from `PAYOFF_OBLIGATIONS` (if present)
   - from planned reveals/twists (if already known)
2) Generate seed candidates (SEED_CATALOG).
3) Place seeds across structure:
   - early: subtle seeds
   - mid: reinforce or misdirect
   - late: pre-payoff reminders (avoid loud telegraph)
4) Build promise-payoff mapping.
5) Validate:
   - unpaid critical promises
   - telegraph density spikes
   - contradictions with logic/pacing
6) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- a critical promise (severity S0) has no payoff path
- foreshadow plan forces an impossible concealment (violates logic constraints)
- payoff occurs with no seed for a hard promise (unearned payoff)

S1 (HIGH) if:
- too many loud seeds cluster before a twist (telegraph risk HIGH)
- repeated obvious reminders create predictability

S2/S3: quality warnings.

---

## 8) NOTES
Foreshadowing is a “contract with audience”:
- raise expectation → you owe payoff
- but if you shout the seed → you lose surprise
This engine keeps it measurable.

---

LOCK: OPEN
