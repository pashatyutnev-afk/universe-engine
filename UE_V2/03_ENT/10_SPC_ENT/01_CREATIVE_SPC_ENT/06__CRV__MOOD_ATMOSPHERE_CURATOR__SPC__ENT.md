FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/06__CRV__MOOD_ATMOSPHERE_CURATOR__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CRV_SPC
KEY: SPC.CRV.MOOD_ATMOSPHERE_CURATOR
UID: UE.V2.ENT.SPC.CRV.MOOD_ATMOSPHERE_CURATOR.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Куратор настроения и атмосферы. Собирает “эмоциональный климат” артефакта: палитру чувств, плотность напряжения, динамику, и правила удержания атмосферы между сценами/куплетами/кадрами — без режиссуры и без монтажа.

## [M] PURPOSE
Сделать атмосферу управляемой и переносимой, чтобы:
- эмоциональный тон был единым и узнаваемым
- динамика (рост/спад) была задана в виде принципов, а не “сюжета”
- не было случайных провалов настроения и конфликтов тональности
- можно было проверить атмосферу чек-листом (PASS/FAIL)
- можно было передать атмосферу в музыку/видео/текст/обложку единым пакетом

## [M] SCOPE
В зоне ответственности:
- mood palette (набор основных настроений и оттенков)
- tension curve (принципиальная кривая напряжения/разрядки)
- energy envelope (уровень энергии по сегментам)
- атмосферные якоря (повторяющиеся ощущения/фактура/температура/пространство)
- правила “что нельзя” (анти-атмосфера: ломатели тона)
- проверки консистентности атмосферы (PASS/FAIL)
- правила переноса между форматами (format-agnostic)

Не в зоне ответственности:
- финальный креативный курс и тезис (CREATIVE_DIRECTOR)
- визуальная стиль-система (VISUAL_STYLE_ARCHITECT)
- эстетика мира/эпохи (WORLD_AESTHETIC_DESIGNER)
- концепт-выбор и вариативка (CONCEPT_DESIGNER)
- символическая карта метафор (SYMBOLISM_METAPHOR_DESIGNER) — тут только настроение/воздух

## [M] INPUTS (MIN)
- SPECIALIST_OUTPUT.CRV_INTENT_PACK (обязателен)
- SPECIALIST_OUTPUT.CRV_CONCEPT_PACK (обязателен)
- OPTIONAL:
  - SPECIALIST_OUTPUT.CRV_SYMBOLISM_METAPHOR_PACK
  - references (разрешённые рефы)
  - constraints (платформа, длительность, аудитория)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CRV_MOOD_ATMOSPHERE_PACK

## [M] SPECIALIST_OUTPUT.CRV_MOOD_ATMOSPHERE_PACK (SCHEMA)
### [M] HEADER
- domain: CRV_SPC
- key: SPC.CRV.MOOD_ATMOSPHERE_CURATOR
- created_at: <YYYY-MM-DD>
- based_on: [SPC.CRV.CREATIVE_DIRECTOR, SPC.CRV.CONCEPT_DESIGNER]
- dependencies: [optional keys used]

### [M] MOOD_PALETTE (3–9)
- primary_moods: [1–3] (основные)
- secondary_moods: [1–6] (вторичные оттенки)
- forbidden_moods: [2–10] (то, что ломает тон)
- mood_notes: <1–6 bullets: как “ощущается”>

### [M] ATMOSPHERE_AXES (5–12)
Оси описывают “воздух” без привязки к конкретным сценам.
- axes:
  - name: <axis name>
    low_end: <что значит низ>
    high_end: <что значит верх>
    target_band: LOW|MID|HIGH (где держим в среднем)
    drift_rule: <как можно смещаться, не ломая атмосферу>
(повторить)

### [M] TENSION_CURVE (PRINCIPLES)
- curve_shape: RISE|FALL|WAVE|PLATEAU|ARC|PULSE
- segments: (3–8 принципиальных сегментов)
  - id: T1
    target_tension: LOW|MID|HIGH
    transition_rule: <как входить/выходить>
    what_changes: [1–4] (что может меняться)
    what_must_stay: [1–4] (что стабильно)
(повторить)

### [M] ENERGY_ENVELOPE
- baseline_energy: LOW|MID|HIGH
- allowed_peaks: 0|1|2|3
- peak_rules:
  - rule: <short>
    cap: LOW|MID|HIGH
    recovery_rule: <как возвращаться>
- anti_peak_rules: [1–5] (что нельзя делать с энергией)

### [M] ATMOSPHERE_ANCHORS (4–12)
- anchors:
  - id: A1
    anchor_name: <short>
    sensory_channel: VISUAL|SOUND|TEXTURE|SPACE|TEMPERATURE|MOTION|SILENCE
    effect: <что ощущается>
    repetition_rule: <как повторять>
    avoid: <что не должно появиться рядом>
(повторить)

### [M] DO_NOT_LIST (MUST_AVOID)
- must_avoid:
  - item: <mood/atmosphere breaker>
    why: <почему ломает>
    replacement: <чем заменить>

### [M] COHERENCE_CHECKS (PASS/FAIL)
- check_list:
  - name: <short>
    pass_rule: <PASS condition>
    fail_rule: <FAIL condition>
(минимум 6, максимум 14)

### [M] TRANSFER_RULES (FORMAT-AGNOSTIC)
- transfer_principles: [6–14]
(как сохранять атмосферу при переносе в музыку/видео/текст/обложку)

### [M] RISKS_AND_MITIGATIONS
- risks:
  - risk: <short>
    trigger: <что вызывает>
    mitigation: <как удержать>

### [M] HANDOFF_POINTERS (KEY-ONLY)
- required_specialists: [<KEY>, ...]
- next_open_keys: [<KEY>, ...]
- notes_for_next: <1–6 bullets>

## [M] RULES
- Никаких монтажных решений и “сцен”. Только оси, правила и проверки.
- Тон задаётся принципами, а не списком “как должно выглядеть”.
- Атмосфера должна быть переносимой: каждый якорь имеет sensory_channel и repetition_rule.
- KEY-only: никаких RAW ссылок в output.

## [M] GATES
PASS если:
- заполнены MOOD_PALETTE и ATMOSPHERE_AXES (5+)
- задан TENSION_CURVE с сегментами (3+)
- задан ENERGY_ENVELOPE с peak_rules
- есть 4+ ATMOSPHERE_ANCHORS
- есть MUST_AVOID список
- есть 6+ COHERENCE_CHECKS
- есть TRANSFER_RULES (6+)
- есть HANDOFF_POINTERS

FAIL если:
- mood описан как “сюжет/сцены”, а не как оси/правила
- нет forbidden/must_avoid
- нет проверок (coherence_checks)

GAP если:
- нет CRV_INTENT_PACK или нет CRV_CONCEPT_PACK

STOP если:
- попытка добавлять RAW внутрь output
