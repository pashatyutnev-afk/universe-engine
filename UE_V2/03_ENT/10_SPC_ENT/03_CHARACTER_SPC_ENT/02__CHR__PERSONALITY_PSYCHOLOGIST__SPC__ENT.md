FILE: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/02__CHR__PERSONALITY_PSYCHOLOGIST__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 03_CHARACTER_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CHR_SPC
KEY: SPC.CHR.PERSONALITY_PSYCHOLOGIST
UID: UE.V2.ENT.SPC.CHR.PERSONALITY_PSYCHOLOGIST.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Personality Psychologist. Моделирует устойчивые черты личности и поведенческую консистентность.

## [M] PURPOSE
Построить PERSONALITY_FRAME так, чтобы:
- поведение персонажа было предсказуемо в рамках его личности (но не плоско)
- реакции на стресс/конфликт были согласованы с типом копинга
- можно было валидировать сцены/диалоги на “это он/она или нет”
- профиль личности работал как “фильтр решений” совместно с Character Architect

## [M] SCOPE
Делает:
- определяет стабильные черты (traits) и их выраженность
- описывает социальную маску vs приватное “я”
- задаёт типовые паттерны коммуникации и границы
- определяет coping-стили и стресс-реакции (в связке с триггерами)
- выдаёт “behavioral tells” (мелкие признаки) для узнаваемости

Не делает:
- травмы/мотивации как первопричины (это `SPC.CHR.TRAUMA_MOTIVATION_DESIGNER`)
- развитие по аркам (это `SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR`)
- разбор отношений как системы (это `SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER`)
- финальную проверку конкретных реплик (это `SPC.CHR.DIALOGUE_BEHAVIOR_ANALYST`)

## [M] INPUTS (MIN)
- CHARACTER_CORE_SPEC (от `SPC.CHR.CHARACTER_ARCHITECT`) или краткое ядро
- OPTIONAL:
  - SCENE_SAMPLES (2–8 примеров поведения/реплик)
  - STRESS_EVENTS (что персонаж переживает)
  - CULTURE_CONTEXT (нормы среды/эпохи)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CHR_PERSONALITY_FRAME

## [M] SPECIALIST_OUTPUT.CHR_PERSONALITY_FRAME (SCHEMA)

### [M] HEADER
- domain: CHR_SPC
- key: SPC.CHR.PERSONALITY_PSYCHOLOGIST
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- character_token: <id/name>
- dependencies_keys: [<KEY>, ...]

### [M] TRAIT_PROFILE
- primary_traits:
  - trait: <e.g., openness, conscientiousness, dominance, empathy, neuroticism>
    level: LOW|MID|HIGH
    notes: <1 line behavioral meaning>
- secondary_traits:
  - trait: <...>
    level: LOW|MID|HIGH
    notes: <1 line>

### [M] TEMPERAMENT_AND_ENERGY
- baseline_energy: LOW|MID|HIGH
- social_energy: INTROVERT|AMBIVERT|EXTROVERT
- stimulation_need: LOW|MID|HIGH
- pace: SLOW|MID|FAST
- recovery_style: ALONE|WITH_TRUSTED|ACTION|SLEEP|RITUAL

### [M] VALUES_AND_MORAL_STYLE (LINKED)
- moral_style: RULE|CARE|LOYALTY|POWER|FREEDOM|PRAGMATIC
- value_conflicts:
  - conflict: <value vs value>
    typical_resolution: <pattern>

### [M] COMMUNICATION_PROFILE
- default_voice: <calm, sharp, playful, formal, etc>
- speech_rhythm: SHORT|MID|LONG
- directness: LOW|MID|HIGH
- humor_usage: NONE|LOW|MID|HIGH
- conflict_style: AVOID|COMPETE|NEGOTIATE|APPEASE|DOMINATE
- boundaries:
  - boundary: <what they won’t discuss/do>
    tell: <how it shows>

### [M] STRESS_AND_COPING
- stress_signals:
  - signal: <behavioral sign>
    escalation_level: 1..5
- coping_modes_ranked:
  - mode: FIGHT|FLIGHT|FREEZE|FAWN|CONTROL|WITHDRAW|INTELLECTUALIZE|HUMOR
    rank: 1..N
    when: <typical trigger>
    cost: <what it breaks>
- meltdown_pattern:
  - threshold: <what pushes over>
  - behavior: <what happens>
  - recovery: <how returns>

### [M] SOCIAL_MASK_VS_PRIVATE_SELF
- public_mask: <how they appear>
- private_self: <how they are with trust>
- reveal_triggers:
  - trigger: <what makes mask drop>
    result: <what changes>

### [M] BEHAVIORAL_TELLS (SIGNATURES)
- tells:
  - tell: <small repeated behavior>
    meaning: <what it signals>
- pet_phrases:
  - <optional; if allowed by style>
- micro_habits:
  - <gesture / routine / reaction>

### [M] CONSISTENCY_RULES (OOC FILTER)
- must_be_true:
  - rule: <if situation X then likely Y>
- cannot_be_true:
  - rule: <they would not do/say Z unless condition>
- ooc_alarm_signals:
  - <signals that writer drifted>

### [M] UNKNOWN_AND_CONFLICTS
- status: OK|UNKNOWN|CONFLICT
- unknown_claims:
  - claim: <unverified trait>
    action: VERIFY|REMOVE|ESCALATE
    required_keys: [<KEY>, ...]

### [M] HANDOFF
- to_dialogue_analyst_notes:
  - <what to watch in lines>
- to_relationship_designer_notes:
  - <attachment style / bonding quirks>
- to_trauma_motivation_designer_notes:
  - <likely origins / fragile points>
- next_best_specialists: [<KEY>, ...]

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] QUALITY_GATES
PASS если:
- TRAIT_PROFILE заполнен (минимум primary_traits)
- STRESS_AND_COPING есть (минимум coping_modes_ranked + stress_signals)
- COMMUNICATION_PROFILE есть
- CONSISTENCY_RULES есть (must_be_true + cannot_be_true)
- UNKNOWN_AND_CONFLICTS присутствует

FAIL если:
- “описание характера” без правил консистентности
- нет стресс-паттернов (персонаж становится “универсальным”)
- отсутствуют ограничения “cannot_be_true”

GAP если:
- нет CHARACTER_CORE_SPEC и нет примеров поведения/реплик

STOP если:
- попытка делать канон-вердикты (это роль Governance) или обход KEY-only routing
