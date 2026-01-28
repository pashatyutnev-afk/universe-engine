# TOPIC — PROMPT PHRASEBOOK & NEGATIVE LIBRARY (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/15__SOUND_MUSIC__PROMPT_PHRASEBOOK_NEGATIVE_LIBRARY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.PHRASEBOOK_NEG.001
OWNER: SYSTEM
ROLE: Atomic library of reusable prompt phrases and negative specs for music generation: categorized snippets for hook timing, vocal clarity, mix translation, structure, UGC moments, and anti-repetition; includes usage rules and pass/fail checks

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created prompt phrasebook + negative library: reusable phrasing by category and rules to apply them as deltas during iteration."
- REASON: "Iteration is slow without a controlled phrase library; negative specs must be standardized to reduce repeats, drift, and mix issues."
- IMPACT: "Entities can iterate faster, keep consistency, and reduce recurring defects across catalogs."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.015

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- phrasebook
- negative_library
- iteration_deltas
- qa_gates
- maturity_seed

---

## 1) PURPOSE
Дать библиотеку готовых формулировок:
- чтобы быстро чинить дефекты (hook/voice/mix/repeat),
- чтобы не повторять ошибки,
- чтобы итерации делались “дельтами”, а не переписыванием всего контракта.

---

## 2) WHEN TO USE
- Любая генерация треков сериями.
- Когда нужно улучшить результат точечной правкой.
- Когда повторяются проблемы: поздний хук, одинаковые голоса, мутный вокал, каша низа.

## 3) WHEN NOT TO USE
- Если промпт вообще не нужен (не тот инструмент) — но в вашей системе обычно нужен.

---

## 4) USAGE RULES (STRICT)
- UR1: использовать фразы как Δ (дельты) в итерационном логе
- UR2: добавлять 1–3 фразы за итерацию, не 20
- UR3: negative spec всегда присутствует (минимум 3 пункта)
- UR4: не смешивать взаимоисключающие фразы (например “wide vocal” и “centered vocal” одновременно)
- UR5: после изменения — прогнать QA (hook/voice/mix/repeat)

---

## 5) PHRASEBOOK — HOOK & TIMING
- "hook in the first 10–15 seconds"
- "drop-less hook, no long intro"
- "immediate hook signal in first 3 seconds"
- "repeat hook with micro-variation, avoid copy-paste"
- "signature tag shout in intro/outro (1–2 words)"

---

## 6) PHRASEBOOK — STRUCTURE & PACING
- "rap verse → melodic chorus → rap verse → bridge call-response → final chorus"
- "half-time stomp sections, with one contrast break"
- "add a breakdown with stutter edits before final chorus"
- "tight 2:40–3:10 full song pacing, no filler"
- "verse 2 must introduce new imagery and rhythm phrasing"

---

## 7) PHRASEBOOK — VOCALS (CLARITY & CONTRAST)
- "russian male vocals, crisp articulation in rap verses"
- "melodic chorus, wider and higher energy than verses"
- "A/B roles clearly distinct (timbre + delivery + persona)"
- "no mumbling, vocals forward and intelligible"
- "controlled aggression, clean but gritty texture"

---

## 8) PHRASEBOOK — MIX & TRANSLATION
- "clean aggressive mix, tight low end"
- "vocal forward, guitars/synths not masking vocals"
- "mono-compatible hook elements, centered lead"
- "avoid harsh top end, smooth highs"
- "punchy kick, controlled sub, no boom"

---

## 9) PHRASEBOOK — UGC MOMENTS
- "include 2–5 second attention spikes (stutter stop + hit)"
- "call-response moment designed for clips"
- "loop-safe 15s and 30s variants"
- "meme-ready one-liner hook phrase"
- "signature glitch tag that repeats once per chorus"

---

## 10) PHRASEBOOK — ANTI-REPEAT / NOVELTY
- "avoid repeated lines beyond chorus"
- "no identical verse structure repeated"
- "reduce lyrical repetition, increase imagery variety"
- "avoid same melodic contour as previous track"
- "avoid same vocal timbre as last 3 tracks"

---

## 11) NEGATIVE LIBRARY (STANDARD SETS)
### NegSet A — anti-pop/EDM drift
- "no EDM build-drop clichés"
- "no glossy pop vocal"
- "no bright happy pop chord progressions"
- "no generic festival drop"

### NegSet B — anti-trap drift
- "no trap hi-hat rolls"
- "no 808 trap bounce"
- "no drill rhythms"

### NegSet C — anti-repetition
- "no repeated lines outside chorus"
- "no chorus copy-paste without variation"
- "no identical verse phrasing"
- "no recycled hook phrase"

### NegSet D — anti-mix problems
- "no muddy midrange"
- "no boomy bass"
- "no harsh sibilance"
- "no digital fizz artifacts masking vocals"

---

## 12) DEFECT → PHRASE MAPPING (FAST FIX)
- D1 hook late → add: "hook in first 10–15 seconds", "drop-less hook"
- M1 vocal buried → add: "vocal forward", "not masking vocals"
- C5 voice collision → add: "avoid same vocal timbre as last 3 tracks", change A/B contrast
- R4/R6 repeats → add NegSet C + "micro-variation"
- M7 mono collapse → add: "mono-compatible hook elements, centered lead"
- Drift → add NegSet A/B

---

## 13) PHRASE PACK TEMPLATE (COPY)
PHRASE PACK:
- Goal (fix):
- Added phrases (1–3):
  - P1:
  - P2:
- Negative spec (>=3):
  - N1:
  - N2:
  - N3:
- Expected impact:
- QA to run:
  - hook test:
  - voice contrast:
  - mix translation:

---

## 14) PASS/FAIL
PASS IF:
- фразы используются как дельты
- negative spec не пустой
- QA улучшился по целевому дефекту

REWORK IF:
- фраз слишком много и эффект непонятен

FAIL IF:
- фразы противоречат друг другу или не привязаны к дефекту

---

## 15) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/14__SOUND_MUSIC__TRACK_FACTORY_ITERATION_LOG.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/04__SOUND_MUSIC__REPEAT_GUARD_ANTI_COLLISION.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 16) COMPLIANCE
- SOURCE_LOCK: required (use as deltas; 1–3 phrases per iteration; negative spec mandatory)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
