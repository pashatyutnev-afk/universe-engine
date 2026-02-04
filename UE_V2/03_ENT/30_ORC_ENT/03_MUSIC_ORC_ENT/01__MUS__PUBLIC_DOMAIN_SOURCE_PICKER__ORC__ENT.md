FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/01__MUS__PUBLIC_DOMAIN_SOURCE_PICKER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.PUBLIC_DOMAIN_SOURCE_PICKER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PUBLIC_DOMAIN_SOURCE_PICKER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.PUBLIC_DOMAIN_SOURCE_PICKER.001
- SCOPE_TAGS: [MUS, SOURCE, KB, POLICY]
- OUTPUT_ARTIFACT: SOURCE_POLICY_TOKEN

---

## [M] PURPOSE
Формирует SOURCE_POLICY_TOKEN: какие референсы допустимы при генерации музыки, текста, метаданных и промптов.
Смысл: держать референсы как принципы (жанр, инструменты, структура, энергетика), не как воспроизведение конкретных произведений.
Если запрос требует копирования, модуль обязан заблокировать или заменить запрос безопасной альтернативой.

---

## [M] INPUTS / OUTPUTS
### Inputs
- MUS_BRIEF (обязателен)
  - target: single_track|ep|album|playlist
  - language: ru|en|other
  - mood / energy
  - style_refs?: user_refs (имена артистов, треки, ссылки, описания "как X")
  - constraints?: explicit constraints (темп, вокал, длительность, платформа)

### Outputs
- SOURCE_POLICY_TOKEN (обязателен при PASS)
- FAIL_CODE? (при FAIL)

---

## [M] TOKEN SCHEMA
### SOURCE_POLICY_TOKEN (v1)
- policy_id: UE.V2.MUS.SOURCE_POLICY.v1
- allowed_reference_types:
  - genre_descriptors: true|false
  - instrumentation_descriptors: true|false
  - structure_descriptors: true|false
  - mix_targets_descriptors: true|false
  - era_vibe_descriptors: true|false
  - named_artist_as_principle_only: true|false
  - direct_track_imitation: false (always)
  - lyrics_quote_or_rewrite: false (always)
  - melody_reconstruction: false (always)
- safe_reference_style:
  - phrasing_rules: ["principles_over_examples", "no_verbatim", "no_melody_copy"]
  - specificity_cap: "high_level"|"medium"|"tight_but_generic"
- banned_request_flags: [COPY_EXACT, MELODY_MATCH, LYRICS_REWRITE, STEM_EXTRACT, VOICE_CLONE, OTHER]
- rewrite_instructions_if_blocked:
  - what_to_keep: [genre, tempo_band, energy, instrumentation, theme_principles]
  - what_to_change: [melody, chord_progression_signature, lyric_lines, hook_phrase, arrangement_fingerprint]
  - safe_alt_prompt_frame: <one_paragraph_frame>
- evidence_notes:
  - user_refs_seen: [<strings>]
  - decision: PASS|FAIL
  - reason: <short>

---

## [M] CORE_RULES
1) Запрещено:
- "сделай один в один как трек X"
- "повтори мелодию/аккорды/хук как X"
- "перепиши текст песни X" или любые цитаты строк
- извлечение стемов, клон голоса, имитация конкретного исполнителя как копия

2) Разрешено:
- описывать жанр, темп-диапазон, энергетический профиль, инструменты, общую структуру (куплет/припев/бридж) без узнаваемого отпечатка конкретного трека
- использовать артистов как ориентир только на уровне принципов (тембр как "тёплый", а не "как у N"; подача как "интимная", а не "скопируй манеру")
- давать референсы на эпоху/сцену/настроение ("ночной дрим-поп 2010-х") без привязки к конкретной композиции

3) При сомнении:
- снижать конкретику (specificity_cap -> medium|high_level)
- возвращать безопасную рамку, что именно можно сохранить и что обязательно изменить

---

## [M] DECISION LOGIC (deterministic)
### Inputs inspected
- MUS_BRIEF.style_refs (если есть)
- формулировки "как", "в стиле", "копия", "один в один", "похоже на"

### Classify request
A) SAFE: нет имён треков, нет "один в один", только жанр/настроение/инструменты  
B) BORDERLINE: есть имена артистов/треков, но явно как "вдохновение", без копирования  
C) BLOCK: есть прямой запрос на копирование, цитирование, совпадение мелодии, перепись текста

### Output mapping
- SAFE -> PASS, named_artist_as_principle_only = true (если упомянуты артисты), specificity_cap = tight_but_generic
- BORDERLINE -> PASS, specificity_cap = medium, add phrasing_rules усиленно, add evidence_notes.reason = "principles only"
- BLOCK -> FAIL, FAIL_CODE = UE.FAIL.RULE_VIOLATION, banned_request_flags заполнить, rewrite_instructions_if_blocked заполнить

---

## [M] KB SCOPE
- KB Inputs: [правила допустимых ссылок, ограничения копирования, safe phrasing patterns]
- KB Outputs: [SOURCE_POLICY_TOKEN]
- KB Boundaries:
  - не добавлять “факты о правах” или юридические утверждения, если их нет во входе
  - не выдавать утверждения о владении правами или лицензиях

---

## [M] GATES
### PASS
- SOURCE_POLICY_TOKEN сформирован
- direct_track_imitation = false
- lyrics_quote_or_rewrite = false
- melody_reconstruction = false
- decision = PASS

### FAIL
- обнаружен BLOCK-класс запроса
- не удаётся переписать запрос в безопасную форму без потери цели пользователя

FAIL_CODE:
- UE.FAIL.RULE_VIOLATION

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff:
  - SOURCE_POLICY_TOKEN -> MUS.GENRE_STYLE_ROUTER
  - SOURCE_POLICY_TOKEN -> MUS.LYRIC_BRIEF_FACTORY

---

## [M] EXAMPLES (safe patterns)
- Плохо: "сделай как трек X один в один"
- Хорошо: "сделай энергичный synthwave, 120–130 bpm, плотный бас, ретро-синты, структура куплет-припев, хук максимально цепкий, без повторения мелодий существующих треков"

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 add token schema, deterministic logic, rewrite frame
