# TOPIC — CREDITS & METADATA POLICY (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/10__SOUND_MUSIC__CREDITS_METADATA_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.CREDITS_METADATA.001
OWNER: SYSTEM
ROLE: Atomic policy for credits and metadata for music releases: required fields, platform variants (YT/Shorts/Spotify-like), rights/source notes, and consistency rules; includes Metadata Card templates and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created credits/metadata policy for music: mandatory fields, platform-tailored metadata, rights notes, and consistency rules."
- REASON: "Releases become risky and low-quality without consistent credits and metadata; policy ensures auditable publishing and reuse."
- IMPACT: "Entities can publish faster with fewer omissions and maintain catalog integrity."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.010

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- credits
- metadata
- rights
- release_policy
- maturity_seed

---

## 1) PURPOSE
Зафиксировать, что у каждого релиза есть:
- корректные кредиты,
- полная метадата,
- notes по правам/источникам,
- единый стиль названий и тегов,
- связь с версией и release pack.

---

## 2) WHEN TO USE
- Любой релиз трека/варианта/шорта.
- Серийный выпуск каталога.
- Публикация на нескольких платформах.

## 3) WHEN NOT TO USE
- Черновики без публикации (но при переходе в релиз — обязательно).

---

## 4) DEFINITIONS (STRICT)
### Credits
Кто сделал что: текст, музыка, продакшн, вокал, микс, арт/обложка.

### Metadata
Заголовок, описание, теги, жанр, bpm, настроение, язык, версия, ссылки.

### Rights note
Что использовано и на каких основаниях (PD/лицензии/оригинал).

---

## 5) REQUIRED FIELDS (MANDATORY)
Для каждого трека (и вариантов):

### A) Identity
- Title (official)
- Artist / Project / Group
- Version (vX.Y.Z)
- Date
- Track ID (если есть)

### B) Content
- Genre tags (2–6)
- BPM
- Mood keywords (3–8)
- Language
- Hook line (1 строка)
- Short summary (1–2 строки)

### C) Credits
- Lyrics:
- Music/Composition:
- Production:
- Vocals:
- Mix/Master:
- Artwork/Thumbnail:
- Tools (если применимо):

### D) Rights / Sources
- Rights note (PD/лицензии/оригинал)
- Source references (если есть)
- Restrictions (если есть)

### E) Distribution
- Platform targets (YT/Shorts/etc)
- Variant list (master/short15/short30/short60/instrumental)
- Hashtags/keywords per platform

---

## 6) PLATFORM VARIANTS (TEMPLATES)
### 6.1 YouTube (full)
- Title: <Artist> — <Track> (Official Audio) [vX.Y.Z]
- Description:
  - 1–2 строки хука
  - кредиты
  - права/источники
  - теги

### 6.2 Shorts/Reels/TikTok (15/30/60)
- Title: <Track> — hook (Short)
- Description:
  - 1 строка
  - 3–8 хештегов
- Note:
  - captions-friendly line (если надо)

### 6.3 Catalog/Archive (internal)
- metadata.md в release pack (см. production release pack)
- обязательно: changelog link + variant inventory

---

## 7) CONSISTENCY RULES (STRICT)
- CR1: Title стабильный между платформами (варианты только в суффиксах)
- CR2: Version везде одинаковая
- CR3: Credits не пропускать (минимум “Lyrics/Music/Production”)
- CR4: Rights note обязателен
- CR5: Tags не должны быть мусором (не 50 хештегов)

---

## 8) METADATA CARD (COPY)
MUSIC METADATA CARD:
- Title:
- Artist/Group:
- Version:
- Date:
- Track ID:
- Genres:
- BPM:
- Mood:
- Language:
- Hook line:
- Short summary:
- Credits:
  - Lyrics:
  - Music:
  - Production:
  - Vocals:
  - Mix/Master:
  - Artwork:
  - Tools:
- Rights/Sources:
- Platform variants:
  - YouTube:
  - Shorts:
  - Archive:
- Tags/Hashtags:
- PASS/FAIL notes:

---

## 9) QA GATES (PASS/FAIL)
PASS IF:
- все required fields заполнены
- credits указаны
- rights note есть
- version совпадает с release pack
- платформенные варианты подготовлены (если нужны)

REWORK IF:
- отсутствуют 1–2 поля метадаты, но всё остальное есть

FAIL IF:
- нет credits или rights note (риски)
- версия не совпадает или непонятно, что публикуем

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE
Title:
- “СБОИ”
Credits:
- Lyrics: …
- Production: …
Rights:
- original lyrics / no external sampling
Variants:
- master + short30 + short15
WHY PASS:
- готово для публикации и архива.

### 10.2 FAIL EXAMPLE
- “трек.mp3”, без авторства, без описания, без прав
WHY FAIL:
- нельзя публиковать и невозможно сопровождать каталог.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/04__PRODUCTION__VERSIONING_DELIVERY_NAMING.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/09__SOUND_MUSIC__UGC_SHORTS_VARIANTS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (no publish without credits + rights + consistent versioning)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
