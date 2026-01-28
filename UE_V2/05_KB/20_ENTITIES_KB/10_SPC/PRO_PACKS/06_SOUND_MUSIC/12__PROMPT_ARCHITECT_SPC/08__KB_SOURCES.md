# SPC PRO PACK — KB SOURCES (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/08__KB_SOURCES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: KB_SOURCES
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.3
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.SOURCES.DRAFT.001
OWNER: SYSTEM
ROLE: Source registry for PROMPT_ARCHITECT pack: how to record external world knowledge as extracted operational principles (no copy-paste), assign authority tiers, define refresh cadence, and keep the pack audit-ready and non-fantasy.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: PATCH
- SUMMARY: "Added SOURCE_RECORD #3 (Suno v4.5 detailed style instructions) with extracted principles for conversational style prompts and structured progression cues."
- REASON: "Continue G4: add T0 provenance for style prompting patterns in Suno v4.5."
- IMPACT: "Improves style prompt clarity and reduces drift via structured, role-based style direction."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.PROMPT.SRC.004

---

## 0) CORE RULE (ABSOLUTE)
This file stores:
- SOURCE RECORDS (metadata)
- EXTRACTED PRINCIPLES (short operational bullets)

This file must NOT store:
- large copied text
- long quotes
- link dumps without extracted principles
- claims not backed by an accessed source

If a tactic is not backed by a recorded source (or memory already validated earlier):
- mark it as UNSOURCED and do not treat it as authoritative.

---

## 1) AUTHORITY TIERS (GUIDE)
AUTHORITY_TIERS:
- T0 (HIGHEST): primary documentation / official specs / direct tool docs
- T1: authoritative practitioners’ guides / textbooks / well-known references
- T2: high-quality articles / case studies with clear methodology
- T3: community posts / forums (use only if repeated and confirmed)
- T4 (LOW): unverified opinions (recorded only as “hypothesis”, never as rule)

Rule:
- Pack-level rules should prefer T0–T2.

---

## 2) SOURCE RECORD TEMPLATE (COPY)
SOURCE_RECORD:
- SOURCE_UID: SRC-YYYYMMDD-001
- TITLE:
- SOURCE_TYPE: OFFICIAL_DOC | BOOK | PAPER | ARTICLE | VIDEO | COMMUNITY | OTHER
- AUTHORITY_TIER: T0/T1/T2/T3/T4
- DATE_ACCESSED: YYYY-MM-DD
- LAST_VERIFIED: YYYY-MM-DD
- REFRESH_INTERVAL: 30d | 90d | 180d | 365d | NEVER
- SCOPE (what this source covers):
- METHOD QUALITY NOTES:
  - why we trust it (short)
  - limitations (short)
- EXTRACTED PRINCIPLES (MAX 5–12 BULLETS):
  - P1:
  - P2:
- APPLIED_IN_PACK (WHERE):
  - file(s) or playbook(s) affected (local paths allowed as labels only)
- CONFLICTS (if any):
  - with which source UIDs
  - resolution note
- COPYRIGHT NOTE:
  - confirm: "no large text copied; principles paraphrased"

---

## 3) EXTRACTED PRINCIPLES FORMAT (STRICT)
Rules:
- Each principle must be:
  - operational (actionable)
  - short (≤ 1–2 lines)
  - non-ambiguous (avoid “usually”)
- Prefer:
  - “Do X when Y” format
  - thresholds as principles (not exact palette/voice model specifics)

Example pattern:
- "If output drifts in style, prune anchors to 3–6 and enforce dominance rule."

---

## 4) REFRESH DISCIPLINE
Refresh required when:
- REFRESH_INTERVAL elapsed
- tool/platform changed (e.g., prompt engine behavior changed)
- repeated failures appear that contradict current principles

Refresh procedure:
1) Re-open source (or newer edition)
2) Verify principles still valid
3) Update LAST_VERIFIED
4) If principle changes:
   - record change note
   - update affected playbooks/gates
   - run REGRESSION GUARD

---

## 5) CONFLICT RESOLUTION (WHEN SOURCES DISAGREE)
If two sources conflict:
- Prefer higher authority tier
- If equal tier:
  - record both as alternative strategies
  - mark as “CONTEXT-DEPENDENT”
  - create a gate/check or case to decide

