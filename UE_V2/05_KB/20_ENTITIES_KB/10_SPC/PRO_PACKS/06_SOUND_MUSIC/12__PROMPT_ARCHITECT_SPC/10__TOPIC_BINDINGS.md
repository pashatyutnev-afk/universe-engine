# SPC PRO PACK — TOPIC BINDINGS (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/10__TOPIC_BINDINGS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOPIC_BINDINGS
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.1
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.BINDINGS.DRAFT.001
OWNER: SYSTEM
ROLE: Deterministic “what to load” map for PROMPT_ARCHITECT: minimal KB topics + operational CTL policies + pack gates/checklists to prevent hallucination and keep prompt compilation consistent.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: PATCH
- SUMMARY: "Bound real operational CTL UIDs (prompt contract, duration, UGC, negative packs, catalog memory, audience segments). Kept KB topic placeholders as GAP until KB topics exist."
- REASON: "This pack must rely on real, non-fiction policy sources where available."
- IMPACT: "Less guessing, stronger determinism, better prompt pack consistency."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.PROMPT.BIND.002

---

## 0) STRICT RULES
- UID-only binding. No PATH/URL used as authority.
- If a KB module/topic does not exist yet → keep as PLACEHOLDER and treat as GAP during execution.
- This file defines loading guidance, not navigation authority.

---

## 1) CORE OPERATIONAL POLICIES (REAL / REQUIRED) — UID-ONLY
These are non-fiction operational constraints that PROMPT_ARCHITECT must follow.

CORE_CTL_UIDS_REQUIRED:
- UE.CTL.MUS.PROMPT_CONTRACT.001
  WHY: mandatory prompt pack schema + limits + prohibited patterns

- UE.CTL.MUS.DURATION_POLICY.001
  WHY: duration modes (SHORT/FULL/ALT_INTRO) + hook timing windows + section budgets

- UE.CTL.MUS.UGC_VIRAL_RULESET.001
  WHY: clip windows + edit points + early recognition for UGC variants

- UE.CTL.MUS.NEGATIVE_SPEC_LIBRARY.001
  WHY: reusable negative packs + anti-bloat rules (avoid “wall of negatives”)

- UE.CTL.MUS.CATALOG_MEMORY.001
  WHY: anti-repeat/collision memory tokens usage rules (read-before-produce)

- UE.CTL.MUS.AUDIENCE_SEGMENTS.001
  WHY: segment-driven constraints (hook formats / tone / duration bias / avoid-mismatches)

---

## 2) PACK-INTERNAL QUALITY LAYER (REQUIRED) — UID-ONLY
These are produced inside this Pro Pack and always available during use.

PACK_GATES_UIDS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001

PACK_CHECKLISTS_UIDS:
- UE.KB.SPC.CHK.PROMPT_ARCHITECT.READINESS.001
- UE.KB.SPC.CHK.PROMPT_ARCHITECT.QUALITY.001
- UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001

PACK_RUBRIC_UID:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.RUBRIC.DRAFT.001

---

## 3) KB TOPICS (DESIRED / CURRENTLY GAP) — UID-ONLY PLACEHOLDERS
These are “world knowledge” modules that should exist under KB TOPICS. If missing: treat as GAP and do not pretend.

KB_TOPICS_PLACEHOLDERS:
- PLACEHOLDER_UID: UE.KB.README.TOPICS.SOUND_MUSIC.001
  GAP: sound/music topics realm README not bound here yet

- PLACEHOLDER_UID: UE.KB.SOUND.TOPIC.STYLE_FINGERPRINT_CONTROL.001
  GAP: style fingerprint topic module not yet bound

- PLACEHOLDER_UID: UE.KB.SOUND.TOPIC.VOCAL_DIVERSITY_INTENT.001
  GAP: vocal diversity topic module not yet bound

- PLACEHOLDER_UID: UE.KB.SOUND.TOPIC.REPEAT_GUARD_METHOD.001
  GAP: repetition control topic module not yet bound

- PLACEHOLDER_UID: UE.KB.SOUND.TOPIC.PROMPT_CONTRACT_METHODS.001
  GAP: prompt craft topic module not yet bound

NOTE:
- Do NOT convert these placeholders into rules.
- Only treat them as future KB anchors.

---

## 4) LOAD PROFILES (WHAT TO LOAD PER TASK)
### PROFILE A — BUILD FROM SCRATCH (PB-01)
LOAD:
- CORE_CTL_UIDS_REQUIRED (all)
- Pack checklists: READINESS + QUALITY
- Gates: at minimum Gate 01; then Gate 02/03/04 as relevant

### PROFILE B — DIAGNOSE & REWORK (PB-03/PB-04)
LOAD:
- CORE_CTL_UIDS_REQUIRED (all)
- Gate 01 + the failed gate(s)
- Compliance checklist (trace + one-axis discipline)
- Regression guard only if rules/templates changed

### PROFILE C — UGC/SHORT VARIANTS (PB-02 + PB-08)
LOAD:
- UE.CTL.MUS.DURATION_POLICY.001 (mandatory)
- UE.CTL.MUS.UGC_VIRAL_RULESET.001 (mandatory)
- UE.CTL.MUS.PROMPT_CONTRACT.001
- UE.CTL.MUS.NEGATIVE_SPEC_LIBRARY.001
- Gates: 01 + 03 + 04 (+02 if vocals relevant)

### PROFILE D — ANTI-REPEAT / COLLISION AVOIDANCE (PB-06 + memory discipline)
LOAD:
- UE.CTL.MUS.CATALOG_MEMORY.001 (mandatory)
- UE.CTL.MUS.NEGATIVE_SPEC_LIBRARY.001 (NO_ENDLESS_REPEAT pack usage)
- Gate 03 (repetition intent) + Gate 05 (discipline if iterating)

### PROFILE E — SEGMENT-TARGETED HOOKS (audience-driven)
LOAD:
- UE.CTL.MUS.AUDIENCE_SEGMENTS.001 (mandatory)
- UE.CTL.MUS.DURATION_POLICY.001
- UE.CTL.MUS.UGC_VIRAL_RULESET.001 (if UGC)
- Gates: 01 + 04 (+02/+03 depending on vocals/lyrics)

---

## 5) OUTPUT TRACE (REQUIRED)
Every run must record:
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO
- CTL_UIDS_APPLIED (UID-only list)
- GATES_RUN (UID-only list)
- GAPS (placeholders encountered)

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- a placeholder UID is treated as real knowledge during execution
- CTL policies are ignored while claiming compliance
- outputs are produced without trace flags and applied-UID list

--- END.
