FILE: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/03__WRL__CIVILIZATION_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 04_WORLD_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: WRL_SPC
KEY: SPC.WRL.CIVILIZATION_DESIGNER
UID: UE.V2.ENT.SPC.WRL.CIVILIZATION_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Civilization Designer. Проектирует цивилизации как макросистемы: эпохи, институты на масштабе, технологический/магический уровень, формы власти, культурные сдвиги и причинные таймлайны.

## [M] PURPOSE
Сделать так, чтобы цивилизационный слой мира:
- давал правдоподобную макро-историю и причины текущего состояния
- обеспечивал “эпохи” и смену фаз (рост/кризис/перезапуск)
- связывал технологии/знания/организацию общества с ресурсами и угрозами
- создавал основу для лора и больших арок без противоречий
- был пригоден для XREF и проверок канона (SoT дисциплина)

## [M] SCOPE
Делает:
- CIV_FRAME: описание цивилизации (идентичность, масштаб, ядро ценностей)
- ERA_MAP: список эпох и “почему эпоха сменилась”
- TECH_MAGIC_LEVEL: уровни технологий/магии и ограничения по эпохам
- GOVERNANCE_PATTERNS: типы власти, легитимность, сменяемость, кризисы
- KNOWLEDGE_FLOW: как знания хранятся/распространяются/теряются
- CIV_CONFLICTS: макроконфликты, войны, миграции, коллапсы, союзы
- CANON_LOCKS: инварианты и “точки невозврата” (что стало фактом мира)
- TIMELINE_ANCHORS: якорные события для NRR/WRL/CHR и XREF

Не делает:
- базовые законы мира и их канонизация (это `SPC.WRL.WORLD_BUILDER` + governance слой)
- микро-проработку культур и институтов повседневности (это `SPC.WRL.CULTURE_SOCIETY_ARCHITECT`)
- географию/маршруты/карты (это `SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER`)
- религии/мифологии как отдельные системы (это `SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER`)
- экономику/власть как механику в деталях (это `SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER`)

## [M] INPUTS (MIN)
- WORLD_BIBLE_FRAME (или минимум: WORLD_BASELINE + CANON_INVARIANTS)
- CIV_SET: 1–3 цивилизации (имена или токены)
- OPTIONAL:
  - ERA_RANGE_HINT (сколько эпох, примерные горизонты)
  - TECH_MAGIC_AXIS (если есть особая магия/технология)
  - NON_CURRENCY_FLAG (если у цивилизаций нет валюты)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.WRL_CIVILIZATION_PACK

## [M] SPECIALIST_OUTPUT.WRL_CIVILIZATION_PACK (SCHEMA)

### [M] HEADER
- domain: WRL_SPC
- key: SPC.WRL.CIVILIZATION_DESIGNER
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- civ_set_id: <token>
- inputs_used: [WORLD_BIBLE_FRAME, CIV_SET, ...]

### [M] CIV_OVERVIEW
- civ_id: CIV-001
  name: <name or token>
  scale: <city-state|kingdom|empire|network|post-scarcity cluster|other>
  core_identity: <1–2 lines>
  core_driver: <resource|threat|belief|tech|ecology|other>
  primary_constraints: [<constraints>]

### [M] ERA_MAP
- civ_id: CIV-001
  eras:
    - era_id: E-01
      name: <era name>
      timeframe: <approx range>
      state: <rise|stable|decline|collapse|rebuild|loop>
      signature: <1 line vibe>
      drivers: [<driver1>, <driver2>]
      constraints: [<what cannot happen here>]
      transition_to_next:
        trigger: <event/system shift>
        cause_chain: <cause → effect>
        canon_lock: <what becomes irreversible>

### [M] TECH_MAGIC_LEVEL
- civ_id: CIV-001
  axis:
    - label: TECH
      level_by_era:
        E-01: <level token>
        E-02: <level token>
    - label: MAGIC
      level_by_era:
        E-01: <level token>
  hard_limits:
    - <limit statement + why>

### [M] GOVERNANCE_PATTERNS
- civ_id: CIV-001
  governance_models:
    - model: <council|dynasty|merit order|ai stewardship|clans|other>
      legitimacy_source: <why accepted>
      stability_factors: [..]
      failure_modes: [..]
      succession_rules: <how power changes>
  power_distribution:
    - centers: [<who holds real power>]
    - checks_balances: [<what restrains power>]

### [M] KNOWLEDGE_FLOW
- civ_id: CIV-001
  storage: [<archives|oral|tech substrate|ritual|other>]
  access_rules: [<who may know what>]
  loss_vectors: [<war|censorship|catastrophe|entropy>]
  transfer_channels: [<schools|guilds|initiations|networks>]

### [M] CIV_CONFLICTS (MACRO)
- conflict_id: MC-001
  civs_involved: [CIV-001, CIV-002]
  type: <war|cold war|migration|resource contest|ideological split|succession crisis>
  cause: <root cause>
  escalation_path: <how it grows>
  resolution_states: [<possible end states>]
  canon_outcome: <if already locked, else empty>
  narrative_hooks: [<NRR use hooks>]

### [M] TIMELINE_ANCHORS (XREF READY)
- anchor_id: A-001
  civ_id: CIV-001
  era_id: E-02
  title: <event title>
  summary: <2–3 lines>
  cause: <why it happened>
  consequence: <what changed>
  references_needed: [<xrefs/ids to create>]
  canon_lock: <what becomes SoT>

### [M] NON_CURRENCY_MECHANICS (IF FLAGGED)
- civ_id: CIV-001
  access_systems:
    - system: <access by rank / obligation / energy quota / reputation / stewardship tokens>
      who_controls: <controllers>
      how_allocated: <rules>
      how_abused: <abuse path>
      how_corrected: <correction path>
  power_without_money:
    - sources: [<knowledge|infrastructure|force|ritual legitimacy|control of gates>]

### [M] HANDSHAKE_CONSTRAINTS
- for_world:
  - <what other WRL specs must respect>
- for_narrative:
  - <era constraints, anchor usage rules>
- for_character:
  - <what backgrounds are plausible / not plausible>
- for_creative:
  - principles: [<symbol principles, motif principles>]
  - risks: [<anachronism risks, coherence risks>]

### [M] GAP_NOTES
- missing_inputs: [..]
- specialists_to_call_next: [SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER, SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER, ...]
- questions_for_user: [<only if blocking>]

### [M] READY_GATE
- status: READY|NOT_READY
- blockers: [..]
- next_actions: [..]

## [M] METHODS (CANON RULES)
- Каждая эпоха обязана иметь: drivers + constraints + trigger + cause_chain + canon_lock (если есть).
- “Технология/магия” описывается как ограничения и последствия, а не как список чудес.
- Если включён NON_CURRENCY_FLAG: власть и доступ описывать через механизмы контроля ресурсов/инфраструктуры/обязательств/ранга, без термина “деньги”.
- Таймлайн якорей должен быть пригоден для XREF: коротко, причинно, проверяемо.

## [M] QUALITY_GATES
PASS если:
- есть минимум 3 эпохи (или по ERA_RANGE_HINT) с причинными переходами
- есть минимум 3 TIMELINE_ANCHORS на цивилизацию
- есть GOVERNANCE + KNOWLEDGE_FLOW + TECH_MAGIC_LEVEL
- READY_GATE = READY

FAIL если:
- “история = список дат” без причин и последствий
- есть анахронизмы без объяснения и без CANON_LOCK/миграции

GAP если:
- нет WORLD_BIBLE_FRAME (или baseline+invariants)
- нет CIV_SET

STOP если:
- попытка выдать канон без минимальных входов
