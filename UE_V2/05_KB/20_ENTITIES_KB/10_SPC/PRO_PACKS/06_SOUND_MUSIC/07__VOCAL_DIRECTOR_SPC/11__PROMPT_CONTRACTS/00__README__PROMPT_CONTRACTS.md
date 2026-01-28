# SPC PRO PACK — PROMPT CONTRACTS (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/11__PROMPT_CONTRACTS/00__README__PROMPT_CONTRACTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: README
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PROMPT_CONTRACTS.README.DRAFT.001
OWNER: SYSTEM
ROLE: Defines “Prompt Contracts” for VOCAL_DIRECTOR: how to translate output-pack artifacts into deterministic prompt blocks for music generation platforms, without violating scope. Includes tiers (MIN/STD/FULL), assembly rules, and forbidden content rules.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PROMPT CONTRACTS README for VOCAL_DIRECTOR: what it is, tiers, assembly rules, forbidden content, and file roadmap."
- REASON: "Need deterministic interface between vocal direction artifacts and external generation prompts."
- IMPACT: "Less prompt drift, better repeatability, safer scope."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.PROMPT.README.001

---

## 0) PURPOSE
A Prompt Contract is a structured, copy-ready prompt blueprint derived from VOCAL_DIRECTOR artifacts.

It:
- constrains vocal performance outcomes (clarity, arc, breath safety)
- is platform-adapted (format rules differ)
- preserves scope boundaries (no lyric rewrites, no mix/master chains)

This folder is NOT a “prompt idea dump”.
It is a strict contract library.

---

## 1) SCOPE RULE (ABSOLUTE)
Prompt Contracts MUST NOT contain:
- lyric rewrites / replacement lines (F1)
- mix/master plugin chains or DAW recipes (F4)
- production ownership decisions beyond principle-level requests

Prompt Contracts MAY contain:
- performance constraints (clarity, articulation, breath)
- arrangement/seat requests ONLY as principles (e.g., “leave perceptual space for lead consonants”)
- negative constraints (what to avoid)

If a change requires lyric/structure ownership:
- emit ESCALATION_NOTES (T14 format), not prompt edits.

---

## 2) INPUT SOURCE OF TRUTH
Prompt Contracts are derived from OUTPUT PACKS:
- MIN / STD / FULL
and their stable artifact blocks.

Rule:
- Prompt Contract must reference only what exists in the output pack.
- No invented details.

---

## 3) CONTRACT TIERS (MIN / STD / FULL)
### 3.1 PROMPT MIN
Use when:
- fast iteration
Requires (derived from OUTPUT MIN/STD):
- MUST_HEAR_WORDS (P0)
- MUST_HEAR_PHRASES (P0) if present
- CLARITY_TARGETS
- language + vocal mode hint (if known)

### 3.2 PROMPT STD
Default:
- includes intelligibility enforcement + delivery profile + breath policy
Requires (derived from OUTPUT STD/FULL):
- MUST_HEAR_WORDS/PHRASES
- INTELLIGIBILITY hard fails (expressed as “avoid” constraints)
- VOCAL_STYLE_PROFILE + FORBIDDEN_STYLES
- MUST_HEAR_PROTECTION_RULES + BREATH_POLICY
- stacking decision (YES/NO)

### 3.3 PROMPT FULL
READY:
- includes arc/contrast + stacking safe + take intent (as prompt constraints)
Requires (derived from OUTPUT FULL):
- PERFORMANCE_ARC_MAP + CONTRAST_LEVERS
- stacking protected zones constraints (if stacking used)
- full forbidden list and QC-driven “avoid” constraints

---

## 4) PROMPT CONTRACT BLOCKS (STABLE NAMES)
Every Prompt Contract file must output ONLY these contract blocks:

PROMPT_HEADER:
- platform:
- tier: MIN | STD | FULL
- language:
- hook_section_label:

PROMPT_CORE:
- vocal_style:
- vocal_delivery_constraints:
- must_hear_targets:
- must_hear_phrases:

PROMPT_ARC (optional; FULL):
- arc_map:
- contrast_levers:

PROMPT_BREATH (optional; STD/FULL):
- breath_policy:
- never_split_phrases:

PROMPT_STACKING (optional; STD/FULL):
- stacking_used: YES/NO
- protected_zones (if YES):

NEGATIVE_SPEC:
- avoid:
  - 1)
  - 2)

SCOPE_NOTICE:
- lyric_rewrite: FORBIDDEN
- mix_chain: FORBIDDEN
- ownership: ESCALATE_ONLY

COPY_READY_PROMPT:
- "<final single prompt text assembled for the platform>"

Rule:
- COPY_READY_PROMPT must be the last block.

---

## 5) ASSEMBLY RULE (HOW TO BUILD COPY_READY_PROMPT)
1) Start with platform style tags / genre if provided externally.
2) Inject vocal performance constraints:
   - clarity / must-hear / articulation
3) Add breath protection (never split P0 phrases).
4) Add arc (if tier FULL).
5) Add stacking constraints (if used).
6) Append negative constraints.
7) Add scope notice (short, non-verbose).
8) Keep it compact (avoid long essays).

---

## 6) MAPPING FROM OUTPUT PACKS → PROMPT CONTRACTS
- MUST_HEAR_WORDS/PHRASES → “must-hear targets/phrases” lines
- HARD_FAIL_TRIGGERS → NEGATIVE_SPEC “avoid …”
- VOCAL_STYLE_PROFILE/FORBIDDEN_STYLES → vocal style + avoid list
- BREATH_POLICY/NEVER_SPLIT → breath constraints
- ARC/LEVERS → arc instructions (FULL)
- STACKING_SAFE artifacts → stacking constraints (FULL; optional STD)

---

## 7) NEXT FILES (ORDER)
Proceed in numeric order (one file per platform/format):
- 01__PROMPT_CONTRACT__UNIVERSAL.md
- 02__PROMPT_CONTRACT__SUNO.md
- 03__PROMPT_CONTRACT__UDIO.md

(If you later add a new platform, add a new file and list it here.)

--- END.
