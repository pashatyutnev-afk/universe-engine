# UGC Moment Map Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md

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
UID: UE.ENG.TG.UGC_MOMENT_MAP.001
OWNER: SYSTEM
ROLE: Designs UGC-ready micro-moments for a track: clip windows, quote lines, beat drops, transitions, and creator-use cases. Ensures the song is "content-friendly" without sacrificing artistry.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined UGC Moment Map: moment types, time windows, creator use-cases, and enforcement rules."
- REASON: "We need tracks that creators want to use (clips, memes, shorts, edits)."
- IMPACT: "Higher reuse, virality, and platform distribution efficiency."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.UGC.MAP.001

---

## 0) PURPOSE (LAW)
This engine produces a **UGC Moment Map (UMM)** — a structured plan of moments that:
- are easy to clip (5–15 sec)
- have obvious “sync points” for editing
- include quote-ready phrases (if lyrics)
- create multiple creator scenarios (comedy, vibe, flex, storytime, edits)

---

## 1) INPUTS (CONSUMES)
- Viral Hook Blueprint (hook timing + hook role)
- Earworm Hook Stack (primary/secondary/microhooks)
- Duration Policy (target length and hook windows)
- Audience Segment Target (creator behavior + attention span)
- Style Fingerprint (identity anchors)
- Release Variants plan (short/long versions, alt intros)

---

## 2) OUTPUTS (PRODUCES)
- UGC Moment Map (UMM Pack):
  - Moment list with timestamps (relative windows)
  - Moment types and creator use-cases
  - Clip recommendations (5s / 10s / 15s)
  - Caption hooks (short text prompts)
  - Transition / cut points for editors
  - “Do/Don’t” for UGC friendliness
- UGC Prompt Notes for Prompt Compiler
- UGC QA checklist

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Viral Hook Blueprint",
  "Earworm Hook Stack",
  "Duration Policy",
  "Audience Segment Target",
  "Style Fingerprint",
  "Release Variants plan"
]
PRODUCES: [
  "UGC Moment Map (UMM pack)",
  "UGC Prompt Notes",
  "UGC QA checklist"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/04__CREATOR_PANEL_QA.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/UGC_MAPS/"

---

## 4) UGC MOMENT MAP — STRUCTURE (UMM PACK)
UMM is always delivered with the same schema.

### 4.1 Summary
- Track intent (what creators will use it for)
- Primary hook location plan
- Number of clip moments (target 4–8)

### 4.2 Moment List (MANDATORY)
Each moment entry:
- ID: M01, M02...
- Window: [t_start–t_end] (relative seconds)
- Clip lengths: 5s / 10s / 15s (which works best)
- Moment type (see Section 5)
- Creator use-case (see Section 6)
- Audio markers (drop, pause, lift, punchline)
- Caption hook (1 line)
- Risk note (if any)

### 4.3 Editor Cut Map (MANDATORY)
- recommended cut points (hard hits / silence / bar lines conceptually)
- transitions: whoosh-friendly / glitch-friendly / snap-friendly

### 4.4 Variant Mapping (OPTIONAL)
- Short version differences (intro compression)
- Alt intro clip window (0:00–0:10)
- “No-vocal” / “instrumental hook” note if needed

---

## 5) MOMENT TYPES (STANDARD SET)
The engine may only use these types (keeps system consistent):

A) HOOK HIT — the main recognizable hook
B) MICROHOOK POP — short 2–4 sec “sticker” moment
C) DROP / SWITCH — energy shift for edits
D) PAUSE / SILENCE SNAP — micro-pause before impact
E) QUOTE LINE — short lyric phrase for captions/memes
F) CALL & RESPONSE — duet/remix-friendly
G) BUILD-UP LIFT — rising tension (for reveals)
H) OUTRO LOOP — end that can loop seamlessly
I) INTRO GRAB — first 3–8 sec “scroll stop”

---

## 6) CREATOR USE-CASE CATALOG (STANDARD SET)
Each moment must map to 1–2 use-cases:

1) COMEDY / POV
2) FLEX / STATUS
3) ROMANCE / FEELING
4) DARK / DRAMA EDIT
5) STORYTIME / CONFESSION
6) TRANSFORMATION (before/after)
7) SPORT / MOTIVATION
8) GAMING / HIGHLIGHTS
9) AESTHETIC / VIBE
10) DANCE / MOVE (even minimal)
11) MEME TEXT OVERLAY
12) CINEMATIC EDITS

Rule: At least **4 different** use-cases per track plan.

---

## 7) UGC DENSITY RULES (ANTI-OVERLOAD)
- Minimum moments: 4
- Ideal moments: 6
- Maximum moments: 9 (if >9 → clutter risk)

Spacing:
- no two major moments closer than 6 seconds (unless microhook)
- at least one strong moment within first 10–15 seconds for short-form targets

---

## 8) TIMING DEFAULTS (GUIDELINES)
These are guidance, final timing depends on Duration Policy:

- Intro Grab: 0:00–0:07
- First microhook: 0:05–0:12
- First hook hit: 0:12–0:25
- First drop/switch: 0:25–0:40
- Quote line: near hook or right after drop
- Loopable outro: last 8–12 sec

---

## 9) UGC-FRIENDLY AUDIO RULES (STRICT)
1) Clear beat grid feel (editors need sync points)
2) Avoid long unstructured intros in short variants
3) Provide at least one “pause/snap” moment
4) Keep hook loud/clear vs background layers
5) Ensure lyric hook is understandable (RU clarity) if used

---

## 10) FAILURE MODES & FIX
1) Creators can’t find a clip moment
- Fix: add 1 pause/snap + 1 quote line moment.

2) Hook too late
- Fix: short variant intro compression; move microhook earlier.

3) Too many moments (confusing)
- Fix: merge moments, keep only the strongest 6.

4) Moments break style fingerprint
- Fix: re-anchor timbre palette and remove off-style switches.

---

## 11) QA CHECKLIST (UGC)
Pass criteria:
- 10-second recognition test: at least one moment works by 0:10–0:15
- 15-second loop test: at least one clip window loops cleanly
- Creator panel test: moments map to 4+ distinct use-cases
- Repeat guard: no boring copy-paste repeats inside moments

---

## 12) HANDOFFS (XREF)
Feeds into:
- `12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md`
- `60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md`
- `60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md`
- `60_QA__QUALITY/10_MUSIC_QA/04__CREATOR_PANEL_QA.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
