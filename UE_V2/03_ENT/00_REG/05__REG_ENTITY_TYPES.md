# 05__REG_CAPABILITIES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REGISTRY / DICTIONARY
UID: UE.V2.REG.CAPABILITIES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Словарь CAP (возможностей) сущностей. Используется для совместимости и выбора участников.

---

## [M] INTENT
Убрать разнобой и "магические" способности: каждый участник объявляет CAP из словаря.

---

## [M] CAP_LIST (CANON)
CORE:
- cap.route              (классификация задачи, выбор домена/пайпа)
- cap.plan               (построение плана шагов)
- cap.orchestrate         (сбор цепочки шагов, сбор токенов)
- cap.control             (политики/лимиты/гейты)
- cap.noise               (ограничение контекста, лимиты сущностей/вариантов)
- cap.coverage            (покрытие Pillars/Topics)
- cap.validate            (проверка правил/метрик)
- cap.docfmt              (формат/маркеры/UID)
- cap.qa                  (оценка качества)
- cap.accept              (приёмка/пассы)
- cap.pack                (упаковка результата)
- cap.signoff             (финальное утверждение)
- cap.map                 (XREF карты)
- cap.index               (индексация/реестр)
- cap.kb_scope            (границы знаний/источники)
- cap.trace               (трекинг, логи решений)

CONTENT (общие):
- cap.generate            (генерация черновика)
- cap.transform           (переработка/улучшение)
- cap.review              (редакторский взгляд)
- cap.score               (скоринг вариантов)
- cap.differentiate       (уникальность/анти-коллизии)
- cap.compliance          (права/канон/ограничения)

MUSIC (добавочные):
- cap.hook                (хук/earworm/скролл-стоп)
- cap.structure           (структура/карта энергии)
- cap.palette             (тембровая палитра)
- cap.prompt_compile      (промпт-спека/параметры)
- cap.mix                 (микс)
- cap.master              (мастер)
- cap.lyrics              (текст/поэзия)
- cap.ugc                 (UGC-ориентированные правила)
- cap.metadata            (метаданные релиза)

VIS (добавочные):
- cap.prompt_vis
- cap.shot_rules
- cap.sync

LOR (добавочные):
- cap.canon
- cap.timeline
- cap.xref_lor

REL (добавочные):
- cap.release_pack
- cap.readiness_matrix

---

## [M] RULES
1) CAP записывается как csv: cap.a,cap.b,cap.c
2) CAP должны соответствовать списку выше.
3) Расширение CAP — только через CHANGE_LOG и обновление словаря.

---

## [M] GATES
PASS если:
- CAP значения в каталоге существуют в словаре
REWORK если:
- CAP содержит неизвестные токены
