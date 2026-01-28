# TOPIC — MIX TRANSLATION QA (SOUND & MUSIC / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/05__SOUND_MUSIC__MIX_TRANSLATION_QA.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.MUSIC.MIX_TRANSLATION_QA.001
OWNER: SYSTEM
ROLE: Atomic method to QA mix translation across playback contexts: device matrix, critical checks (bass, vocal, harshness, mono), defect taxonomy, and fix strategies; includes Mix QA Scorecard and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created mix translation QA: device/context matrix, critical listening checks, defect taxonomy, and fix playbook for generator outputs."
- REASON: "Generated mixes often sound good in one context and fail in others; translation QA is required for release readiness."
- IMPACT: "Entities can ship cleaner, tighter mixes that work on phones, cars, earbuds, and mono playback."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.MUSIC.005

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_sound_music
- type_topic
- mix_qa
- translation
- loudness_balance
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Проверить “переводимость” микса:
- чтобы трек звучал хорошо в разных условиях,
- вокал был читаем,
- низ был плотный, но не “жвачка”,
- не было убийственной резкости,
- моно не ломало хук.

---

## 2) WHEN TO USE
- Готовишь трек к релизу.
- В наушниках норм, а в машине/телефоне плохо.
- Вокал тонет или бас раздувает.
- Нужен clean aggressive mix для rap rock/industrial/nu metal.

## 3) WHEN NOT TO USE
- Черновик для идеи (но можно быстро прогнать базовый чек).

---

## 4) DEFINITIONS (STRICT)
### Translation
Стабильность восприятия на разных устройствах и в разных условиях.

### Context matrix
Набор тестовых сценариев прослушивания.

### Mono compatibility
Трек не разваливается при моно (суммирование каналов).

---

## 5) CONTEXT MATRIX (MINIMUM SET)
Минимум 6 контекстов:
- C1: Studio headphones
- C2: Cheap earbuds
- C3: Phone speaker (mono-ish)
- C4: Laptop speakers
- C5: Car system (road noise)
- C6: Small Bluetooth speaker

Optional:
- C7: TV soundbar
- C8: Club-ish (if relevant)

---

## 6) CRITICAL CHECKS (WHAT TO LISTEN FOR)
### A) Vocal intelligibility
- слова читаются в куплете и припеве?
- не маскируются гитарами/синтами?
- согласные не “съедены”?

### B) Low end tightness
- бас не гудит?
- кик читается?
- низ не “разваливает” телефон/колонку?

### C) Harshness / fatigue
- нет ли режущих частот (особенно на дешёвых наушниках)?
- не устаёт ли ухо за 30 секунд?

### D) Balance (instrument vs vocal)
- вокал не слишком тихий/громкий
- гитары не убивают припев

### E) Mono check
- в моно хук сохраняется?
- не исчезают ключевые элементы (фазовые отмены)?

### F) Dynamic feel
- трек не “плоский”?
- припев ощущается шире/выше?

---

## 7) DEFECT TAXONOMY (MIX)
- M1: Vocal buried (вокал утонул)
- M2: Vocal too loud/harsh
- M3: Mud (грязная середина, всё в каше)
- M4: Bass boomy (гудит низ)
- M5: Kick disappears (нет удара)
- M6: Harsh top (режет верх)
- M7: Mono collapse (в моно пропадает хук)
- M8: Too flat (нет динамики ощущений)
- M9: Sibilance (с/ш слишком ярко)
- M10: Generator artifacts (цифровая грязь/шипение)

---

## 8) FIX PLAYBOOK (WHAT TO CHANGE)
Без конкретных цифр (генераторы разные), но логика такая:

### Fix for M1 (vocal buried)
- просить “vocal forward / present”
- уменьшить плотность синтов в припеве
- попросить меньше distortion на гитарах в области вокала

### Fix for M4 (bass boomy)
- “tight low end, controlled sub, less boom”
- “punchy kick, less sustained bass”
- попросить меньше reverb/room на низе

### Fix for M7 (mono collapse)
- запретить wide-only элементы как ключевые
- попросить “mono-compatible, centered hook elements”
- добавить “centered lead + supportive width”

### Fix for M6/M9 (harsh/sibilance)
- “smooth top end, no harshness”
- “controlled sibilance”
- меньше “crispy” синтов, меньше aggressive hi-hats

### Fix for M10 (artifacts)
- “clean aggressive mix, no digital fizz”
- “avoid glitch noise masking vocals” (если мешает)

---

## 9) MIX QA SCORECARD (COPY)
MIX QA SCORECARD:
- Track:
- Style:
- Context matrix results:
  - C1:
  - C2:
  - C3:
  - C4:
  - C5:
  - C6:
- Checks:
  - Vocal intelligibility:
  - Low end tightness:
  - Harshness/fatigue:
  - Balance:
  - Mono:
  - Dynamic feel:
- Defects (M1..M10):
  - M?:
- Fix plan (ordered):
  1)
  2)
- Decision: PASS | REWORK | FAIL

---

## 10) PASS/REWORK/FAIL THRESHOLDS
PASS IF:
- вокал читается в C2/C3/C5
- низ не ломает C3/C6
- моно не убивает хук
- нет M10 тяжёлых артефактов

REWORK IF:
- 1–2 дефекта средней силы (M1/M4/M6) и они исправимы правкой контракта

FAIL IF:
- mono collapse + vocal buried + artifacts (комбо)
- трек не переводится в 3+ контекстах

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE
- C3 phone: хук слышен, вокал читается
- C5 car: кик держит, низ не гудит
Decision: PASS

### 11.2 REWORK EXAMPLE
- C2 earbuds: вокал утонул (M1)
- Fix: “vocal forward, reduce dense synth layers”
Decision: REWORK

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (must test ≥6 contexts; must run mono check; fix plan must be explicit)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
