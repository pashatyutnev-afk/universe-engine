# TOPIC — TRACK FACTORY: ITERATION LOG (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/14__SOUND_MUSIC__TRACK_FACTORY_ITERATION_LOG.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.TRACK_FACTORY_LOG.001
OWNER: SYSTEM
ROLE: Atomic method to run track creation as an iteration factory with deterministic logging: prompt contract versions, attempt records, QA defects, fix deltas, and release readiness; includes Iteration Log templates and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created track factory iteration log: attempt records, contract diffs, QA defects, and fix actions to prevent random generation and enable systematic improvement."
- REASON: "Without logging, generation becomes lottery; iteration logs preserve learning and reduce repetition/collisions."
- IMPACT: "Entities can converge faster to high-quality tracks, audit decisions, and scale catalog production."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.014

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- track_factory
- iteration_log
- prompt_iteration
- qa_defects
- maturity_seed

---

## 1) PURPOSE
Сделать генерацию треков “фабрикой”, а не лотереей:
- каждый заход = запись,
- промпт = контракт версии,
- дефекты фиксируются именами,
- правки делаются “дельтами” (что изменили),
- видно прогресс и причины.

---

## 2) WHEN TO USE
- Серийно делаешь треки/альбомы.
- Нужно удержать стиль, но повысить качество.
- Нужна память по удачным/плохим формулировкам.
- Хочешь быстро находить, почему результат плохой.

## 3) WHEN NOT TO USE
- Разовый трек без повторения (но можно лог минимальный).

---

## 4) DEFINITIONS (STRICT)
### Attempt
Одна генерация (A01, A02…).

### Contract version
Версия промпт-контракта, которая использовалась.

### Delta
Изменение между попытками:
- что поменяли в контракте (конкретно), и зачем.

### QA defect
Дефект по рубрике (например D1 hook late, M1 vocal buried).

---

## 5) FACTORY LOOP (CORE)
LOOP:
1) Contract (vX.Y.Z)
2) Attempt (A##)
3) QA scorecard (defects)
4) Fix plan (deltas)
5) Next attempt
6) Release pack (если PASS)

---

## 6) REQUIRED RECORDS (MINIMUM)
Для каждого трека:
- Track ID + working title
- Style fingerprint
- Contract vX.Y.Z
- Attempts list (A01..)
- Best attempt candidate
- QA result history
- Collision checks vs catalog
- Final release decision

---

## 7) ATTEMPT RECORD TEMPLATE (COPY)
ATTEMPT RECORD:
- TRACK:
- Attempt ID: A##
- Date:
- Contract version:
- Prompt delta vs previous:
  - Changed:
  - Reason:
- Output notes:
  - Hook timing:
  - Voice A/B:
  - Repeats:
  - Mix issues:
- QA defects:
  - D? (narrative/music):
  - M? (mix):
- Decision:
  - KEEP / REWORK / DISCARD
- Next step:

---

## 8) TRACK MASTER LOG TEMPLATE (COPY)
TRACK MASTER LOG:
- Track:
- Style fingerprint:
- Target blueprint (BP):
- Voice A/B (VP):
- Contract baseline (v1.0.0):
- Attempts:
  - A01: decision + key notes
  - A02: ...
- Best candidate:
- Defect trends:
  - recurring defects:
- Fix library (what works):
  - phrase that improved vocals:
  - phrase that reduced repetition:
- Final decision:
  - PASS to Release Pack / Continue / Kill

---

## 9) DEFECT TAGGING (STANDARD)
Использовать единые теги:
- Hook: D1 (no hook), late hook
- Repeat: R4/R6 (repeat guard)
- Voice: C5 collision
- Mix: M1/M4/M7/M10
- Style drift: drift (genre drift)

---

## 10) FIX DELTAS (HOW TO ITERATE)
Правило:
- одна попытка = 1–3 дельты, не 20 изменений.

Типы дельт:
- ΔHook: “hook in first 10s, drop-less”
- ΔVoice: смена 3 осей voice profile
- ΔRepeat: добавить negative spec “no repeated lines”
- ΔMix: “vocal forward, tight low end”
- ΔStructure: смена blueprint BP1→BP2
- ΔUGC: добавить call-response moment

---

## 11) PASS/FAIL GATES
PASS IF:
- QA gates PASS (music scorecard)
- нет collision vs last 3–10
- hook ≤ 0:15–0:25
- vocals readable in phone/earbuds
- repeat guard ok

REWORK IF:
- 1–2 дефекта, исправимо дельтами

KILL IF:
- 4+ попытки без прогресса
- постоянный voice/hook collision
(тогда меняем основу: другой hook phrase / другой blueprint / другой fusion fingerprint)

---

## 12) EXAMPLES (MANDATORY)
### 12.1 PASS EXAMPLE (iteration)
A01:
- hook late (D1), vocal buried (M1) → REWORK
Δ:
- “hook in first 10s”, “vocal forward”
A02:
- hook ok, vocal ok, repeats minor → KEEP
WHY PASS:
- итерации точечные и измеримые.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/04__SOUND_MUSIC__REPEAT_GUARD_ANTI_COLLISION.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (no blind bulk generation; every attempt logged; deltas limited per attempt)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
