# AUDIENCE SEGMENTS — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: AUDIENCE_SEGMENTS
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.AUDIENCE_SEGMENTS.001
OWNER: SYSTEM
ROLE: Defines internal audience segments for music production and how segments translate into runnable constraints:
tempo band tendencies, hook formats, UGC patterns, lyric tone constraints, and prohibited mismatches.
Used by Group Foundation, Trend Engineer, Portfolio Planner, and Prompt/Hooks planning.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Audience Segments CTL: segment registry + constraint mapping for hooks/UGC/duration/lyrics tone."
- REASON: "Without segment definitions, production targets are vague and trend alignment becomes random."
- IMPACT: "Clear targeting, higher hit-rate, consistent catalog strategy."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.AUDIENCE.SEGMENTS.001

---

## 0) PURPOSE (LAW)
This controller provides a **small internal segmentation system** so production can target:
- hooks
- UGC clip behavior
- lyric tone and delivery
with consistent constraints.

This is not a market research doc — it is an operational constraint registry.

---

## 1) SEGMENT OUTPUT CONTRACT (MANDATORY)
When a segment is selected, it must provide:
- segment id + label
- hook template bias
- UGC clip pattern bias
- duration mode bias (short/full)
- lyric tone constraints
- “avoid mismatches” list

---

## 2) SEGMENT REGISTRY (CANON LIST)
This list is internal and adjustable via future versions.

### SEG.A1 — UGC LOOPERS
- Intent: loopable, addictive, repeat-safe hooks
- Bias:
  - duration: SHORT
  - hook: early + chant/slogan/motif
  - UGC: clean clip windows + pause/snap points
- Avoid: long intro, slow build, complex narratives

### SEG.A2 — EMO CLIP QUOTES
- Intent: quote lines, caption-ready emotions
- Bias:
  - duration: SHORT or FULL (but must have short clip window)
  - hook: Q-line centered
  - UGC: quote window 10–25s
- Avoid: abstract lyrics, muddy vocals, too-fast delivery

### SEG.B1 — CLUB/GYM ENERGY
- Intent: energy, drive, rhythmic hooks
- Bias:
  - duration: FULL or SHORT_CUT variant
  - hook: rhythmic motif, drop emphasis
  - UGC: drop/switch peaks
- Avoid: sleepy tempo bands, too soft palettes

### SEG.B2 — CHILL / NIGHT DRIVE
- Intent: vibe, texture, smooth flow
- Bias:
  - duration: FULL
  - hook: subtle but recognizable
  - UGC: aesthetic clip windows (15–45s)
- Avoid: aggressive chant spam, harsh vocals (unless style demands)

### SEG.C1 — STORY / CINEMATIC
- Intent: narrative arc and emotional progression
- Bias:
  - duration: FULL
  - hook: theme motif; less repetitive
  - UGC: 1–2 curated moments only
- Avoid: over-optimization for UGC that kills story

### SEG.D1 — MEME / COMEDY PUNCH
- Intent: short comedic hook, caption-ready punchline
- Bias:
  - duration: SHORT
  - hook: slogan/punchline
  - UGC: hard cut points + call/response
- Avoid: subtlety, long verses

---

## 3) CONSTRAINT MAPPING (HOW SEGMENTS AFFECT PRODUCTION)
### Hook format bias
- A1: chant/motif + repeat-safe variation
- A2: Q-line must be strong and intelligible
- B1: drop-centric motif + rhythm hook
- B2: vibe hook + signature tag
- C1: motif hook, fewer repeats
- D1: punchline hook + clear edit points

### UGC bias
- A1/D1: strict clip windows + cut points mandatory
- A2: quote window mandatory
- B1: drop/switch peaks mandatory
- B2/C1: softer UGC; curated moments only

### Duration bias
- A1/D1: SHORT mandatory
- A2: SHORT preferred; FULL allowed with strong clip
- B1: FULL with SHORT_CUT release
- B2/C1: FULL preferred

---

## 4) MISMATCH RULES (AVOID LIST)
If segment is selected, avoid:
- A1: long intros, ambient builds, weak hook
- A2: unclear vocals, no Q-line, overly abstract text
- B1: weak drums, no drop energy, low drive
- B2: harsh spammy chants, overly busy arrangement
- C1: cheap viral tricks that break narrative arc
- D1: subtle/vague hooks, no punchline, no edit points

---

## 5) REQUIRED USAGE (WHO MUST APPLY THIS)
- Group Foundation ENG must record the chosen segment (or default).
- Trend Engineer SPC must produce a Trend Signal Pack aligned to the segment.
- Prompt Architect and Hook/UGC planning must encode segment constraints.

---

## 6) DEFAULT SELECTION RULE
If no segment is specified:
- default to SEG.A1 (UGC LOOPERS) for UGC-first factory mode
- record the default selection in outputs

---

## 7) REFERENCES (RAW)
Used by:
- Group Foundation ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md
- Portfolio Planner ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
