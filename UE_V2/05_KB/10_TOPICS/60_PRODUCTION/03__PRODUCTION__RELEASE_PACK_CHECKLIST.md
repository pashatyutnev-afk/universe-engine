# TOPIC — RELEASE PACK & CHECKLIST (PRODUCTION / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.PROD.RELEASE_PACK.001
OWNER: SYSTEM
ROLE: Atomic method to assemble a release-ready artifact pack (book/episode/track) with required metadata, quality checklist, rights/credits, and distribution variants; includes Release Pack Template and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created release pack standard: required artifacts + metadata + QA checklist + rights/credits + distribution variants."
- REASON: "Quality and reuse collapse when outputs are shipped without a consistent pack; release packs make production auditable and scalable."
- IMPACT: "Entities can publish reliably across platforms, avoid missing assets, and enforce consistent branding/metadata."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.PROD.003

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_production
- type_topic
- release_pack
- checklist
- metadata
- rights_credits
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Сделать выпуск (релиз) повторяемым и безопасным:
- каждый релиз имеет полный “пак” артефактов,
- есть метадата и права/кредиты,
- есть QC/QA-гейты,
- есть варианты под платформы.

---

## 2) WHEN TO USE
- Выпускаешь трек/эпизод/главу/модуль.
- Нужно стандартизировать публикации.
- Постоянно “не хватает” файлов: обложки/описания/метадаты/версии/кредитов.
- Хочешь масштабировать производство и не терять качество.

## 3) WHEN NOT TO USE
- Ты делаешь черновик, который не будет публиковаться.
- Ты пишешь внутренние заметки.

---

## 4) INPUTS (MINIMUM)
- Тип релиза: track / episode / chapter / short / pack.
- Название, авторство/участники, дата/версия.
- Целевая платформа(ы): YouTube, Spotify, TikTok, site, etc.
- Ограничения: длительность, формат, требования к обложке.

## 5) OUTPUTS (MINIMUM)
- Release Pack (набор файлов/текстов/метадаты).
- QA checklist (PASS/FAIL).
- Distribution variants (форматы/длины/описания).

---

## 6) DEFINITIONS (STRICT)
### Release pack
Полный комплект, который можно отдать:
- в публикацию
- в архив
- в повторное использование (remix/adaptation)

### Variant
Версия под платформу:
- длина, интро/аутро, формат видео, громкость, обложка, описание.

### QC / QA
Проверка качества:
- техническая (форматы, уровни)
- смысловая (хуки, понятность)
- правовая (кредиты/права)

---

## 7) RELEASE PACK CONTENT (REQUIRED)
Минимальный состав (по типу):

### 7.1 UNIVERSAL (always)
- Title (официальное)
- ID / UID (если есть)
- Version + date
- Short description (1–2 строки)
- Long description (5–12 строк)
- Credits (кто сделал что)
- Rights note (источники, лицензии, PD policy)
- Tags/keywords
- Thumbnail/Cover (если требуется)
- QA checklist result

### 7.2 TRACK (music)
- Audio master (WAV/FLAC)
- Platform audio (MP3/AAC)
- Lyrics (final)
- Prompt/production notes (если AI/генерация)
- Mix notes (если есть)
- Hook timestamps (где хук)
- Variants: radio edit / short / instrumental (по задаче)

### 7.3 EPISODE (series)
- Script (final)
- Episode outline (beats)
- Logline + synopsis
- Title card text
- Captions/subtitles (если надо)
- Thumbnail
- Variants: teaser / trailer / short clips

### 7.4 CHAPTER (book)
- Chapter text (final)
- Chapter summary (3–7 строк)
- Hook line (зачем читать дальше)
- Continuity notes (что изменилось в state)
- Variants: audiobook read notes (если надо)

---

## 8) QA CHECKLIST (PASS/FAIL)
### A) Technical
- [ ] корректные форматы (wav/mp3, md/pdf, etc)
- [ ] файловые имена согласованы
- [ ] нет битых ссылок/пустых файлов

### B) Content quality
- [ ] есть хук (первые секунды/первые строки)
- [ ] нет воды/лекций (если narrative)
- [ ] state change присутствует (если сцена/эпизод)
- [ ] основной смысл/настроение считывается

### C) Branding & metadata
- [ ] заголовок/описание/теги заполнены
- [ ] обложка/превью соответствует
- [ ] единый стиль/словарь

### D) Rights & credits
- [ ] кредиты указаны
- [ ] источники/PD/лицензии указаны
- [ ] нет запрещённого контента/заимствований без прав

RESULT:
- PASS / REWORK / FAIL

---

## 9) RELEASE PACK TEMPLATE (COPY)
RELEASE PACK:
- TYPE: track|episode|chapter|short|pack
- TITLE:
- VERSION:
- DATE:
- AUTHORS / CREDITS:
- RIGHTS / SOURCES NOTE:
- SHORT DESC:
- LONG DESC:
- TAGS:
- FILES:
  - Master:
  - Platform:
  - Cover/Thumb:
  - Text/Lyrics/Script:
  - Notes:
- VARIANTS:
  - Variant 1:
  - Variant 2:
- QA CHECKLIST:
  - Technical: PASS/FAIL
  - Content: PASS/FAIL
  - Metadata: PASS/FAIL
  - Rights: PASS/FAIL
- FINAL RESULT: PASS | REWORK | FAIL

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (track)
FILES:
- WAV master + MP3
- lyrics final
- short clip variant 0:30
QA:
- hook in first 10s, loudness ok, credits included
WHY PASS:
- можно публиковать без доработок.

### 10.2 FAIL EXAMPLE
- нет credits, нет rights note, нет описания
WHY FAIL:
- юридический и качественный риск.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/01__PRODUCTION__FORMAT_BOOK_SERIES_GAME.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/02__PRODUCTION__ADAPTATION_PIPELINE.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/00__README__TOPICS_SOUND_MUSIC.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (no release without pack + QA + rights/credits)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
