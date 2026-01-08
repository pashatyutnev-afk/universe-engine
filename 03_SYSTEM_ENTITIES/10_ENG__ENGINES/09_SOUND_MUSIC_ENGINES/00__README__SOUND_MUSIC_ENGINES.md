# 09_SOUND_MUSIC_ENGINES — REALM README (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: SOUND (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.FAM.09.README.001
OWNER: SYSTEM
ROLE: Realm definition for Deep Sound & Music engines: ownership boundaries, canonical order, execution pipelines, and template contracts. Owns deep composition/harmony/melody/arrangement/vocal/sound design/mix-master.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Family README created: defines deep sound/music boundaries and canon order; production audio explicitly excluded."
- REASON: "Stamping requires strict separation: production placement vs deep music craft."
- IMPACT: "Music identity and sound design become reusable, auditable, and consistent across scenes."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.MUSIC.README.001

---

## 0) PURPOSE (LAW)
This FAMILY owns **DEEP MUSIC + DEEP SOUND DESIGN**:
- music identity (themes/motifs), cue taxonomy, tonal direction
- song/cue structure (sections/forms)
- harmony/chords system
- melody/hook generation rules
- rhythm/groove (musical rhythm)
- rhyme/meter (lyric structure)
- lyrics drafting (constrained)
- arrangement/instrumentation (orchestration)
- vocal performance specification
- deep sound design language (sonic motifs/palettes)
- style consistency enforcement for music assets
- mapping music to scene intent (abstract hitpoints)
- mix/master finishing policies and QC

Hard rule:
- This family creates **deep audio assets & specs**. It does NOT own production placement/sync/clarity (that is 08 production sound).

---

## 1) BOUNDARIES (STRICT)
IN SCOPE:
- composing and defining music/sound identities and their rulesets
- creating musical structures and harmonic/melodic/rhythmic systems
- generating constrained lyrics and vocal performance specs
- defining sonic motif libraries and transformation constraints
- enforcing music style consistency across assets
- producing mix/master target policies, stems, QC gates

OUT OF SCOPE:
- placing audio on the edit timeline, sync to EDL, dialogue clarity guardrails (08 production sound)
- video editing/montage decisions (08 editing engine)
- story canon creation (domain narrative/character/world engines)
- tone/mood/atmosphere ownership (06 family owns primitives; 09 can consume them)

CRITICAL BOUNDARY (from your law):
- Production audio (sync/design/placement/clarity) → `08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md`
- Deep music (composition/harmony/arrangement/vocal/mix-master) → this family (09)

---

## 2) CANON ORDER (MANDATORY)
Engines in this family are canonical in this order:

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

Rule:
- 11 (consistency) can run after any subset of 01–10 outputs exist, but canon order remains for navigation.

---

## 3) TEMPLATES (MANDATORY)
ENGINE TEMPLATE:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md

README TEMPLATE:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__README__SOUND_MUSIC_ENGINES.md

---

## 4) CANON MAP (RAW-ONLY NAV)
01 — Music Composition Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG.md

02 — Song Structure Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG.md

03 — Harmony / Chord Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/03__HARMONY_CHORD_ENG.md

04 — Melody / Hook Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/04__MELODY_HOOK_ENG.md

05 — Rhythm / Groove Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/05__RHYTHM_GROOVE_ENG.md

06 — Rhyme / Meter Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/06__RHYME_METER_ENG.md

07 — Lyrics Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/07__LYRICS_ENG.md

08 — Arrangement / Instrumentation Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/08__ARRANGEMENT_INSTRUMENTATION_ENG.md

09 — Vocal Performance Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/09__VOCAL_PERFORMANCE_ENG.md

10 — Sound Design Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/10__SOUND_DESIGN_ENG.md

11 — Music Style Consistency Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/11__MUSIC_STYLE_CONSISTENCY_ENG.md

12 — Music To Scene Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/12__MUSIC_TO_SCENE_ENG.md

13 — Mix / Master Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/13__MIX_MASTER_ENG.md

---

## 5) OUTPUT TARGETS (DEFAULT)
Default storage (recommended):
- PROJECT_ARTIFACTS/<project>/MUSIC/COMPOSITION/
- PROJECT_ARTIFACTS/<project>/MUSIC/STRUCTURE/
- PROJECT_ARTIFACTS/<project>/MUSIC/HARMONY/
- PROJECT_ARTIFACTS/<project>/MUSIC/MELODY/
- PROJECT_ARTIFACTS/<project>/MUSIC/RHYTHM/
- PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS_STRUCTURE/
- PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS/
- PROJECT_ARTIFACTS/<project>/MUSIC/ARRANGEMENT/
- PROJECT_ARTIFACTS/<project>/MUSIC/VOCALS/
- PROJECT_ARTIFACTS/<project>/SOUND_DESIGN/
- PROJECT_ARTIFACTS/<project>/MUSIC/CONSISTENCY/
- PROJECT_ARTIFACTS/<project>/MUSIC/TO_SCENE/
- PROJECT_ARTIFACTS/<project>/MUSIC/MIX_MASTER/

---

## 6) USAGE PIPELINES (DETERMINISTIC)

### A) Full Track / Song pipeline
1) Composition (01)
2) Structure (02)
3) Harmony (03)
4) Melody (04)
5) Rhythm (05)
6) Rhyme/Meter (06) + Lyrics (07) (if vocal)
7) Arrangement (08)
8) Vocal Performance (09) (if vocal)
9) Sound Design (10) (optional)
10) Consistency (11)
11) Music→Scene mapping (12) (if audiovisual)
12) Mix/Master (13)

### B) Underscore / Cue pipeline
1) Composition (01) → Structure (02) → Harmony (03) → Rhythm (05)
2) Arrangement (08) + optional Sound Design (10)
3) Consistency (11)
4) Music→Scene (12) (optional)
5) Mix/Master (13)

Validation:
- Each engine emits gates. Any S0 fail = STOP.

---

## 7) HARD BOUNDARY NOTES (CRITICAL)
- No placement/timecodes here. That is production audio layer.
- No “edit rhythm” ownership here. That is production editing.
- Lyrics must respect rhyme/meter constraints or be flagged FAIL.

--- END.

LOCK: FIXED
