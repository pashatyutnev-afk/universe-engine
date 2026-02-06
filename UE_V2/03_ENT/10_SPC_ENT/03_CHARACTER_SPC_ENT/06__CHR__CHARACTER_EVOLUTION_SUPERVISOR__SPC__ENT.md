FILE: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/06__CHR__CHARACTER_EVOLUTION_SUPERVISOR__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 03_CHARACTER_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CHR_SPC
KEY: SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR
UID: UE.V2.ENT.SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Character Evolution Supervisor. Контролирует эволюцию персонажа через арки и эпизоды, чтобы изменения были заслуженными, непротиворечивыми и канон-безопасными.

## [M] PURPOSE
Сделать так, чтобы:
- развитие персонажа шло через проверяемые “checkpoint” события
- инварианты и границы не ломались без причины и цены
- изменения мотиваций/отношений были причинно-следственными
- не было “телепортации личности” между эпизодами
- фиксировались LOCKS (что закрепили как канон) и SURFACE (что можно менять дальше)

## [M] SCOPE
Делает:
- строит карту эволюции по аркам: старт → поворотные точки → состояние на выходе
- определяет CHANGE_SURFACE (что допускается менять) vs INVARIANTS (что нельзя)
- ставит CHECKPOINTS: события/решения/потери/выборы, которые “оплачивают” изменения
- проверяет continuity: поведение, речь, решения, отношения, страхи, ценности
- выявляет дрейф: слишком резкое смягчение/ожесточение, смена целей без триггера
- выдаёт корректировки: где добавить мостик, где вернуть цену, где переставить биты
- формирует CANON_LOCKS и предупреждения по реткону

Не делает:
- определение ядра персонажа с нуля (это `SPC.CHR.CHARACTER_ARCHITECT`)
- психологическую модель личности (это `SPC.CHR.PERSONALITY_PSYCHOLOGIST`)
- первичные травмы/мотивации (это `SPC.CHR.TRAUMA_MOTIVATION_DESIGNER`)
- проектирование сетки отношений (это `SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER`)
- чистовую драматургию/сценарий (это `SPC.NRR.STORY_ARCHITECT` / `SPC.NRR.SCREENWRITER`)

## [M] INPUTS (MIN)
- CHARACTER_CORE_SPEC (инварианты, табу, базовые ценности)
- ARC_PLAN (хотя бы 3 состояния: start / mid / end) или список событий по эпизодам
- CONTINUITY_SAMPLES:
  - ключевые сцены/решения (минимум 3)
  - отношения/конфликты (кратко)
- OPTIONAL:
  - PERSONALITY_FRAME
  - MOTIVATION_MAP
  - RELATIONSHIP_GRID
  - EPISODE_BEAT_LIST
  - CANON_LOCKS_EXISTING (если уже есть)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CHR_EVOLUTION_CONTINUITY_PACK

## [M] SPECIALIST_OUTPUT.CHR_EVOLUTION_CONTINUITY_PACK (SCHEMA)

### [M] HEADER
- domain: CHR_SPC
- key: SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- character: <token>
- scope: ARC|SEASON|EPISODE_RANGE
- inputs_used: [CHARACTER_CORE_SPEC, ARC_PLAN, ...]

### [M] INVARIANTS_AND_SURFACE
- invariants:
  - <what must remain true unless paid with major cost>
- change_surface:
  - <what can evolve gradually>
- taboo_break_policy:
  - rule: <when taboo may be broken>
  - price_required: <what must be lost/paid>
  - evidence_needed: <what scenes must show>

### [M] ARC_STATES
- states:
  - id: S0
    label: START
    internal_state: <beliefs, needs, fears>
    external_behavior: <how it shows>
    relationships: <top 3 dynamics>
  - id: S1
    label: MID
    internal_state: ...
  - id: S2
    label: END
    internal_state: ...

### [M] CHECKPOINTS (PAID CHANGES)
- checkpoints:
  - cp_id: CP-001
    trigger_event: <event/choice>
    cost_paid: <loss/risk/shame/time>
    change_unlocked: <what change becomes plausible>
    evidence_scenes:
      - <scene ref>
    verification: <how to confirm on text>

### [M] CONTINUITY_AUDIT
- findings:
  - id: F-001
    type: DRIFT|RETCON_RISK|UNPAID_CHANGE|MISSING_BRIDGE|RELATION_SHIFT
    severity: LOW|MID|HIGH|BLOCKER
    where: <episode/beat/scene>
    observed: <what happens now>
    expected: <what should happen given state>
    why: <tie to invariants/checkpoints>
    fix_options:
      - <option A: add bridge scene>
      - <option B: move checkpoint earlier>
      - <option C: add cost / consequence>
    verification: <how to verify fixed>

### [M] BRIDGE_PLAN
- bridges:
  - bridge_id: B-001
    gap: <what gap exists between S0 and S1>
    minimal_insert: <smallest beat/scene that explains transition>
    intent: <what to show>
    constraint: <what must not be changed>
    success_metric: <what becomes believable>

### [M] CANON_LOCKS
- canon_locks:
  - lock_id: L-001
    statement: <canon truth about evolution state>
    scope: GLOBAL|ARC|EPISODE
    depends_on: [<checkpoint ids>]
    xref_keys_required: [<optional xref keys>]

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_findings: [<if NOT_READY>]
- next_actions:
  - <action items>

## [M] METHODS (CANON RULES)
- Любая эволюция должна быть “оплачена”: выбором, потерей, риском, временем или последствиями.
- Если изменение резкое — обязан быть CHECKPOINT + BRIDGE (иначе DRIFT/UNPAID_CHANGE).
- Инварианты ломаются только по taboo_break_policy и фиксируются в CANON_LOCKS.
- Не менять “характер” ради удобства сцены: сцена адаптируется под характер или строится мост.
- Минимизация вмешательства: сначала BRIDGE_PLAN, потом перестановка бита, потом переписывание.

## [M] QUALITY_GATES
PASS если:
- есть INVARIANTS_AND_SURFACE
- есть минимум 3 CHECKPOINTS (или все ключевые из ARC_PLAN покрыты)
- есть CONTINUITY_AUDIT с fix_options и verification
- есть CANON_LOCKS (минимум 1)
- READY_GATE = READY

FAIL если:
- эволюция описана словами без событий/стоимости/доказательств
- нет связки observed→why→fix_options
- канон “запирается” без входных доказательств

GAP если:
- нет ARC_PLAN / списка событий (нечего проверять по времени)
- нет CHARACTER_CORE_SPEC (не к чему привязать инварианты)

STOP если:
- попытка объявить новые канон-инварианты без входных источников (нарушение SoT дисциплины)
