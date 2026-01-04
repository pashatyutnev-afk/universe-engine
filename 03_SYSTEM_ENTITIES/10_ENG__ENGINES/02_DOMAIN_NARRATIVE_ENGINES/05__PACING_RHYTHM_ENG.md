# Pacing & Rhythm Engine
FILE: 05__PACING_RHYTHM_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Controls narrative pacing and rhythm; defines how scene/beat lengths, density, and release windows are distributed across scope to keep engagement and clarity; produces reproducible pacing maps

---

## PURPOSE

Pacing & Rhythm — это “дыхание истории”:
- как быстро меняется состояние
- насколько плотные сцены
- где ускоряем, где даём паузу
- как чередуются типы сцен

Без этого:
- история кажется затянутой или рваной
- кульминации “не поднимаются”
- зритель устаёт или скучает

---

## NON-GOALS

- не определяет структуру актов (Story Structure)
- не определяет драматическую кривую (Dramatic Arc)
- не делает монтаж (Editing engine)
Он переводит структуру/дугу в **план темпа** на уровне сцен и битов.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Story Structure Spec (SSS)
- Dramatic Arc Spec (DAS)
- Scene Specs (SS) or scene list draft
- Platform constraints (optional):
  - episode duration, page count, game segment length

### PRODUCES
- PACING MAP (PM) — canonical artifact
- SCENE DENSITY plan
- RHYTHM PATTERN rules (alternation)
- RELEASE WINDOW plan (micro/major rests)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/03__DRAMATIC_ARC_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md

### OUTPUT_TARGET
- Feeds Tension & Stakes (06) and Continuity (09)
- Provides targets to production editing/sound engines

---

## CANON TERMS

### PACING
Скорость прогрессии: сколько “изменений состояния” за единицу времени.

### RHYTHM
Паттерн чередования:
- action vs quiet
- dialogue vs movement
- reveal vs obstacle
- pressure vs relief

### DENSITY
Плотность событий:
- low: 1–2 значимых изменения на сцену
- medium: 2–3
- high: 3–5 (опасно, может ломать ясность)

### BREATH
Осознанные паузы, где зритель “успевает догнать”.

---

## PACING MODES (TOOLBOX)

Choose 1 dominant:
- SLOW-BUILD: медленное накопление давления
- BALANCED WAVE: волны плотности с ростом к финалу
- FAST-CHAIN: быстрые сцены, много событий
- PUZZLE-REVEAL: темп держится раскрытиями (осторожно)
- SURVIVAL-DRIVE: темп держится угрозой/таймером

Rule:
- pacing mode must be declared in PM.

---

## REQUIRED ARTIFACT: PACING MAP (PM)

### PM SCHEMA (CANON)

- PM_ID:
- SCOPE:
  - episode | arc | season | book
- PACING MODE:
- PLATFORM TARGET:
  - minutes/pages/segments (optional)
- GLOBAL RULES:
  - max consecutive high-density scenes:
  - required breath frequency:
  - reveal spacing rule:

### SCENE GRID (ORDERED)
For each scene (or planned slot):
- SCENE_ID (or SLOT_ID):
- SCENE TYPE:
  - setup | action | dialogue | reveal | travel | aftermath | decision | chase | interlude
- INTENSITY (0–10):
- DENSITY (low/med/high):
- BEAT COUNT TARGET:
  - range (e.g., 5–8)
- LENGTH TARGET:
  - short | medium | long (or time/pages if known)
- RELIEF:
  - none | micro | major
- PURPOSE:
  - what it accomplishes structurally
- NOTES:
  - optional flags

### RHYTHM PATTERN
- alternation rule:
  - e.g., “high -> low -> medium -> high”
- no-repeat constraint:
  - e.g., “no 3 dialogue scenes in a row”
- reveal placement rule:
  - e.g., “every 2–3 scenes a reveal or turn”

### RISK FLAGS
- plateau risk segments
- overload risk segments
- too-much-breath risk (stall)
- reveal spam risk (puzzle fatigue)

---

## PACING RULES (CANON)

### PR1 — No uncontrolled plateaus
3 сцены подряд с одинаковой интенсивностью без сдвига ставки/инфо → риск стагнации.

### PR2 — High density must be buffered
После high-density сцены обязателен:
- micro relief, или
- low-density сцена
Иначе зритель “перегревается”.

### PR3 — Repetition kills rhythm
Одинаковый тип сцены 3 раза подряд запрещён, если не заявлено intentional (и это редкость).

### PR4 — Reveals need spacing
Слишком частые reveals ломают вес каждого reveal.
Правило по умолчанию:
- 1 крупный reveal на 2–4 сцены (scope episode)
(можно менять, но должно быть declared)

### PR5 — Beat count aligns with pacing
Если сцене назначен long length, она обязана иметь:
- либо больше beats,
- либо более глубокий change (иначе “вода”).

### PR6 — Climax acceleration
Перед кульминацией темп чаще ускоряется:
- короче сцены
- выше плотность
Но ясность не должна падать.

---

## PROCEDURE (HOW TO RUN)

1) Read SSS + DAS and list scenes/slots
2) Choose pacing mode
3) Assign each scene:
   - type, intensity, density, beat count, length
4) Define rhythm pattern (alternation rules)
5) Place relief windows
6) Check reveal spacing
7) Flag risks and revise grid
8) Output PM

---

## QC CHECKLIST (MANDATORY)

- is pacing mode declared?
- does intensity vary across scenes?
- any 3 same-type scenes in a row?
- are high-density scenes buffered?
- are relief windows present?
- reveal spacing respected?
- beat count targets plausible vs length?
- does pacing support DAS peaks?

---

## VALIDATION RULES

- PV1: PM contains scene grid with intensity/density targets.
- PV2: Rhythm rules exist (alternation + no-repeat constraint).
- PV3: Relief windows exist and align with arc.
- PV4: No obvious plateau/overload risks left unaddressed.

---

OWNER: Universe Engine
LOCK: FIXED
