# KB — KB SCOPE DOMAIN BOUNDARY SUMMARY (TABLE) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/22__KB_SCOPE_DOMAIN_BOUNDARY_SUMMARY_TABLE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.SCOPE_BOUNDARY_TABLE.022
OWNER: SYSTEM
ROLE: Compact boundary reference table for KB scopes/domains: what belongs where, what is forbidden to mix, and which scopes typically complement each other. Prevents misplacement and drift.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced KB scope boundary summary table for fast domain separation decisions."
- REASON: "As KB grows, boundary confusion increases; a compact table prevents misfiled modules and mixed scopes."
- IMPACT: "Faster correct module placement and safer cross-domain referencing."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MAP.022

---

## 0) PURPOSE (KB)
Provide a fast lookup table:
- scope intent (what it is)
- allowed content (what goes there)
- forbidden content (what must not go there)
- typical complements (what it pairs with)

No URLs/RAW in this module.

---

## 1) DOMAIN BOUNDARY TABLE (CANON)

| KB_SCOPE | INTENT (1 LINE) | ALLOWED (KEY TYPES) | FORBIDDEN (DO NOT MIX) | TYPICAL COMPLEMENTS |
|---|---|---|---|---|
| GOVERNANCE | how KB/system work deterministically | protocols, dictionaries, maps, audits, existence rules | domain craft, RAW registries beyond master index, second entrypoints | MAPS, META, REFERENCE |
| META | KB operational brain (usage/nav/anti-drift) | usage protocols, nav standards, memory rules, gap handling, QA/audit | domain craft toolkits, narrative/music/marketing methods | GOVERNANCE, MAPS |
| MAPS | selection logic (which scope/modules to load) | enums, matrices, deterministic selection algorithms, fail conditions | indexes/RAW link hubs, how-to craft tutorials | GOVERNANCE, TOPICS |
| REFERENCE | fast lookup assets | short dictionaries/enums/taxonomies | long tutorials, procedures, essays | TOPICS, GOVERNANCE |
| TOPICS.NARRATIVE | story construction methods | scene craft, pacing, tension, continuity, dialogue methods | world lore dumps, character bios, marketing/prod rules | TOPICS.CHARACTER, TOPICS.WORLD, TOPICS.VISUAL |
| TOPICS.CHARACTER | character craft methods | motivation, psychology, behavior, relationships, voice patterns | plot/episode structure, world geopolitics | TOPICS.NARRATIVE, TOPICS.WORLD |
| TOPICS.WORLD | setting constraints & worldbuilding | world laws, timeline, civs, geopolitics, economy/resource constraints, ecology, tech limits | plot beats, character trauma/psych | TOPICS.NARRATIVE, TOPICS.CHARACTER, TOPICS.VISUAL |
| TOPICS.VISUAL | how it looks (principles+constraints) | composition, style principles, camera grammar, lighting principles, image-gen constraints/risks | montage/editing solutions, plot logic, hardcoded palettes if principles-first | TOPICS.NARRATIVE, TOPICS.WORLD |
| TOPICS.SOUND_MUSIC | how it sounds (craft+QA) | hook engineering, structure, vocals, mix translation, anti-repeat/collision, UGC moments | marketing/distribution how-to, production governance | TOPICS.PRODUCTION, TOPICS.MARKETING |
| TOPICS.PRODUCTION | how it ships (pipeline) | workflows, handoffs, format adaptation, release packs, QA gates, versioning delivery | deep domain craft tutorials, KB governance/nav | TOPICS.SOUND_MUSIC, TOPICS.MARKETING, TOPICS.NARRATIVE |
| TOPICS.MARKETING | how it reaches people | positioning, personas, packaging, channels, launch windows, engagement loops, SEO, monetization | music craft, production governance details, KB nav | TOPICS.PRODUCTION, TOPICS.SOUND_MUSIC |
| TOPICS.REFERENCE (domain reference) | stable domain dictionaries | enums/term glossaries for domain | full tutorials/procedures (go to TOPICS) | domain TOPICS |

Notes:
- Complement means “often used together”, not dependency.
- Dependencies must be expressed via REL dictionary elsewhere (if used).

---

## 2) HARD FAIL CONDITIONS
FAIL IF:
- a module is filed in a scope whose FORBIDDEN column matches its content type
- scopes are used as navigation (URLs/RAW inside)
- governance/meta modules contain domain craft methods

---

## 3) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.GOVERNANCE.021 | WHY: governance scope boundary rules
- XREF: UE.KB.STD.SCOPE.META.012 | WHY: meta scope boundary rules
- XREF: UE.KB.STD.SCOPE.MAPS.013 | WHY: maps scope boundary rules
- XREF: UE.KB.STD.SCOPE.REFERENCE.010 | WHY: reference scope boundary rules
- XREF: UE.KB.STD.SCOPE.TOPICS.011 | WHY: topics scope standard
- XREF: UE.KB.STD.SCOPE.NARRATIVE.017 | WHY: narrative boundary
- XREF: UE.KB.STD.SCOPE.CHARACTER.018 | WHY: character boundary
- XREF: UE.KB.STD.SCOPE.WORLD.019 | WHY: world boundary
- XREF: UE.KB.STD.SCOPE.VISUAL.020 | WHY: visual boundary
- XREF: UE.KB.STD.SCOPE.SOUND_MUSIC.015 | WHY: sound/music boundary
- XREF: UE.KB.STD.SCOPE.PRODUCTION.014 | WHY: production boundary
- XREF: UE.KB.STD.SCOPE.MARKETING.016 | WHY: marketing boundary

--- END.
