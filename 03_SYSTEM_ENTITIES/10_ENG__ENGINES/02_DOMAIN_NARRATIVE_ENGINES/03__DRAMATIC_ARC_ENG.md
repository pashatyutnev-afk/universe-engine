# Dramatic Arc Engine
FILE: 03__DRAMATIC_ARC_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Models dramatic/emotional progression across a scope; produces an explicit Dramatic Arc Spec that maps tension, hope/fear, stakes escalation, and payoff timing to structure and scenes

---

## PURPOSE

Драматическая дуга — это “эмоциональная математика истории”.
Она отвечает за:
- рост напряжения
- распределение надежды/страха
- точки разрядки
- ощущение прогрессии и “необратимости”

Без дуги:
- история кажется плоской или рваной
- кульминации “не работают”
- зритель устает или теряет интерес

---

## NON-GOALS

- не задаёт монтажный ритм (это Editing engine)
- не задаёт стиль/жанр (Genre/Style family)
- не заменяет структуру истории (Story Structure)
Он описывает эмоциональную кривую поверх структуры.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Story Structure Spec (SSS)
- Narrative Logic Spec (NLS)
- Theme hook (optional)
- Key character stakes (optional)

### PRODUCES
- DRAMATIC ARC SPEC (DAS)
- ARC CURVE MAP (tension over time)
- RELEASE POINTS map (where relief happens)
- PAYOFF TIMING map (when setups pay emotionally)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG.md

### OUTPUT_TARGET
- Feeds Scene Construction (04) and Pacing & Rhythm (05)
- Informs Tension & Stakes (06)
- Provides targets for production families (editing/sound sync hooks)

---

## CANON TERMS

### TENSION
Ощущение “сейчас что-то решается”.
Не обязательно экшен — это может быть моральная дилемма.

### PRESSURE
Нагрузка на героя/систему, которая заставляет делать выбор.

### RELIEF (RELEASE)
Разрядка напряжения (победа, комедия, пауза, тишина).
Без релиза напряжение “перегорает”.

### PAYOFF TIMING
Когда эмоционально “возвращается” то, что было поставлено.

---

## DRAMATIC CURVE TYPES (TOOLBOX)

Выбираешь один основной тип:

- RISING: постоянный рост к финалу
- WAVE: волны (напряжение/релиз) с общим ростом
- DESCENT: падение в бездну (трагедия)
- ASCENT: подъём из тьмы (искупление)
- DOUBLE-PEAK: два пика (mid + finale)

Rule:
- тип должен быть заявлен в DAS.

---

## REQUIRED ARTIFACT: DRAMATIC ARC SPEC (DAS)

### DAS SCHEMA (CANON)

- DAS_ID:
- SCOPE:
  - episode | arc | season | book
- CURVE_TYPE:
  - rising | wave | descent | ascent | double-peak | custom
- BASELINE TONE:
  - calm | tense | bleak | hopeful | mixed
- PRIMARY EMOTION AXIS:
  - hope/fear | trust/betrayal | control/chaos | love/loss | etc

### ARC SEGMENTS (ORDERED)
For each segment (act/episode block):
- SEGMENT_ID:
- PURPOSE:
- TENSION_LEVEL (0–10):
- PRESSURE SOURCE:
  - external | internal | relational | existential
- STAKES LEVEL (0–10):
- RELIEF POINT:
  - none | micro | major
- EMOTIONAL SHIFT:
  - what changes emotionally

### PEAKS + RELEASES
- MIDPOINT PEAK (if any):
  - location + reason
- FINAL PEAK:
  - location + reason
- RELEASE WINDOWS:
  - where relief is allowed (and why)

### PAYOFF MAP (EMOTIONAL)
- setup -> emotional payoff target (segment)

### RISK FLAGS
- flat curve risk
- too many peaks risk
- no relief risk
- stakes jump without build risk

---

## ARC RULES (CANON)

### DA1 — Escalation must be earned
Если tension/stakes растут, должен быть “pressure cause”.
Иначе — искусственный накрут.

### DA2 — Relief is mandatory (unless declared tragedy lock)
Нужны точки разрядки.
Исключение: намеренная “давилка” (должно быть заявлено как lock).

### DA3 — Peak placement must align with structure
Пики дуги должны совпадать с major turns SSS.
Если пики живут отдельно — история ощущается “не там”.

### DA4 — Avoid plateau
Два сегмента подряд с одинаковым tension/stakes без изменения pressure → риск скуки.

### DA5 — Emotional payoff must exist
У истории должен быть хотя бы один осознанный эмоциональный payoff,
иначе дуга не закрывается.

---

## PROCEDURE (HOW TO RUN)

1) Read SSS and pick curve type
2) Choose primary emotion axis
3) For each segment:
   - tension level
   - pressure source
   - stakes level
   - relief policy
   - emotional shift
4) Place peaks (mid/final)
5) Map payoffs
6) Run checklist
7) Output DAS

---

## CHECKLIST (QC)

- is curve type declared?
- does tension change across segments?
- are pressure sources explicit?
- are there relief windows?
- do peaks align with major turns?
- is escalation earned (build -> peak)?
- are payoffs mapped?

---

## VALIDATION RULES

- DAV1: DAS includes segment list with tension/stakes values.
- DAV2: Peaks and releases are explicit.
- DAV3: Curve aligns with SSS turn map.
- DAV4: No unearned jumps without explanation.

---

OWNER: Universe Engine
LOCK: FIXED
