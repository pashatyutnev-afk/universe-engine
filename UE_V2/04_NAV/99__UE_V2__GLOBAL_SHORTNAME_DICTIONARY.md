FILE: UE_V2/04_NAV/99__UE_V2__GLOBAL_SHORTNAME_DICTIONARY.md
SCOPE: UE_V2 / 04_NAV
DOC_TYPE: DICTIONARY (GLOBAL_SHORTNAMES)
UID: UE.V2.NAV.SHORTNAME_DICTIONARY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-05
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: Single Source of Truth for shortnames. No guessing.

---

## [M] PURPOSE
Единый словарь расшифровок всех сокращённых токенов UE_V2.
Нужен для:
- детерминированного понимания имён сущностей/доменных ярлыков/ролей/папок
- снятия “угадываний” при интерпретации названий файлов и KEYS
- согласованности между INDEX_MANIFEST / PIPELINE_CONTRACT / ROUTER / PROMPT_PACKS

## [M] HARD_RULES
- Этот файл — SoT для shortnames.
- Любое новое сокращение добавляется сюда до использования в сущностях/файлах.
- Если есть конфликт (одно сокращение = разные смыслы) → запрещено. Нужно развести токены.
- Описание короткое, 1–2 строки.
- Не хранить RAW ссылок на всё подряд: только “где используется” как категории/пути.
- Не привязываться к конкретной реализации: смысл должен переживать рефактор.

## [M] DICT_SCHEMA (v1)
- TOKEN: <SHORT_TOKEN>
  TYPE: DOMAIN|ROLE|LAYER|ENTITY_FAMILY|PIPE|IDX|ARTIFACT|TAG|OTHER
  FULL: <FULL_CANON_NAME>
  DESC: <ONE_LINE_MEANING>
  EXAMPLES: [<EXAMPLE_KEYS_OR_FILENAMES>]
  USED_IN: [<PATH_PREFIXES_OR_REALMS>]
  STATUS: ACTIVE|DEPRECATED
  UPDATED: 0000-00-00
  NOTES: <OPTIONAL>

---

## [M] TOKENS

