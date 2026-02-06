FILE: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/08__NRR__EMOTIONAL_ARC_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 02_NARRATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: NRR_SPC
KEY: SPC.NRR.EMOTIONAL_ARC_DESIGNER
UID: UE.V2.ENT.SPC.NRR.EMOTIONAL_ARC_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Emotional arc designer. Специалист по эмоциональной дуге эпизода и точкам перелома.
Делает так, чтобы зритель “проходил” историю сердцем: подъёмы, падения, разрядки, катарсис.

## [M] PURPOSE
Выпустить EMOTION_ARC_PACK так, чтобы:
- эмоции были осмысленным следствием событий, а не случайными качелями
- был понятный эмоциональный вектор главного героя и ключевых фигур
- напряжение росло/сбрасывалось управляемо (tension management)
- каждый важный бит имел эмоциональную функцию (impact)
- можно было проверить: где скука, где перегрев, где недожим

## [M] SCOPE
Делает:
- эмоциональную “кривую” эпизода (moment-to-moment + beat-to-beat)
- карту эмоций персонажей (особенно POV / main)
- рекомендации: усилить/ослабить, где добавить паузу, где ускорить
- привязку эмоций к ставкам, конфликту, теме и клиффхэнгеру
- маркеры: turning points, relief beats, resonance lines

Не делает:
- сюжетный каркас и причинность (STORY_ARCHITECT / DRAMATURG)
- переписывание сцен целиком (SCREENWRITER)
- диалоговую полировку (DIALOGUE_WRITER)
- канон/лор-решения (LORE_MASTER / GVN)

## [M] INPUTS (MIN)
- EPISODE_STRUCTURE (биты/план) или SCENE_LIST
- CURRENT_DRAFT (краткое содержание сцен или черновик)
- POV_FOCUS (кто “ведёт” эмоцию)
- OPTIONAL:
  - THEME_AXIS (от `SPC.NRR.THEME_MEANING_CURATOR`)
  - HOOK_OPTIONS (от `SPC.NRR.CLIFFHANGER_SPECIALIST`)
  - constraints: tone, rating, target audience, references

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.NRR_EMOTION_ARC_PACK

## [M] SPECIALIST_OUTPUT.NRR_EMOTION_ARC_PACK (SCHEMA)

### [M] HEADER
- domain: NRR_SPC
- key: SPC.NRR.EMOTIONAL_ARC_DESIGNER
- created_at: <YYYY-MM-DD>
- dependencies_keys: [<KEY>, ...]
- decision_mode: FAST|RELEASE_READY|MASTERPIECE

### [M] ARC_OVERVIEW
- arc_label: <1 line: “from X to Y”>
- core_emotion: <primary emotion to carry>
- secondary_emotions: [<...>]
- catharsis_target: <what release should feel like>
- audience_feel_goal: <what viewer should feel leaving episode>

### [M] EMOTION_CURVE (BEATS)
- beats:
  - id: B1
    scene_id: <id or empty>
    event_summary: <what happens>
    pov_emotion_before: <emotion>
    pov_emotion_after: <emotion>
    tension_level: 0-10
    valence: NEG|MIX|POS
    function: SETUP|PRESSURE|RELIEF|REVEAL|BOND|LOSS|VICTORY|REVERSAL|CLIMAX|AFTERMATH
    note: <why this beat matters emotionally>

  - id: B2
    ...

### [M] CHARACTER_EMOTION_MAP
- characters:
  - name: <POV/Main>
    baseline: <who they are emotionally at start>
    key_shifts:
      - at: <beat_id>
        shift: <from -> to>
        trigger: <what causes it>
        credibility_check: OK|CHECK
  - name: <Other>
    ...

### [M] TURNING_POINTS
- turning_points:
  - beat_id: <id>
    type: UP|DOWN|TWIST|RELIEF
    description: <what changes emotionally>
    must_be_felt: <how to make it land>

### [M] RELIEF_AND_BREATHING
- relief_beats:
  - beat_id: <id>
    purpose: <reset / intimacy / humor / calm>
    risk_if_missing: <fatigue / numbness / monotony>
- breathing_notes:
  - <1-3 bullets on pacing and pauses>

### [M] PROBLEM_SPOTS (DIAGNOSTIC)
- flat_sections:
  - range: <B3-B5>
    symptom: <no change / same tension>
    fix_options:
      - <option>
- overload_sections:
  - range: <...>
    symptom: <too intense too long>
    fix_options:
      - <option>
- incoherence_flags:
  - beat_id: <id>
    issue: <emotion not earned / jump>
    fix: <minimal patch>

### [M] PATCHLIST (MINIMAL)
- minimal_patches:
  - where: <scene/beat>
    change: <small change>
    expected_effect: <emotion shift>
    cost: LOW|MED|HIGH

### [M] HANDOFF
- next_best_specialists: [<KEY>, ...]
- questions_for_showrunner:
  - <question>
- notes_for_writer_room:
  - <actionable note>
- tie_to_hook:
  - beat_id: <final>
    how_it_primes_cliffhanger: <explain>

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] EMOTION_TOOLBOX (REFERENCE)
- Tension vs Valence:
  - tension_level = насколько “держит”
  - valence = окраска (плюс/минус/смешанная)
- Удержание интереса:
  - микросдвиги каждые 1–3 бита
  - “контраст”: после давления нужна разрядка, иначе онемение
- Честность:
  - эмоция всегда привязана к событию/выбору/потере/обретению
- Посадка катарсиса:
  - готовится заранее: посев → давление → цена → выпуск

## [M] QUALITY_GATES
PASS если:
- есть ARC_OVERVIEW + EMOTION_CURVE по битам
- есть TURNING_POINTS и RELIEF_AND_BREATHING
- есть PROBLEM_SPOTS и PATCHLIST (минимальные правки)
- есть tie_to_hook или пометка CHECK если хука ещё нет

FAIL если:
- кривая эмоций не связана с событиями (придуманная сверху)
- нет разрядок и эпизод “горит” без воздуха
- резкие скачки эмоций без триггера
- нет actionable patchlist

GAP если:
- нет EPISODE_STRUCTURE/SCENE_LIST или нет CURRENT_DRAFT

STOP если:
- попытка обхода KEY-only routing или вставка RAW в рабочие пакеты