Never silently overwrite.

---

## 6) SOURCES (REAL RECORDS)
SOURCES:

SOURCE_RECORD:
- SOURCE_UID: SRC-20260115-001
- TITLE: "Prompt Like a Master" — Udio Help Center
- SOURCE_TYPE: OFFICIAL_DOC
- AUTHORITY_TIER: T0
- DATE_ACCESSED: 2026-01-15
- LAST_VERIFIED: 2026-01-15
- REFRESH_INTERVAL: 180d
- SCOPE (what this source covers):
  - prompt composition: topic + genre/tags + mood/instruments/tempo/thematic framing
  - using tags and lyric editor markup for vocals/sections
  - pronunciation/stress control tactics
  - iteration: generate variants and tweak details
- METHOD QUALITY NOTES:
  - why we trust it: official tool documentation describing intended usage patterns
  - limitations: guidance is non-deterministic; adherence may vary; requires testing + one-axis iteration discipline
- EXTRACTED PRINCIPLES (10):
  - P1: Compose prompts from a small core: topic/theme + genre/tags + key mood/instruments; avoid long adjective chains.
  - P2: For stronger controllability, encode song structure using bracketed section tags (e.g., [Verse], [Chorus], [Bridge]) inside lyrics input.
  - P3: Treat tags as guidance, not hard commands; plan for multiple generations and iterative refinement.
  - P4: For vocals/lyrics control, use explicit markup (section labels, parenthetical backing layers) instead of vague “make it sound good”.
  - P5: If pronunciation is wrong, modify spelling into syllables, spell out acronyms, or add simple expressive phonetics to steer articulation.
  - P6: Use small targeted edits between runs (change instruments/tempo/one detail) rather than rewriting many blocks at once.
  - P7: When aiming for instrumentals, explicitly request instrumental mode and/or instrument tags; don’t rely on implicit absence of lyrics.
  - P8: Use repeated key words sparingly only to emphasize the primary intent (avoid repetition spam).
  - P9: Prefer “clear vision” framing (mood/genre/tempo/instruments/story) before adding extra constraints; clarity first.
  - P10: If a platform offers a stricter/manual mode, use it when you need tag-only precision (expect less creative refinement).
- APPLIED_IN_PACK (WHERE):
  - 03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_WORKFLOW.md
  - 03__METHOD_PLAYBOOKS/02__PLAYBOOK__ONE_AXIS_VARIANTS.md
  - 05__KB_GATES/01__GATE__PROMPT_CONTRACT_CLARITY.md
  - 05__KB_GATES/02__GATE__VOICE_DIVERSITY_INTENT.md
  - 05__KB_GATES/03__GATE__REPETITION_CONTROL_INTENT.md
- CONFLICTS (if any):
  - none recorded
- COPYRIGHT NOTE:
  - confirm: "no large text copied; principles paraphrased"

SOURCE_RECORD:
- SOURCE_UID: SRC-20260115-002
- TITLE: "How to Make a Song with Suno" — Suno Hub Guide (Date Updated: 2025-12-02)
- SOURCE_TYPE: OFFICIAL_DOC
- AUTHORITY_TIER: T0
- DATE_ACCESSED: 2026-01-15
- LAST_VERIFIED: 2026-01-15
- REFRESH_INTERVAL: 180d
- SCOPE (what this source covers):
  - prompt specificity (genre/mood/keywords/instrumentation)
  - Custom mode vs Simple mode
  - structure cues via section tags [Verse]/[Chorus]/[Bridge]
  - iterative workflow: generate multiple versions and refine with small tweaks
  - adding context in lyrics (not only style field) for better results
- METHOD QUALITY NOTES:
  - why we trust it: official Suno guidance describing recommended user workflow and structure tagging
  - limitations: guide is general; platform behavior varies per model version; validate via cases + gates
