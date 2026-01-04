# Tone & Mood Engine
FILE: 01__TONE_MOOD_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines and locks the emotional tone and mood palette of a project/world/arc; produces Tone Bibles, Mood Curves, Do/Don't lists, and Consistency Gates that align narrative, visuals, audio, pacing, and performance into a stable “feel” that remains recognizable across outputs

---

## PURPOSE

TONE/MOOD — это “как ощущается вселенная”.
Один и тот же сюжет можно сделать:
- тревожным
- героическим
- саркастичным
- хоррорным
- сакральным

Движок нужен, чтобы:
- зафиксировать “нерв” и атмосферу
- не допустить дрейф стиля между сценами/эпизодами/артами
- связать тон с монтажом/камера/звук/диалоги
- дать измеримые правила консистентности

---

## NON-GOALS

- не заменяет “Atmosphere Engine” (мир и среда как ощущаются через детали)
- не заменяет “Emotional Resonance” (почему это пробивает)
- не заменяет “Art Style” (визуальный рендер)
Он задаёт **эмоциональную оболочку** и её lock.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Genre target(s) and format constraints
- Theme/Meaning targets
- Conflict & stakes map
- Audience intent (fear/comfort/awe/etc)
- Existing style locks (if any)

### PRODUCES
- TONE BIBLE (TB) — canonical artifact
- MOOD CURVE (MC) — per arc/episode curve
- DO/DON'T LIST (DDL)
- CONSISTENCY GATES (TG)
- CROSS-DEPT TRANSLATION (CDT) — mapping to visual/audio/editing/performance

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG.md (alignment)
- 02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md
- 05_EXPRESSION_ENGINES/05__CLIMAX_ENG.md (tone handling at peaks)
- 08_KNOWLEDGE_PRODUCTION_ENGINES family (translation)

### OUTPUT_TARGET
- Feeds:
  - dialogue choices
  - pacing/edit rhythm
  - sound palette
  - camera/lighting choices
  - prompt packs and style bibles

---

## CANON TERMS

### TONE
Авторская позиция и “температура речи”:
- серьёзно/иронично/мрачно/надеждно

### MOOD
Эмоциональная погода в кадре/сцене:
- тревога, эйфория, холод, благоговение

### TONE LOCK
Набор признаков, которые нельзя нарушать без разрешения.

### MOOD CURVE
График настроения во времени:
- подъемы/падения/паузы

---

## TONE/MOOD RULES (CANON)

### TM1 — Tone is a contract with the audience
Тон задаёт ожидания.
Если ты их ломаешь — ты должен это делать осознанно (и помечать).

### TM2 — Mood is scene-local, tone is world-global
- tone — глобальный фон
- mood — локальные состояния сцен
Но они должны быть совместимы.

### TM3 — Peaks follow the tone
Кульминации могут быть ярче, но не “из другой вселенной”.

### TM4 — No unlogged drift
Если тон меняется между эпизодами:
- это фиксируется как intentional shift
- и объясняется сюжетно

### TM5 — Translation to departments is mandatory
Тон должен уметь “переводиться” в:
- диалоги
- визуал
- звук
- монтаж
Иначе он не контролируется.

---

## REQUIRED ARTIFACT A: TONE BIBLE (TB)

### TB SCHEMA (CANON)

Header:
- TB_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - world | project | arc | season
- VERSION:
- STATUS:
  - draft | canon | deprecated

Core:
- PRIMARY TONE (1):
- SECONDARY TONES (0–2):
- TONE TEMPERATURE:
  - cold | neutral | warm
- SERIOUSNESS LEVEL (0–10):
- HUMOR POLICY:
  - none | dry | black | occasional | frequent
- HOPE vs DREAD BALANCE (0–10):
- VIOLENCE FEEL:
  - clean | brutal | implied
- MORAL FEEL:
  - clear | gray | nihilistic | sacred
- SPEED FEEL:
  - calm | tense | frantic

Language:
- DICTION:
  - simple | poetic | technical | ritual
- META/IRONY ALLOWED:
- SWEAR POLICY (if any):
- DIALOGUE ENERGY:
  - low | mid | high

Audience promise:
- WHAT AUDIENCE SHOULD FEEL MOST OFTEN:
- WHAT MUST NEVER DOMINATE:
- SAFE SURPRISE ZONES:
  - where tone can flex

