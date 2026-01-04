# Timeline & Epoch Engine
FILE: 03__TIMELINE_EPOCH_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines time structure of the world (calendars, scales, epochs, anchors, causality constraints); produces a Timeline Master, Epoch Registry, and Event Anchor system enabling consistent history, chronology, and continuity across narratives and world systems

---

## PURPOSE

Таймлайн — это “когда что возможно”.
Движок нужен, чтобы:
- история мира не противоречила сама себе
- эпохи имели границы и признаки
- события имели якоря и зависимости
- любые “прошлое/настоящее” сцены были согласованы
- технологические/политические уровни не прыгали хаотично

---

## NON-GOALS

- не описывает географию (World Structure)
- не описывает культуру детально (Civilization)
- не пишет сюжет серии (Narrative engines)
Он задаёт **временной каркас** мира.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Structure Spec (WSS) (regions/layers)
- World Law Spec (WLS) (time-related constraints if any)
- Civilization/Tech notes (if available)
- Narrative requirements (key historical beats needed by story)

### PRODUCES
- TIMELINE MASTER (TM) — canonical artifact
- EPOCH REGISTRY (ER) — epochs + signatures
- EVENT ANCHOR SYSTEM (EAS) — anchors + dependencies
- RETCON POLICY for time (handoff to governance)

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md (sync)

### OUTPUT_TARGET
- Feeds:
  - Civilization engine (rise/fall)
  - Geopolitics engine (borders through time)
  - Economy/Resource engine (routes eras)
  - Technology & Magic engine (tech levels by epoch)
  - Narrative engines (flashbacks, lore, reveals)

---

## CANON TERMS

### EPOCH
Эпоха — период с:
- границей начала/конца (или “ongoing”)
- набором признаков (signature)
- доминирующими силами/технологиями/порядком

### ANCHOR EVENT
Якорное событие — фиксированная точка,
от которой зависят другие даты.

### RELATIVE TIME
Если точных лет нет, используем относительное:
- “через 12 лет после X”
- “в конце эпохи Y”

### CAUSALITY DEPENDENCY
Зависимость:
- B не может случиться, пока не случилось A.

---

## TIME REPRESENTATION (STANDARD)

Поддерживаем 2 режима:

### Mode A — Absolute (calendar)
- Year/Month/Day
- local calendar rules if needed

### Mode B — Relative (anchor-based)
- T+N relative to anchor event
- useful when years are unknown or intentionally vague

Rule:
- Canon must have at least:
  - 5–20 anchor events
  - epoch registry
  - dependencies graph

---

## REQUIRED ARTIFACT A: EPOCH REGISTRY (ER)

### ER SCHEMA (CANON)

Header:
- ER_ID:
- WORLD_ID:
- VERSION:
- STATUS:

Epochs (repeat):
- EPOCH_ID:
- NAME:
- START:
  - absolute date OR anchor reference
- END:
  - absolute OR anchor OR ongoing
- SIGNATURES (3–10):
  - tech level, power structures, major threats, aesthetic
- DOMINANT POWERS (optional):
- CORE CONFLICTS (optional):
- TRAVEL/COMMS BASELINE:
  - how fast info/movement is in this epoch
- CANON “NO-GO”:
  - what cannot exist here (tech/power/politics)
- EVIDENCE MARKERS:
  - artifacts/ruins/documents that indicate this epoch

---

## REQUIRED ARTIFACT B: TIMELINE MASTER (TM)

### TM SCHEMA (CANON)

Header:
- TM_ID:
- WORLD_ID:
- MODE:
  - absolute | relative | mixed
- VERSION:
- STATUS:

Anchor Events (repeat):
- ANCHOR_ID:
- NAME:
- DATE:
  - absolute OR relative expression
- EPOCH:
  - EPOCH_ID
- DESCRIPTION (short):
- CAUSALITY LOCK:
  - what this enables/disables
- WORLD IMPACT:
  - regions affected
- CONTINUITY LOCK:
  - never retcon lightly

Events (repeat):
- EVENT_ID:
- NAME:
- DATE:
  - absolute OR relative to anchor
- EPOCH:
- REGION/LAYER (optional):
- TYPE:
  - war | discovery | collapse | migration | revolution | disaster | treaty
- DEPENDS ON:
  - list of ANCHOR_ID/EVENT_ID
- CONSEQUENCES:
  - list of state changes
- SOURCES (in-world):
  - records/ruins/myths (optional, for flavor)
- CONFIDENCE:
  - high | medium | low (if intentionally uncertain lore)

Rule:
- If CONFIDENCE != high, it must be declared that lore is disputed.

---

## REQUIRED ARTIFACT C: EVENT ANCHOR SYSTEM (EAS)

### EAS RULESET (CANON)

- Anchors are minimal but immovable.
- New events should attach to anchors when possible.
- If a new event threatens anchor order:
  - it must pass governance change control.

Dependency Graph Rules:
- No circular dependencies.
- Each major epoch transition requires at least 1 anchor event.
- Each major tech/power shift must be tied to:
  - an anchor OR explicit “unknown transition window”.

---

## TIMELINE RULES (CANON)

### T1 — Epoch signatures must be consistent
Если эпоха заявлена “пост-коллапс”,
нельзя иметь повсеместные мегаполисы без объяснения.

### T2 — Causes precede effects
События, требующие предпосылок, не могут стоять раньше.

### T3 — Retcon is governance-only
Любая правка якорей/границ эпох:
- change control
- canon authority
- audit log

### T4 — Mixed mode must declare precision
Если часть дат точная, часть нет:
- указывать CONFIDENCE
- не делать сюжетные решения на “low confidence” как на факт

### T5 — Time travel / temporal anomalies
Если в мире есть временные аномалии:
- это закон мира (WLS) + исключения (ERX)
- таймлайн ведётся с пометками “branch/loop”
Иначе запрет.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- event depends on tech that doesn't exist in its epoch
- wars happen before borders/powers exist
- migrations ignore travel baselines
- same artifact appears in two epochs with no explanation
- circular dependency in events
- “low confidence” treated as hard fact

Fix options:
- move event relative to anchor
- add missing enabling event
- split epoch or redefine signature
- declare disputed lore + limit its usage
- add transition window

---

## PROCEDURE (HOW TO RUN)

1) Define timeline mode (absolute/relative/mixed)
2) Create epoch registry with signatures and no-go list
3) Define 5–20 anchor events
4) Attach events to anchors with dependencies
5) Add consequences and continuity locks
6) Run inconsistency checks
7) Lock TM/ER via governance if changed later

---

## QC CHECKLIST (MANDATORY)

- epoch registry exists with signatures + no-go?
- anchors exist (>=5)?
- major transitions anchored?
- dependencies listed and non-circular?
- events declare confidence if uncertain?
- continuity locks set for anchors?

---

## VALIDATION RULES

- TLV1: Epochs + anchors exist and support consistent chronology.
- TLV2: Dependencies enforce causality (no effects before causes).
- TLV3: Tech/power/logistics match epoch signatures.
- TLV4: Retcons of anchors go through governance.

---

OWNER: Universe Engine
LOCK: FIXED
