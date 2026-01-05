# ENG FAMILY README — SOUND_MUSIC_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: MUS
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.SOUND_MUSIC.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for SOUND_MUSIC family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **SOUND_MUSIC_ENGINES**.
Семейство отвечает за глубокую музыку как произведение:
- композиция
- структура песни/куска
- гармония/аккорды
- мелодия/хук
- ритм/грув (музыкальный)
- рифма/метр (для текста)
- лирика (как текст песни)
- аранжировка/инструментовка
- вокальная подача
- саунд-дизайн (музыкальный дизайн, не продакшн-плейсмент)
- консистентность стиля музыки
- музыка к сцене (scoring logic)
- микс/мастер (как финал аудио-трека)

### EXISTENCE RULE (MUSIC)
> Если проект использует музыку как смысловой слой — должен существовать Music Bible / Style Consistency + хотя бы один scoring pack.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: SOUND_MUSIC_ENGINES  
FAMILY_CODE: MUS  
FAMILY_CLASS: SOUND  
FAMILY_LEVEL: L3  

FAMILY_PATH: `10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/`  
README_FILE: `00__README__SOUND_MUSIC_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- создание музыки: композиция → аранж → исполнение → микс/мастер
- музыкальная драматургия (на уровне музыки)
- scoring: соответствие музыки сцене по смыслу и эмоции (но не монтаж клипа)

### 2.2 DOES NOT OWN (hard boundaries)
- production audio placement/sync/clarity в финальном видео → 08 Sound (Production Layer)
- монтаж/тайминг кадров/секунды видео → 08 Editing
- тон/атмосфера как общий закон проекта → 06 Style (музыка подчиняется как dependency)
- сюжет/акты/сцены → 02 Narrative (музыка получает сцены как вход)
- события/конфликт атомы → 05 Expression (музыка получает “что происходит” как вход)
- мир/эпохи/культура → 04 World (музыкальные коды могут зависеть)
- governance решения → 00 Governance

Boundary rule:
> 09 создает треки и музыкальные системы. 08 размещает и синхронизирует их в продукте.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — композиция/структура/гармония/мелодия/ритм
- BUILDER — аранж/вокал/саунд-дизайн
- VALIDATOR — стиль консистентность + музыка-к-сцене логика
- OUTPUT — финальные треки + stems + music packs + music bible

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Music Composition Engine | FOUNDATION | DEFINE |
| 02 | Song Structure Engine | FOUNDATION | DEFINE |
| 03 | Harmony / Chord Engine | FOUNDATION | DEFINE |
| 04 | Melody / Hook Engine | FOUNDATION | DEFINE |
| 05 | Rhythm / Groove Engine | FOUNDATION | DEFINE |
| 06 | Rhyme / Meter Engine | BUILDER | BUILD |
| 07 | Lyrics Engine | BUILDER | BUILD |
| 08 | Arrangement / Instrumentation Engine | BUILDER | BUILD |
| 09 | Vocal Performance Engine | BUILDER | BUILD |
| 10 | Sound Design Engine | BUILDER | BUILD |
| 11 | Music Style Consistency Engine | VALIDATOR | CHECK |
| 12 | Music To Scene Engine | VALIDATOR | CHECK |
| 13 | Mix / Master Engine | OUTPUT | PRODUCE |

---

## 4) MUSIC PACK STANDARD (MANDATORY)

Каждый music output pack обязан иметь:
- MUSIC_PACK_ID
- INPUT_CONSTRAINTS:
  - STYLE_CONSTRAINTS_PACK (06) — DEPENDS_ON
  - NARRATIVE_SCENE_CONTEXT (02) — CANON_REF
  - WORLD_CULTURE_CONTEXT (04) — DEPENDS_ON (если применимо)
- TRACK_SPEC:
  - mood targets, tempo range (можно), instrument palette, motifs
- DELIVERABLES:
  - master
  - stems (optional)
  - alt versions (loop, sting)
- RIGHTS/USAGE (если нужно)
- XREF pointers + provenance

Rule:
> Music pack обязан быть пригоден для передачи в 08 production (placement), но не содержит инструкций монтажа.

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `13_MUSIC/`
  - `01_IDEAS/`
  - `02_SPECS/`
  - `03_STEMS/`
  - `04_MASTERS/`

Recommended:
- L0: идеи/мотивы/референсы
- L1: черновые наброски и структуры
- L2: music bible canon + style consistency canon
- L3: masters/stems packs

---

## 6) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (masters)
- `REG.PRJ.<PROJECT_ID>.ASSETS` (audio assets)
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (music bible / style consistency)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ASSET_GRAPH.md`

Hard rule:
> Любой мастер-трек обязан иметь CANON_REF на scene context (если scoring) или на style bible (если общий трек).

---

## 8) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 8.1 INPUT TYPES
- STYLE_CONSTRAINTS_PACK (06)
- EMOTIONAL_TARGETS (06/02)
- SCENE_CONTEXT / ARC_CONTEXT (02)
- WORLD_CULTURE_CONTEXT (04)
- DELIVERY_SPEC (07/08) (optional)

### 8.2 OUTPUT TYPES
- MUSIC_BIBLE
- THEME_MOTIF_SET
- TRACK_SPEC
- SCORE_CUE_LIST
- MASTER_TRACK
- STEMS_SET
- ALT_VERSIONS (loop/sting)
- MIX_NOTES / MASTER_NOTES
- MUSIC_PACK

---

## 9) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__README__SOUND_MUSIC_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md`

---

## 10) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Music Composition Engine  
02 — Song Structure Engine  
03 — Harmony / Chord Engine  
04 — Melody / Hook Engine  
05 — Rhythm / Groove Engine  
06 — Rhyme / Meter Engine  
07 — Lyrics Engine  
08 — Arrangement / Instrumentation Engine  
09 — Vocal Performance Engine  
10 — Sound Design Engine  
11 — Music Style Consistency Engine  
12 — Music To Scene Engine  
13 — Mix / Master Engine  

---

## FINAL RULE (LOCK)

> 09 создает музыку как произведение.  
> 08 размещает/синхронизирует музыку в медиапродукте.  
> Связь — через music packs со ссылками на канон и стиль.

OWNER: Universe Engine  
LOCK: FIXED
