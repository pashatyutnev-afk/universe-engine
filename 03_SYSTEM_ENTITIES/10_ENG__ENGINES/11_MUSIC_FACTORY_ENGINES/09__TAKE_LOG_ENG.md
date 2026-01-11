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
VERSION: 1.0.0
UID: UE.ENG.MF.TAKE_LOG.001
OWNER: SYSTEM
ROLE: Captures every generation attempt (“take”) with minimal but sufficient metadata: what was requested, what was produced, gate results, collisions, and next actions.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Take Log Engine: take record schema, pass/fail gates, and catalog memory integration."
- REASON: "Without a take log, the system repeats itself and cannot learn what works."
- IMPACT: "Deterministic memory, anti-repeat, and scalable hit-making analytics."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.TAKE_LOG.001

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
Primary:
- **Take Log Record** (single record per attempt)

Secondary:
- **Catalog Memory Update Note** (what to add to memory: fingerprint, hook grammar, title candidates)
- **Learning Signals** (simple tags: why it worked)

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
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/CATALOG/TAKES/"

---

## 4) TAKE LOG RECORD — STANDARD (MANDATORY FIELDS)
Each record must include:

### A) Identity
- TAKE_ID: <date-time + short hash style>
- DATE: <YYYY-MM-DD>
- GROUP_ID:
- ALBUM_ID: <optional>
- TRACK_ID: <optional>
- VARIANT_ID: <V1/V2/...>

### B) What was asked
- TRACK_ROLE:
- STYLE_TAGS_USED: <short list>
- DURATION_TARGET:
- LEAD_PERSONA:
- HOOK_INTENT: <1 line>
- UGC_WINDOW: <if any>

### C) What happened
- GENERATOR: <SUNO|UDIO|...>
- OUTPUT_LINK: <optional>
- NOTES: <what came out>

### D) Gates (the most important)
- GATE_LIKED: <YES/NO>
- GATE_DEVELOP: <YES/NO>
- WHY_LIKED / WHY_REJECTED: <bullets>
- NEXT_ACTION: <discard / revise / regenerate / doc-pack / release-pack>

### E) Collision & Differentiation
- COLLISION_STATUS: <PASS/SOFT/HARD/NOT_RUN>
- COLLISION_VECTORS: <if any>
- MUTATION_APPLIED: <if any>

### F) QA/VAL Snapshot (short)
- PROMPT_FIDELITY: <PASS/FAIL/NR>
- UGC_READY: <PASS/FAIL/NR>
- HOOK_TIMING: <PASS/FAIL/NR>
- LOOP_QA: <PASS/FAIL/NR>

### G) Memory update payload (compact)
- FINGERPRINT_ANCHORS: <3–8 anchor tokens>
- HOOK_GRAMMAR_TOKEN: <short token>
- INTRO_SIGNATURE_TOKEN: <short token>
- TITLE_CANDIDATES: <if any>
- PD_FRAGMENTS_USED: <if any; short>

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
