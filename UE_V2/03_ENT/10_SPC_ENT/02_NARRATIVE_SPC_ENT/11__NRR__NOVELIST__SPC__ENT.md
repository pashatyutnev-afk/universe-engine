FILE: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/11__NRR__NOVELIST__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 02_NARRATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: NRR_SPC
KEY: SPC.NRR.NOVELIST
UID: UE.V2.ENT.SPC.NRR.NOVELIST.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Novelist. Превращает narrative-структуру (beats/scenes) в прозаический текст (главы/сцены) без поломки канона и тональности.

## [M] PURPOSE
Выпустить NOVEL_CHAPTER_DRAFT_PACK так, чтобы:
- структура (beats) сохранилась, но текст стал “читаемым” как проза
- голос повествования и тон были стабильны и контролируемы
- экспозиция дозировалась, а не “вываливалась”
- диалоги и внутренний монолог работали на тему и арку
- все лор/канон-ограничения соблюдены или явно помечены как UNKNOWN/ESCALATE
- результат можно было итеративно улучшать через step-run без переписывания с нуля

## [M] SCOPE
Делает:
- преобразование: OUTLINE/SCENE_DRAFT → CHAPTER_PROSE
- настройку POV, времени (past/present), дистанции и ритма прозы
- сцено-описания, переходы, “склейки”, внутренние состояния
- мягкую интеграцию диалогов (в сотрудничестве с `SPC.NRR.DIALOGUE_WRITER`)
- выпуск набора “вариантов” для сложных сцен (A/B), если нужно

Не делает:
- изменения структуры истории без согласования (`SPC.NRR.STORY_ARCHITECT` / `SPC.NRR.EPISODE_SHOWRUNNER`)
- лор-вердикты (это `SPC.NRR.LORE_MASTER`)
- финальную редактуру стиля/литературной чистоты уровня издателя (может быть отдельный редактор позже)

## [M] INPUTS (MIN)
- STORY_STRUCTURE / EPISODE_BEATS / ARC_OUTLINE
- SCENE_LIST (кто-где-когда + цель сцены)
- OPTIONAL:
  - TONE_GUIDE (если есть)
  - CHARACTER_VOICES (если есть)
  - LORE_CONSTRAINTS_PACK (желательно)
  - STYLE_CONSTRAINTS (темп, длина, уровень метафор, степень “киношности”)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.NRR_NOVEL_CHAPTER_DRAFT_PACK

## [M] SPECIALIST_OUTPUT.NRR_NOVEL_CHAPTER_DRAFT_PACK (SCHEMA)

### [M] HEADER
- domain: NRR_SPC
- key: SPC.NRR.NOVELIST
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- format: NOVEL|NOVELLA|SERIAL|WEB
- pov_mode: 1ST|3RD_LIMITED|3RD_OMNI|MIXED
- tense: PAST|PRESENT|MIXED
- target_length:
  - chapters: <int>
  - words_per_chapter: <int or range>
- dependencies_keys: [<KEY>, ...]

### [M] CHAPTERS
- chapters:
  - chapter_id: CH1
    title: <optional>
    summary_1line: <1 line>
    beats_covered: [B1, B2, ...]
    pov_character: <name>
    setting: <place/time>
    prose_draft: |
      <chapter text here>

### [M] SCENE_MODULES (OPTIONAL)
Использовать, если нужно отдавать сценами, а не целой главой.
- scenes:
  - scene_id: S1
    beat_ref: B3
    goal: <what changes>
    conflict: <core friction>
    outcome: <result>
    prose_draft: |
      <scene text here>

### [M] STYLE_AND_VOICE_CONTROLS
- style_tokens:
  - token: <e.g., "short sentences", "dense imagery", "minimal metaphor">
    level: LOW|MED|HIGH
- voice_rules:
  - rule: <short rule>
- banned_patterns:
  - pattern: <what to avoid>
    reason: <why>

### [M] EXPO_BALANCE (MUST)
- exposition_checks:
  - check: "info dump risk"
    result: OK|RISK|FAIL
    note: <1 line>
  - check: "context clarity"
    result: OK|RISK|FAIL
    note: <1 line>

### [M] CANON_AND_LORE_COMPLIANCE
- lore_alignment:
  - status: OK|UNKNOWN|CONFLICT
  - evidence_keys: [<KEY>, ...]
  - notes: <short>
- unknown_claims:
  - claim: <what is asserted but not verified>
    where: <chapter/scene>
    action: VERIFY|REMOVE|ESCALATE
    required_keys: [<KEY>, ...]

### [M] VARIANTS (OPTIONAL)
- variants:
  - id: V1
    target: CH2|S5
    axis: PACING|VOICE|IMAGERY|DIALOGUE_DENSITY|EXPOSITION
    prose_draft: |
      <variant text>

### [M] REVISION_NOTES
- notes:
  - item: <what to improve next>
    priority: P0|P1|P2
- questions_to_room:
  - <question that blocks a clean draft>

### [M] HANDOFF
- next_best_specialists: [<KEY>, ...]
- suggestions:
  - to: SPC.NRR.DIALOGUE_WRITER
    note: <what to tune>
  - to: SPC.NRR.DRAMATURG
    note: <what to validate>
  - to: SPC.NRR.LORE_MASTER
    note: <what to verify>
  - to: SPC.NRR.HEAD_WRITER
    note: <tone/coherence notes>

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] QUALITY_GATES
PASS если:
- есть минимум 1 глава/сцена в прозе (не только план)
- явно задан POV + tense
- EXPO_BALANCE заполнен
- CANON_AND_LORE_COMPLIANCE заполнен (даже если “UNKNOWN”)
- есть REVISION_NOTES + HANDOFF
- нет скрытых структурных изменений без отметки

FAIL если:
- выдан “литературный текст” без привязки к beats/scenes
- нет контроля голоса/POV/tense
- канон/лор никак не отмечены (как будто “само понятно”)

GAP если:
- нет структуры (beats/scenes) или неясно что писать

STOP если:
- попытка обхода KEY-only routing или вставка RAW в рабочие пакеты
