# Track Factory Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md

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
UID: UE.ENG.MF.TRACK_FACTORY.001
OWNER: SYSTEM
ROLE: Produces 2–5 track variants per blueprint slot, optimized for prompt fidelity + hooks + UGC loops, then runs a “test-first → docs-if-approved” gate.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Track Factory Engine: variant generation, prompt package, test gate, and documentation request flow."
- REASON: "We must iterate fast without bloating the system; docs only for winners."
- IMPACT: "Higher hit-rate, reduced clutter, deterministic iteration."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.TRACK_FACTORY.001

---

## 0) PURPOSE
This engine creates track candidates for a given album slot:
- builds a **Track Brief** (what the track must do)
- compiles a **Prompt Package** aligned with platform (e.g., Suno)
- generates multiple **Variants** (2–5) with distinct hook strategies
- evaluates quickly via validators/QA gates
- outputs a **single recommended full prompt** + short alt options
- asks user: **“develop this track?”** and only then triggers docs checklist

This engine is the operational bridge between system design and generator execution.

---

## 1) INPUTS (CONSUMES)
- Album Blueprint Spec (track slot record)
- Group DNA Spec (style + constraints)
- Artist Roster Spec (who leads / timbre palette)
- UGC/Viral policy CTL
- Prompt Contract CTL
- Negative Spec library CTL
- PD poem strategy (if lyrics mode uses poets)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- **Track Candidate Pack** (variants + one recommended variant)

Secondary:
- **Suno Prompt Package** (ready to paste)
- **Quick Evaluation Notes** (why variant A is best)
- **Docs Request Checklist** (only if user approves)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Album Blueprint Slot",
  "Group DNA Spec",
  "Artist Roster Spec",
  "UGC Viral Ruleset CTL",
  "Prompt Contract CTL",
  "Negative Spec Library CTL",
  "Poet/PD Strategy (optional)"
]
PRODUCES: [
  "Track Candidate Pack",
  "Suno Prompt Package (recommended)",
  "Alt Variant Notes",
  "Test Gate Result",
  "Docs Request Checklist (conditional)"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/06__HOOK_PANEL_QA.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/GROUPS/<GROUP_ID>/ALBUMS/<ALBUM_ID>/TRACKS/<TRACK_ID>/"

---

## 4) TRACK BRIEF MODEL (MANDATORY)
Each candidate must have a brief with:

- TRACK_ID
- TRACK_ROLE (from album blueprint)
- PROMISE (1 sentence: what listener gets)
- MOOD + ENERGY CURVE
- TEMPO WINDOW (or groove label)
- HOOK DESIGN:
  - hook phrase idea (RU)
  - hook timing intent
  - earworm mechanics (repeat grammar)
- UGC LOOP WINDOW:
  - start second, end second, what repeats
- PERFORMER PLAN:
  - lead persona
  - support persona(s)
  - instrument hook owner
- LYRICS MODE:
  - PD_ONLY / PD_PLUS_PATCHES / ORIGINAL
- NEGATIVE SPEC (top 8–15 avoid items)
- SUCCESS CRITERIA (3–6 bullets)

---

## 5) VARIANT STRATEGY (2–5 VARIANTS)
Variants must differ by at least 2 axes:
- hook placement (early / delayed / double hook)
- hook type (phrase / melody / rhythm / call-response)
- groove choice (straight / swing / half-time)
- arrangement density (minimal vs dense)
- vocalist delivery (clean vs raspy vs whispery)
- instrumentation lead (guitar vs synth vs folk)

Variant naming:
- V1: “Direct Viral Hook”
- V2: “Story + Hook”
- V3: “Rhythm Hook”
- V4: “Contrast/Experimental” (optional)
- V5: “Minimal earworm loop” (optional)

---

## 6) SUNO PROMPT PACKAGE (OPERATIONAL OUTPUT)
The engine must output in Suno-ready structure:

A) TITLE (working title; can be placeholder)
B) STYLE TAGS (concise, concrete)
C) INSTRUMENTATION (key instruments)
D) VOCAL DESCRIPTION (delivery, register)
E) STRUCTURE (intro/verse/pre/chorus/bridge/outro)
F) LYRICS (RU; with hook phrase repetition)
G) NEGATIVE SPEC (avoid list, if platform supports)
H) DURATION TARGET (range)

IMPORTANT:
- Keep style tags short (avoid essays).
- Control drift by explicit “do/don’t”.
- If PD lyrics are used: mention “based on public-domain fragments” (no author claim).

---

## 7) TEST GATE (FAST EVALUATION)
After generation (user runs it on platform), the system asks:

### Gate Question 1 — “ЗАШЛО?”
- If NO: discard / log only minimal record, propose next variant.
- If YES: proceed to documentation request checklist.

### Gate Question 2 — “РАЗВИВАЕМ?”
Options:
- A) Keep base, improve hook
- B) Keep hook, improve arrangement
- C) Keep vibe, change vocal delivery
- D) Make short UGC cut first
- E) Make full release first

Validators/QA to consult (lightweight):
- PROMPT_FIDELITY_VAL (was output close to brief?)
- UGC_READY_VAL
- HOOK_PANEL_QA
- LOOP_15S_QA (if short cut)

---

## 8) DOCS REQUEST CHECKLIST (CONDITIONAL)
Only if user says “ДА, РАЗВИВАЕМ”:
Create/queue docs list:

Required docs for a winning track:
1) Track Passport (ID, role, version, status)
2) Prompt Pack (final prompt + deltas from earlier)
3) Lyrics Source Note (PD fragments used + transformation notes)
4) Hook Map (phrase + timing + loop window)
5) Release Variants Plan (short/main/alt)
6) QA/VAL Results snapshot
7) Credits/Metadata draft (policy-controlled)

If user says “НЕТ”:
- store only minimal Take Log entry (variant id + reason rejected).

---

## 9) FAILURE MODES & FIXES
1) **Prompt drift (platform adds own stuff)**
- Fix: tighten style tags + add stronger negative spec + shorten instructions.

2) **Hook not sticky**
- Fix: apply earworm stack rules; repeat grammar; hook earlier.

3) **Lyrics sound “machine”**
- Fix: use PD fragments “juice”; tighten rhyme/meter; simplify language.

4) **Tracks start identical across catalog**
- Fix: enforce different intros; rotate lead instrument; change first 10 seconds signature.

---

## 10) HANDOFFS (XREF)
NEXT ORC:
- `20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md`

NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md`

REQUIRED CTL:
- `01__PROMPT_CONTRACT_CTL`
- `02__UGC_VIRAL_RULESET_CTL`
- `12__NEGATIVE_SPEC_LIBRARY_CTL`

REQUIRED VAL/QA:
- `08__PROMPT_FIDELITY_VAL`
- `02__UGC_READY_VAL`
- `01__HOOK_TIMING_VAL`
- `06__HOOK_PANEL_QA`
- `02__LOOP_15S_QA`

---

## 11) OUTPUT PACK (MANDATORY LIST)
Always output:
1) Track Brief (per variant)
2) 2–5 Variant Summaries (short)
3) ONE full recommended Suno Prompt Package (complete)
4) Quick evaluation rationale (why recommended)
5) Gate questions (ЗАШЛО? / РАЗВИВАЕМ?)
6) Conditional docs checklist (only if “ДА”)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
