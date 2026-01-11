# Artist Factory Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/02__ARTIST_FACTORY_ENG.md

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
UID: UE.ENG.MF.ARTIST_FACTORY.001
OWNER: SYSTEM
ROLE: Constructs a deterministic roster of “Artists” (voices + instrumental personas + producer persona) with style contracts, ranges, and signature behaviors.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Artist Factory Engine: member contracts for vocalist/instrumentalist/producer, timbre identities, constraints, and diversity control."
- REASON: "Groups must have repeatable, non-random performers to prevent drift and enable scaling."
- IMPACT: "Consistent artist identity across albums/tracks; controllable voice/instrument variety."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.ARTIST_FACTORY.001

---

## 0) PURPOSE
This engine turns **Group DNA** into a concrete **cast roster**:
- vocal personas (lead / backing / rap-chant / choir)
- instrumental personas (lead guitar / synth lead / bass / drums / folk instruments etc.)
- producer persona (arrangement taste + mix aesthetic)
- “signature techniques” + “no-go rules” per member
- diversity rules (avoid same vocal timbre across groups; avoid same instrument patterns)

This is not “real people”. This is a **contracted identity** used to steer AI generation.

---

## 1) INPUTS (CONSUMES)
- Group DNA Spec (from `01__GROUP_FOUNDATION_ENG`)
- Style Fingerprint anchors (from trend/style engines)
- Prompt Contract constraints (CTL)
- Voice diversity policy (VAL/QA reference)
- Optional: platform constraints (short/long format guidance)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- **Artist Roster Spec** (canonical list of performers and personas)

Secondary:
- **Performer Contracts Pack** (one contract per persona)
- **Timbre Palette Map** (what sonic colors belong to whom)
- **Role Boundaries Matrix** (who owns what space, to reduce clashes)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group DNA Spec",
  "Style Fingerprint Anchors",
  "Prompt Contract CTL",
  "Voice Diversity Rules (VAL/QA)",
  "Format Constraints (optional)"
]
PRODUCES: [
  "Artist Roster Spec",
  "Performer Contracts Pack",
  "Timbre Palette Map",
  "Role Boundaries Matrix"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/09__VOCAL_PERFORMANCE_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/08__ARRANGEMENT_INSTRUMENTATION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/GROUPS/<GROUP_ID>/CAST/"

---

## 4) MEMBER MODEL (STANDARD)
Each persona must be described by the following schema (text form, no JSON required):

### A) Identity
- ARTIST_ID: <short stable id>
- ROLE_TYPE: <VOCALIST|INSTRUMENTALIST|PRODUCER>
- ROLE: <lead / backing / rhythm / texture / hook-driver / etc>
- SIGNATURE_LINE: <1 sentence: who is this persona>

### B) Style Contract
- STYLE_TAGS: <5–14 tags max; concrete, no fluff>
- DO: <3–8 rules>
- DONT: <3–10 rules>
- SIGNATURE_TECHNIQUES: <2–6 techniques>
- ENERGY_RANGE: <low/med/high + curve note>

### C) Range / Register (for vocals) OR Range / Space (for instruments)
VOCALS:
- REGISTER: <low/mid/high>
- DELIVERY: <soft/breathy/raspy/power/clean>
- ARTICULATION: <tight/loose/legato/staccato>
- ACCENT: <if needed; RU by default neutral>

INSTRUMENTS:
- TIMBRE: <clean/crunch/analog/warm/metallic/etc>
- SPACE_OWNERSHIP: <low/mid/high + stereo note>
- RHYTHMIC_ROLE: <driver/ornamentation/pulse>
- MOTIF_BEHAVIOR: <repeats? evolving? call-response?>

### D) Hook Responsibilities
- HOOK_OWNER: <YES/NO>
- HOOK_GRAMMAR: <how this persona builds repeats/catches>

### E) Collision Guards
- AVOID_PATTERNS: <what makes it too similar to existing catalog>
- UNIQUENESS_ANCHOR: <the one thing that is “only us”>

---

## 5) WORKFLOW (OPERATIONAL STEPS)
1) **Choose roster size**
   - Minimum recommended: 3 personas
     - 1 vocal identity
     - 1 rhythm identity
     - 1 texture identity
   - Typical: 5–7 personas (for richer catalog scaling)

2) **Assign roles**
   - Hook-driver (may be vocal or instrument)
   - Groove driver (drums/bass)
   - Texture (pads/strings/guitars)
   - Contrast color (folk instrument / synth texture / percussive hook)

3) **Build vocalist personas**
   - Define 1–2 vocalists max for clarity.
   - Optional: rap/chant persona only if style demands.
   - Lock language handling: RU.

4) **Build instrumental personas**
   - At least 2:
     - rhythm foundation (drums+bass behavior)
     - hook or texture instrument (guitar/synth)
   - Optional: signature “rare instrument” persona for uniqueness.

5) **Build producer persona**
   - Arrangement taste: dense vs minimal, retro vs modern.
   - Mix aesthetic: dry/close vs wide/atmo, punch vs smooth.

6) **Role boundaries matrix**
   - Ensure no two personas own the same hook space.
   - Ensure low/mid/high coverage is balanced.

7) **Diversity check**
   - Compare to group catalog memory:
     - vocal timbre collisions
     - instrument motif collisions
   - If conflict: mutate at least 1 vocalist delivery + 1 instrument timbre.

---

## 6) IMPORTANT CLARIFICATION (YOUR QUESTION)
Yes, **this applies to musicians too, not only the singer**.
- Instruments have “style” (timbre, groove, motif behavior, arrangement habits).
- Producer has “style” (mix taste, dynamics, stereo, density).
This engine makes that explicit so tracks don’t become random.

---

## 7) FAILURE MODES & FIXES
1) **Vocal same-everywhere syndrome**
- Fix: change DELIVERY + REGISTER + articulation + hook grammar.

2) **Instrumental mush (no separation)**
- Fix: enforce SPACE_OWNERSHIP + role boundaries matrix.

3) **AI adds extra random instruments**
- Fix: tighten negative specs + define “allowed palette” clearly.

4) **Hook is weak / no earworm**
- Fix: assign explicit HOOK_OWNER and hook grammar; escalate to earworm stack engine.

---

## 8) HANDOFFS (XREF)
NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`

REQUIRED CTL:
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md`

REQUIRED VAL/QA:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md`
- `60_QA__QUALITY/10_MUSIC_QA/08__VOICE_DIVERSITY_AUDIT_QA.md`

---

## 9) OUTPUT PACK (MANDATORY LIST)
1) Artist Roster Spec
2) Performer Contracts Pack (one per persona)
3) Timbre Palette Map
4) Role Boundaries Matrix
5) Diversity Check Note (pass/fail + mutations)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
