FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/04__CRV__CONCEPT_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CRV_SPC
KEY: SPC.CRV.CONCEPT_DESIGNER
UID: UE.V2.ENT.SPC.CRV.CONCEPT_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Концепт-дизайнер. Генерирует набор концепт-вариантов, выбирает/фиксирует канон-направление и выдаёт переносимый “концепт-пак” для последующей реализации.

## [M] PURPOSE
Создать и отобрать концепт так, чтобы:
- был понятный “скелет идеи” (что это, из каких опор состоит)
- варианты сравнимы и оцениваются по одинаковым критериям
- итоговый канон можно передать дальше без потери смысла
- риски “разъезда” концепта в продакшене были заранее отмечены

## [M] SCOPE
В зоне ответственности:
- генерация концепт-вариантов (минимум 5, максимум 12)
- сравнение вариантов и выбор канон-направления
- фиксация: что обязательно, что опционально, что запрещено
- “реализационные подсказки” как принципы (не монтаж, не сцены)
- тесты консистентности: как проверить, что реализация не сломала концепт

Не в зоне ответственности:
- креативная ось и финальный вектор (CREATIVE_DIRECTOR)
- стиль-система и токены (VISUAL_STYLE_ARCHITECT)
- эстетическая рамка мира (WORLD_AESTHETIC_DESIGNER)
- символизм/метафора как слой (SYMBOLISM_METAPHOR_DESIGNER)
- эмоциональная кривая/атмосфера (MOOD_ATMOSPHERE_CURATOR)
- стратегии разрыва и провокации (ARTISTIC_RISK_DESIGNER) — здесь только риски концепта

## [M] INPUTS (MIN)
- SPECIALIST_OUTPUT.CRV_INTENT_PACK (обязателен)
- OPTIONAL:
  - SPECIALIST_OUTPUT.CRV_WORLD_AESTHETIC_FRAME
  - references (разрешённые источники/рефы)
  - platform constraints (обложка/видео/постер/текст/арт)
  - duration/format constraints (например: 8 сек, вертикалка, 1 персонаж)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CRV_CONCEPT_PACK

## [M] SPECIALIST_OUTPUT.CRV_CONCEPT_PACK (SCHEMA)
### [M] HEADER
- domain: CRV_SPC
- key: SPC.CRV.CONCEPT_DESIGNER
- created_at: <YYYY-MM-DD>
- based_on: [SPC.CRV.CREATIVE_DIRECTOR]
- dependencies: [optional keys used]

### [M] CONCEPT_GOAL
- one_line_goal: <1 строка — что должен “сделать” концепт>
- audience_feel_target: <1 строка — какое ощущение должно остаться>
- success_signals: [3–7] (наблюдаемые признаки успеха)

### [M] VARIANT_BATCH (5–12)
- variants:
  - id: V1
    name: <short>
    core_hook: <1 строка>
    pillars: [3–6]            (опоры концепта)
    signature_elements: [5–10] (узнаваемые элементы)
    constraints: [3–8]         (ограничения/правила)
    risks: [2–6]               (чем ломается)
    best_for: [1–3]            (где вариант сильнее)
  (повторить для V2..)

### [M] SELECTION
- selection_method: <short> (например: scoring)
- score_axes: [3–8] (новизна, читаемость, переносимость, вирусность, и т.д.)
- winner: <V#>
- runner_ups: [V#, V#]
- rationale: [3–8 bullets] (почему победил)

### [M] CANON_CONCEPT (WINNER REFINEMENT)
- canon_name: <short>
- canon_hook: <1 строка>
- must_keep: [5–12]          (без этого концепт не концепт)
- can_vary: [5–12]           (что допускает вариации)
- must_avoid: [5–12]         (что запрещено)
- coherence_rules: [5–12]    (правила консистентности)

### [M] REALIZATION_GUIDE (PRINCIPLES)
- composition_principles: [3–10]   (как строить образ/идею без кадрирования)
- detail_density: LOW|MID|HIGH
- clarity_principles: [3–8]        (как не потерять читаемость)
- escalation_principles: [2–6]     (как усиливать, не ломая)

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
- Варианты должны быть сравнимыми: одинаковая структура, одинаковые оси оценки.
- Никаких режиссёрских сцен/раскадровок: только принципы концепта.
- Анти-шум: короткие формулировки, списки, без лирики.
- KEY-only: никаких RAW в output.

## [M] GATES
PASS если:
- есть 5–12 вариантов в VARIANT_BATCH
- есть SELECTION с winner + rationale
- CANON_CONCEPT заполнен: must_keep / can_vary / must_avoid
- есть 6+ COHERENCE_CHECKS
- есть RISKS_AND_MITIGATIONS
- есть HANDOFF_POINTERS (next_open_keys)

FAIL если:
- меньше 5 вариантов или они не сопоставимы
- нет запретов/границ (must_avoid пуст)
- концепт описан как “сцена/монтаж”, а не как переносимые принципы

GAP если:
- нет CRV_INTENT_PACK

STOP если:
- попытка добавить RAW ссылки внутрь output
