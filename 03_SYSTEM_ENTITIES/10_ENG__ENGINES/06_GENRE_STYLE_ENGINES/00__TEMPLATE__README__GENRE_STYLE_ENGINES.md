# ENG FAMILY README — GENRE_STYLE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: STY
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.GENRE_STYLE.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for GENRE_STYLE family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **GENRE_STYLE_ENGINES**.
Семейство отвечает за “чтобы чувствовалось”:
- тон и настроение
- атмосфера
- эмоциональный резонанс
- символизм
- метафоры
- сенсорные детали (звук/запах/температура/текстуры/свет как ощущение)

### EXISTENCE RULE (STYLE)
> Любой проект обязан иметь style constraints pack (тон + атмосфера минимум).  
> Без style constraints outputs других слоёв становятся “безликими”.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: GENRE_STYLE_ENGINES  
FAMILY_CODE: STY  
FAMILY_CLASS: STYLE  
FAMILY_LEVEL: L3  

FAMILY_PATH: `10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/`  
README_FILE: `00__README__GENRE_STYLE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- Tone & mood: базовый эмоциональный режим
- Atmosphere: среда ощущений, “воздух”
- Emotional resonance: какие эмоции должны остаться в зрителе/читателе
- Symbolism: системы символов и их значения
- Metaphor: метафорические конструкции, повторяющиеся образы
- Sensory detail: сенсорные “палитры” (без продакшн микса)

### 2.2 DOES NOT OWN (hard boundaries)
- Сюжетная структура/арки/сцены → Narrative
- Атомы событий/конфликтов/кульминаций → Expression
- Психология/мотивация персонажей → Character
- Законы мира/эпохи/экономика → World
- Реальные продакшн параметры: цвета LUT, fps, монтажный тайминг, уровни звука → Knowledge Production (08)
- Глубокая музыка (композиция/гармония/аранж) → Sound Music (09)
- Governance/канон решения → Governance

Boundary rule:
> Style задаёт constraints и словарь ощущений, но не производит монтаж/тех параметры и не строит сюжет.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — tone/mood + atmosphere (ядро)
- BUILDER — resonance, symbolism, metaphor, sensory palettes
- VALIDATOR — consistency across outputs (не “прыгает стиль”)
- BRIDGE — перевод style constraints в usable packs для narrative/character/production
- OUTPUT — style bible / style constraints pack

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Tone & Mood Engine | FOUNDATION | DEFINE |
| 02 | Atmosphere Engine | FOUNDATION | DEFINE |
| 03 | Emotional Resonance Engine | BUILDER | BUILD |
| 04 | Symbolism Engine | BUILDER | BUILD |
| 05 | Metaphor Engine | BUILDER | BUILD |
| 06 | Sensory Detail Engine | BRIDGE | PACKAGE |

---

## 4) STYLE CONSTRAINTS STANDARD (MANDATORY)

Каждый style pack обязан иметь:
- STYLE_ID
- TONE_RANGE (allowed / forbidden)
- ATMOSPHERE_NOTES
- EMOTIONAL_TARGETS (what viewer should feel)
- SYMBOL_SET (symbols + meaning)
- METAPHOR_SET (repeating metaphors)
- SENSORY_PALETTES (touch/smell/temp/sound-as-feel/light-as-feel)
- VOICE_GUIDE (language register constraints) — но без конкретных реплик (это Character)
- PRODUCTION_HINTS (high-level) — без чисел и тех параметров

Rule:
> Любой стиль “только красивыми словами” без allowed/forbidden и без палитр — incomplete.

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `10_STYLE/` (project style)
- `05_PROJECT__L3/` (style packs for production)

Recommended:
- L0: moodboards текстом, ощущения, ассоциации
- L1: черновые палитры и списки символов
- L2: style bible canon (единый закон ощущений)
- L3: constraints pack для потребителей (narrative/character/production)

File examples:
- L2: `03_CANON_L2/00__STYLE_BIBLE_CANON.md`
- L3: `04_OUTPUT_L3/00__STYLE_CONSTRAINTS_PACK.md`

---

## 6) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (style bible canon)
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (constraints packs)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`

Hard rule:
> Любой output narrative/character/production должен иметь DEPENDS_ON на STYLE_CONSTRAINTS_PACK.

---

## 8) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 8.1 INPUT TYPES
- WORLD_CONTEXT (what world feels like)
- NARRATIVE_REQUIREMENTS (desired emotional path)
- CHARACTER_VOICE_REQUIREMENTS (register constraints)
- PRODUCTION_NEEDS (art direction needs) — high-level

### 8.2 OUTPUT TYPES
- TONE_RANGE
- ATMOSPHERE_PROFILE
- EMOTIONAL_PATH (targets)
- SYMBOL_SET
- METAPHOR_SET
- SENSORY_PALETTES
- STYLE_BIBLE (canon)
- STYLE_CONSTRAINTS_PACK (for consumers)

---

## 9) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__README__GENRE_STYLE_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md`

---

## 10) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Tone & Mood Engine  
02 — Atmosphere Engine  
03 — Emotional Resonance Engine  
04 — Symbolism Engine  
05 — Metaphor Engine  
06 — Sensory Detail Engine  

---

## 11) GOVERNANCE COMPATIBILITY (MANDATORY)

Изменение tone range / символов / метафор:
- фиксируется как change (WHY)
- обновляет constraints packs
- требует перессылки dependents через XREF__DEPENDENCIES (чтобы было понятно, что надо пересобрать)

---

## FINAL RULE (LOCK)

> Style family задаёт закон ощущений.  
> Он обязателен как dependency для Narrative/Character/Production outputs.

OWNER: Universe Engine  
LOCK: FIXED
