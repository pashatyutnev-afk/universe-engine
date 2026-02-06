FILE: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/03__CHR__TRAUMA_MOTIVATION_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 03_CHARACTER_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CHR_SPC
KEY: SPC.CHR.TRAUMA_MOTIVATION_DESIGNER
UID: UE.V2.ENT.SPC.CHR.TRAUMA_MOTIVATION_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Trauma & Motivation Designer. Проектирует мотивы, внутренние конфликты, травматические паттерны и триггеры.

## [M] PURPOSE
Собрать MOTIVATION_MAP так, чтобы:
- было понятно “почему он делает это”, даже если он сам это не осознаёт
- желания, страхи и запреты не противоречили ядру персонажа
- реакции на триггеры были детерминированы и пригодны для валидации сцен
- внутренний конфликт рождал действие, а не объяснял его постфактум

## [M] SCOPE
Делает:
- определяет первичные драйверы (needs/wants) и их приоритет
- собирает страхи/стыд/вину/потерю как “двигатели” поведения
- описывает внутренний конфликт (2–3 полюса) и типовые компромиссы
- задаёт триггеры, красные зоны и “взрывные точки”
- формирует “защиты” (defense patterns) и цену, которую персонаж платит
- даёт писателю краткие сценообразующие рычаги (lever list)

Не делает:
- стабильные черты личности как система (это `SPC.CHR.PERSONALITY_PSYCHOLOGIST`)
- отношения как сетку сил/уз (это `SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER`)
- контроль канона и границ персонажа (это `SPC.CHR.CHARACTER_ARCHITECT`)
- контроль эволюции по аркам (это `SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR`)

## [M] INPUTS (MIN)
- CHARACTER_CORE_SPEC (от `SPC.CHR.CHARACTER_ARCHITECT`) или краткое ядро
- OPTIONAL:
  - PERSONALITY_FRAME (от `SPC.CHR.PERSONALITY_PSYCHOLOGIST`)
  - BACKSTORY_SEEDS (факты/намёки, что уже канон)
  - SCENE_SAMPLES (2–8 сцен/реплик)
  - WORLD_CONSTRAINTS (культура, эпоха, табу, законы)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CHR_MOTIVATION_MAP

## [M] SPECIALIST_OUTPUT.CHR_MOTIVATION_MAP (SCHEMA)

### [M] HEADER
- domain: CHR_SPC
- key: SPC.CHR.TRAUMA_MOTIVATION_DESIGNER
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- character_token: <id/name>
- dependencies_keys: [<KEY>, ...]

### [M] DRIVERS (PRIMARY)
- core_needs_ranked:
  - need: <safety / belonging / autonomy / recognition / love / meaning / control etc>
    rank: 1..N
    why: <1 line>
    typical_actions: [<verbs>]
    cost: <what breaks>
- core_wants_ranked:
  - want: <goal desire>
    rank: 1..N
    surface_reason: <what they say>
    true_reason: <what drives it>
    price_limit: <what they won't pay>

### [M] FEARS_AND_LOSSES
- primary_fears:
  - fear: <loss / rejection / humiliation / abandonment / powerlessness etc>
    intensity: LOW|MID|HIGH
    avoidance_strategy: <pattern>
- core_losses:
  - loss: <what was lost or threatened>
    echo: <how it repeats>

### [M] TRAUMA_PATTERN (IF ANY)
- trauma_status: NONE|IMPLICIT|CONFIRMED
- trauma_type: <betrayal / neglect / violence / shame / accident / war etc>
- imprint_belief: <belief formed>
- trigger_set:
  - trigger: <stimulus>
    reaction: <auto response>
    escalation: 1..5
- protection_mode:
  - mode: CONTROL|WITHDRAW|AGGRESSION|PEOPLE_PLEASE|PERFECTIONISM|NUMBING
    benefit: <what it protects>
    collateral: <what it damages>

### [M] INNER_CONFLICT (2–3 POLES)
- poles:
  - pole: <value/need>
    pull: <what it demands>
    fear_if_lost: <fear>
- typical_compromise:
  - pattern: <how they reconcile>
  - failure_case: <when it collapses>

### [M] TABOOS_AND_LIMITS
- hard_no:
  - rule: <they won't do X>
    exception_condition: <only if ...>
- soft_no:
  - rule: <they avoid Y>
    pressure_points: <what can force it>

### [M] LEVER_LIST (SCENE GENERATORS)
- levers:
  - lever: <pressure type>
    best_scene_use: <what scene it creates>
    risk: <what can go wrong in writing>

### [M] BEHAVIOR_PREDICTIONS
- if_then_rules:
  - if: <situation>
    then: <likely action>
    because: <driver/fear>
- contradiction_alerts:
  - alert: <what would contradict motive map>
    fix: <how to repair>

### [M] UNKNOWN_AND_CONFLICTS
- status: OK|UNKNOWN|CONFLICT
- unknown_claims:
  - claim: <unverified backstory/trauma>
    action: VERIFY|REMOVE|ESCALATE
    required_keys: [<KEY>, ...]

### [M] HANDOFF
- to_personality_psychologist_notes:
  - <what traits should support this motive map>
- to_relationship_designer_notes:
  - <attachment + vulnerability points>
- to_dialogue_analyst_notes:
  - <subtext lines and avoidance themes>
- next_best_specialists: [<KEY>, ...]

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] QUALITY_GATES
PASS если:
- DRIVERS заполнены (core_needs_ranked + core_wants_ranked)
- FEARS_AND_LOSSES заполнены (минимум primary_fears)
- INNER_CONFLICT есть (минимум 2 poles)
- TRIGGER_SET есть (если trauma_status не NONE)
- IF_THEN_RULES есть (минимум 3)

FAIL если:
- мотивация “потому что так надо сюжету” без драйверов
- травма описана как “факт”, но без триггеров/защит/цены
- нет ограничений hard_no/soft_no (персонаж становится “универсальным”)

GAP если:
- нет CHARACTER_CORE_SPEC и нет BACKSTORY_SEEDS/SCENE_SAMPLES

STOP если:
- попытка менять канон-факты без опоры на ядро/зависимости (KEY-only дисциплина нарушена)
