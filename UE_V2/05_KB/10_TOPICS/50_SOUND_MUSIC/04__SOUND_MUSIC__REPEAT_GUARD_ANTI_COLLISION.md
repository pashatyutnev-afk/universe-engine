# TOPIC — REPEAT GUARD & ANTI-COLLISION (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/04__SOUND_MUSIC__REPEAT_GUARD_ANTI_COLLISION.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.REPEAT_GUARD.001
OWNER: SYSTEM
ROLE: Atomic method to prevent repetition and collisions in generated music catalogs: repeat taxonomy, collision dimensions (lyric/melody/rhythm/voice), guardrails, and QA checks; includes Repeat Audit Sheet and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created repeat guard & anti-collision standard: classify repeats, detect collisions across recent catalog, and apply fixes via constraint edits instead of full rewrites."
- REASON: "Generators converge to repeated patterns; without guards catalogs feel samey and low-quality."
- IMPACT: "Entities can keep novelty while preserving brand style; reduces 'same chorus' and 'same voice' problems."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.004

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- repeat_guard
- collision_guard
- novelty
- qa_gates
- maturity_seed

---

## 1) PURPOSE
Запретить разрушительные повторы:
- повтор текста/рифм/паттернов,
- повтор мелодического контура хука,
- повтор ритм-рисунка и аранжа,
- повтор голоса и манеры.

И сделать это через guards + тесты.

---

## 2) WHEN TO USE
- Генератор “залипает” на одинаковых словах и ритмах.
- Разные треки звучат как один и тот же.
- Куплеты повторяют строки почти дословно.
- Хуки похожи на предыдущие хиты каталога.

## 3) WHEN NOT TO USE
- Если задача — намеренный луп/мантра (тогда фиксировать это как художественную норму и ограничить длительность).

---

## 4) DEFINITIONS (STRICT)
### Repeat
Повтор внутри одного трека (может быть полезен, но контролируем).

### Collision
Сходство между треками каталога, вызывающее “перепутал песню/голос”.

### Guard
Правило, которое запрещает определённый тип повтора/коллизии.

---

## 5) REPEAT TAXONOMY (INSIDE A TRACK)
- R1: Hook repeat (нормальный повтор припева)
- R2: Line repeat (одна и та же строка слишком много раз)
- R3: Phrase echo (повтор 2–4 слов в куплетах)
- R4: Rhyme loop (одинаковая рифма/окончание 6+ строк подряд)
- R5: Pattern loop (одинаковая ритмика фраз весь куплет)
- R6: Arrangement loop (аранж не меняется 60+ секунд)
- R7: Vocal loop (одна манера/тембр без переключений ролей)

Правило:
- допустимы R1 + ограниченный R2/R3
- опасны R4/R5/R6/R7

---

## 6) COLLISION DIMENSIONS (BETWEEN TRACKS)
Сравнивать с last 3–10 треков:

- C1: Lyric collision (слова/ключевая фраза/схема рифм)
- C2: Hook contour collision (мелодический контур припева)
- C3: Rhythm groove collision (одинаковый “удар” и рисунок)
- C4: Arrangement signature collision (одни и те же хуки инструментов/интро)
- C5: Voice collision (тембр/подача/акцент)
- C6: Sound tag collision (один и тот же glitch-tag)

---

## 7) GUARDS (STRICT RULES)
### G1 — Line repeat cap
Одна строка (вне припева) не может повторяться > 2 раз.

### G2 — Rhyme loop cap
Одинаковая рифма/окончание не более 4 строк подряд.

### G3 — Verse uniqueness
Куплет 2 обязан:
- иметь новые образы/формулировки,
- не копировать куплет 1 по структуре строк 1:1.

### G4 — Arrangement change marker
Каждые 30–45 секунд должен быть слышимый сдвиг:
- drop/stop, новый слой, смена ритма, смена тембра.

### G5 — Voice role switch
Если есть A/B:
- минимум 2 переключения ролей или явный контраст секций.

### G6 — Catalog collision check
Перед выпуском:
- сравнить с last 3–10 треков по C1..C6.
Если 2+ коллизий → REWORK.

---

## 8) PROCEDURE (REPEAT AUDIT → FIX)
### Step 1 — Audit inside track
Отметить:
- R2/R3/R4/R5/R6/R7

### Step 2 — Audit against catalog (last 3–10)
Отметить коллизии C1..C6.

### Step 3 — Decide severity
- Minor: 1 маленькая коллизия (C6 tag), чинится легко
- Medium: 1–2 коллизии (например C3+C4)
- High: 2+ коллизии включая C2 или C5 (hook/voice) → срочно править

### Step 4 — Apply fixes (do not rewrite everything)
**Fix set A (lyrics)**
- заменить ключевые слова/метафоры
- поменять рифмовку (ABAB→AABB)
- добавить 2 уникальных строки во 2 куплет

**Fix set B (hook)**
- изменить слоган 1–2 слова
- изменить ритм слогов (длина/паузы)
- изменить контур (вверх→вниз)

**Fix set C (arrangement)**
- новый sound tag
- stutter/stop в другом месте
- смена слоя в припеве (гитары шире/уже)

**Fix set D (voice)**
- сменить 3–4 оси voice profile (см. voice diversity)
- добавить контраст (грит/клин, низ/середина)

### Step 5 — Re-run audit
Только после фикс-пакета.

---

## 9) REPEAT AUDIT SHEET (COPY)
REPEAT AUDIT SHEET:
- Track:
- Inside-track repeats:
  - R2 line repeat:
  - R4 rhyme loop:
  - R6 arrangement loop:
  - R7 vocal loop:
- Catalog collisions (last N):
  - C1:
  - C2:
  - C3:
  - C4:
  - C5:
  - C6:
- Severity: Minor|Medium|High
- Fix plan:
  1)
  2)
- Result after fix: PASS/REWORK

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] line repeat cap соблюдён
- [ ] rhyme loop cap соблюдён
- [ ] verse 2 уникален относительно verse 1
- [ ] есть arrangement change каждые 30–45s
- [ ] A/B контраст соблюдён
- [ ] catalog collision check пройден (last 3–10)
- [ ] нет 2+ коллизий, включая hook/voice

PASS IF:
- все пункты true

REWORK IF:
- есть 1–2 minor/medium коллизии

FAIL IF:
- hook/voice collision или 2+ коллизии

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE
Трек:
- припев повторяется (R1) — ок
- куплет 2 новые образы (G3) — ок
- sound tag новый — нет C6
WHY PASS:
- стиль единый, но контент свежий.

### 11.2 FAIL EXAMPLE
- куплет 2 копирует куплет 1 строка-в-строку
- голос совпадает с прошлым треком
- хук очень похож по контуру
WHY FAIL:
- G3 + C5 + C2 → FAIL.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/02__SOUND_MUSIC__VOICE_DIVERSITY_RULES.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (guards mandatory; collisions must trigger rework/fail)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
