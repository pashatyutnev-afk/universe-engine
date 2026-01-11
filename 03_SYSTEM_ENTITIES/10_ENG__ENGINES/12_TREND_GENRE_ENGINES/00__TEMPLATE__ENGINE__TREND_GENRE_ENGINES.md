# Earworm Hook Stack Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 12_TREND_GENRE_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: TREND_GENRE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.TG.EARWORM_HOOK_STACK.001
OWNER: SYSTEM
ROLE: Designs earworm-grade hook materials (melodic, rhythmic, lyrical) as a controlled stack: short motifs + phrase hooks + repetition geometry + variation rules. Prevents dull looping and "AI spam repeats".

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined earworm hook stack: hook types, repetition geometry, variation grammar, and anti-annoyance gates."
- REASON: "We need hooks that stick without turning into low-quality repetition."
- IMPACT: "Higher retention + replay, better viral potential and UGC reuse."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.EARWORM.001

---

## 0) PURPOSE (LAW)
This engine manufactures **hook material** that:
- is instantly recognizable
- can repeat without becoming annoying
- survives remixing/UGC clipping
- stays consistent with the group style fingerprint

---

## 1) INPUTS (CONSUMES)
- Style Fingerprint (core anchors + timbre palette)
- Viral Hook Blueprint (hook timing + hook role)
- Audience Segment Target (attention span + preferred density)
- Lyrics source constraints (PD mosaic or original brief)
- Duration Policy (hook windows)
- Catalog Memory (avoid hook collisions)

---

## 2) OUTPUTS (PRODUCES)
- Earworm Hook Stack (EHS) — structured hook pack:
  - Hook A: Primary (main identity hook)
  - Hook B: Secondary (counter-hook or response)
  - Micro-hook(s): 1–3 short motifs (2–4 sec)
  - Phrase Hook(s): 1–2 lyrical “sticky lines” (if lyrics)
  - Rhythm Hook: a repeatable rhythm cell (drum/bass/clave)
  - Variation Rules (how to repeat without boredom)
  - Forbidden Patterns (what to avoid)
- Hook Timing Recommendations (where to place)
- Hook Test Checklist (quick QA gates)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Style Fingerprint",
  "Viral Hook Blueprint",
  "Audience Segment Target",
  "Duration Policy",
  "Lyrics constraints (optional)",
  "Catalog Memory"
]
PRODUCES: [
  "Earworm Hook Stack (EHS pack)",
  "Hook Timing Recommendations",
  "Hook Test Checklist"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/HOOKS/"

---

## 4) HOOK STACK STRUCTURE (EHS PACK)
The Earworm Hook Stack is always delivered in the same schema:

### 4.1 Hook A — Primary
- Type: melodic / lyric / rhythm / timbre
- Length intent: 4–8 sec
- Identity anchors: 1–2 (signature sound)
- Recognizable contour: describe simply (not music theory heavy)

### 4.2 Hook B — Secondary
- Role: response / lift / contrast / pre-hook
- Length: 2–6 sec
- Must NOT overshadow Hook A
- Designed for call-and-response potential

### 4.3 Micro-hooks (1–3)
- 2–4 sec “clip-worthy” moments
- can appear before main hook to prime recognition

### 4.4 Phrase Hooks (optional)
- 1–2 short sticky lines (6–10 words each)
- should be easy to quote, meme, subtitle
- must match RU phonetics (simple consonant flow)

### 4.5 Rhythm Hook
- repeatable rhythm cell (drums/bass) that supports hook identity
- avoid overcomplexity; must “bounce” quickly

### 4.6 Variation Rules (MANDATORY)
- repetition geometry and how to vary:
  - instrumentation swap
  - octave shift / texture change
  - call-response alternation
  - silence-drop trick (brief gaps)
  - rhythmic displacement (small offset)

### 4.7 Forbidden Patterns (MANDATORY)
- over-repeat of same phrase without variation
- too-long hook intro (>12 sec) for short-form targets
- “AI chant” (flat repeated syllables)
- random genre switch mid-hook
- muddy mix hiding the hook

---

## 5) EARWORM PRINCIPLES (STRICT)
1) **One dominant identity hook** per track.
2) **Recognition > novelty** in hook core; novelty lives in arrangement.
3) **Repeatable without boredom**: repeat + micro-variation.
4) **Phonetic stickiness** (RU): clear vowels, punchy consonants.
5) **Rhythm supports the hook**, not competes.

---

## 6) REPETITION GEOMETRY (ANTI-ANNOYANCE)
Allowed repetition patterns:
- A / A’ / A (small timbre change)
- A / B / A
- A / A / Drop / A (silence + comeback)
- A (short) + A (full)

Hard limits:
- same exact hook phrase repeated > 3 times back-to-back → FAIL
- same exact melodic contour without variation across 2 full sections → SOFT FAIL

---

## 7) HOOK TYPES (TOOLBOX)
The engine may choose one or combine two:
- Melodic hook (lead vocal/synth)
- Lyric hook (catch line)
- Timbre hook (signature sound texture)
- Rhythm hook (drum groove / bass bounce)
- Harmony hook (distinct chord move — only if fits style)

Rule:
- never stack more than 2 hook types as “primary” (avoid clutter)

---

## 8) AUDIENCE SEGMENT ADAPTATION (FAST RULES)
If segment expects short-form virality:
- hook should appear early (≤ 20 sec)
- micro-hook within first 10 sec recommended

If segment tolerates longer build:
- micro-hook early, full hook later (≤ 40 sec)

The engine only sets intent; Duration Policy finalizes target.

---

## 9) COLLISION AVOIDANCE (CATALOG MEMORY)
Before finalizing:
- compare Hook A contour + phrase hooks against known catalog memory
- if collision risk: change 1 axis only (timbre OR rhythm OR phrase)

---

## 10) HOOK TEST CHECKLIST (POST-GEN)
Quick checks:
1) 10-second recognition test: is the hook obvious by 0:10?
2) 15-second loop test: does it stay pleasant on loop?
3) Quote test: can a viewer type the hook line easily (if lyrics)?
4) Distinctiveness: does it sound like “us” (group identity anchors)?
5) Repeat guard: no “AI spam repeats”

---

## 11) FAILURE MODES & FIX
1) Hook not sticky (forgettable)
- Fix: simplify contour, reduce notes, increase rhythmic clarity, add one phrase hook.

2) Hook annoying
- Fix: reduce repetition, apply A/A’/A geometry, add silence-drop, swap instrumentation.

3) Hook buried in mix
- Fix: force “hook forward” mix directive; reduce competing layers.

4) Hook clashes with style fingerprint
- Fix: re-anchor timbre palette and remove off-style tags.

---

## 12) HANDOFFS (XREF)
Feeds into:
- `12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md`
- `12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md`
- `12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md`
- `60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md`
- `60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
