# ENG FAMILY README — SOUND_MUSIC_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for Sound/Music realm README. Compatible with base family template v2 and base engine template v2. Defines deep music creation pipeline and strict boundary vs Production Sound.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **SOUND_MUSIC_ENGINES** отвечает за музыку как произведение:
- композиция (музыкальная идея)
- структура трека/песни
- гармония/аккорды
- мелодия/хук
- ритм/грув
- рифма/размер (для текста)
- лирика
- аранжировка/инструментовка
- вокал/исполнение
- саунд-дизайн (как часть музыки)
- консистентность музыкального стиля
- музыка к сцене (драматургическая функция)
- микс/мастер (как музыкальный финал)

EXISTENCE RULE:
> Музыкальный артефакт валиден, когда есть: theme/hook + structure + arrangement + mix/master + provenance.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: SOUND_MUSIC_ENGINES
FAMILY_CODE: MUS
FAMILY_CLASS: SOUND
FAMILY_LEVEL: L3

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/`

README_FILE:
`00__README__SOUND_MUSIC_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- создание музыки и музыкальных компонентов
- музыкальный саунд-дизайн как часть трека
- музыкальный микс/мастер (как финал трека)

### 2.2 DOES NOT OWN (hard boundaries)
- production sound (sync/design/placement/clarity для видео) → 08 Production Sound
- монтаж звука под кадры как техпроцесс → 08 Production
Rule:
> MUS создаёт музыку. PRD размещает/синхронит музыку в видео.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: composition/structure/harmony/melody/rhythm
- BUILDER: lyrics/arrangement/vocal/sound design/style consistency
- OUTPUT: music-to-scene + mix/master

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
| 11 | Music Style Consistency Engine | BUILDER | CHECK |
| 12 | Music To Scene Engine | OUTPUT | PRODUCE |
| 13 | Mix / Master Engine | OUTPUT | PRODUCE |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default root:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Music workspace:
- `03_AUDIO/MUS_<TRACK_NAME>/<LEVEL_FOLDER>/`

Final exports:
- `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/<FORMAT>/AUDIO/`
or if you store music library:
- `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/MUSIC_LIBRARY/`

Rule:
> Music artifacts must be traceable via provenance and linked to scene refs if “music to scene”.

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (final exports)
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.RUNS.md` (recommended: music runs)

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Music-specific (recommended):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__MUSIC_CUES.md` (music-to-scene)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__THEME_LIBRARY.md`

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__README__SOUND_MUSIC_ENGINES.md

---

## 8) CANON ORDER (MANDATORY)

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

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Governance required when:
- changing musical theme library used across episodes
- swapping style consistency rules mid-project
- re-authoring cues already synced in production outputs

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__README__SOUND_MUSIC_ENGINES.md

---

## FINAL RULE (LOCK)

> MUS creates music. PRD places it in media.

LOCK: FIXED
