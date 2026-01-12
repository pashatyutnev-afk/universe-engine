# Take Log Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.MF.TAKE_LOG.001
OWNER: SYSTEM
ROLE: Captures every generation attempt (“take”) with minimal but sufficient metadata:
what was requested, what was produced, gate results, collisions, and next actions.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Take Log Engine: take record schema, pass/fail gates, and catalog memory integration."
- REASON: "Without a take log, the system repeats itself and cannot learn what works."
- IMPACT: "Deterministic memory, anti-repeat, and scalable hit-making analytics."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.TAKE_LOG.001
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; no semantic changes."
- REASON: "Compressed formatting is error-prone during edits."
- IMPACT: "Safer copy/paste; easier audits."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.TAKE_LOG.002

---

## 0) PURPOSE
Take Log is the operational memory of Music Factory:
- records every attempt (even rejected) in a lightweight way
- stores “why it worked / why it failed”
- prevents repeating the same hook/intro/fingerprint patterns
- feeds portfolio planning and audience targeting

This is not a full database spec — it’s a deterministic text record standard.

---

## 1) INPUTS (CONSUMES)
- Group DNA Spec reference
- Album Blueprint slot reference (if applicable)
- Track Candidate Pack reference (variant ID)
- Prompt Package (final used)
- Gate result (“зашло?” / “развиваем?”)
- Collision Report (if run)
- QA/VAL snapshot

---

## 2) OUTPUTS (PRODUCES)

### Primary
- **Take Log Record** (single record per attempt)

### Secondary
- **Catalog Memory Update Note**
  - what to add to memory: fingerprint, hook grammar, title candidates
- **Learning Signals**
  - simple tags: why it worked

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group/Album/Track references",
  "Prompt Package used",
  "Gate result (liked? develop?)",
  "Collision Report (optional)",
  "QA/VAL snapshot (optional)"
]
PRODUCES: [
  "Take Log Record",
  "Catalog Memory Update Note",
  "Learning Signals"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS//CATALOG/TAKES/"

---

## 4) TAKE LOG RECORD — STANDARD (MANDATORY FIELDS)
Each record must include:

### A) Identity
- TAKE_ID:
- DATE:
- GROUP_ID:
- ALBUM_ID:
- TRACK_ID:
- VARIANT_ID:

### B) What was asked
- TRACK_ROLE:
- STYLE_TAGS_USED:
- DURATION_TARGET:
- LEAD_PERSONA:
- HOOK_INTENT: <1 line>
- UGC_WINDOW:

### C) What happened
- GENERATOR:
- OUTPUT_LINK:
- NOTES:

### D) Gates (the most important)
- GATE_LIKED:
- GATE_DEVELOP:
- WHY_LIKED / WHY_REJECTED:
- NEXT_ACTION:

### E) Collision & Differentiation
- COLLISION_STATUS:
- COLLISION_VECTORS:
- MUTATION_APPLIED:

### F) QA/VAL Snapshot (short)
- PROMPT_FIDELITY:
- UGC_READY:
- HOOK_TIMING:
- LOOP_QA:

### G) Memory update payload (compact)
- FINGERPRINT_ANCHORS: <3–8 anchor tokens>
- HOOK_GRAMMAR_TOKEN:
- INTRO_SIGNATURE_TOKEN:
- TITLE_CANDIDATES:
- PD_FRAGMENTS_USED:

---

## 5) RECORD SIZE RULE (ANTI-BLOAT)
- Keep each record short (target: 25–60 lines max).
- Do NOT paste full lyrics/audio; store references and tokens only.
- Full prompts may be stored only for “winners”; otherwise store “delta summary”.

---

## 6) WORKFLOW (OPERATIONAL STEPS)
1) After each generation attempt, create a record.
2) If rejected: record minimal fields + reason.
3) If liked: record full gate info + next action.
4) If develop=YES: attach docs checklist pointer from Track Factory.
5) Push memory update tokens to Catalog Memory CTL storage.

---

## 7) FAILURE MODES & FIXES
1) People forget to log  
- Fix: Track Factory output must always end with “TAKE LOG REQUIRED” block.

2) Logs become too big  
- Fix: enforce record size rule; move long text into track docs only after approval.

3) Memory tokens inconsistent  
- Fix: normalize tokens (same naming scheme for anchors/grammar/signature).

---

## 8) HANDOFFS (XREF)
Feeds:
- `20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md`
- `11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md`

---

## 9) OUTPUT PACK (MANDATORY LIST)
1) Take Log Record (per attempt)
2) Memory update tokens (compact)
3) Learning signals (why it worked / why failed)
4) Next action directive (what pipeline step runs next)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
