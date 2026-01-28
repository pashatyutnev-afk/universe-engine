# KB — KB_SCOPE.TOPICS.SOUND_MUSIC: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/15__KB_SCOPE_SOUND_MUSIC_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.SOUND_MUSIC.015
OWNER: SYSTEM
ROLE: Define the boundaries and required content types for Sound/Music topics: composition, arrangement, vocal direction, mix/master translation, hook engineering, anti-repeat/collision, UGC moments, and catalog consistency.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.TOPICS.SOUND_MUSIC boundaries: hook/structure/vocals/mix/UGC/anti-collision."
- REASON: "Music quality requires specialist knowledge modules; boundaries keep music craft operational and prevent mixing with governance or navigation."
- IMPACT: "Sound/Music specialists can generate higher quality tracks consistently with deterministic procedures and QA gates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.015

---

## 0) PURPOSE (KB)
Sound/Music topics define how to craft audio outcomes:
- songwriting and structure
- genre/style fingerprints
- vocal performance direction
- mix/master translation checks
- repeat/collision prevention
- UGC moment engineering and short variants
- catalog consistency

They turn entities into competent music specialists.

---

## 1) ABSOLUTE BOUNDARIES
Sound/Music topics must NOT:
- redefine production pipelines (belongs to Production topics)
- redefine marketing packaging/distribution (belongs to Marketing topics)
- redefine KB governance or navigation (Meta/Governance)
- embed RAW links or act as an index

Sound/Music topics MAY:
- reference production topics (release pack) by UID-only as complementary
- reference marketing topics when a music artifact needs packaging (still keep craft separate)

---

## 2) ALLOWED SOUND_MUSIC TOPIC TYPES
Allowed:
- SONG STRUCTURE BLUEPRINTS (timing, section maps)
- HOOK ENGINEERING (hook windows, patterns, QA)
- LYRICS / RHYME / METER TOOLKITS (stress-safe writing)
- VOCAL DIRECTION (A/B roles, articulation, energy arc)
- ARRANGEMENT / INSTRUMENTATION (must-haves, contrast points)
- GENRE FUSION FINGERPRINTS (markers, proportions, drift guards)
- MIX TRANSLATION QA (phone/earbuds/mono checks)
- ANTI-REPEAT / ANTI-COLLISION (catalog memory, repetition guards)
- UGC MOMENTS & SHORTS VARIANTS (15/30/60, loop-safe)
- ITERATION LOG / PHRASEBOOK (deltas, negative library)

---

## 3) FORBIDDEN SOUND_MUSIC CONTENT
Forbidden:
- “how to run a release window” (marketing)
- “release pack governance” (production)
- “how to use KB” (meta)
- “master index rules” (navigation)
- long essays without procedures/templates

---

## 4) REQUIRED STRUCTURE (MINIMUM)
Each Sound/Music topic should include:
- Purpose
- When to use / when not
- Definitions (strict)
- Inputs/Outputs
- Procedure (step-by-step)
- Templates/Cards (copy)
- QA gates (PASS/REWORK/FAIL)
- Related (UID-only if required)
- Compliance (no-fantasy + trace as applicable)

---

## 5) CORE QUALITY AXES (MUSIC)
Sound/Music topics should cover at least one axis explicitly:
- Timing & hook placement
- Vocal clarity & contrast (A/B)
- Mix translation & mono safety
- Uniqueness (anti-collision)
- UGC clip-ability (moments)
- Style identity (fingerprint)

---

## 6) HOW ENTITIES USE SOUND_MUSIC TOPICS
- SPC music roles: open 1–3 core topics (hook + vocals + structure) + optional mix QA.
- ENG music engines: implement a method; must align with fingerprint and repeat guards.
- VAL/QA: validate using mix translation, hook timing, repeat/collision checks.
- ORC: may include sound/music topics as steps inside a production pipeline (but orchestration rules live in production).

---

## 7) EXAMPLES
GOOD:
- "Vocal Performance Direction" (role contracts + QA)
- "UGC Moments Map" (moment types + loop rules + tests)
- "Genre Fusion Fingerprints" (markers + drift guard)

BAD:
- "How to publish on YouTube" (marketing)
- "KB master index map" (meta)
- "Everything about music" (non-atomic)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.TOPICS.011 | WHY: sound/music is a domain topics scope
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: no-fantasy and trace rule apply
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossrefs
- XREF: UE.KB.STD.SCOPE.PRODUCTION.014 | WHY: production complements music when shipping artifacts

--- END.
