# ENG ENGINE TEMPLATE — SOUND_MUSIC_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Music family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds track/cue schemas, music-to-scene contract, theme library, and run/provenance requirements.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.MUS.<NN>.<ENGINE_NAME>

FAMILY_CODE: MUS
ENGINE_NN_IN_FAMILY: <01..13>
ENGINE_CLASS: SOUND
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- which musical component it defines (composition/harmony/melody/etc)
- what artifacts it outputs (themes, stems, cue sheets, masters)
- how Production Sound consumes outputs (placement/sync only)

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

OWNS:
- music creation decisions (notes/rhythm/arrangement/lyrics)
- musical mix/master of the track

DOES NOT OWN:
- sync/placement in video timeline
- dialogue cleanup or production audio tasks (PRD)

Rule:
> If it's about timecode placement in edit — belongs to PRD.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- need new theme/cue for scene/arc
- style consistency drift
- arrangement required for emotional intent
- final mastering required for release deliverables

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- FORMAT_SPEC (optional, for output targets)
- STYLE_LAW_PACK (optional but common)
- NARRATIVE_CONTEXT (optional)
- MUSIC_THEME_LIBRARY (if exists)
- existing tracks/stems (if iterating)

PRODUCES:
- TRACK_BLUEPRINT (composition/structure)
- THEMES_MOTIFS
- STEMS
- CUES (music-to-scene mappings)
- FINAL_MASTERS
- PROVENANCE_RECORDS

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET:
- track workspace:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/03_AUDIO/MUS_<TRACK_NAME>/<LEVEL_FOLDER>/`
- exports:
  `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/<FORMAT>/AUDIO/`
  or `.../MUSIC_LIBRARY/`

Rule:
> Every exported master must have provenance and version tag.

---

## 5) MUSIC SCHEMAS (MANDATORY)

### 5.1 THEME_ENTRY (library)

THEME_ID: <THM_<NAME>>
MOOD: <...>
TEMPO_RANGE: <...>
KEY_CENTER: <optional>
MOTIF_DESC: <one line>
ASSOCIATED_WITH:
- characters: [CHR_*]
- factions: [FAC_*]
- concepts: [CPT_*]
CANON_REFS: [ ... ]

---

### 5.2 TRACK_BLUEPRINT

TRK_ID: <MUS_TRK_<NAME>>
STYLE_TAGS: [ ... ]
INSTRUMENTS: [ ... ]
TEMPO: <bpm or range>
METER: <...>
HARMONY_PLAN: <...>
MELODY_PLAN: <...>
STRUCTURE:
- intro
- verse
- chorus
- bridge
- outro
STEMS_REQUIRED: [DRUMS|BASS|PAD|LEAD|VOCALS|FX|...]

---

### 5.3 CUE_SHEET (music to scene)

CUE_ID: <CUE_<NAME>>
SCENE_OR_EVENT_REFS: [SCN_*|EVT_*|ARC_*]
FUNCTION: <tension|wonder|loss|victory|mystery|...>
THEME_REFS: [THM_*]
DURATION_INTENT: <short|medium|long> (no timecodes here)
TRANSITIONS: <fade|hard_cut|rise|...> (intent only)
NOTES: ...

Rule:
> Timecode placement belongs to PRD editing/sound; MUS provides cue intent.

---

### 5.4 MIX_MASTER_RECORD

MM_ID: <MM_<NAME>>
TARGETS_INTENT:
- loudness: <intent target, not technical spec>
- dynamics: <...>
- clarity: <...>
EXPORTS:
- master_files: [ ...paths... ]
- stems: [ ...paths... ]
VERSION: <...>
PROVENANCE_REF: <...>

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC): []
CONTROLLED_BY (CTL): []

VALIDATED_BY (VAL):
- <VAL.MUS.01.STYLE_COHERENCE> (placeholder) or []
- <VAL.MUS.02.CUE_FUNCTION> (placeholder) or []

QA_BY (QA):
- <QA.MUS.01.AUDIO_QUALITY> (placeholder) or []
- <QA.MUS.02.CONSISTENCY> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES for exported deliverables
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.RUNS.md` (recommended)

XREF_UPDATES:
- REQUIRED: YES
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__MUSIC_CUES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__THEME_LIBRARY.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

---

## 7) PROCESS (HOW TO EXECUTE)

1) Read style intent + narrative function (if any).
2) Select/extend theme library entry.
3) Draft blueprint (structure/harmony/melody/rhythm).
4) Arrange + produce stems.
5) Create cue sheet (intent mapping to scenes).
6) Mix/master and export.
7) Update registries + xref + provenance.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- cue function is explicit
- theme library links to entities
- exports have stems + masters + provenance
- no timecode placement inside MUS docs

FAIL if:
- music described only as “vibe”
- no theme/cue mapping
- missing provenance/version

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md

---

## FINAL RULE (LOCK)

> MUS defines musical content and cue intent. PRD handles timeline placement.

LOCK: FIXED
