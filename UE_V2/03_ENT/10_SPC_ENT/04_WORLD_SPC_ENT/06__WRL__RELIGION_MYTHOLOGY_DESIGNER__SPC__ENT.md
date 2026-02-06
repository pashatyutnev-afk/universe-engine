FILE: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/06__WRL__RELIGION_MYTHOLOGY_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 04_WORLD_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: WRL_SPC
KEY: SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER
UID: UE.V2.ENT.SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Religion & Mythology Designer. Проектирует религиозные системы, мифологические карты, символы, ритуалы и их социальные функции. Следит за канон-безопасностью и непротиворечивостью мифов с миром/цивилизациями.

## [M] PURPOSE
Сделать религию и мифологию не “украшением”, а работающим слоем мира:
- объясняет смысл, страхи, надежды, табу, мораль и легитимность власти
- создаёт символическую систему и ритуальную практику
- задаёт миф-карты происхождения, судьбы, границ и “почему мир такой”
- обеспечивает сюжетные рычаги: конфликты веры, ереси, культов, расколов
- даёт безопасные канон-ограничения (что нельзя/что обязательно) для других артефактов

## [M] SCOPE
Делает:
- MYTH_MAP: пантеон/сущности/силы, роли и отношения
- COSMOLOGY_FRAME: картина мира (происхождение, устройство, пределы, загробное/между)
- SYMBOL_SYSTEM: символы, знаки, цвета-принципы (не палитры), тотемы, сакральные артефакты
- RITUAL_PRACTICES: ритуалы, праздники, обряды, жертвоприношения/клятвы/инициации
- TABOO_RULES: табу/запреты/чистота/скверна и последствия
- MORAL_CODE: этика/добродетели/грехи в терминах общества
- CULT_VARIANTS: секты/культы/ереси/региональные версии (вариативность без поломки канона)
- LEGITIMACY_LAYER: как религия легитимизирует власть/право/доступ
- MYTH_CONFLICT_ENGINES: генераторы конфликтов (раскол, пророчество, богоизбранность, святыня)
- XREF_ANCHORS: канон-якоря и требования к ссылкам/проверкам

Не делает:
- экономику/власть как механику (это `SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER`, но легитимность согласуется)
- культуру/социальные нормы в деталях (это `SPC.WRL.CULTURE_SOCIETY_ARCHITECT`, но табу/праздники согласуются)
- экосистемы/выживание (это `SPC.WRL.ECOLOGY_SURVIVAL_DESIGNER`, но сакральные места/ресурсы согласуются)
- географию/маршруты (это `SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER`, но святыни/паломничества согласуются)
- таймлайн цивилизаций (это `SPC.WRL.CIVILIZATION_DESIGNER`, но эпохальные религ. сдвиги согласуются)

## [M] INPUTS (MIN)
- WORLD_BASELINE (физика/магия/тех, если есть)
- SOCIETY_SET или CIV_SET (минимум 1 общество/цивилизация)
- OPTIONAL:
  - FACTION_LIST (жречество/ордена/культы)
  - POWER_MAP (если уже есть, для согласования легитимности)
  - KEY_PLACES (святыни/центры/пороги)
  - “CANON_LIMITS” (жёсткие запреты мира)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.WRL_RELIGION_MYTHOLOGY_PACK

## [M] SPECIALIST_OUTPUT.WRL_RELIGION_MYTHOLOGY_PACK (SCHEMA)

### [M] HEADER
- domain: WRL_SPC
- key: SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- societies: [<soc_id>...]
- inputs_used: [WORLD_BASELINE, SOCIETY_SET|CIV_SET, ...]

### [M] SOCIETY_FRAME (PER SOCIETY)
- soc_id: S-01
  name: <token/name>
  belief_style: <animism|polytheism|monotheism|ancestor|cosmic law|tech-faith|hybrid>
  myth_density: <low|mid|high>
  core_question_answered: <what the faith answers in 1 line>

### [M] COSMOLOGY_FRAME
- cos_id: COS-01
  soc_id: S-01
  origin_myth: <1–3 lines>
  world_structure: <layers/realms/between/afterlife tokens>
  fate_logic: <how fate/choice works>
  boundaries:
    - <what cannot be crossed / what happens if crossed>
  contradictions_allowed: <none|folk_variants|schisms>  # controlled variance

### [M] MYTH_MAP
- entities:
  - ent_id: D-01
    soc_id: S-01
    name: <deity/spirit/principle>
    kind: <deity|spirit|ancestor|saint|law|void|machine-god|other>
    domains: [<domain tokens>]
    temperament: <1 line>
    relations: [<links to other ent_id with relation tokens>]
    demanded_offerings: [<service|oath|silence|risk|artifact|other>]
    taboos: [<taboo tokens>]
- myths:
  - myth_id: M-01
    soc_id: S-01
    title: <token>
    purpose: <explains origin/legitimacy/taboo/season/war/afterlife>
    summary: <3–6 lines>
    canon_invariants: [<what must remain true>]
    variants_allowed: [<folk versions allowed>]

