FILE: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/05__WRL__ECONOMY_POWER_SYSTEMS_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 04_WORLD_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: WRL_SPC
KEY: SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER
UID: UE.V2.ENT.SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Economy & Power Systems Designer. Проектирует механику власти, распределения ресурсов, доступа и мотиваций в обществе/цивилизациях. Поддерживает миры без валюты как норму.

## [M] PURPOSE
Сделать так, чтобы “как мир держится” было понятно и стабильно:
- кто принимает решения и почему
- кто чем владеет / кто чем управляет (без привязки к деньгам)
- как распределяются ресурсы, доступ, статус, влияние
- какие рычаги контроля и где уязвимости системы
- какие стимулы двигают персонажей и фракции
- как это влияет на сюжетные конфликты и поведение обществ

## [M] SCOPE
Делает:
- POWER_MAP: карта центров власти и их инструментов
- ACCESS_ECONOMY: модель доступа (право/статус/роль/долг/служение/священный мандат/ресурсные квоты)
- RESOURCE_FLOW: потоки ресурсов (вода/еда/энергия/материалы/знания/безопасность) и узлы контроля
- INCENTIVE_SYSTEM: стимулы и “цена” действий (репутация, долг, обряд, риск, потери доступа)
- GOVERNANCE_MECHANICS: механика управления (назначения, суды, санкции, ритуалы легитимности)
- CONFLICT_ENGINES: генераторы конфликтов (дефицит, монополии, перекрытие доступа, информационная асимметрия)
- STABILITY_RULES: что делает систему устойчивой, что рушит
- NON_CURRENCY_MODELS: типовые модели без денег (gift/merit/queue/mandate/quota/commons/ritual)
- XREF_ANCHORS: якоря систем для канон-проверок и ссылок

Не делает:
- детализация географии/маршрутов (это `SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER`)
- религиозные доктрины и миф-легитимации (это `SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER`, но власть-ритуалы согласуются)
- экология/выживание (это `SPC.WRL.ECOLOGY_SURVIVAL_DESIGNER`, но дефицит/ресурсы согласуются)
- культурные нормы в деталях (это `SPC.WRL.CULTURE_SOCIETY_ARCHITECT`, но статус/роль/табу согласуются)
- макро-цивилизационный таймлайн (это `SPC.WRL.CIVILIZATION_DESIGNER`, но эпохальные сдвиги учитываются)

## [M] INPUTS (MIN)
- WORLD_BASELINE (ограничения физики/магии/теха, если есть)
- REGION_SET или CIV_SET (минимум 1 цивилизация/общество)
- OPTIONAL:
  - RESOURCE_LIST (ключевые ресурсы: вода/еда/энергия/металлы/знания/безопасность)
  - FACTION_LIST (если уже есть)
  - “NO_CURRENCY” flag (по умолчанию: TRUE для великих цивилизаций)
  - CONFLICT_HINTS (если нужен конкретный тип конфликта)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.WRL_ECON_POWER_SYSTEMS_PACK

## [M] SPECIALIST_OUTPUT.WRL_ECON_POWER_SYSTEMS_PACK (SCHEMA)

### [M] HEADER
- domain: WRL_SPC
- key: SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- societies: [<soc_id>...]
- non_currency_default: TRUE|FALSE
- inputs_used: [WORLD_BASELINE, REGION_SET|CIV_SET, ...]

### [M] SOCIETY_FRAME (PER SOCIETY)
- soc_id: S-01
  name: <token/name>
  scale: <tribe|city-state|empire|network|post-scarcity|other>
  baseline_assumption:
    non_currency: TRUE|FALSE
    tech_magic_level: <token>
  core_driver: <what keeps it running in 1 line>

### [M] POWER_MAP
- power_centers:
  - pc_id: P-01
    soc_id: S-01
    name: <council|clan elders|AI core|priesthood|guild|military|archive|other>
    legitimacy_source: <merit|ritual|heritage|service|knowledge|force|mandate|other>
    instruments:
      - <access control>
      - <law/sanctions>
      - <resource routing>
      - <information control>
      - <violence/security>
    dependencies: [<resource_id or system token>]
    vulnerabilities: [<vuln tokens>]
    notes: <1–2 lines>

### [M] ACCESS_ECONOMY (NO-CURRENCY FIRST)
- access_models:
  - model_id: A-01
    soc_id: S-01
    model_type: <merit|mandate|quota|commons|gift|queue|reputation|ritual|service|hybrid>
    what_is_exchanged: <access rights / time / safety / knowledge / energy / etc>
    access_keys:
      - key: <role|rank|oath|license|initiation|token>
        grants: [<what it unlocks>]
        revocation: <how it can be removed>
    pricing_logic:
      - cost_type: <risk|duty|time|service|exposure|sacrifice>
        rule: <rule statement>
    fairness_claim: <how system claims to be fair>
    shadow_market:
      exists: TRUE|FALSE
      form: <favors|black access|smuggling|info leak|corruption|other>

### [M] RESOURCE_FLOW
- resources:
  - resource_id: RSC-01
    name: <water|energy|food|ore|data|security|medicine|other>
    scarcity: <low|mid|high>
    renewability: <renewable|finite|cyclical|unknown>
    criticality: <low|mid|high|existential>
