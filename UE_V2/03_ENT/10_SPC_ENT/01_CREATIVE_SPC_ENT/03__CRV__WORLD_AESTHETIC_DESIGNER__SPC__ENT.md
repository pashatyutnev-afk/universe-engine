FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/03__CRV__WORLD_AESTHETIC_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CRV_SPC
KEY: SPC.CRV.WORLD_AESTHETIC_DESIGNER
UID: UE.V2.ENT.SPC.CRV.WORLD_AESTHETIC_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Дизайнер эстетики мира. Формирует “как ощущается мир” (эпоха, материалность, мотивы, культурные отпечатки) и выдаёт переносимую эстетическую рамку для всех артефактов.

## [M] PURPOSE
Зафиксировать эстетическую идентичность сеттинга/мира так, чтобы:
- визуал, тексты, обложки, видео и промпты не расползались
- можно было делать варианты, но внутри одной эстетической оси
- была понятна “материальность”: что из чего сделано, какая среда, какая культура/технологичность
- появлялись явные запреты и риски визуального/смыслового шума

## [M] SCOPE
В зоне ответственности:
- Aesthetic Frame (эпоха/тон/материальность/культура)
- Motif Map (повторяемые мотивы/детали/символы как признаки мира)
- Material & Tech Feel (уровень технологичности, индустриальность, ручная работа, износ)
- Environmental Feel (климат/свет/пыль/влага/атмосфера как ощущение среды)
- Cultural Imprint (архитектура/орнаменты/формы/поведение объектов — как принципы)
- Coherence tests (PASS/FAIL): “это точно из этого мира” vs “сломалось”

Не в зоне ответственности:
- финальная креативная ось/намерение (CREATIVE_DIRECTOR)
- стиль-токены и композиционные ограничения (VISUAL_STYLE_ARCHITECT)
- генерация концептов (CONCEPT_DESIGNER)
- символизм/метафора как слой смысла (SYMBOLISM_METAPHOR_DESIGNER)
- кривая эмоций (MOOD_ATMOSPHERE_CURATOR)
- стратегия художественного разрыва (ARTISTIC_RISK_DESIGNER) — здесь только эстетические риски мира

## [M] INPUTS (MIN)
- SPECIALIST_OUTPUT.CRV_INTENT_PACK (обязателен)
- OPTIONAL:
  - references (разрешённые источники/референсы)
  - platform constraints (обложка/клип/постер/комикс/текст)
  - continuity constraints (если это серия/сезон/альбомная линия)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CRV_WORLD_AESTHETIC_FRAME

## [M] SPECIALIST_OUTPUT.CRV_WORLD_AESTHETIC_FRAME (SCHEMA)
### [M] HEADER
- domain: CRV_SPC
- key: SPC.CRV.WORLD_AESTHETIC_DESIGNER
- created_at: <YYYY-MM-DD>
- based_on: [SPC.CRV.CREATIVE_DIRECTOR]

### [M] WORLD_IDENTITY
- world_one_liner: <1 строка — “что это за мир по ощущению”>
- era_feel: <коротко: эпоха/век/стадия развития как ощущение>
- tech_level: LOW|MID|HIGH|MIXED
- civilization_texture: <2–4 bullets: “какая цивилизация на коже мира”>

### [M] MATERIALITY
- primary_material_families: [5–12]   (например: камень, металл, стекло, ткань, дерево, композит)
- wear_age_principles: [3–8]          (как выглядит износ/возраст)
- craftsmanship_principles: [3–8]     (ручное/индустриальное/био-органическое — как принцип)
- forbidden_materiality: [2–8]        (что “не из этого мира”)

### [M] ENVIRONMENT_FEEL
- climate_feel: <1 строка>
- air_particles_principles: [2–6]     (пыль/дымка/влага — как ощущение)
- light_in_world_principles: [2–6]    (не монтаж, а “какой свет типично бывает”)
- sound_imagery_hints: [2–6]          (опционально: “как звучит среда” — 1–2 слова)

### [M] CULTURAL_IMPRINT
- architecture_principles: [3–9]      (формы/модули/ритм)
- ornament_language: [2–8]            (узоры/знаки как язык)
- object_design_principles: [3–9]     (как выглядят предметы быта/техника)
- taboo_elements: [2–8]               (что запрещено культурно/эстетически)

### [M] MOTIF_MAP (SIGNATURES)
- signature_motifs: [5–15]            (повторяемые “фирменные” мотивы мира)
- micro_signs: [5–15]                 (малые признаки, которые делают “узнаваемо”)
- motif_usage_limits: [2–8]           (не переборщить)

### [M] VARIATION_LANES
- allowed_variations: [2–8]           (как можно варьировать не ломая мир)
- forbidden_variations: [2–8]         (что сразу ломает)

### [M] COHERENCE_CHECKS (PASS/FAIL)
- check_list:
  - name: <short>
    pass_rule: <PASS condition>
    fail_rule: <FAIL condition>
  (минимум 6, максимум 12)

### [M] RISKS_AND_MITIGATIONS
- risks:
  - risk: <short>
    trigger: <что вызывает>
    mitigation: <как удержать>

### [M] HANDOFF_POINTERS (KEY-ONLY)
- required_specialists: [<KEY>, ...]
- next_open_keys: [<KEY>, ...]
- notes_for_next: <1–3 bullets>

## [M] RULES
- Никаких “монтажных/режиссёрских решений” (кадры, движения, сцены) — только принципы мира.
- Всё формулируется как переносимые правила: “как принято/как ощущается”, а не конкретные сценарии.
- Anti-noise: коротко, структурно, без лирики.
- KEY-only: никаких RAW в output.

## [M] GATES
PASS если:
- заполнены блоки: WORLD_IDENTITY + MATERIALITY + CULTURAL_IMPRINT + MOTIF_MAP
- есть 6+ COHERENCE_CHECKS с pass_rule/fail_rule
- есть VARIATION_LANES + RISKS_AND_MITIGATIONS
- есть HANDOFF_POINTERS (next_open_keys)

FAIL если:
- “это сценарий/сцена” вместо эстетической рамки
- нет мотивов/нет проверок когерентности
- эстетика расплывчатая без запретов/границ

GAP если:
- нет CRV_INTENT_PACK

STOP если:
- попытка добавить RAW ссылки внутрь output
