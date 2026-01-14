# TOPIC — PROMPT CONTRACTS (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.PROMPT_CONTRACT.001
OWNER: SYSTEM
ROLE: Atomic method to write reproducible generation prompts as contracts: required fields, parameter blocks, negative spec, voice/structure constraints, and QA gates for music generators (e.g., Suno/Udio); includes Prompt Contract Template and pass/fail checks

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created prompt contract standard for music generation: mandatory fields, structure blocks, negative specs, and QA gates for reproducibility."
- REASON: "Music generation quality collapses when prompts are ad-hoc; contracts make results repeatable and improvable."
- IMPACT: "Entities can generate consistent tracks, reduce collisions, and iterate deterministically."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.001

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- prompt_contract
- reproducibility
- negative_spec
- qa_gates
- maturity_seed

---

## 1) PURPOSE
Сделать промпты воспроизводимыми:
- один и тот же контракт → сопоставимые результаты
- можно итеративно улучшать, не теряя стиль/структуру
- меньше “голос одинаковый/повторы/рандом”

---

## 2) WHEN TO USE
- Генерируешь треки сериями, альбомами, под группы.
- Нужно удержать стиль/голос/структуру.
- Нужны чистые итерации (v1.0 → v1.1), а не “с нуля”.
- Возникают проблемы: одинаковые голоса, повторяющиеся паттерны, мутный вокал.

## 3) WHEN NOT TO USE
- Разовый эксперимент без дальнейших итераций.

---

## 4) DEFINITIONS (STRICT)
### Prompt contract
Структурированный промпт с обязательными секциями:
- STYLE, TEMPO, STRUCTURE, VOICE, LYRICS, MIX, NEGATIVE SPEC, DURATION.

### Negative spec
Запреты/исключения:
- что НЕ должно появиться (стиль, инструменты, приёмы, содержание).

### Reproducibility
Возможность повторить “направление результата” при новых генерациях.

---

## 5) PROMPT CONTRACT (REQUIRED SECTIONS)
### A) STYLE FINGERPRINT
- жанры/поджанры (2–4)
- ключевые “маркерные” приёмы (2–6)
- reference vibe (1–2 фразы без имён)

### B) TEMPO / GROOVE
- bpm
- feel (half-time, double-time, swing/no swing)
- groove notes (stomp, syncopation)

### C) STRUCTURE MAP
- sections (intro/verse/chorus/bridge/outro)
- где хук (time or section)
- длительность трека (примерно)

### D) INSTRUMENTATION
- core instruments (guitars, synths, drums, bass)
- signature elements (glitch hits, stutter edits)

### E) VOICE SPEC
- язык
- тип вокала (rap vs melodic)
- характер (clean/aggressive, nasal/chesty)
- запреты (не фальцет/не женский и т.д.)

### F) MIX / PRODUCTION
- low end tight, vocal forward, clean aggressive mix
- loudness target (описательно)
- stereo width (описательно)

### G) LYRICS (if used)
- полный текст или “lyric intent”
- ударения/слоги/стоп-слова

### H) NEGATIVE SPEC (MANDATORY)
- исключить: нежелательные жанры/инструменты/техники
- исключить: нежелательные темы/слова/клише
- исключить: нежелательные вокальные особенности

### I) QA TARGETS
- hook in first 10–15s
- vocal intelligibility
- no excessive repetition
- style consistency

---

## 6) NEGATIVE SPEC LIBRARY (EXAMPLES)
- No EDM build-drop clichés
- No pop glossy vocal
- No trap hi-hat rolls (если не надо)
- No long spoken monologues
- No chorus copy-paste 3 times without variation
- No same vocal timbre as previous track (voice diversity)

---

## 7) PROCEDURE (WRITE PROMPT CONTRACT)
### Step 1 — Write STYLE FINGERPRINT (2 lines)
### Step 2 — Declare TEMPO/GROOVE
### Step 3 — Declare STRUCTURE MAP (sections + hook placement)
### Step 4 — Declare VOICE SPEC
### Step 5 — Declare MIX
### Step 6 — Add NEGATIVE SPEC
### Step 7 — Add QA TARGETS
### Step 8 — Run mini-QA after generation
- если провал: править контракт (не “с нуля”)

---

## 8) PROMPT CONTRACT TEMPLATE (COPY)
PROMPT CONTRACT:
STYLE:
- genres:
- fingerprint markers:
TEMPO:
- bpm:
- feel:
STRUCTURE:
- sections:
- hook placement:
- duration target:
INSTRUMENTATION:
- core:
- signature:
VOICE:
- language:
- delivery:
- character:
MIX:
- target:
LYRICS:
- text/intent:
NEGATIVE SPEC:
- style:
- arrangement:
- vocals:
- lyrics/themes:
QA TARGETS:
- hook:
- vocal clarity:
- repetition guard:
- style consistency:

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] все секции A–I присутствуют
- [ ] negative spec заполнен (не пустой)
- [ ] есть structure map
- [ ] voice spec конкретный
- [ ] есть QA targets
- [ ] контракт можно повторить (не одноразовый)

PASS IF:
- всё заполнено и конкретно

REWORK IF:
- секции есть, но слишком общие (“круто, мощно”)

FAIL IF:
- нет negative spec или нет структуры/голоса

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (industrial nu metal)
STYLE:
- electronic nu metal + industrial rock, rap rock
TEMPO:
- 94 bpm, half-time stomp
STRUCTURE:
- verse rap → chorus melodic → verse → bridge → final chorus
VOICE:
- russian male, rap verses + melodic chorus
NEGATIVE:
- no pop sheen, no trap rolls, no excessive repetition
QA:
- hook ≤ 15s, vocal readable
WHY PASS:
- контракт воспроизводим и проверяем.

### 10.2 FAIL EXAMPLE
“Сделай крутой трек, чтобы качало”
WHY FAIL:
- нет структуры, нет негативов, нет воспроизводимости.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (contracts must include negative spec + QA targets)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
