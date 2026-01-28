# TOPIC — SONG STRUCTURE BLUEPRINTS (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/07__SOUND_MUSIC__STRUCTURE_SONG_BLUEPRINTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.SONG_STRUCTURE.001
OWNER: SYSTEM
ROLE: Atomic blueprint library for structuring songs (esp. rap verse + melodic chorus) with timing targets, hook windows, contrast plans, and variants (full/short/loop); includes Structure Cards and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created song structure blueprints: common section maps with timing targets, hook placement, contrast rules, and UGC variants."
- REASON: "Generated tracks often drift structurally; blueprints enforce pacing and hook cadence for consistent outcomes."
- IMPACT: "Entities can generate full tracks and short variants with predictable energy arcs and better retention."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.007

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- song_structure
- blueprint_library
- hook_cadence
- ugc_variants
- maturity_seed

---

## 1) PURPOSE
Дать каркасы (blueprints), по которым строится песня:
- порядок секций,
- тайминг (примерно),
- где хук должен появиться,
- где контраст/стоп/переключение ролей,
- как из full сделать short/loop.

---

## 2) WHEN TO USE
- Трек “плывёт”, нет ясной формы.
- Хук поздно или слабый.
- Нужны версии 15/30/60 и loop для shorts.
- Нужна стабильность структуры между треками группы/альбома.

## 3) WHEN NOT TO USE
- Свободная экспериментальная композиция без формы (но тогда нужно явно это зафиксировать как контракт).

---

## 4) DEFINITIONS (STRICT)
### Blueprint
Схема секций с целевыми окнами времени и правилами контраста.

### Hook window
Окно появления хука:
- target: 0:10–0:20
- hard max: 0:25

### Contrast point
Место, где меняется ощущение:
- плотность/тембр/ритм/голос/ширина.

---

## 5) BLUEPRINT LIBRARY (CORE SET)
### BP1 — Standard full song (≈3:00) rap+melodic
- 0:00–0:08 Intro tag (H4)
- 0:08–0:38 Verse 1 (rap, B)
- 0:38–1:05 Chorus 1 (melodic, A) [HOOK]
- 1:05–1:35 Verse 2 (rap, B) (новые образы)
- 1:35–2:02 Chorus 2 (A) (вариация + шире)
- 2:02–2:25 Bridge (A/B call-response) [contrast]
- 2:25–2:55 Final chorus (A) (peak)
- 2:55–3:00 Outro tag

### BP2 — Fast hook entry (≈2:30)
- 0:00–0:05 Cold open hook (A) [HOOK]
- 0:05–0:25 Verse (B)
- 0:25–0:50 Chorus (A)
- 0:50–1:20 Verse 2 (B)
- 1:20–1:50 Chorus 2 (A)
- 1:50–2:20 Bridge/Break
- 2:20–2:30 Outro

### BP3 — UGC 30s (hook loop)
- 0:00–0:05 Tag + stomp hit
- 0:05–0:20 Hook line A/A'
- 0:20–0:30 Hook repeat + stutter stop (loop-friendly)

### BP4 — UGC 15s (micro hook)
- 0:00–0:03 Tag
- 0:03–0:12 Hook line + signature hit
- 0:12–0:15 Stop + restart (loop)

### BP5 — Heavy intro (industrial/nu metal build, ≈3:10)
- 0:00–0:15 Industrial intro (texture)
- 0:15–0:45 Verse 1 (B)
- 0:45–1:12 Chorus 1 (A) [HOOK]
- 1:12–1:42 Verse 2 (B)
- 1:42–2:10 Chorus 2 (A)
- 2:10–2:35 Breakdown (riff + stutter)
- 2:35–3:05 Final chorus
- 3:05–3:10 Outro

---

## 6) STRUCTURE RULES (STRICT)
- SR1: hook в первом окне (≤ 0:25)
- SR2: Verse 2 = новые образы/новая динамика (не копия)
- SR3: минимум 1 contrast point (bridge/breakdown)
- SR4: финальный припев должен быть “пик” (шире/выше/плотнее)
- SR5: outro короткое и “брендовое” (tag)

---

## 7) ROLE SWITCH RULES (A/B)
- A (melodic) должен доминировать в hook sections
- B (rap) доминирует в verses
- 1 call-response момент обязателен (bridge или интро)

---

## 8) VARIANTS (FULL → SHORT)
### Full → 30s
- вырезать: Verse 2
- оставить: Hook (A/A') + tag + stutter stop
- обеспечить loop (конец совпадает по энергии с началом)

### Full → 15s
- только: tag + hook line + stop

### Full → instrumental
- hook остаётся инструментальным (melodic lead)
- vocal phrases заменены synth lead / guitar motif

---

## 9) STRUCTURE CARD TEMPLATE (COPY)
STRUCTURE CARD:
- Track:
- Blueprint: BP1..BP5
- Hook window target:
- Sections (time ranges):
- Contrast point:
- A/B role plan:
- Variants needed: 15s|30s|60s|instrumental
- QA:
  - Hook <= 0:25:
  - Verse2 uniqueness:
  - Contrast present:
  - Final peak:
- Result: PASS/REWORK

---

## 10) PASS/FAIL TESTS
PASS IF:
- хук ≤ 0:25
- есть минимум 1 contrast point
- Verse 2 не копия Verse 1
- финальный припев пик энергии
- есть короткий outro tag

REWORK IF:
- хук поздний или контраста мало

FAIL IF:
- структура “плывёт”, нет повторяемого каркаса

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (your track)
Blueprint:
- BP1
Hook:
- “Сбо́и в голове — но я вижу маршрут” на 0:38 (OK)  
(или ускорить под BP2, если надо)
Contrast:
- bridge call-response “Сейчас—режим”
WHY PASS:
- каркас держит энергию и делает трек понятным.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/04__SOUND_MUSIC__REPEAT_GUARD_ANTI_COLLISION.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (hook timing + blueprint selection mandatory for reproducible structure)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
