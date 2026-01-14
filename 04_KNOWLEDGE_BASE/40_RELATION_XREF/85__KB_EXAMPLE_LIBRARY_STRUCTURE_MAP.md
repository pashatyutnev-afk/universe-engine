# KB — EXAMPLE LIBRARY STRUCTURE MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/85__KB_EXAMPLE_LIBRARY_STRUCTURE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.EXAMPLE_LIBRARY_STRUCT.085
OWNER: SYSTEM
ROLE: Orientation map for structuring the KB example library by domain, skill tags, and gate linkage. This map does not provide navigation; it defines organizational axes to keep examples discoverable and curated.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created structural map for organizing example library by domain/tag/gate axes."
- REASON: "Examples must be discoverable; a structure map prevents chaotic dumping and improves curation workflows."
- IMPACT: "Cleaner example library, faster retrieval, better QA calibration."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MAP.085

---

## 0) PURPOSE (KB)
Define organizational axes for examples:
- by domain
- by skill tag clusters
- by linked gate/standard/pack

No URLs/RAW; navigation is via master index and folder conventions.

---

## 1) ORGANIZATION AXES (CANON)
AXIS A — Domain
- SOUND_MUSIC
- NARRATIVE
- CHARACTER
- WORLD
- VISUAL
- PRODUCTION
- MARKETING
- META

AXIS B — Skill tags
- Use canonical taxonomy.
- Prefer “cluster folders” for critical tag groups.

AXIS C — Gate linkage
- Examples must link to a gate/standard/pack UID.
- Grouping by gate UID improves QA calibration.

---

## 2) RECOMMENDED STRUCTURE (ORIENTATION)
Within each domain:
- 10_GOOD
- 20_BAD
- 30_BORDERLINE
Optional:
- 40_BY_GATE (subfolders keyed by gate UID or gate category label)
- 50_BY_TAG (subfolders keyed by tag cluster labels)

Alternative (if flat):
- encode label and tag cluster in filename tokens.

---

## 3) TAG CLUSTER RECOMMENDATIONS (HIGH SIGNAL)
### MUSIC clusters
- HOOK (music.hook.*)
- VOCALS (music.vocals.*)
- MIX_TRANSLATION (music.mix.translation_check, music.mix.mono_safety)
- UNIQUENESS (music.uniqueness.*)
- GENRE_FINGERPRINT (music.genre.*)

### NARRATIVE clusters
- SCENE (narrative.scene.*)
- TENSION (narrative.tension.*)
- CONTINUITY (narrative.continuity.*)
- DIALOGUE (narrative.dialogue.*)

### VISUAL clusters
- COMPOSITION (visual.composition.*)
- LIGHTING (visual.lighting.*)
- CONTINUITY (visual.continuity.*)

### META clusters
- TRACE (meta.kb.*trace*)
- UID_ONLY (meta.kb.uid_only_xref)
- NO_FANTASY (meta.kb.usage_no_fantasy)

---

## 4) CURATION FLOW (HOW STRUCTURE IS USED)
- When adding an example:
  - assign domain + label + tags + gate linkage
  - place according to domain/label
- When curating:
  - check duplicates inside label bucket
  - ensure each critical tag cluster has GOOD+BAD
  - ensure gate linkage exists

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- examples are stored without domain/label
- examples not linked to gates/standards
- structure map is used as navigation authority (URLs/RAW introduced)
- library fills with duplicates and uncurated dumps

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: library policy and curation principles
- XREF: UE.KB.RULE.EXAMPLE_GATE_LINK.084 | WHY: mandatory gate linkage for every example
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical skill tag taxonomy

--- END.
