# SPC PRO PACK — SCOPE & SKILL TREE (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/01__SCOPE_AND_SKILL_TREE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: SKILL_TREE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.SKILLTREE.DRAFT.001
OWNER: SYSTEM
ROLE: Defines responsibilities, forbidden actions, and a leaf-skill tree with observable outcomes for the PROMPT_ARCHITECT specialization (music generator prompt craft).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined PROMPT_ARCHITECT scope + skill tree with leaf skills and observable outcomes."
- REASON: "Need deterministic competence decomposition before playbooks/gates/cases."
- IMPACT: "Enables measurable training, rubric design, and gate mapping."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.SKILLTREE.001

---

## 0) RESPONSIBILITIES (WHAT THIS SPC MUST DO)
RESPONSIBILITIES:
- Convert intent into a prompt contract that is controllable and testable.
- Enforce structure: sections, hooks, energy curve, constraints.
- Control style fingerprint (genre markers) without drifting or colliding with existing catalog.
- Control vocal intent (distinct voices/delivery) and reduce sameness across tracks.
- Reduce repetition (phrases, rhyme, motif loops) via prompt-level tactics.
- Prepare prompt variants for A/B (one-axis changes).
- Produce rework patches when QA/VAL fails (minimal change strategy).
- Emit trace notes (UID-only sources used + whether memory reused).

---

## 1) FORBIDDEN ACTIONS (WHAT THIS SPC MUST NOT DO)
FORBIDDEN_ACTIONS:
- Inventing “facts” or claiming rules exist without KB backing.
- Writing domain topics inside this pack (must reference Topics realm only).
- Using URL/PATH as authority in operational references (UID-only).
- Overloading prompt with irrelevant specs (“everything at once”) without control intent.
- Ignoring QA/VAL outcomes; “arguing with gates” instead of changing inputs.
- Copying large external text into KB_SOURCES; only extracted principles allowed.

---

## 2) SKILL TREE (BRANCHES → LEAF SKILLS)
SKILL_TREE:

### BRANCH A — Prompt Contract Architecture (core)
A1 — LEAF: Define prompt goal and success criteria
- OBSERVABLE_OUTCOME:
  - A one-line goal + “what must be true” checks (e.g., hook appears ≤ X sec; chorus readable; vocal split present).
- COMMON_FAILS:
  - goal is vibes-only; no measurable checks.

A2 — LEAF: Build section plan (full song)
- OBSERVABLE_OUTCOME:
  - Prompt includes explicit sections (Intro/Verse/Chorus/Bridge/Outro) and expected role of each.
- COMMON_FAILS:
  - sections missing; generator outputs mush.

A3 — LEAF: Encode energy curve (low→high) as constraints
- OBSERVABLE_OUTCOME:
  - Prompt describes energy progression in 2–4 steps (not montage), aligned to sections.
- COMMON_FAILS:
  - constant intensity; no contrast.

A4 — LEAF: Compose “positive spec block” (what to do)
- OBSERVABLE_OUTCOME:
  - Clear style + instrumentation + vocal intent + tempo/feel when needed, without contradictions.
- COMMON_FAILS:
  - too generic or too contradictory.

A5 — LEAF: Compose “negative spec block” (what to avoid)
- OBSERVABLE_OUTCOME:
  - 5–12 targeted negatives matching known failure modes (repetition, same voice, muddy mix, etc).
- COMMON_FAILS:
  - negatives too broad (“no bad”) or too many (kills output).

---

### BRANCH B — Genre Fingerprint Control (consistency without drift)
B1 — LEAF: Select fingerprint markers (genre anchors)
- OBSERVABLE_OUTCOME:
  - 3–6 anchor markers (rhythm feel, guitar tone role, synth texture role) that define the genre.
- COMMON_FAILS:
  - too many anchors → clutter; too few → drift.

B2 — LEAF: Control sub-genre blending (safe fusion)
- OBSERVABLE_OUTCOME:
  - Fusion defined as “primary genre + secondary touch”, with limits (what must stay dominant).
- COMMON_FAILS:
  - equal blending → identity loss.

B3 — LEAF: Detect potential “catalog collision” risk signals (prompt-level)
- OBSERVABLE_OUTCOME:
  - Prompt avoids overly specific signature hooks/phrases; uses variability levers.
- COMMON_FAILS:
  - clones of prior patterns.

---

### BRANCH C — Vocal Differentiation (key weakness area)
C1 — LEAF: Define vocal roles per section
- OBSERVABLE_OUTCOME:
  - Prompt specifies who leads which section (rap vs melodic) and how contrast is maintained.
