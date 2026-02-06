FILE: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/04__CHR__RELATIONSHIP_DYNAMICS_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 03_CHARACTER_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CHR_SPC
KEY: SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER
UID: UE.V2.ENT.SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Relationship Dynamics Designer. Проектирует динамику отношений, баланс сил, привязанности, конфликтные петли и точки разрыва.

## [M] PURPOSE
Собрать RELATIONSHIP_GRID так, чтобы:
- отношения были сценогенерирующими (дают действия и выбор, а не справку)
- баланс сил, потребности и уязвимости были видны и проверяемы
- изменения отношений по событиям были детерминированы
- конфликт не был случайным, а вытекал из драйверов и ограничений

## [M] SCOPE
Делает:
- строит карту связей (кто кому кто, что хочет, что боится потерять)
- фиксирует баланс сил (power), зависимость (dependency), доверие (trust)
- описывает тип привязанности и типичные паттерны поведения в паре/группе
- проектирует конфликтные петли (trigger → reaction → escalation → repair)
- задаёт границы, табу, условия примирения и условия разрыва
- формирует сценообразующие “hooks” между персонажами

Не делает:
- ядро персонажа и инварианты (это `SPC.CHR.CHARACTER_ARCHITECT`)
- личностные черты как система (это `SPC.CHR.PERSONALITY_PSYCHOLOGIST`)
- травму/мотивационные карты как первопричины (это `SPC.CHR.TRAUMA_MOTIVATION_DESIGNER`)
- проверку “out-of-character” реплик (это `SPC.CHR.DIALOGUE_BEHAVIOR_ANALYST`)
- контроль эволюции по аркам (это `SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR`)

## [M] INPUTS (MIN)
- CHARACTER_CORE_SPEC (от `SPC.CHR.CHARACTER_ARCHITECT`) или краткое ядро
- RELATIONSHIP_TARGETS: список 2..N персонажей/сторон, для которых строится сетка
- OPTIONAL:
  - PERSONALITY_FRAME (от `SPC.CHR.PERSONALITY_PSYCHOLOGIST`)
  - MOTIVATION_MAP (от `SPC.CHR.TRAUMA_MOTIVATION_DESIGNER`)
  - SCENE_SAMPLES (2–10 сцен/реплик/ситуаций)
  - WORLD_CONSTRAINTS (культура, законы, табу, статусные лестницы)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CHR_RELATIONSHIP_GRID

## [M] SPECIALIST_OUTPUT.CHR_RELATIONSHIP_GRID (SCHEMA)

### [M] HEADER
- domain: CHR_SPC
- key: SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- focal_character_token: <id/name>
- relationship_scope: <pair / team / family / faction / community>
- dependencies_keys: [<KEY>, ...]

### [M] CAST_REGISTRY
- focal: <id/name>
- others:
  - token: <id/name>
    role_in_grid: <ally / rival / mentor / lover / sibling / boss / follower / enemy / unknown>

### [M] RELATIONSHIP_EDGES (PAIRWISE)
- edges:
  - a: <token>
    b: <token>
    relation_label: <one line, e.g. "mentor with hidden leverage">
    bond_type: TRUST|UTILITY|BLOOD|IDEAL|SURVIVAL|ROMANCE|FEAR|CONTROL|DEBT
    attachment_style: SECURE|ANXIOUS|AVOIDANT|DISORGANIZED|MIXED
    power_balance:
      a_over_b: 0..10
      b_over_a: 0..10
      axis: [STATUS, MONEY, VIOLENCE, INFO, LOVE, SKILL, LAW, CHARISMA]
    dependency:
      a_needs_from_b: [<needs>]
      b_needs_from_a: [<needs>]
      switching_cost: LOW|MID|HIGH
    trust_level: 0..10
    respect_level: 0..10
    intimacy_level: 0..10
    loyalty_level: 0..10
    secrecy_level: 0..10
    jealousy_risk: LOW|MID|HIGH
    core_tension:
      want: <what a wants from b or vice versa>
      fear: <what they fear in this relation>
      taboo: <what cannot be said/done>
    vulnerability_points:
      - point: <weak spot>
        exposure_trigger: <when it shows>
        defense: <how they hide>
    conflict_loop:
      trigger: <what starts it>
      reaction_a: <default response>
      reaction_b: <default response>
      escalation_levels:
        - level: 1
          behavior: <mild>
        - level: 2
          behavior: <medium>
        - level: 3
          behavior: <hard>
      repair_path:
        conditions: [<what must happen to repair>]
        gestures: [<what works>]
        cost: <price of repair>
      break_path:
        conditions: [<what breaks it for good>]
        irreversible_line: <hard line crossed>
    scene_hooks:
      - hook: <scene generator>
        best_use: <situation type>
        risk: <what can go wrong in writing>

### [M] GROUP_DYNAMICS (IF SCOPE > 2)
- group_rules:
  hierarchy: <formal/informal ladder>
  coalition_map:
    - bloc: <name>
      members: [<tokens>]
      shared_interest: <one line>
  fault_lines:
    - line: <where group splits>
      trigger: <what activates>
  group_pressure:
    - pressure: <norm/expectation>
      effect_on_focal: <behavior push>
  trust_network_notes:
    - note: <who trusts whom and why>

### [M] CHANGE_EVENTS (STATE TRANSITIONS)
- events:
  - event: <what happened or must happen>
    affected_edges: [<a-b labels>]
    delta:
      trust: -3..+3
      power: -3..+3
      intimacy: -3..+3
      loyalty: -3..+3
    new_constraints:
      - <rule after event>

### [M] BEHAVIOR_PREDICTIONS
- if_then_rules:
  - if: <pressure situation between a and b>
    then: <likely action>
    because: <power/dependency/attachment>
- contradiction_alerts:
  - alert: <what would contradict established dynamics>
    fix: <how to repair>

### [M] UNKNOWN_AND_CONFLICTS
- status: OK|UNKNOWN|CONFLICT
- unknown_claims:
  - claim: <unverified relation fact>
    action: VERIFY|REMOVE|ESCALATE
    required_keys: [<KEY>, ...]

### [M] HANDOFF
- to_dialogue_analyst_notes:
  - <subtext levers, avoidance topics, dominance markers>
- to_story_team_notes:
  - <best conflict hooks, repair hooks, break hooks>
- next_best_specialists: [<KEY>, ...]

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] QUALITY_GATES
PASS если:
- есть CAST_REGISTRY (focal + минимум 2 others)
- есть минимум 2 edges с заполненными power_balance, dependency, trust_level
- у каждой ключевой пары есть conflict_loop (trigger + escalation + repair_path)
- есть scene_hooks (минимум 3 на реалм)

FAIL если:
- отношения описаны только ярлыками без power/dependency/loop
- нет условий repair/break (отношение становится “бесконечным”)
- нет уязвимостей и табу (нет напряжения, сцены не рождаются)

GAP если:
- нет RELATIONSHIP_TARGETS или нет ядра персонажа (CHARACTER_CORE_SPEC)

STOP если:
- попытка объявить канон-факт об отношениях без опоры на зависимости и проверки (KEY-only дисциплина нарушена)
