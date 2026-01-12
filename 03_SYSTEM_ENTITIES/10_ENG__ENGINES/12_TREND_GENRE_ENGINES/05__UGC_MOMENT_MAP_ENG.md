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
VERSION: 1.0.1
UID: UE.ENG.TG.UGC_MOMENT_MAP.001
OWNER: SYSTEM
ROLE: Defines a deterministic map of UGC-ready moments (clip windows, pause/snap cuts, quote lines, call-response hooks)
so tracks are creator-friendly and platform-native.

Outputs an executable UGC plan consumed by Hook Blueprint and Prompt Compiler.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created UGC moment map: moment types, window requirements, and output schema for creator-friendly clips."
- REASON: "Virality requires edit points and reusable moments."
- IMPACT: "Higher creator adoption, better retention and reuse."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.UGC.MOMENT.001
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; no semantic changes."
- REASON: "Compressed formatting is error-prone during edits."
- IMPACT: "Safer copy/paste; easier audits."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.TG.UGC.MOMENT.002

---

## 0) PURPOSE (LAW)
UGC Moment Map outputs a **UGC PLAN** for a track/variant:
- where creators can cut clips (windows)
- where pause/snap points exist (hard cuts)
- where quote lines or slogans live (memetic text)
- where call-response patterns allow duets
- where drops/switches create “edit peaks”

---

## 1) INPUTS (CONSUMES)
- Audience Segment Target
- Viral Hook Blueprint (or desired template)
- Earworm Hook Stack (H1/H2/S-tag/Q-line)
- Duration Strategy (short/full)
- Style Fingerprint (anchors and forbiddens)
- UGC Viral Ruleset CTL (platform constraints)
- Negative Spec Library (avoid anti-UGC artifacts)

---

## 2) OUTPUTS (PRODUCES)
- UGC Moment Map (UGC-MAP):
  - list of moments (1–5)
  - time windows (relative)
  - moment type + purpose
  - required audio features (pause, clear quote, beat stop, drop)
  - instruction snippet for prompt compiler
- Clip Window Summary:
  - primary window (best)
  - secondary window(s)
- Validator Notes:
  - what must pass for UGC readiness

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Audience Segment Target",
  "Viral Hook Blueprint template (or hook plan)",
  "Earworm Hook Stack",
  "Duration Strategy",
  "Style Fingerprint",
  "UGC Viral Ruleset CTL",
  "Negative Spec Library"
]
PRODUCES: [
  "UGC Moment Map (UGC-MAP)",
  "Clip Window Summary",
  "Validator Notes"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS//UGC_MAPS/"

---

## 4) MOMENT TYPES (STANDARD)
Choose 1–5 moments total.

### M1 — QUOTE LINE / SLOGAN
- a short line people can repeat / caption
- must be clear and isolated enough

### M2 — PAUSE / SNAP CUT
- a clear stop, breath, snap, or beat cut
- helps creators make transitions

### M3 — DROP / SWITCH PEAK
- energy shift that creates an edit point
- strong beat entry or texture switch

### M4 — CALL / RESPONSE (DUET READY)
- line A leaves space for line B
- or hook split into two sides

### M5 — MEME GESTURE / SOUND TAG
- signature sound tag (S-tag), chant, or recognizable hit
- useful as recurring “stamp”

---

## 5) WINDOW RULES (CLIPABLE)
Each moment must define:
- WINDOW_START
- WINDOW_END
- WINDOW_LENGTH

Guidelines:
- 8–15s preferred for short-form
- at least 1 primary window must exist
- at least 1 hard cut point is strongly recommended (pause/snap)

---

## 6) UGC MAP OUTPUT SCHEMA (MANDATORY)
UGC-MAP fields:

### Header
- TRACK_UID:
- VARIANT: (SHORT/FULL/ALT)
- AUDIENCE_SEGMENT:
- TEMPLATE_HINT: (A/B/C from hook blueprint)

### Moments (table-like list)
For each moment:
- MOMENT_ID:
- TYPE:
- WINDOW:
- PURPOSE:
- REQUIRED_FEATURES:
- PROMPT_HINT:

### Summary
- PRIMARY_CLIP_WINDOW:
- SECONDARY_CLIP_WINDOWS:
- HARD_CUT_POINTS:
- DUET_READY: YES/NO
- VALIDATOR_NOTES:

---

## 7) DESIGN RULES (OPERATIVE)
- Moments must not contradict Style Fingerprint anchors.
- Do not stack all moments in one small region; spread them.
- Quote line must be intelligible RU (if lyrical).
- Pause/snap must be clean (no muddy tails).
- Drop/switch must be obvious and not delayed too late.

---

## 8) FAILURE MODES & FIX
1) No clear clip window  
- Fix: insert pause/snap; shorten section; simplify textures.

2) Quote line unclear  
- Fix: reduce layers under vocal; shorten line; use tighter articulation.

3) Drop weak  
- Fix: increase contrast before drop; use silence/pause; add signature hit.

4) Too many moments → chaos  
- Fix: reduce to 2–3 moments max; keep one primary.

---

## 9) HANDOFFS (XREF)
Feeds into:
- `12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md`
- `12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md`
- `60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
