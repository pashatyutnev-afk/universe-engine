# PLAYBOOK — CORE WORKFLOW (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_WORKFLOW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.CORE.001
OWNER: SYSTEM
ROLE: Deterministic core workflow to build a music generator prompt contract from intent: section plan, style fingerprint, vocal intent, negatives, constraints, and initial A/B variants. Designed for QA-driven iteration.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created core workflow playbook for PROMPT_ARCHITECT: intent→contract blocks→variants→precheck→trace."
- REASON: "Need a repeatable method to avoid random prompts and reduce repetition/collision."
- IMPACT: "More controllable prompts and faster QA convergence."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.CORE.001

---

## 0) INPUTS (REQUIRED)
INPUTS_REQUIRED:
- TARGET_GENRE / STYLE (human description)
- BPM / TEMPO FEEL (optional but preferred)
- SONG LENGTH TARGET (e.g., ~3:00)
- VOCAL MODE:
  - single voice OR A/B roles (rap vs melodic)
- LANGUAGE
- KEY CONSTRAINTS:
  - what MUST happen (e.g., hook early, half-time stomp)
  - what MUST NOT happen (e.g., no repeated lines)

INPUTS_OPTIONAL:
- reference bands/era (principles only; avoid “copy exactly”)
- lyric draft (if provided)
- mood keywords (only as secondary)
- instrumentation preferences (roles, not inventory)
- target platform constraints (short/loop/full)

If any required input missing:
- proceed with defaults but mark UNKNOWN in trace.

---

## 1) OUTPUTS
PRIMARY_OUTPUT:
- PROMPT_CONTRACT (ready to paste):
  - STYLE_BLOCK
  - STRUCTURE_BLOCK
  - VOCAL_INTENT_BLOCK
  - NEGATIVE_SPEC_BLOCK
  - CONSTRAINTS_BLOCK (duration/format/energy)
SECONDARY_OUTPUTS:
- VARIANT_SET (2–5 variants; one-axis changes)
- RECHECK_MINI (what to verify after generation)
- RUN_TRACE_NOTES (UID-only sources + changes)

---

## 2) METHOD (DETERMINISTIC STEPS)
### Step 1 — Define success criteria (1–3 checks)
Write 1–3 observable checks:
- hook appears early (≤ X seconds) OR hook is clearly identifiable
- chorus is distinct from verse
- vocal roles clearly differentiated
- repetition limited to chorus/hook

### Step 2 — Build STRUCTURE_BLOCK (sections)
Pick structure:
- Intro (optional)
- Verse 1 (role A/B)
- Chorus (hook)
- Verse 2
- Bridge (optional)
- Final chorus
- Outro (optional)

Encode as:
- section list + role per section + energy note (low/mid/high)

### Step 3 — Build STYLE_BLOCK (fingerprint anchors)
Select:
- PRIMARY genre
- SECONDARY touch (optional)
- 3–6 anchor markers:
  - drum feel (half-time stomp / driving)
  - guitar role (riff/chugs/palm-mute)
  - synth role (glitch leads / industrial hits)
  - texture (clean aggressive vs gritty; choose one direction)
Define dominance:
- “primary + touch” (no equal blending)

### Step 4 — Build VOCAL_INTENT_BLOCK (anti same-singer)
Define:
- Voice A: rap delivery traits (tight rhythm, percussive)
- Voice B: melodic chorus traits (open vowels, sustained)
Add contrast levers (principles):
- range separation (low vs mid)
- timbre contrast (darker vs brighter)
- section role separation (A owns verses, B owns chorus)
Optional:
- call/response tags for chorus or bridge

### Step 5 — Build NEGATIVE_SPEC_BLOCK (targeted)
Choose 5–12 negatives from known fails:
- avoid repeated phrases/lines in verses
- avoid identical vocal timbre across sections
- avoid muddy low end / uncontrolled sub
- avoid monotone dynamics (no constant wall)
- avoid generic EDM clichés (if not desired)
Keep it short and specific.

### Step 6 — Build CONSTRAINTS_BLOCK (format + energy)
Include:
- full song ~3 minutes (or loop)
- energy curve summary (e.g., build to chorus; bridge drop then final lift)
- “clean aggressive mix, tight low end” as principle if needed

### Step 7 — Assemble PROMPT_CONTRACT
Assemble blocks in order:
1) STYLE_BLOCK
2) STRUCTURE_BLOCK
3) VOCAL_INTENT_BLOCK
4) NEGATIVE_SPEC_BLOCK
5) CONSTRAINTS_BLOCK

### Step 8 — Create VARIANT_SET (one-axis changes)
Create 2–5 variants, each changes only one axis:
- V1: hook earlier / stronger hook emphasis
- V2: more vocal contrast (role separation stronger)
- V3: reduce glitch texture / simplify synth role
- V4: tighten anti-repetition constraints
- V5: slight tempo feel adjustment (only if needed)

Rule:
- do not change structure + style + vocals all at once.

### Step 9 — RECHECK_MINI (post-gen)
Define 6 quick checks:
- hook clarity
- chorus distinctness
- vocal role separation
- repetition only in chorus
- style fingerprint present
- low end not muddy (if relevant)

---

## 3) CHECKPOINTS (GATES/CHECKLISTS UID-ONLY)
(Replace placeholders when real UIDs exist.)

CHECKPOINTS_UID_ONLY:
- UE.KB.SOUND.GATE.HOOK_TIMING.??? | WHY: early hook criterion
- UE.KB.SOUND.VAL.REPEAT_GUARD.??? | WHY: prevent repeated patterns
- UE.KB.SOUND.QA.LOOP_15S.??? | WHY: loopability/retention
- UE.KB.SOUND.QA.VOICE_DIVERSITY.??? | WHY: voice sameness control

If checkpoints missing:
- run internal mini checks + mark GAP.

---

## 4) COMMON FAILS → FAST FIXES
F1 — Output is mush / no chorus identity
- Fix: strengthen STRUCTURE_BLOCK; explicitly label chorus hook; reduce style clutter.

F2 — Same voice everywhere
- Fix: strengthen VOCAL_INTENT_BLOCK: explicit role ownership + stronger contrast levers + targeted negatives.

F3 — Repeated lines/patterns
- Fix: add verse novelty constraint + negative spec; limit repeats to chorus only.

F4 — Style drift / random mix
- Fix: reduce anchors to 3–4; enforce “primary + touch”; remove conflicting descriptors.

F5 — Too many constraints (quality drops)
- Fix: cut negative list to top 8; cut instrument inventory; keep roles only.

---

## 5) TRACE (MINIMUM)
RUN_TRACE_NOTES (COPY):
- TARGET:
- PROMPT_VERSION: V0 / V1 / ...
- AXIS_CHANGED (if rework):
- SUCCESS_CRITERIA:
- TOPIC_UIDS_USED (UID-ONLY):
  - <uid>
- CHECKPOINT_UIDS_RUN (UID-ONLY):
  - <uid>
- RESULT: PASS/REWORK/FAIL (self)
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO
- GAPS:
  - <missing uid/criterion>

--- END.
