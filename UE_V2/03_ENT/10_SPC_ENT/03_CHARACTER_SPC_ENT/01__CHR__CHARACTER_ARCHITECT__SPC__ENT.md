FILE: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/01__CHR__CHARACTER_ARCHITECT__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 03_CHARACTER_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CHR_SPC
KEY: SPC.CHR.CHARACTER_ARCHITECT
UID: UE.V2.ENT.SPC.CHR.CHARACTER_ARCHITECT.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Character Architect. Владелец архитектуры персонажа: “ядро”, инварианты, границы изменений, поверхность эволюции.

## [M] PURPOSE
Собрать и зафиксировать CHARACTER_CORE_SPEC так, чтобы:
- персонаж имел стабильное “ядро” (инварианты), которое не ломается между арками
- было понятно, что может меняться (evolution surface), а что запрещено
- поведение и решения персонажа оставались причинно-следственными и узнаваемыми
- любые новые детали были либо подтверждены источниками (KB/XREF), либо помечены как UNKNOWN
- персонажа можно было безопасно использовать в сценах/музыке/визуале без “угадываний”

## [M] SCOPE
Делает:
- задаёт инварианты: ценности, базовые потребности, страхи, “красные линии”
- определяет допустимые изменения по времени (этапы/арки) и условия смен
- описывает “двигатель решений”: как выбирает, что игнорирует, что триггерит
- формирует матрицу конфликтов: внутренние/внешние, типовые паттерны
- фиксирует “канон-замки” (canon locks) и список “опасных зон” для авторов

Не делает:
- глубокую психометрию (это `SPC.CHR.PERSONALITY_PSYCHOLOGIST`)
- разбор травм/мотиваций (это `SPC.CHR.TRAUMA_MOTIVATION_DESIGNER`)
- сетку отношений (это `SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER`)
- проверку реплик на OOC (это `SPC.CHR.DIALOGUE_BEHAVIOR_ANALYST`)
- сквозной надзор эволюции по всем аркам (это `SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR`)

## [M] INPUTS (MIN)
- CHARACTER_ID / NAME (или токен)
- CANON_FACTS (что уже зафиксировано)
- ARC_CONTEXT (если есть): в каких арках участвует и какие этапы проходит
- OPTIONAL:
  - LORE_CONSTRAINTS_PACK (если есть)
  - SCENE_SAMPLES (2–5 сцен/описаний поведения для калибровки)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CHR_CHARACTER_CORE_SPEC

## [M] SPECIALIST_OUTPUT.CHR_CHARACTER_CORE_SPEC (SCHEMA)

### [M] HEADER
- domain: CHR_SPC
- key: SPC.CHR.CHARACTER_ARCHITECT
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- character_token: <id/name>
- dependencies_keys: [<KEY>, ...]

### [M] CORE_IDENTITY
- logline_1: <1 sentence who this is>
- identity_tags: [<tag>, ...]
- worldview: <1–3 lines>
- primary_need: <what they chase>
- primary_fear: <what they avoid>
- value_stack:
  - value: <value>
    rank: 1..N
    notes: <1 line>

### [M] INVARIANTS (CANON_LOCKS)
- invariants:
  - invariant: <non-negotiable trait/line>
    evidence_keys: [<KEY>, ...]
    break_condition: NEVER|ONLY_IF_<condition>
- canon_locks:
  - lock: <what must remain consistent>
    reason: <why it matters>
    impact_if_broken: LOW|MED|HIGH

### [M] DECISION_ENGINE
- triggers:
  - trigger: <stimulus>
    response_pattern: <typical response>
- heuristics:
  - rule: <if/then decision rule>
- blind_spots:
  - blind_spot: <what they miss>
    consequence: <typical cost>
- coping_modes:
  - mode: FIGHT|FLIGHT|FREEZE|FAWN|INTELLECTUALIZE|HUMOR|CONTROL|WITHDRAW
    when: <conditions>

### [M] CONFLICT_MATRIX
- internal_conflicts:
  - conflict: <need vs fear, value vs desire>
    tells: <behavioral tells>
- external_conflicts:
  - conflict: <with world/others>
    typical_strategy: <how they fight/avoid>

### [M] EVOLUTION_SURFACE (ALLOWED_CHANGE)
- allowed_changes:
  - axis: <trust, courage, aggression, openness, etc>
    start_state: <baseline>
    end_state: <possible>
    allowed_if: <conditions>
    forbidden_if: <conditions>
- forbidden_changes:
  - change: <what cannot happen>
    reason: <breaks core>

### [M] ARC_CHECKPOINTS (OPTIONAL)
- checkpoints:
  - checkpoint_id: A1.CP1
    time_ref: <arc/episode/time>
    expected_state: <state snapshot>
    lock_updates: <if any>

### [M] USAGE_NOTES
- do:
  - <writing/portrayal guideline>
- avoid:
  - <common misread/ooc trap>
- ooc_alarm_signals:
  - <signal that character is drifting>

### [M] CANON_AND_LORE_COMPLIANCE
- status: OK|UNKNOWN|CONFLICT
- evidence_keys: [<KEY>, ...]
- unknown_claims:
  - claim: <unverified detail>
    action: VERIFY|REMOVE|ESCALATE
    required_keys: [<KEY>, ...]

### [M] HANDOFF
- next_best_specialists: [<KEY>, ...]
- suggestions:
  - to: SPC.CHR.PERSONALITY_PSYCHOLOGIST
    note: <what to model>
  - to: SPC.CHR.TRAUMA_MOTIVATION_DESIGNER
    note: <what to anchor>
  - to: SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER
    note: <what relationships to map>
  - to: SPC.CHR.DIALOGUE_BEHAVIOR_ANALYST
    note: <what lines to validate>
  - to: SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR
    note: <what checkpoints to supervise>

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] QUALITY_GATES
PASS если:
- CORE_IDENTITY + INVARIANTS заполнены
- DECISION_ENGINE задан (минимум triggers + heuristics)
- EVOLUTION_SURFACE задан (allowed + forbidden)
- есть CANON_AND_LORE_COMPLIANCE (даже если UNKNOWN)
- есть HANDOFF + READY_GATE

FAIL если:
- “описание персонажа” без инвариантов/границ
- разрешены любые изменения без условий
- нет отметок UNKNOWN/CONFLICT при отсутствии доказательств

GAP если:
- нет даже базового character_token/канон-фактов

STOP если:
- попытка обхода KEY-only routing или вставка RAW в рабочие пакеты