- EXTRACTED PRINCIPLES (10):
  - P1: For better structure adherence, include section tags / structure cues (e.g., [Verse], [Chorus], [Bridge]) to define song flow.
  - P2: Increase prompt specificity by naming genre + mood + a few instrumentation cues; avoid vague prompts when you want control.
  - P3: Use Custom mode when you need more control (lyrics, style, instrumental/vocals toggles, and other parameters) instead of relying on Simple mode.
  - P4: If you want your own lyrics, provide them; otherwise explicitly choose lyric generation—don’t leave lyrics intent ambiguous.
  - P5: Expect multiple generations: create variations and iterate with small prompt tweaks rather than aiming for perfection in one run.
  - P6: When refining, change one detail at a time (one-axis discipline) to learn what improved the output.
  - P7: If you need a specific structure, explicitly list sections (Intro/Verse/Chorus/Bridge/Outro) and keep labels consistent.
  - P8: Add extra context in the lyrics field (not only style) when you need the model to follow narrative/structure intent more closely.
  - P9: Use concrete examples of what you want (e.g., “big synth hook chorus, intimate piano verse”) instead of abstract labels when results matter.
  - P10: After choosing the better version, refine from that baseline rather than rewriting everything; preserve what worked.
- APPLIED_IN_PACK (WHERE):
  - 03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_WORKFLOW.md
  - 03__METHOD_PLAYBOOKS/02__PLAYBOOK__ONE_AXIS_VARIANTS.md
  - 03__METHOD_PLAYBOOKS/03__PLAYBOOK__DIAGNOSE_AND_REWORK.md
  - 05__KB_GATES/01__GATE__PROMPT_CONTRACT_CLARITY.md
  - 05__KB_GATES/05__GATE__ONE_AXIS_CHANGE_DISCIPLINE.md
- CONFLICTS (if any):
  - none recorded
- COPYRIGHT NOTE:
  - confirm: "no large text copied; principles paraphrased"

SOURCE_RECORD:
- SOURCE_UID: SRC-20260115-003
- TITLE: "Create in V4.5: Detailed Style Instructions" — Suno Help Center
- SOURCE_TYPE: OFFICIAL_DOC
- AUTHORITY_TIER: T0
- DATE_ACCESSED: 2026-01-15
- LAST_VERIFIED: 2026-01-15
- REFRESH_INTERVAL: 180d
- SCOPE (what this source covers):
  - writing more detailed style instructions in v4.5
  - moving from keyword lists to conversational style prompts
  - embedding progression cues (begin/build) to guide evolution across the song
- METHOD QUALITY NOTES:
  - why we trust it: official Suno documentation describing intended prompt behavior in v4.5
  - limitations: examples are illustrative; actual adherence varies; validate via gates + cases
- EXTRACTED PRINCIPLES (8):
  - P1: In v4.5 you can use more detailed, conversational style prompts instead of only short keyword lists.
  - P2: Use “progression cues” (e.g., begin → build gradually) to steer how the arrangement evolves over time.
  - P3: Keep the style prompt coherent: describe one primary identity and its evolution rather than listing many unrelated styles.
  - P4: Prefer role-based descriptors (textures, rhythms, layers, groove) over long inventories of instruments.
  - P5: Encode structure-like guidance inside the style narrative when useful (e.g., intro ambience → groove → melodic layers) without contradicting your explicit STRUCTURE_BLOCK.
  - P6: When adding detail, maintain one consistent mix/texture direction (avoid “clean” + “lo-fi” contradictions).
  - P7: If results drift, reduce detail and re-anchor to the essential identity (shorten the style narrative + keep core anchors).
  - P8: Use the detailed style narrative as a complement to your constraints, not a replacement—clarity still comes from explicit structure and repetition policy.
- APPLIED_IN_PACK (WHERE):
  - 03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_WORKFLOW.md
  - 03__METHOD_PLAYBOOKS/07__PLAYBOOK__STYLE_FINGERPRINT_STABILIZER.md
  - 05__KB_GATES/01__GATE__PROMPT_CONTRACT_CLARITY.md
  - 05__KB_GATES/04__GATE__STYLE_FINGERPRINT_STABILITY.md
- CONFLICTS (if any):
  - none recorded
- COPYRIGHT NOTE:
  - confirm: "no large text copied; principles paraphrased"

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- this file becomes a link dump without extracted principles
- large external text is pasted
- sources are used without being recorded here (when they change pack behavior)
- principles are asserted as rules without provenance

---

## 8) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.REGRESSION.DRAFT.001 | WHY: run regression after source-driven changes
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.POLICY.DRAFT.001 | WHY: no-fantasy + anti-copy constraints
- UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001 | WHY: compliance checks include provenance discipline

--- END.
