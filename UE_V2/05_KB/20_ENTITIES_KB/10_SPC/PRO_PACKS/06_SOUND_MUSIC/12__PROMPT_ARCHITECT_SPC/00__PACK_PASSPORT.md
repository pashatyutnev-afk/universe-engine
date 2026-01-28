# SPC PRO PACK — PACK PASSPORT (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/00__PACK_PASSPORT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PACK_PASSPORT
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.DRAFT.001
OWNER: SYSTEM
ROLE: Identity + boundary + dependencies contract for VOCAL_DIRECTOR specialization (vocal delivery, intelligibility, performance arc). Defines readiness criteria and audit boundaries.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Pro Pack passport for VOCAL_DIRECTOR_SPC (L3 target)."
- REASON: "Need deterministic, reusable knowledge capsule for vocal performance ownership and intelligibility gates."
- IMPACT: "Enables consistent vocal direction outputs, repeatable takes, and lyric intelligibility across tracks."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.001

---

## 0) IDENTITY
PACK_IDENTITY:
- PACK_UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.DRAFT.001
- SPC_ENTITY_UID: UE.SPC.SOUND_MUSIC.VOCAL_DIRECTOR.001
- SPC_CANON_NAME: VOCAL_DIRECTOR_SPC
- TARGET_PROFICIENCY_LEVEL: L3 (PRO)
- DOMAIN: SOUND_MUSIC
- PRIMARY FUNCTION:
  - Own vocal performance: delivery profile, performance arc by sections, intelligibility gates, phrasing/timing notes, and recording direction pack (take goals + risk lines).

CURRENT READINESS:
- L3 READY: NO (STARTER)
- BLOCKING_GAPS:
  - Pro Pack core modules not yet created (skill tree, playbooks, gates, cases, sources, regression).
- NON_BLOCKING_GAPS:
  - none.

---

## 1) SCOPE (BOUNDARY)
COVERS:
- Vocal Delivery Profile (principles): tone/energy/articulation/breath policy
- Performance Arc (by sections): verse→chorus dynamics and emotion shaping
- Intelligibility Gates: must-hear words, diction failure modes, pass/fail checklist
- Timing & Phrasing Notes: accents, stretch/cut guidance aligned to topline constraints
- Harmony/Stacking Strategy (high-level): where/why harmonies/backs (not notes writing)
- Recording Direction Pack: take goals, risk lines, repeatability constraints
- Escalation requests when text/structure must change (to Lyricist/Songwriter)

EXCLUDES (from entity boundary):
- writing lyrics (Lyrics owner)
- changing song structure ownership (Songwriter owner)
- arrangement ownership (Arranger owner)
- mix/master settings (Mix/Master owner)
- video montage decisions

---

## 2) REQUIRED OUTPUTS (WHAT THIS SPC MUST PRODUCE)
PRIMARY_OUTPUTS:
- Vocal Delivery Profile (principles)
- Performance Arc Map (by sections)
- Intelligibility Gates Checklist (pass/fail)
- Phrasing/Timing Notes (accent points)
- Harmony/Stacking Plan (high-level, where/why)
- Recording Direction Pack (take goals + risk lines + fix directives)
- Escalation Notes (what must change in lyrics/structure/arrangement, and who owns it)

TRACE OUTPUT (MANDATORY):
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO
- UIDS_APPLIED (ENG/CTL/SPC): UID list
- GATES_RUN (local pack gates): UID list
- GAPS: placeholders encountered

---

## 3) HARD LIMITS (NON-NEGOTIABLE)
HARD_LIMITS:
- No-fantasy: do not invent vocal “facts” or capabilities not supported by KB sources or entity contracts.
- Intelligibility is mandatory: if must-hear words are not defined → NOT READY output.
- Do not change lyric meaning; only request revisions via escalation (Lyricist/Songwriter).
- Do not prescribe mix/master chains; only provide priority notes (principles).
- UID-only operational linking (deps are UIDs; paths are labels only).

---

## 4) DEPENDENCIES (UID-ONLY)
DEPENDENCIES_UID_ONLY:

SPC (BOUND):
- UE.SPC.SOUND_MUSIC.VOCAL_DIRECTOR.001 | WHY: pack’s operational SPC entity

ENG (BOUND, INTERFACES):
- UE.ENG.SOUND.VOCAL.PERFORMANCE.001 | WHY: performance spec schema + gates (range/stress/delivery contradictions)
- UE.ENG.SOUND.LYRICS.001 | WHY: structured lyric drafts and constraints feeding intelligibility work

ENG (SECONDARY, OPTIONAL / GAP UNTIL CONFIRMED NEED):
- PLACEHOLDER_UID: UE.ENG.SOUND.ARRANGEMENT.??? | WHY: seat constraints and density vs vocal clarity (bind when confirmed)
- PLACEHOLDER_UID: UE.ENG.SOUND.MIX_MASTER.??? | WHY: only for downstream notes boundary (bind when confirmed)

---

## 5) ACCEPTANCE (READY WHEN…)
PACK_READY_CRITERIA (L3 TARGET):
- has skill tree with leaf skills + observable outcomes → [ ]
- has ≥ 6 playbooks (incl. diagnose/rework loop) → [ ]
- has ≥ 3 measurable gates (incl. intelligibility gate) → [ ]
- has ≥ 25 cases (good/bad/borderline/edge) → [ ]
- has anchored rubric → [ ]
- has regression guard + run record → [ ]
- has KB sources recorded with extracted principles → [ ]
- has deterministic XREF bindings (who calls, where outputs go) → [ ]

STATUS:
- L3 READY: NO (STARTER)

---

## 6) NEXT FILES TO CREATE (ORDER)
NEXT_FILL_ORDER (ONE-BY-ONE):
1) 01__SCOPE_AND_SKILL_TREE.md
2) 02__GOLDEN_PRINCIPLES_AND_LIMITS.md
3) 03__METHOD_PLAYBOOKS/00__README__PLAYBOOKS.md
4) 05__KB_GATES/00__README__GATES.md
5) 06__CASE_LIBRARY/00__README__CASES.md
6) 08__KB_SOURCES.md
7) 09__REGRESSION_GUARD.md
8) 10__TOPIC_BINDINGS.md
9) 11__XREF_BINDINGS.md
10) 12__PACK_COMPLETION_CHECK.md

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.SPC.TOP.DOC_CONTROLLER.001 | WHY: doc-control gate discipline for pack files

--- END.
