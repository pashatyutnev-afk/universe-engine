FILE: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/09__NRR__THEME_MEANING_CURATOR__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 02_NARRATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: NRR_SPC
KEY: SPC.NRR.THEME_MEANING_CURATOR
UID: UE.V2.ENT.SPC.NRR.THEME_MEANING_CURATOR.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Theme and meaning curator. Специалист по теме, смыслу и “о чём на самом деле” на уровне эпизода/арки.
Держит смысловую ось, чтобы события работали на идею, а не просто происходили.

## [M] PURPOSE
Выпустить THEME_MEANING_PACK так, чтобы:
- тема была сформулирована ясно (1–2 предложения), без философской воды
- каждый ключевой бит имел смысловую функцию (что он доказывает/опровергает)
- мотивы повторялись осмысленно и усиливали чувство истории
- конфликт, ставки и развязка были согласованы с темой
- можно было быстро проверить: “эпизод говорит то, что мы хотим сказать”

## [M] SCOPE
Делает:
- формулировку THEME_AXIS (тезис/антитезис/вопрос)
- карту смыслов по битам (meaning-by-beat)
- мотивы/символы/повторы и якорные фразы (motif anchors)
- анти-тезисы и “опасные трактовки” (что зритель может понять не так)
- минимальные правки (patchlist) чтобы подтянуть смысл без переписывания всего

Не делает:
- канон-решения и факты лора (LORE_MASTER / GVN)
- причинность/драматургию как таковую (DRAMATURG / STORY_ARCHITECT)
- чисто эмоциональную дугу (EMOTIONAL_ARC_DESIGNER)
- детальный сценарный текст (SCREENWRITER / DIALOGUE_WRITER)

## [M] INPUTS (MIN)
- EPISODE_STRUCTURE (биты/план) или SCENE_LIST
- CURRENT_DRAFT (краткое содержание сцен или черновик)
- OPTIONAL:
  - WORLD_LORE_CONSTRAINTS (от `SPC.NRR.LORE_MASTER`)
  - EMOTION_ARC_PACK (от `SPC.NRR.EMOTIONAL_ARC_DESIGNER`)
  - tone, genre, audience, rating constraints
  - reference works (allowed)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.NRR_THEME_MEANING_PACK

## [M] SPECIALIST_OUTPUT.NRR_THEME_MEANING_PACK (SCHEMA)

### [M] HEADER
- domain: NRR_SPC
- key: SPC.NRR.THEME_MEANING_CURATOR
- created_at: <YYYY-MM-DD>
- dependencies_keys: [<KEY>, ...]
- decision_mode: FAST|RELEASE_READY|MASTERPIECE

### [M] THEME_AXIS
- core_question: <1 sentence: “что проверяет история”>
- thesis: <позиция A>
- antithesis: <позиция B>
- resolution_direction: <куда склоняем ответ к финалу эпизода>
- scope_note: <эпизод/арка/сезон>

### [M] MEANING_BY_BEAT
- beats:
  - id: B1
    event_summary: <что происходит>
    meaning_function: PROPOSE|CHALLENGE|REFUTE|CONFIRM|COST|CHOICE|CONSEQUENCE|REVEAL|TEST
    what_it_says: <1 line: смысл бита>
    theme_link: <как связано с тезисом/антитезисом>
    risk_of_misread: <если есть>

  - id: B2
    ...

### [M] MOTIFS_AND_ANCHORS
- motifs:
  - name: <motif>
    meaning: <что символизирует>
    placements:
      - beat_id: <id>
        form: VISUAL|LINE|ACTION|SOUND|OBJECT
        note: <как проявляется>
- anchor_lines:
  - <короткие фразы/образы, которые стоит повторить или отзеркалить>

### [M] SYMBOLISM_MAP (OPTIONAL)
- symbols:
  - symbol: <object/image>
    interpretation_primary: <primary>
    interpretation_secondary: <secondary>
    avoid: <bad reading to avoid>

### [M] MISREAD_RISKS
- risks:
  - risk: <нежелательная трактовка>
    cause: <почему так может считаться>
    fix: <минимальная правка/уточнение>

### [M] PATCHLIST (MINIMAL)
- minimal_patches:
  - where: <scene/beat>
    change: <маленькое действие/реплика/деталь>
    intended_meaning: <какой смысл усилит>
    cost: LOW|MED|HIGH

### [M] HANDOFF
- next_best_specialists: [<KEY>, ...]
- questions_for_showrunner:
  - <вопрос на подтверждение смысловой оси>
- notes_for_writer_room:
  - <конкретное указание, где усилить тему>
- canon_alignment_note:
  - OK|CHECK
  - if CHECK: <что нужно сверить с LORE_MASTER/GVN>

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] THEME TOOLBOX (REFERENCE)
- Тема ≠ мораль. Тема = вопрос/напряжение смыслов.
- Хороший тест: “если убрать тему, что сломается” — должны сломаться решения персонажей.
- Минимальные усилители:
  - зеркала (то же событие с другим исходом)
  - цена выбора (cost)
  - повтор мотива в новой окраске
  - короткая якорная фраза до и после перелома

## [M] QUALITY_GATES
PASS если:
- есть THEME_AXIS (question+thesis+antithesis)
- есть MEANING_BY_BEAT минимум по ключевым битам
- есть MOTIFS_AND_ANCHORS или честная пометка OPTIONAL пусто
- есть MISREAD_RISKS + PATCHLIST (минимальные правки)
- есть HANDOFF и canon_alignment_note

FAIL если:
- тема расплывчатая, общая, “про жизнь”
- биты не связаны с смыслом (нет функций/связей)
- смысл противоречит финальным решениям персонажей
- нет конкретных патчей

GAP если:
- нет EPISODE_STRUCTURE/SCENE_LIST или нет CURRENT_DRAFT

STOP если:
- попытка обхода KEY-only routing или вставка RAW в рабочие пакеты
