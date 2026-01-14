# TOPIC — VERSIONING, DELIVERY & NAMING (PRODUCTION / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/04__PRODUCTION__VERSIONING_DELIVERY_NAMING.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.PROD.VERSIONING_DELIVERY.001
OWNER: SYSTEM
ROLE: Atomic method to enforce consistent versioning, file naming, and delivery packaging across artifacts (tracks/episodes/chapters/packs) to prevent loss, duplicates, and non-auditable releases; includes naming rules, delivery pack conventions, and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created production standard for versioning + naming + delivery: deterministic filenames, variant tags, version bumps, and delivery structure."
- REASON: "Production collapses without deterministic names and version rules; duplicates and missing sources become unavoidable."
- IMPACT: "Releases become auditable, comparable, and automatable; teams can scale outputs without chaos."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.PROD.004

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_production
- type_topic
- versioning
- naming
- delivery
- auditability
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Зафиксировать жёсткие правила:
- как именуются файлы,
- как ставятся версии и что значит bump,
- как упаковываются deliverables и варианты,
- как исключить дубликаты и “потерянные” артефакты.

---

## 2) WHEN TO USE
- Ты выпускаешь релизы регулярно (музыка/эпизоды/главы/шорты).
- Есть много вариантов (short/radio/alt mix/teaser).
- Теряются “финальные” версии, появляются копии.
- Нужно быстро понять: что актуально, что устарело, что можно публиковать.

## 3) WHEN NOT TO USE
- Один разовый черновик без публикации и без повторного использования.

---

## 4) DEFINITIONS (STRICT)
### Artifact
Единица результата: track / episode / chapter / short / pack.

### Variant
Вариант под платформу или форму:
- short, teaser, radio edit, instrumental, vertical, etc.

### Version
Номер версии артефакта:
- MAJOR.MINOR.PATCH
Где:
- MAJOR: большие изменения смысла/структуры/контракта
- MINOR: заметные улучшения внутри (текст/аранж/монтаж)
- PATCH: исправления/мелкие правки без смены сути

### Delivery package
Папка/набор файлов для передачи/публикации.

---

## 5) NAMING RULES (FILES)
### 5.1 Canon filename skeleton (recommended)
<DATE>__<ARTIFACT_TYPE>__<TITLE_SLUG>__v<MAJOR>.<MINOR>.<PATCH>__<VARIANT>.<ext>

Пример:
2026-01-14__track__pomehi__v1.0.0__master.wav
2026-01-14__track__pomehi__v1.0.0__short30.mp3
2026-01-14__episode__pilot__v1.2.0__script.md

### 5.2 Required fields
- DATE
- ARTIFACT_TYPE
- TITLE_SLUG (latin, lowercase, underscore)
- VERSION
- VARIANT (если применимо)

### 5.3 Forbidden
- “final_final2_new”
- “(1)(2)(3)”
- пробелы в имени файла
- “без версии”
- кириллица в имени файла (допускается внутри документов, но не в filename)

---

## 6) VARIANT TAGS (STANDARD)
Общий словарь (использовать как suffix):
- master
- platform
- instrumental
- acapella
- radio
- altmix
- teaser
- trailer
- short15
- short30
- short60
- vertical
- captions
- cover
- thumb
- notes
- lyrics
- script
- outline

Правило:
- если варианта нет — ставь __master или __primary.

---

## 7) DELIVERY STRUCTURE (PACK)
Рекомендуемая структура доставки:

DELIVERY/<ARTIFACT_TYPE>/<TITLE_SLUG>/v<version>/
- 00__META/
  - metadata.md
  - credits.md
  - rights.md
  - changelog.md
- 10__PRIMARY/
  - master.* (главный файл)
- 20__PLATFORMS/
  - platform variants...
- 30__TEXT/
  - lyrics/script/outline...
- 40__ASSETS/
  - cover/thumb...
- 90__NOTES/
  - prompts/production_notes...

Правило:
- релиз можно отправить “как есть” целиком папкой версии.

---

## 8) VERSIONING POLICY (BUMP RULES)
### 8.1 PATCH bump
- орфография/мелкие правки текста
- небольшой микс-фикс без смены структуры
- исправление метадаты

### 8.2 MINOR bump
- меняется куплет/припев частично
- меняется аранжировка заметно (но не новая песня)
- добавлены/изменены важные сцены/биты в эпизоде
- изменён hook placement

### 8.3 MAJOR bump
- новая структура (другой припев/концепт)
- смена центральной идеи/темы
- смена формата или контракта (book→series)
- сильная переработка так, что сравнивать как тот же артефакт нельзя

---

## 9) CHANGELOG (MANDATORY FOR RELEASE)
Каждая версия обязана иметь CHANGELOG запись:

CHANGELOG ENTRY:
- DATE:
- VERSION:
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:
- CHANGE_ID: <optional>

Запрет:
- релиз без changelog (кроме very early drafts с пометкой DRAFT ONLY).

---

## 10) DELIVERY GATES (PASS/FAIL)
PASS IF:
- filenames детерминированы (см. §5)
- версии выставлены корректно (см. §8)
- variants именованы стандартно (см. §6)
- есть delivery structure (см. §7)
- есть metadata + credits + rights + changelog (см. §7, §9)
- есть release pack checklist PASS (см. release pack topic)

REWORK IF:
- структура есть, но названия/версии местами “гуляют”
- нет одного из meta файлов, но артефакт готов

FAIL IF:
- “финал” без версии
- дубли и непонятно, что актуально
- нет credits/rights (риски)
- отсутствует master/primary файл

---

## 11) QUICK CHECKLIST (COPY)
- [ ] filename skeleton соблюдён
- [ ] title_slug валиден
- [ ] version выставлена и bump обоснован
- [ ] variant tags из стандарта
- [ ] delivery folder создана: DELIVERY/<type>/<slug>/vX.Y.Z/
- [ ] 00__META заполнено: metadata/credits/rights/changelog
- [ ] 10__PRIMARY содержит master/primary
- [ ] platform variants лежат в 20__PLATFORMS
- [ ] release pack checklist = PASS

---

## 12) EXAMPLES (MANDATORY)
### 12.1 PASS EXAMPLE (track)
DELIVERY/track/sboi/v1.1.0/
- 10__PRIMARY/2026-01-14__track__sboi__v1.1.0__master.wav
- 30__TEXT/2026-01-14__track__sboi__v1.1.0__lyrics.md
- 00__META/changelog.md (MINOR bump: переписан припев)
WHY PASS:
- ясно, что актуально и чем отличается версия.

### 12.2 FAIL EXAMPLE
Файлы:
- final.wav
- final2.wav
- final_new.wav
Нет changelog, нет credits.
WHY FAIL:
- нельзя понять, что выпускать; высокий риск.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/02__PRODUCTION__ADAPTATION_PIPELINE.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (no ambiguous filenames; no release without meta + changelog)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
