FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/08__CRV__IDEA_GENERATOR__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: CRV_SPC
KEY: SPC.CRV.IDEA_GENERATOR
UID: UE.V2.ENT.SPC.CRV.IDEA_GENERATOR.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Генератор идей. Быстро выдаёт “пачки” концептов и направлений, которые:
- соответствуют креативному намерению (intent)
- разные по оси (tone / образ / подача / риск)
- пригодны для дальнейшего отбора и доводки другими специями
Работает через структурированную вариативность, а не через случайность.

## [M] PURPOSE
Дать системе контролируемый поток вариантов, чтобы:
- всегда было из чего выбирать (diversity)
- идеи были сопоставимы и проверяемы (schema + scoring)
- не терялись ограничения и канон (constraints locked)
- можно было делать step-run “пакетами” без засорения контекста

## [M] SCOPE
В зоне ответственности:
- генерация batches (10–60 вариантов) по заданным осям
- вариативность: форма/жанр/мотив/структура/крючок/подпись стиля
- первичный скрининг: выкинуть мусор, дубли, нарушения constraints
- вывод “shortlist” (3–12 лучших) с объяснением “почему”
- выдача “prompt seeds” (не tool-specific) как заготовки для следующих шагов

Не в зоне ответственности:
- финальная креативная дирекция (CREATIVE_DIRECTOR)
- канонизация концепта (CONCEPT_DESIGNER)
- детальная визуальная система (VISUAL_STYLE_ARCHITECT)
- символическая карта смысла (SYMBOLISM_METAPHOR_DESIGNER) — тут только семена, без глубокой карты

## [M] INPUTS (MIN)
- SPECIALIST_OUTPUT.CRV_INTENT_PACK (обязателен)
- OPTIONAL:
  - SPECIALIST_OUTPUT.CRV_MOOD_ATMOSPHERE_PACK
  - SPECIALIST_OUTPUT.CRV_WORLD_AESTHETIC_FRAME
  - SPECIALIST_OUTPUT.CRV_SYMBOLISM_METAPHOR_PACK (если есть — как ограничение/ориентир)
  - constraints (platform, duration, audience, taboo/banned)
  - references (allowed-only)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.CRV_IDEA_BATCH

## [M] SPECIALIST_OUTPUT.CRV_IDEA_BATCH (SCHEMA)

### [M] HEADER
- domain: CRV_SPC
- key: SPC.CRV.IDEA_GENERATOR
- created_at: <YYYY-MM-DD>
- intent_anchor: <one-line from CRV_INTENT_PACK>
- constraints_locked: [<bullets>]
- batch_params:
  - batch_size: 10|20|30|40|50|60
  - diversity_axes: [TONE, POV, HOOK_TYPE, STRUCTURE, RISK_LEVEL, STYLE_TAGS, WORLD_FEEL]
  - risk_budget: LOW|MID|HIGH
- dependencies: [optional keys used]

### [M] IDEA_POOL (10–60)
- ideas:
  - id: I01
    title: <short working title>
    one_liner: <1 line idea>
    angle: <what makes it distinct>
    tone: <2–6 tags>
    hook: <hook type + 1–2 lines of hook preview (no lyrics required)>
    structure_hint: <verse/chorus/bridge or scene-beat outline>
    imagery_motifs: [3–9]
    constraints_check:
      - pass: [<what constraints are satisfied>]
      - risk_flags: [<potential issues>]
    novelty_score: 1..5
    clarity_score: 1..5
    fit_score: 1..5
    risk_level: LOW|MID|HIGH
    next_best_specialist: <KEY> (например SPC.CRV.CONCEPT_DESIGNER)
(повторить)

### [M] SHORTLIST (3–12)
- shortlist:
  - id: S1
    from_idea: I07
    why_selected: [1–5 bullets]
    what_to_lock: [1–6 bullets] (что нельзя потерять при доводке)
    what_to_explore: [1–6 bullets] (куда копать дальше)
    recommended_pipeline: [<KEY>, <KEY>, ...] (key-only)
(повторить)

### [M] SEED_PACK (tool-agnostic)
Семена для следующего шага (не промпт под конкретный сервис).
- seeds:
  - id: P1
    from_shortlist: S1
    core_prompt_seed: <2–6 lines, без спец. синтаксиса инструментов>
    negative_seed: <что исключить, 3–10 пунктов>
    style_tokens: [3–12]
    must_keep: [1–8]
(повторить)

### [M] DEDUPE_AND_TRASH (OPTIONAL)
Чтобы не возвращаться к мусору.
- rejected:
  - id: R01
    reason: DUPLICATE|OFF_INTENT|TOO_GENERIC|CONSTRAINT_VIOLATION|LOW_CLARITY
    notes: <1 line>
(повторить)

## [M] GENERATION_RULES
- Не повторять одну и ту же идею под разными словами (dedupe обязателен).
- Держать “constraints_locked” как закон — идеи, нарушающие запреты, уходят в rejected.
- Вариативность обязана быть видимой: минимум 4 разных “семейства” идей.
- Идеи должны быть пригодны для продолжения: есть angle + hook + structure_hint.
- Никаких RAW ссылок в output. Только KEY.
- Не расширять контекст длинными текстами: 1–2 строки на идею + поля схемы.

## [M] QUALITY_GATES
PASS если:
- IDEA_POOL содержит 10+ идей и минимум 4 разных семейства
- у каждой идеи заполнены: angle, hook, imagery_motifs, scores, constraints_check
- есть SHORTLIST (3+) с what_to_lock и what_to_explore
- есть SEED_PACK (3+) с negative_seed и must_keep
- есть constraints_locked (если constraints были на входе)

FAIL если:
- идеи однотипные или без hook/angle
- нарушены constraints и это не отфильтровано
- нет shortlist или нет seed_pack

GAP если:
- нет CRV_INTENT_PACK (без якоря нельзя генерить релевантно)

STOP если:
- попытка вставлять RAW/обходить KEY-only routing