- COMMON_FAILS:
  - same voice everywhere; no role separation.

C2 — LEAF: Define delivery mode constraints (texture/attitude)
- OBSERVABLE_OUTCOME:
  - Clear delivery adjectives tied to behavior (clean/aggressive/whisper/chant) without being vague.
- COMMON_FAILS:
  - abstract mood words only.

C3 — LEAF: Prevent “same singer syndrome”
- OBSERVABLE_OUTCOME:
  - Prompt includes explicit diversity constraints (range, timbre contrast, call/response, formant-like descriptors as principles).
- COMMON_FAILS:
  - one vocalist feels cloned across tracks.

---

### BRANCH D — Anti-Repetition & Variation Engineering
D1 — LEAF: Phrase variation strategy for lyrics
- OBSERVABLE_OUTCOME:
  - Constraints that encourage line variation (avoid repeating same syntactic pattern; vary line length).
- COMMON_FAILS:
  - identical lines and rhymes repeating.

D2 — LEAF: Motif control (repeat with purpose)
- OBSERVABLE_OUTCOME:
  - Repetition allowed only for hook/chorus; verses constrained to novelty.
- COMMON_FAILS:
  - chorus-like repetition everywhere.

D3 — LEAF: “Patch prompt” minimal-change repair
- OBSERVABLE_OUTCOME:
  - A patch instruction that changes 1–2 axes only (e.g., vocals diversity + negative spec), leaving rest stable.
- COMMON_FAILS:
  - patch rewrites everything; loses identity.

---

### BRANCH E — QA-Driven Prompt Tuning
E1 — LEAF: Translate QA failure into prompt fix
- OBSERVABLE_OUTCOME:
  - For a given failed gate, propose a minimal edit plan and recheck step.
- COMMON_FAILS:
  - random changes not aligned to failure.

E2 — LEAF: Produce A/B prompt variants (one-axis changes)
- OBSERVABLE_OUTCOME:
  - 2–5 variants each changing only one axis (hook timing, vocal contrast, rhythm feel).
- COMMON_FAILS:
  - variants change everything; no learning.

E3 — LEAF: Prepare recheck protocol (what to listen for)
- OBSERVABLE_OUTCOME:
  - A short checklist of what must be verified in the next generation.
- COMMON_FAILS:
  - no recheck; loop repeats.

---

### BRANCH F — Trace & Compliance Discipline
F1 — LEAF: UID-only bindings discipline
- OBSERVABLE_OUTCOME:
  - All referenced knowledge is UID-only in bindings; no URL/PATH used as authority.
- COMMON_FAILS:
  - links pasted as “source of truth” inside pack.

F2 — LEAF: Provenance logging for external-derived tactics
- OBSERVABLE_OUTCOME:
  - If a tactic is borrowed, it is recorded in KB_SOURCES as extracted principle.
- COMMON_FAILS:
  - “best practice” asserted with no provenance.

---

## 3) SUPPORT TOPICS (UID-ONLY PLACEHOLDERS)
(Replace with real UIDs when those topic modules exist.)

SUPPORT_TOPICS_UID_ONLY:
- SOUND_MUSIC core:
  - UE.KB.README.TOPICS.SOUND_MUSIC.001 | WHY: realm scope
- Prompt craft:
  - UE.KB.SOUND.TOPIC.PROMPT_CONTRACT.??? | WHY: contract pattern module (future)
  - UE.KB.SOUND.TOPIC.NEGATIVE_SPEC_LIBRARY.??? | WHY: curated negatives (future)
- QA:
  - UE.KB.QA.STD.CONNECTOR.001 | WHY: QA workflow reference
  - UE.KB.SOUND.GATE.HOOK_TIMING.??? | WHY: hook timing gate (future)

---

## 4) SKILL TREE COMPLETENESS CHECK (FAST)
SKILLTREE_QA_FAST:
- [ ] responsibilities and forbidden actions listed
- [ ] each branch has leaf skills
- [ ] every leaf has observable outcome
- [ ] common fails noted for key leaves
- [ ] support topics listed (UID-only)

Result: PASS/REWORK/FAIL

---

## 5) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.STD.PRO_PACK.001 | WHY: pro pack structure requirements
- UE.KB.COV.SPC_PROFICIENCY.004 | WHY: L3 proficiency expectations
- UE.KB.RULE.ENTITIES.001 | WHY: boundaries and UID-only discipline

--- END.
