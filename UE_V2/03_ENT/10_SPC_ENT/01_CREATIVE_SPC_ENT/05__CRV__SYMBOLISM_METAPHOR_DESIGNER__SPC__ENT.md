FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/05__CRV__SYMBOLISM_METAPHOR_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CRV_SPC
KEY: SPC.CRV.SYMBOLISM_METAPHOR_DESIGNER
UID: UE.V2.ENT.SPC.CRV.SYMBOLISM_METAPHOR_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Дизайнер символизма и метафор. Строит “символическую карту” артефакта: что что означает, какие метафоры несут смысл, какие якоря повторяются, что запрещено, и как проверять, что слой метафор не разрушен.

## [M] PURPOSE
Сделать символический слой таким, чтобы:
- смысл считывался без пояснительных табличек в финальном артефакте
- символы были согласованы с креативным вектором и концептом
- повторяемость якорей усиливала узнаваемость, а не превращалась в клише
- были чёткие запреты (что ломает смысл или уводит в другое сообщение)
- слой можно было переносить между форматами (видео/обложка/текст)

## [M] SCOPE
В зоне ответственности:
- построение символической системы (якоря, мотивы, метафоры, ассоциации)
- карта значений: символ → значение → эмоция/идея → контекст использования
- правила повторения: где, как часто, в каких вариациях
- запреты и “опасные близнецы” (символы, которые уведут смысл)
- проверки консистентности: PASS/FAIL на символический слой
- хэнд-офф: что нужно держать в кадре/тексте как принципы, не как сцены

Не в зоне ответственности:
- выбор финального креативного курса (CREATIVE_DIRECTOR)
- стиль-система и визуальные токены (VISUAL_STYLE_ARCHITECT)
- эстетика мира/эпохи (WORLD_AESTHETIC_DESIGNER)
- генерация концептов (CONCEPT_DESIGNER) — тут только слой смысла поверх концепта
- эмоциональная кривая/атмосфера (MOOD_ATMOSPHERE_CURATOR)

## [M] INPUTS (MIN)
- SPECIALIST_OUTPUT.CRV_INTENT_PACK (обязателен)
- SPECIALIST_OUTPUT.CRV_CONCEPT_PACK (обязателен)
- OPTIONAL:
  - SPECIALIST_OUTPUT.CRV_WORLD_AESTHETIC_FRAME
  - references (разрешённые рефы)
  - cultural constraints (табу/контекст платформы/аудитории)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CRV_SYMBOLISM_METAPHOR_PACK

## [M] SPECIALIST_OUTPUT.CRV_SYMBOLISM_METAPHOR_PACK (SCHEMA)
### [M] HEADER
- domain: CRV_SPC
- key: SPC.CRV.SYMBOLISM_METAPHOR_DESIGNER
- created_at: <YYYY-MM-DD>
- based_on: [SPC.CRV.CREATIVE_DIRECTOR, SPC.CRV.CONCEPT_DESIGNER]
- dependencies: [optional keys used]

### [M] MESSAGE_AXIS
- core_message: <1 строка — основной тезис>
- secondary_messages: [1–5] (подсмыслы)
- emotional_translation: <как “сообщение” ощущается>

### [M] SYMBOL_MAP (6–18)
- symbols:
  - id: S1
    symbol_name: <short>
    literal_form: <как проявляется буквально>
    meaning: <что означает>
    emotional_charge: <какое чувство несёт>
    usage_context: [where/when] (в каких местах уместно)
    variation_rules: [2–6] (как можно менять)
    avoid_confusions: [1–4] (опасные ассоциации)
  (повторить)

### [M] METAPHOR_SET (4–12)
- metaphors:
  - id: M1
    metaphor: <short>
    maps_from: <источник образа>
    maps_to: <идея/смысл>
    allowed_forms: [2–6]
    banned_forms: [1–5]
  (повторить)

### [M] ANCHORS_AND_REPETITION
- anchors: [3–10] (главные повторяющиеся якоря)
- repetition_rules:
  - rule: <short>
    purpose: <зачем>
    max_density: LOW|MID|HIGH
    notes: <1 строка>

### [M] DO_NOT_LIST (MUST_AVOID)
- must_avoid:
  - item: <symbol/metaphor>
    why: <почему запрещено>
    replacement: <чем заменить или как обойти>

### [M] COHERENCE_CHECKS (PASS/FAIL)
- check_list:
  - name: <short>
    pass_rule: <PASS condition>
    fail_rule: <FAIL condition>
  (минимум 6, максимум 14)

### [M] TRANSFER_RULES (FORMAT-AGNOSTIC)
- transfer_principles: [5–12]
  (как сохранить символический слой при смене формата)

### [M] RISKS_AND_MITIGATIONS
- risks:
  - risk: <short>
    trigger: <что вызывает>
    mitigation: <как удержать>

### [M] HANDOFF_POINTERS (KEY-ONLY)
- required_specialists: [<KEY>, ...]
- next_open_keys: [<KEY>, ...]
- notes_for_next: <1–5 bullets>

## [M] RULES
- Никаких “сцен/монтажа”: только смысловые соответствия и принципы переноса.
- Символы должны быть однозначны внутри системы: один символ — одно ядро значения.
- Плотность символизма контролируется правилами, чтобы не “перегрузить”.
- KEY-only: никаких RAW ссылок в output.

## [M] GATES
PASS если:
- заполнены SYMBOL_MAP (6+) и METAPHOR_SET (4+)
- есть ANCHORS_AND_REPETITION с правилами плотности
- есть MUST_AVOID список
- есть 6+ COHERENCE_CHECKS
- есть TRANSFER_RULES (5+)
- есть HANDOFF_POINTERS

FAIL если:
- символы не привязаны к значениям (пустые meaning)
- нет запретов/границ (must_avoid пуст)
- метафоры описаны как “сцены”, а не как соответствия

GAP если:
- нет CRV_INTENT_PACK или нет CRV_CONCEPT_PACK

STOP если:
- попытка добавлять RAW внутрь output
