# TOPIC — GENRE FUSION FINGERPRINTS (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/11__SOUND_MUSIC__GENRE_FUSION_FINGERPRINTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.GENRE_FUSION.001
OWNER: SYSTEM
ROLE: Atomic method to design genre-fusion “style fingerprints” for consistent track identity: marker lists per genre, proportion rules, must-have elements, forbidden drift, and QA recognition tests; includes Fusion Card templates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created genre fusion fingerprints: marker taxonomy, proportion rules, must-haves, negative drift guards, and recognition QA."
- REASON: "Fusion tracks fail when genres are mixed randomly or drift toward default pop/EDM; fingerprints enforce stable identity."
- IMPACT: "Entities can build repeatable, branded hybrid styles (e.g., electronic nu metal + industrial + rap rock) with controlled variation."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.011

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- genre_fusion
- style_fingerprint
- drift_guard
- qa_tests
- maturity_seed

---

## 1) PURPOSE
Сделать стиль гибрида управляемым:
- жанры не “мешаются в кашу”,
- есть список маркеров, которые обязаны быть слышны,
- есть пропорции (кто доминирует),
- есть запреты (куда не скатываться),
- есть тест “узнаваемости” за 10 секунд.

---

## 2) WHEN TO USE
- Серийно делаешь треки в одном гибридном стиле.
- Генератор “утягивает” в поп/EDM/trap.
- Нужно сделать “фирменный отпечаток” группы/альбома.
- Нужно различать подстили между группами.

## 3) WHEN NOT TO USE
- Один экспериментальный трек без повторения.

---

## 4) DEFINITIONS (STRICT)
### Marker
Слышимый элемент жанра:
- ритм, тембр, гармония, вокальная подача, приём продакшна.

### Proportion
Вес жанров в треке:
- primary (50–70%)
- secondary (20–40%)
- accent (5–15%)

### Drift
Скатывание в чужой жанр/типовой шаблон.

---

## 5) MARKER TAXONOMY (BY LAYER)
Размечаем маркеры по слоям:
- Rhythm markers (groove, drums)
- Harmonic markers (chords, mode)
- Timbre markers (guitars/synths)
- Vocal markers (delivery)
- Production markers (stutter, glitch, mix style)

---

## 6) CORE MARKERS (EXAMPLE SETS)
### A) Nu metal markers
- heavy down-tuned guitars, palm-mute riffs
- half-time stomp / big snare
- verse→chorus contrast (rap→sing)
- aggressive but clean mix, tight low end

### B) Industrial rock markers
- mechanical drum hits, metallic percussion
- synth noise textures, machine-like pulses
- stutter edits / gated transitions
- cold atmosphere

### C) Rap rock markers
- rhythmic rap cadence in verse
- groove lock between drums and vocal
- hooky chorus with singable slogan
- call-response moments

---

## 7) FUSION RULES (PROPORTION + MUST-HAVES)
### Step 1 — Choose proportions
Example:
- Primary: nu metal (60%)
- Secondary: industrial (30%)
- Accent: rap rock (10%)

### Step 2 — Declare MUST-HAVES (3–6)
Must-have list (example):
- MH1: half-time stomp
- MH2: heavy guitars + riff
- MH3: glitch tag / stutter
- MH4: rap verse + melodic chorus
- MH5: tight low end, clean aggressive mix

### Step 3 — Declare FORBIDDEN DRIFT (negative spec)
- no EDM build-drop clichés
- no glossy pop vocal
- no trap hi-hat rolls (если не надо)
- no bright happy major pop progression (если не надо)

---

## 8) VARIATION WITHIN FINGERPRINT (SAFE ZONE)
Разрешённая вариативность (не ломает стиль):
- менять sound tag (glitch signature)
- менять тембр синта (lead vs pad)
- менять темп ± 6 bpm
- менять контур хука (но оставить слоган и контраст)

Запрет:
- менять must-haves или пропорции без версии/обоснования.

---

## 9) RECOGNITION QA (MANDATORY)
Тесты:
- T1: 10-second recognition
  Слушатель должен сказать: “это nu metal/industrial hybrid” за 10 секунд.
- T2: Must-have audit
  Все MH слышны?
- T3: Drift audit
  Нет ли forbidden drift?

RESULT:
- PASS / REWORK

---

## 10) FUSION CARD TEMPLATE (COPY)
FUSION CARD:
- Style name:
- Primary genre (%):
- Secondary genre (%):
- Accent genre (%):
- Must-haves (3–6):
  - MH1:
- Marker checklist:
  - Rhythm:
  - Timbre:
  - Vocals:
  - Production:
- Forbidden drift (negative spec):
- Safe variation zone:
- QA:
  - 10s recognition:
  - Must-have audit:
  - Drift audit:
- Result: PASS/REWORK

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (your target)
Primary:
- electronic nu metal
Secondary:
- industrial rock
Accent:
- rap rock
Must-haves:
- half-time stomp, heavy guitars, glitch stutter, rap verse + melodic hook
Drift:
- no pop gloss, no EDM drop
WHY PASS:
- стиль узнаваем, но есть электронный характер.

### 11.2 FAIL EXAMPLE
Трек уехал в EDM с билдом и дропом, гитары исчезли.
WHY FAIL:
- пропали must-haves, случился drift.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/04__SOUND_MUSIC__REPEAT_GUARD_ANTI_COLLISION.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (proportions + must-haves + drift guard mandatory; recognition QA required)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