### [M] CORE LAYERS / REALMS
- TOKEN: NAV
  TYPE: LAYER
  FULL: Navigation Layer
  DESC: Routing/IDX panels and deterministic entrypoints for runtime navigation.
  EXAMPLES: [NAV.IDX.BOOT, NAV.IDX.ENT]
  USED_IN: [UE_V2/04_NAV]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: ENT
  TYPE: LAYER
  FULL: Entities Layer
  DESC: Families of entities (SPC/ORC/CTL/VAL/QA/XREF etc) and their index manifests.
  EXAMPLES: [03_ENT/10_SPC_ENT, 03_ENT/30_ORC_ENT]
  USED_IN: [UE_V2/03_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: PIPE
  TYPE: LAYER
  FULL: Pipeline Layer
  DESC: Step-run pipelines and contracts that orchestrate execution.
  EXAMPLES: [PIPELINE_CONTRACT]
  USED_IN: [UE_V2/06_PIPE, UE_V2/03_ENT/*/00__PIPELINE_CONTRACT*]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: KB
  TYPE: LAYER
  FULL: Knowledge Base
  DESC: Knowledge inputs/outputs/boundaries used by runtime; not “random notes”.
  EXAMPLES: [KB_SCOPE]
  USED_IN: [UE_V2/??_KB]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: REG
  TYPE: LAYER
  FULL: Registry
  DESC: Registries of rules, canonical lists, UID rules, constraints registries.
  EXAMPLES: [UID_RULES]
  USED_IN: [UE_V2/??_REG]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: XREF
  TYPE: LAYER
  FULL: Cross-Reference
  DESC: Cross-links resolution and pointer discipline across artifacts/entities.
  EXAMPLES: [XREF.RESOLVE]
  USED_IN: [UE_V2/??_XREF]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: LOG
  TYPE: LAYER
  FULL: Logging Layer
  DESC: Run logs, token archive, decision logs, audit trails.
  EXAMPLES: [RUN_LOG, DECISION_LOG]
  USED_IN: [UE_V2/14_LOG]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

### [M] ENTITY FAMILIES / ROLES
- TOKEN: SPC
  TYPE: ROLE
  FULL: Specialist
  DESC: Role-entities that produce structured outputs with constraints and gates.
  EXAMPLES: [SPC.GVN.MACHINE_ARCHITECT, SPC.CRV.CREATIVE_DIRECTOR]
  USED_IN: [UE_V2/03_ENT/10_SPC_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: ORC
  TYPE: ROLE
  FULL: Orchestrator
  DESC: Orchestrates steps, routes execution, assembles packs; does not invent canon.
  EXAMPLES: [MUS.GENRE_STYLE_ROUTER, MUS.RELEASE_PACK]
  USED_IN: [UE_V2/03_ENT/30_ORC_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: CTL
  TYPE: ROLE
  FULL: Controller
  DESC: Enforces controls/constraints, blocking rules, and deterministic checks.
  EXAMPLES: [CTL.*]
  USED_IN: [UE_V2/03_ENT/??_CTL_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: VAL
  TYPE: ROLE
  FULL: Validator
  DESC: Validates artifacts/claims against gates; returns PASS/FAIL with evidence.
  EXAMPLES: [VAL.*]
  USED_IN: [UE_V2/03_ENT/??_VAL_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: QA
  TYPE: ROLE
  FULL: Quality Assurance
  DESC: QA checklists/gates for readiness; may block release if missing evidence.
  EXAMPLES: [MUS.QA_CHECKS]
  USED_IN: [UE_V2/03_ENT/??_QA_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

### [M] DOMAINS (пример. расширяем по мере системы)
- TOKEN: MUS
  TYPE: DOMAIN
  FULL: Music Domain
  DESC: Music artifacts, lyrics, metadata, release packs, portfolio planning.
  EXAMPLES: [MUS.LYRIC_DRAFTER, MUS.RELEASE_PACK]
  USED_IN: [UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT, UE_V2/04_NAV/12__IDX_MUSIC.md]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: AUD
  TYPE: DOMAIN
  FULL: Audio Domain
  DESC: Audio-specific routing/checks (recording/mix/mastering constraints and outputs).
  EXAMPLES: [NAV.IDX.AUD]
  USED_IN: [UE_V2/04_NAV/05__IDX_AUD.md]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: VIS
  TYPE: DOMAIN
  FULL: Visual Domain
  DESC: Visual/video/image domain routing and constraints.
  EXAMPLES: [NAV.IDX.VIS]
  USED_IN: [UE_V2/04_NAV/06__IDX_VIS.md]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

### [M] SPC DOMAINS (из твоих реалмов)
- TOKEN: GVN
  TYPE: DOMAIN
  FULL: Governance
  DESC: Governance specialists: canon verdicts, standards lifecycle, doc-control, pipeline architecture.
  EXAMPLES: [SPC.GVN.GOVERNANCE_OWNER, SPC.GVN.DOC_CONTROLLER]
  USED_IN: [UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: CRV
  TYPE: DOMAIN
  FULL: Creative
  DESC: Creative specialists: creative direction, style system, concepts, symbolism, mood, risks, ideas.
  EXAMPLES: [SPC.CRV.CONCEPT_DESIGNER, SPC.CRV.MOOD_ATMOSPHERE_CURATOR]
  USED_IN: [UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: NRR
  TYPE: DOMAIN
  FULL: Narrative
  DESC: Narrative specialists: story structure, dialogues, theme, cliffhangers, lore, prose.
  EXAMPLES: [SPC.NRR.STORY_ARCHITECT, SPC.NRR.LORE_MASTER]
  USED_IN: [UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: CHR
  TYPE: DOMAIN
  FULL: Character
  DESC: Character specialists: personality, motivation, relationships, character evolution and consistency.
  EXAMPLES: [SPC.CHR.PERSONALITY_PSYCHOLOGIST, SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR]
  USED_IN: [UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05

- TOKEN: WRL
  TYPE: DOMAIN
  FULL: World
  DESC: World specialists: cultures, geography, ecology, systems of power (incl non-currency civilizations).
  EXAMPLES: [SPC.WRL.CIVILIZATION_DESIGNER, SPC.WRL.ECOLOGY_SURVIVAL_DESIGNER]
  USED_IN: [UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT]
  STATUS: ACTIVE
  UPDATED: 2026-02-05