### [M] SYMBOL_SYSTEM
- symbols:
  - sym_id: SYM-01
    soc_id: S-01
    form: <sigil|totem|gesture|phrase|mark|sound>
    meaning: <1–2 lines>
    usage_rules: <where/how used>
    misuse_consequence: <social/ritual consequence>
- color_principles:
  - principle_id: CP-01
    soc_id: S-01
    principle: <contrast/clarity principle, not palette>
    implication: <what it communicates>

### [M] RITUAL_PRACTICES
- rituals:
  - rit_id: RIT-01
    soc_id: S-01
    name: <token>
    trigger: <season/event/crisis/coming-of-age>
    participants: <who can/should attend>
    steps: [<step tokens, 3–7 items>]
    effect_claimed: <what believers think it does>
    social_effect: <what it actually enforces socially>
    risks: [<risk tokens>]
- calendar:
  - cal_id: CAL-01
    soc_id: S-01
    key_days:
      - <festival/fast/commemoration tokens>

### [M] TABOO_RULES
- taboos:
  - tab_id: TAB-01
    soc_id: S-01
    rule: <do not ...>
    rationale_myth: <linked myth_id or 1 line>
    enforcement: <who enforces>
    violation_consequence: <sanction tokens>
    loopholes: <if any, controlled>

### [M] MORAL_CODE
- virtues: [<virtue tokens>]
- sins: [<sin tokens>]
- redemption_paths:
  - <confession|service|pilgrimage|trial|oath|other>

### [M] CULT_VARIANTS (CONTROLLED VARIANCE)
- variants:
  - var_id: VAR-01
    soc_id: S-01
    type: <sect|cult|heresy|regional variant>
    difference_axis: <doctrine/ritual/symbol/authority>
    conflict_risk: <low|mid|high>
    integration_option: <tolerated|suppressed|absorbed|unknown>

### [M] LEGITIMACY_LAYER (POWER HANDSHAKE)
- legitimacy_claims:
  - lc_id: LGC-01
    soc_id: S-01
    claim: <why ruler/center is legitimate>
    ritual_proof: <rit_id or rule token>
    authority_holders: [<priesthood/order/council tokens>]
    failure_mode: <what breaks legitimacy>

### [M] MYTH_CONFLICT_ENGINES
- conflict_generators:
  - cg_id: MCE-01
    soc_id: S-01
    type: <schism|prophecy|relic|holy site|purity|blasphemy|conversion|holy war>
    trigger_conditions: [<conditions>]
    escalation_path: <1–2 lines>
    deescalation_path: <1–2 lines>
    story_hooks: [<hook tokens>]

### [M] XREF_ANCHORS (SYSTEM SoT)
- anchor_id: XA-RM-01
  soc_id: S-01
  title: <canonical religion anchor>
  summary: <2 lines>
  invariants: [<what must remain true>]
  links_needed: [<xrefs/ids to create>]

### [M] VISUAL_NOTES (NO DIRECTING)
- constraints_only:
  - <what must be communicated as principle>
  - <what must NOT appear to avoid contradictions>
- risks:
  - <misread risk>
  - <anachronism risk>

### [M] HANDSHAKE_CONSTRAINTS
- with_econ_power:
  - <legitimacy alignment requirements>
- with_culture_society:
  - <taboo/norm alignment requirements>
- with_geography:
  - <holy sites/pilgrimage alignment requirements>
- with_narrative:
  - <usable myth conflict engines list>

### [M] GAP_NOTES
- missing_inputs: [..]
- specialists_to_call_next: [SPC.WRL.CULTURE_SOCIETY_ARCHITECT, SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER, ...]
- questions_for_user: [<only if blocking>]

### [M] READY_GATE
- status: READY|NOT_READY
- blockers: [..]
- next_actions: [..]

## [M] METHODS (CANON RULES)
- В каждом обществе должен быть: (1) COSMOLOGY_FRAME, (2) минимум 3 entities, (3) минимум 2 rituals, (4) минимум 3 taboos.
- LEGITIMACY_LAYER обязателен, если у общества есть власть/иерархия.
- CULT_VARIANTS разрешены, но только с явным “что не ломается” (canon_invariants).
- VISUAL_NOTES: только ограничения/риски/принципы считывания. Без монтажных решений и без конкретных палитр.

## [M] QUALITY_GATES
PASS если:
- минимум 1 society
- есть COSMOLOGY_FRAME
- есть минимум 3 entities и 2 myths
- есть минимум 2 rituals и 3 taboos
- есть минимум 2 conflict_generators
- XREF_ANCHORS присутствуют (минимум 2)
- READY_GATE = READY

FAIL если:
- мифология не связана с обществом (нет social_effect / enforcement)
- табу есть, но нет последствий/механики
- LEGITIMACY_LAYER отсутствует при наличии власти
- VISUAL_NOTES содержит режиссуру/монтаж/конкретные палитры

GAP если:
- нет SOCIETY_SET/CIV_SET и нечего якорить
- WORLD_BASELINE конфликтует с миф-утверждениями (не описано как “folk variant”)

STOP если:
- попытка закрепить религиозный канон без минимальных входов
