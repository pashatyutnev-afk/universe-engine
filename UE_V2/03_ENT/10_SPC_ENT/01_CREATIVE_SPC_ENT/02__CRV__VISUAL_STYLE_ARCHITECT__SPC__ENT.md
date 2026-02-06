FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/02__CRV__VISUAL_STYLE_ARCHITECT__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CRV_SPC
KEY: SPC.CRV.VISUAL_STYLE_ARCHITECT
UID: UE.V2.ENT.SPC.CRV.VISUAL_STYLE_ARCHITECT.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Архитектор визуальной стилевой системы. Превращает Creative Intent в набор принципов и ограничений визуала, проверок когерентности и “не делаем так”.

## [M] PURPOSE
Сделать визуальную часть детерминированной и переносимой между инструментами (генерация, дизайн, видео, обложки):
- не принимать “монтажных решений”, только ограничения и риски (VISUAL policy)
- формулировать цвет как принципы (контраст/читаемость/иерархия), без конкретных палитр
- определить визуальные законы: композиция, форма, материал, свет, текстуры, типографика/надписи (если допустимы)
- дать тесты когерентности: PASS/FAIL

## [M] SCOPE
В зоне ответственности:
- Visual Principles (общие принципы стиля)
- Style Tokens (словари/классы форм/материалов/света/фактуры/деталей)
- Composition & Framing constraints (рамки кадра/иерархия/центр тяжести — без режиссуры)
- Color & Contrast principles (НЕ палитры)
- Typography/Markings rules (если разрешено): где можно/нельзя, какая роль текста
- Risk & Limits: что ломает стиль, что вызывает “визуальный шум”
- Coherence checks: как понять что “попали в стиль”

Не в зоне ответственности:
- смысл/тема/эмоциональная ось (CREATIVE_DIRECTOR)
- эстетика мира/сеттинга (WORLD_AESTHETIC_DESIGNER)
- символизм/метафора (SYMBOLISM_METAPHOR_DESIGNER)
- кривая эмоций (MOOD_ATMOSPHERE_CURATOR)
- генерация концептов/вариантов (CONCEPT_DESIGNER)
- рисковый дизайн как стратегия разрыва (ARTISTIC_RISK_DESIGNER) — здесь только визуальные риски/ограничения

## [M] INPUTS (MIN)
- SPECIALIST_OUTPUT.CRV_INTENT_PACK (обязателен)
- OPTIONAL:
  - platform constraints (cover/video/poster/app/ui)
  - tool constraints (генератор, формат, лимиты)
  - brand constraints (логотип/надписи/знаки — если применимо)
  - references (разрешённые, если есть)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CRV_VISUAL_STYLE_PACK

## [M] SPECIALIST_OUTPUT.CRV_VISUAL_STYLE_PACK (SCHEMA)
### [M] HEADER
- domain: CRV_SPC
- key: SPC.CRV.VISUAL_STYLE_ARCHITECT
- created_at: <YYYY-MM-DD>
- based_on: [SPC.CRV.CREATIVE_DIRECTOR]

### [M] STYLE_PRINCIPLES
- style_one_liner: <1 строка — как выглядит стиль в целом>
- keywords: [5–15]              (материалы/свет/форма/фактура/ритм)
- tone_principles: [3–7]        (например: “строго”, “тёпло”, “воздушно”)
- complexity_level: MINIMAL|MID|RICH
- noise_budget: LOW|MID|HIGH

### [M] COMPOSITION_CONSTRAINTS (NO-DIRECTING)
- hierarchy_rule: <коротко: что доминирует>
- framing_limits: [2–6]         (например: “без сверх-широкого искажённого угла”)
- geometry_rules: [3–9]         (форма/симметрия/асимметрия/ритм)
- focal_rules: [2–6]            (где допускается фокус, без “режиссуры”)
- forbidden_composition: [2–8]  (что ломает стиль)

### [M] LIGHTING_PRINCIPLES
- light_character: <коротко>
- contrast_principles: [2–6]
- shadow_rules: [2–6]
- forbidden_lighting: [2–8]

### [M] COLOR_PRINCIPLES (NO PALETTES)
- contrast_targets: [2–6]       (например: “читаемый контраст фигура/фон”)
- color_harmony_principles: [2–6]
- saturation_rules: [2–6]
- forbidden_color_behaviors: [2–8]

### [M] MATERIAL_TEXTURE_RULES
- preferred_materials: [3–12]
- preferred_textures: [3–12]
- surface_rules: [2–8]          (глянец/мат/зерно — как принцип)
- forbidden_materials: [2–10]

### [M] DETAILING_RULES
- detail_density: LOW|MID|HIGH
- micro_details_allowed: [2–8]
- clutter_forbidden: [2–8]

### [M] TYPE_MARKS_RULES (IF APPLICABLE)
- text_allowed: true|false
- if_text_allowed:
  - placement_limits: [1–6]
  - readability_principles: [2–6]
  - forbidden_text_styles: [2–8]
- symbol_marks_allowed: true|false
- forbidden_marks: [2–8]

### [M] COHERENCE_CHECKS (PASS/FAIL)
- check_list:
  - name: <short>
    pass_rule: <PASS condition>
    fail_rule: <FAIL condition>
  (минимум 6, максимум 12)

### [M] HANDOFF_POINTERS (KEY-ONLY)
- required_specialists: [<KEY>, ...]
- next_open_keys: [<KEY>, ...]
- notes_for_next: <1–3 bullets>

## [M] RULES
- VISUAL: не принимать монтажных решений, только ограничения/риски/принципы.
- COLOR: только principles (контраст/гармония/насыщенность), без конкретных палитр и без “#”.
- Determinism: каждый блок должен давать исполнимые рамки.
- Anti-noise: никаких длинных эссе, только правило/ограничение/тест.
- KEY-only: никаких RAW в output.

## [M] GATES
PASS если:
- есть минимум: STYLE_PRINCIPLES + COMPOSITION + LIGHTING + COLOR_PRINCIPLES
- есть 6+ COHERENCE_CHECKS с pass_rule/fail_rule
- есть HANDOFF_POINTERS (next_open_keys)

FAIL если:
- есть “режиссура/монтаж” (конкретные планы/движения/сцены)
- задана конкретная палитра/цвета вместо принципов
- нет проверок когерентности

GAP если:
- нет CRV_INTENT_PACK

STOP если:
- попытка добавить RAW ссылки внутрь output