Locks:
- NON-NEGOTIABLE TRAITS (3–7):
- ALLOWED VARIATIONS:
- FORBIDDEN DRIFTS:

---

## REQUIRED ARTIFACT B: MOOD CURVE (MC)

### MC SCHEMA (CANON)

- MC_ID:
- TB_ID:
- SCOPE:
  - episode | arc | season

Curve points (ordered):
For each segment:
- SEGMENT ID:
- MOOD STATE:
  - dread | awe | relief | wonder | anger | grief | etc
- INTENSITY (0–10):
- DURATION:
- TRIGGER:
  - what causes this mood shift
- REQUIRED “BREATH” (pause) AFTER? (yes/no)

Rule:
- No constant high intensity. Curves need breath.

---

## REQUIRED ARTIFACT C: DO/DON'T LIST (DDL)

### DDL SCHEMA (CANON)

- DDL_ID:
- TB_ID:

DO (examples):
- what we do to keep tone
- what kind of metaphors, rhythms, silence

DON’T (examples):
- forbidden jokes
- forbidden camera feel
- forbidden music tropes
- forbidden lighting aesthetics

Rule:
- Must include at least 5 DO and 5 DON’T.

---

## REQUIRED ARTIFACT D: CONSISTENCY GATES (TG)

### TG SCHEMA (CANON)

- TG_ID:
- TB_ID:

Gates:
1) Dialogue check:
   - diction and humor policy match TB
2) Visual check:
   - contrast/lighting aligns with tone temperature
3) Audio check:
   - sound palette supports mood, not fights it
4) Editing check:
   - rhythm mode fits seriousness and speed feel
5) Performance check:
   - acting energy aligns with world tone
6) Drift detection:
   - if drift exists, mark intentional and justify

Rule:
- Any artifact that fails 2+ gates is non-canon until fixed.

---

## REQUIRED ARTIFACT E: CROSS-DEPT TRANSLATION (CDT)

### CDT SCHEMA (CANON)

- CDT_ID:
- TB_ID:

Mapping:
- TO CAMERA:
  - lenses, movement feel (handheld vs stable), distance
- TO LIGHTING:
  - soft/hard, warmth, shadow policy
- TO ART STYLE:
  - texture/grain/noise, shape language
- TO SOUND:
  - ambience density, silence policy, music role
- TO EDITING:
  - avg shot length, cut aggressiveness
- TO PERFORMANCE:
  - gesture scale, speech tempo, micro/macro emotion

Rule:
- At least 1 concrete directive per department.

---

## INTENTIONAL TONE SHIFT POLICY

Allowed shifts:
- “descent into horror”
- “false safety”
- “victory high then crash”
- “sacred revelation”

Requirements:
- must be logged as SHIFT EVENT
- must have a return or a new baseline
- must update TB/MC if permanent

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- jokes appear in sacred/tragic sequences without policy
- visuals become glossy/cute in a grim world
- music becomes heroic when tone is nihilistic
- pacing becomes frantic with a “calm dread” tone
- characters speak in a different diction (modern slang vs ritual)

Fix options:
- tighten DDL don’ts
- update CDT mappings (camera/music/edit)
- mark and justify intentional shift
- adjust mood curve breath points
- align dialogue energy and vocabulary rules

---

## PROCEDURE (HOW TO RUN)

1) Choose genre target and theme/meaning backbone
2) Draft TB with primary tone and locks
3) Build MC for scope (episode/arc/season)
4) Write DDL (do/don’t)
5) Translate to departments via CDT
6) Run gates (TG) on sample scenes/art/audio
7) Canonize TB/MC and enforce drift logging

---

## QC CHECKLIST (MANDATORY)

- TB has primary tone + non-negotiable traits?
- MC has breath and intensity variation?
- DDL exists and forbids key drifts?
- CDT maps to camera/lighting/sound/editing/performance?
- TG gates defined and measurable?
- intentional shift policy exists?

---

## VALIDATION RULES

- TMV1: Tone is locked and translated across departments.
- TMV2: Mood curve is controlled, with breath and justified shifts.
- TMV3: Drift is detected, logged, and corrected.
- TMV4: Outputs remain recognizably “same universe”.

---

OWNER: Universe Engine
LOCK: FIXED
