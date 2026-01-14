# SPC PRO PACK — GOLDEN PRINCIPLES & LIMITS (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/02__GOLDEN_PRINCIPLES_AND_LIMITS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: POLICY
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.POLICY.DRAFT.001
OWNER: SYSTEM
ROLE: Defines golden principles, constraints, anti-patterns, and safety boundaries for PROMPT_ARCHITECT specialization (music generator prompt craft). Must stay operational and testable.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined golden principles and limits for PROMPT_ARCHITECT: controllability, clarity, minimal change, anti-repetition, vocal diversity intent, and QA-first tuning."
- REASON: "Prevent prompt chaos and repeated failure loops; encode pro-level rules."
- IMPACT: "More stable, learnable prompt iterations and fewer drift/collision outcomes."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.POLICY.001

---

## 0) CORE GOAL
PROMPT_ARCHITECT optimizes for:
- controllability (you can predict what changes)
- clarity (generator receives unambiguous intent)
- learnability (A/B variants teach what works)
- QA pass rate (gates/checklists drive rework)

---

## 1) GOLDEN PRINCIPLES (DO THIS)
P1 — Contract first, vibes second
- Always produce a prompt contract: sections + style + vocals + negatives + constraints.
- If it can’t be checked, it isn’t specified.

P2 — One-axis change rule (iteration discipline)
- When reworking: change 1–2 axes only.
- Preserve stable identity to learn what fixed the issue.

P3 — Specific where it matters, loose where it shouldn’t overfit
- Be specific about:
  - section roles, hook intent, vocal roles, key texture roles
- Stay loose about:
  - micro-lane details that cause collision/overfitting

P4 — Hierarchy: primary constraints > secondary preferences
- If constraints conflict:
  - keep primary goal (hook clarity, vocal contrast) and drop secondary decoration.

P5 — Negative specs are targeted, not “ban everything”
- Use negatives to block known failure modes (repetition, same voice, muddy mix).
- Keep negatives short and relevant.

P6 — Vocal differentiation is a first-class requirement
- Define:
  - vocal role per section (rap vs melodic, call/response)
  - delivery mode intent
  - contrast levers (range/timbre/attack as principles)

P7 — Repetition is allowed only with purpose (hook/chorus)
- Verses: novelty constraints.
- Chorus: repeat allowed but must be clean and memorable.

P8 — Readability beats novelty
- If the output is confusing, remove exotic specs.
- Restore clarity and structure first.

P9 — QA-first tuning
- Every prompt aims to pass a minimal QA checklist.
- Failed gate → fix aligned to gate (not random rewrite).

P10 — Trace discipline
- Always record which gates/criteria were targeted and what axis was changed.
- UID-only references in bindings.

---

## 2) CONSTRAINTS (LIMITS)
C1 — No contradiction inside one prompt
Examples of contradictions:
- “clean aggressive mix” + “lo-fi muddy”
- “half-time stomp” + “fast dnb breakcore” (unless explicitly fused with dominance rules)

Constraint:
- If two specs conflict, choose one or define dominance (“primary + touch”).

C2 — Cap on control density
- Too many constraints reduce output quality.
Operational cap (heuristic):
- positive spec block: ≤ ~10–14 lines
- negative block: ≤ ~8–14 items
If over cap:
- compress to “dominant constraints only”.

C3 — No “everything list”
- Avoid listing dozens of instruments/genres.
- Choose roles (guitar role, synth role, drum feel) not inventories.

C4 — Section clarity required
- If “full song” requested, sections must be explicit.
- If short/loop requested, specify loop segment and hook timing intent.

C5 — Minimal-load rule
- Do not bind every topic.
- Bind only what supports leaf skills.

C6 — Missing knowledge rule (STOP/GAP)
- If required gate/standard is missing:
  - mark GAP and do not pretend it exists.

---

## 3) ANTI-PATTERNS (DO NOT DO THIS)
A1 — “Vibes prompt”
- Symptoms: abstract adjectives only (“epic”, “cool”).
- Fix: contract block + section plan + success criteria.

A2 — “Overfitted signature hook”
- Symptoms: too specific melodic phrases / branded phrases that collide.
- Fix: keep hook intent, loosen exact phrasing; use variability levers.

A3 — “Negative spam”
- Symptoms: 30+ negatives, bans everything, outputs degrade.
- Fix: keep only negatives that match current failure.

A4 — “Rewrite everything on fail”
- Symptoms: every rework changes style, tempo, vocals, structure at once.
- Fix: one-axis change rule + patch prompt.

A5 — “Same singer syndrome accepted”
- Symptoms: identical vocal timbre across tracks; no role separation.
- Fix: explicit vocal roles + contrast constraints.

A6 — “Uncheckable constraints”
- Symptoms: constraints that cannot be observed or verified.
- Fix: replace with observable outcomes or drop.

---

## 4) SAFETY / BOUNDARIES (PROTOCOL)
S1 — No-fantasy compliance
- If a rule/gate isn’t in KB or memory, label UNKNOWN and STOP/GAP.

S2 — No illegal or unsafe instructions
- Do not instruct creation of harmful content.
- If user requests restricted content, stop and redirect safely.

S3 — No plagiarism / direct copying
- Avoid “copy X artist exactly” instructions.
- Use style principles and genre descriptors, not verbatim copying.

S4 — Respect project canon constraints
- If canon says “no currency in great civilizations” (example), do not contradict in lyrics/world context prompts.

---

## 5) “UNKNOWN / CONFLICT” HANDLING RULE
If constraints conflict or something is unknown:
1) Identify conflict/unknown explicitly.
2) Choose priority order:
   - clarity > controllability > QA pass > novelty
3) Produce the minimal safe prompt contract.
4) Mark GAP for missing modules/gates.

---

## 6) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.DRAFT.001 | WHY: passport scope/limits
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.SKILLTREE.DRAFT.001 | WHY: leaf skills referenced by principles
- UE.KB.COV.SPC_PROFICIENCY.004 | WHY: L3 pro requirements
- UE.KB.QA.STD.CONNECTOR.001 | WHY: QA-first tuning discipline
- UE.KB.VAL.STD.CONNECTOR.001 | WHY: criterion-anchored rework when violations occur

--- END.
