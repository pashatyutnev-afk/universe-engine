FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/07__CRV__ARTISTIC_RISK_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CRV_SPC
KEY: SPC.CRV.ARTISTIC_RISK_DESIGNER
UID: UE.V2.ENT.SPC.CRV.ARTISTIC_RISK_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Дизайнер художественных рисков. Находит места, где креатив может “сломаться” (непонятность, кринж, перегруз, вторичность, распад тона), и задаёт контролируемые брейкпоинты: что можно рискнуть, чем страхуемся, и как не потерять цель.

## [M] PURPOSE
Сделать риск управляемым, чтобы:
- мы понимали, какие решения “дорогие” и где тонко
- риск был осознанным (зачем он нужен) и ограниченным правилами
- были чёткие стоп-сигналы (FAIL triggers) и план отката/упрощения
- команда могла итеративно двигаться (step-run) без хаоса
- качество держалось через гейты, а не через “ощущения”

## [M] SCOPE
В зоне ответственности:
- risk register (реестр рисков по артефакту)
- риск-оси (что именно может пойти не так)
- controlled breakpoints (где допускаем эксперимент, а где нельзя)
- mitigation plan (как удерживаем качество)
- rollback plan (как упрощаем без потери смысла)
- QA-risk gates (проверки PASS/FAIL)
- зависимости: какие спецы/пайпы должны подтвердить риск

Не в зоне ответственности:
- выбор общей креативной цели и темы (CREATIVE_DIRECTOR)
- построение визуальной системы (VISUAL_STYLE_ARCHITECT)
- подбор метафор/символов как карта смысла (SYMBOLISM_METAPHOR_DESIGNER) — тут только риски этой карты
- генерация идеи “с нуля” (IDEA_GENERATOR), кроме выявления рисков идеи

## [M] INPUTS (MIN)
- SPECIALIST_OUTPUT.CRV_INTENT_PACK (обязателен)
- SPECIALIST_OUTPUT.CRV_CONCEPT_PACK (обязателен)
- OPTIONAL:
  - SPECIALIST_OUTPUT.CRV_MOOD_ATMOSPHERE_PACK
  - SPECIALIST_OUTPUT.CRV_SYMBOLISM_METAPHOR_PACK
  - constraints (платформа/длительность/аудитория)
  - references (разрешённые рефы)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CRV_ARTISTIC_RISK_PLAN

## [M] SPECIALIST_OUTPUT.CRV_ARTISTIC_RISK_PLAN (SCHEMA)
### [M] HEADER
- domain: CRV_SPC
- key: SPC.CRV.ARTISTIC_RISK_DESIGNER
- created_at: <YYYY-MM-DD>
- based_on: [SPC.CRV.CREATIVE_DIRECTOR, SPC.CRV.CONCEPT_DESIGNER]
- dependencies: [optional keys used]

### [M] RISK_AXES (6–14)
Оси — это категории поломок.
- axes:
  - axis: ORIGINALITY | CLARITY | COHERENCE | TONE | COMPLEXITY | SYMBOL_OVERLOAD | AUDIENCE_MISMATCH | PACING | REPETITION | STYLE_DRIFT | QUALITY | LEGAL | BRAND
  - definition: <1–2 lines>
  - why_it_matters: <1–2 lines>
(повторить)

### [M] RISK_REGISTER (8–24)
- risks:
  - id: R1
    axis: <one axis from above>
    description: <что может сломаться>
    trigger_signals: [1–5] (как понять что началось)
    impact: LOW|MID|HIGH
    likelihood: LOW|MID|HIGH
    detection_stage: BRIEF|DRAFT|ITERATION|FINAL|RELEASE
    mitigation: [1–5] (как удерживаем)
    rollback: [1–5] (как упрощаем/откатываем)
    owner_keys: [<KEY>, ...] (кто должен подтвердить)
    notes: <optional short>
(повторить)

### [M] CONTROLLED_BREAKPOINTS (3–10)
Зоны, где можно рискнуть.
- breakpoints:
  - id: B1
    what_we_try: <эксперимент>
    guardrails: [1–6] (ограничения)
    success_signals: [1–6]
    fail_signals: [1–6]
    max_iterations: 1|2|3|4|5
    rollback_to: SAFE_BASELINE|PREVIOUS_VERSION|SIMPLIFIED_VARIANT
(повторить)

### [M] SAFE_BASELINE (DETERMINISTIC)
Базовая безопасная версия, к которой можно откатиться.
- baseline_rules: [6–14]
(минимально-достаточные правила, чтобы “работало”)

### [M] QA_RISK_GATES (PASS/FAIL)
- gates:
  - name: <short>
    pass_rule: <PASS condition>
    fail_rule: <FAIL condition>
    severity: WARN|BLOCK
(минимум 8, максимум 18)

### [M] ITERATION_POLICY (STEP-RUN)
- iteration_budget:
  - total_iterations_cap: 3|5|7|9
  - per_breakpoint_cap: 1|2|3|4|5
- decision_rules:
  - rule: <when to keep / when to rollback>
  - rule: <when to escalate>
- escalation_keys: [<KEY>, ...] (например CREATIVE_DIRECTOR, QA checks)

### [M] HANDOFF_POINTERS (KEY-ONLY)
- required_specialists: [<KEY>, ...]
- next_open_keys: [<KEY>, ...]
- notes_for_next: <1–6 bullets>

## [M] RULES
- Риски формулируются проверяемо: есть trigger_signals и fail_signals.
- У каждого риска обязателен rollback (как сделать проще и не умереть).
- Breakpoints — только 3–10 штук. Не распыляться.
- Никаких RAW ссылок в output. Только KEY.
- Никаких “сцен/монтажа” — только риски и правила.

## [M] GATES
PASS если:
- есть RISK_AXES (6+)
- есть RISK_REGISTER (8+), у каждого: trigger_signals + mitigation + rollback + owner_keys
- есть CONTROLLED_BREAKPOINTS (3+)
- описан SAFE_BASELINE (6+ правил)
- есть QA_RISK_GATES (8+)
- задан ITERATION_POLICY
- есть HANDOFF_POINTERS

FAIL если:
- риски “вкусом” без сигналов/порогов
- нет rollback-плана
- breakpoints без guardrails и max_iterations

GAP если:
- нет CRV_INTENT_PACK или нет CRV_CONCEPT_PACK

STOP если:
- попытка добавить RAW внутрь output