- control_nodes:
  - node_id: N-01
    soc_id: S-01
    node_type: <source|refinery|storage|transport hub|archive|sanctuary|generator>
    controlled_by: <pc_id/faction/token>
    resources: [RSC-01, RSC-02]
    leverage: <what control gives in 1 line>
- flows:
  - flow_id: F-01
    from_node: N-01
    to_node: N-02
    method: <pipeline|caravan|portal|network|ritual|other>
    bottlenecks: [<bottleneck tokens>]
    failure_modes: [<failure tokens>]
    conflict_pressure: <low|mid|high>

### [M] INCENTIVE_SYSTEM
- incentives:
  - inc_id: I-01
    soc_id: S-01
    desired_behavior: <behavior>
    reward: <status|access|safety|knowledge|belonging|other>
    punishment: <ban|downgrade|exile|risk exposure|other>
    tracking_mechanism: <how society tracks compliance>
- social_currency_tokens (allowed even when NO money):
  - token_id: SC-01
    name: <honor|rank|seal|oath-marker|merit-score|memory-credit>
    minted_by: <power center>
    used_for: <what it unlocks>
    fraud_risks: [<risks>]

### [M] GOVERNANCE_MECHANICS
- governance_loops:
  - loop_id: G-01
    soc_id: S-01
    decision_entry: <how issues enter the system>
    deliberation: <who debates/how>
    verdict: <approve/reject/conditional>
    enforcement: <who enforces and how>
    appeal: <is there appeal>
- law_sanction_types:
  - <restriction of access>
  - <service/duty assignment>
  - <ritual penalty>
  - <containment>
  - <memory/record alteration> (если допустимо базовым миром)
- legitimacy_rituals:
  - ritual_id: LR-01
    soc_id: S-01
    trigger: <when performed>
    effect: <what it legitimizes>
    risks: [<risks>]

### [M] CONFLICT_ENGINES
- conflict_generators:
  - cg_id: CEG-01
    soc_id: S-01
    type: <scarcity|monopoly|border control|class access|ideology|information|security|other>
    trigger_conditions: [<conditions>]
    typical_story_arcs: [<arc tokens>]
    escalation_path: <1–2 lines>
    deescalation_path: <1–2 lines>
    hotspots: [<nodes/regions/locations tokens>]

### [M] STABILITY_RULES
- stability_factors:
  - sf_id: ST-01
    soc_id: S-01
    factor: <redundancy|trust|ritual cohesion|tech stability|resource buffer|other>
    how_maintained: <1 line>
- collapse_conditions:
  - cc_id: CL-01
    soc_id: S-01
    condition: <what breaks>
    early_signals: [<signals>]
    consequences: [<consequences>]

### [M] XREF_ANCHORS (SYSTEM SoT)
- anchor_id: XA-EC-01
  soc_id: S-01
  title: <canonical system anchor>
  summary: <2 lines>
  invariants: [<what must remain true>]
  links_needed: [<xrefs/ids to create>]

### [M] VISUAL_NOTES (NO DIRECTING)
- constraints_only:
  - <what must be visible/communicated as principle>
  - <what must NOT appear to avoid contradictions>
- risks:
  - <anachronism risk>
  - <misread of non-currency system risk>

### [M] HANDSHAKE_CONSTRAINTS
- with_world:
  - <resource geography alignment requirements>
- with_culture_society:
  - <status/role alignment requirements>
- with_religion_mythology:
  - <legitimacy ritual alignment requirements>
- with_narrative:
  - <conflict engines usable by story>

### [M] GAP_NOTES
- missing_inputs: [..]
- specialists_to_call_next: [SPC.WRL.CULTURE_SOCIETY_ARCHITECT, SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER, ...]
- questions_for_user: [<only if blocking>]

### [M] READY_GATE
- status: READY|NOT_READY
- blockers: [..]
- next_actions: [..]

## [M] METHODS (CANON RULES)
- По умолчанию: великие цивилизации работают без валюты. Разрешены “токены статуса/доступа”, но не деньги.
- Каждая власть обязана иметь: legitimacy_source + instruments + vulnerabilities.
- Каждый ресурс обязан иметь: scarcity + control_nodes + flows.
- Каждый конфликт обязан иметь: trigger_conditions + escalation_path + deescalation_path.
- VISUAL_NOTES: только ограничения/риски/принципы читаемости, без монтажных решений.

## [M] QUALITY_GATES
PASS если:
- есть минимум 1 society и 3 power_centers
- есть минимум 5 resources и 3 control_nodes
- есть минимум 3 conflict_generators
- non-currency логика явная и непротиворечивая (или явно выключена)
- XREF_ANCHORS присутствуют (минимум 2)
- READY_GATE = READY

FAIL если:
- “власть без рычагов”: power_centers перечислены без instruments/vulnerabilities
- “экономика без потоков”: нет control_nodes/flows
- валюта используется как костыль без объяснения, при включённом non_currency_default
- VISUAL_NOTES содержит режиссуру/монтажные указания

GAP если:
- нет ни REGION_SET ни CIV_SET
- нет RESOURCE_LIST и невозможно вывести ключевые ресурсы из WORLD_BASELINE

STOP если:
- попытка закрепить канон экономики без минимальных входов
