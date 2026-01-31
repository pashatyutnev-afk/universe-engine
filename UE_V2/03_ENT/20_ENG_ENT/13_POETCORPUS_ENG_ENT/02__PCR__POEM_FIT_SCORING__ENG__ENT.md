# Poem Fit Scoring Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 13_POET_PD_CORPUS_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: POET_PD_CORPUS
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.PD.POEM_FIT_SCORING.001
OWNER: SYSTEM
ROLE: Scores PD-eligible poems/fragments against a specific Track Intent Brief (genre/fingerprint/hook/UGC/duration),
and outputs a ranked shortlist plus fit rationales for downstream Juice Extractor and Mosaic Composer.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Poem Fit Scoring: scoring dimensions, weights, deterministic procedure, and ranked shortlist output."
- REASON: "Without fit scoring, the system extracts juice from random PD texts and loses hook/genre alignment."
- IMPACT: "Higher lyrical-hook density, better cadence fit, fewer failed takes."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.PD.FIT_SCORING.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Which PD texts fit THIS track best?”**

It must:
- take only PD-eligible candidates (from PD Filter)
- score them deterministically with a standard rubric
- produce a ranked shortlist (top K) with reasons and “fit notes”
- output “avoid reasons” to help collision/memory later

---

## 1) INPUTS (CONSUMES)
From PD Filter:
- ALLOWED_CORPUS_SUBSET (ACS): list of PD-eligible works/fragments

From Music Factory / Trend-Genre:
- Track Intent Brief (role + theme + mood)
- Style Fingerprint anchors + forbiddens
- Genre family (A) + fusion recipe (optional)
- Earworm Hook Stack (needs: Q-line / slogan / cadence)
- UGC Moment Map (clip window needs)
- Duration Strategy (short/full; how dense text should be)

Policy / memory:
- PD Policy CTL (constraints on quoting/fragment size)
- Excerpt Collision memory (if any exists; otherwise empty)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- FIT_RANKING (FRANK): ranked list of PD candidates

Secondary:
- TOP_K_SHORTLIST (K=3..10)
- FIT_NOTES per candidate:
  - best lines potential (not full quotes)
  - cadence/rhythm suitability
  - theme resonance
  - “quoteability” likelihood
- REJECTION_REASONS (why top candidates failed)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Allowed Corpus Subset (PD-eligible)",
  "Track Intent Brief",
  "Style Fingerprint (anchors/forbiddens)",
  "Genre A + Fusion (optional)",
  "Earworm Hook Stack (Q-line needs)",
  "UGC Moment Map",
  "Duration Strategy",
  "PD Policy CTL",
  "Excerpt Collision memory (optional)"
]
PRODUCES: [
  "Fit Ranking (FRANK)",
  "Top-K Shortlist",
  "Fit Notes (per candidate)",
  "Rejection Reasons"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/01__PD_FILTER_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS//PD_CORPUS/FIT_SCORING/"

---

## 4) SCORING MODEL (STANDARD RUBRIC)
Each candidate receives a 0–100 FIT score.

### Dimensions (0–10 each, weighted)
D1 THEME_MATCH (weight 2.0)
- matches track theme/role/mood

D2 CADENCE_FIT (weight 2.0)
- line rhythm supports hook phrasing
- pronounceable RU (or target language)

D3 QUOTEABILITY (weight 1.5)
- can yield a short Q-line / slogan
- memorable phrasing potential

D4 IMAGERY_POWER (weight 1.0)
- strong vivid images, metaphor density

D5 GENRE_COMPATIBILITY (weight 1.5)
- works with genre family A and fingerprint tone

D6 HOOK_STACK_SUPPORT (weight 1.0)
- supports H1/H2/Q-line requirements (e.g., call-response)

D7 UGC_FRIENDLINESS (weight 0.5)
- lines can sit inside clip windows cleanly

D8 NOVELTY_SAFETY (weight 0.5)
- avoids overly famous overused lines (if collision memory flags them)

Total Score:
- FIT = sum(Di * weight) normalized to 0–100

---

## 5) HARD FILTERS (BEFORE SCORING)
If any hard filter fails → candidate is REJECTED (score = 0 with reason).

HF1 — PD eligibility must be PASS (from PD Filter)
HF2 — Language compatibility must match track plan (RU by default)
HF3 — Policy constraints: “no full poem dump”; fragments-only readiness
HF4 — If excerpt collision memory marks “blocked lines” as dominant content → reject (or penalize by policy)

---

## 6) PROCEDURE (DETERMINISTIC)
1) Load Track Intent Brief + Fingerprint anchors/forbiddens.
2) Load PD Policy constraints (fragment size guidance, quoting rules).
3) For each PD candidate in ACS:
   a) apply hard filters HF1..HF4
   b) if passed: score D1..D8 using rubric
   c) write Fit Notes:
      - 2–5 “candidate lines ideas” (paraphrase/keywords, not full quotes)
      - cadence notes (short/long lines, punchiness)
      - why it fits hook/UGC
4) Rank by FIT score descending.
5) Output TOP_K shortlist.
6) Output rejection reasons summary (top 5 rejections).
7) Emit “scoring tokens” for later collision tracking:
   - author/work ids
   - theme tags
   - cadence type tags

---

## 7) OUTPUT SCHEMA (MANDATORY)

### FIT_RANKING (FRANK)
- TRACK_UID:
- DATE:
- INPUT_CORPUS_SIZE:
- TOP_K:
- RANKED_LIST:
  - rank:
    candidate_id:
    author:
    work:
    fit_score_0_100:
    dimension_scores:
      D1:
      D2:
      D3:
      D4:
      D5:
      D6:
      D7:
      D8:
    fit_notes:
      theme:
      cadence:
      quoteability:
      hook_support:
      ugc_support:
    risk_notes:
      famous_lines_risk:
      collision_risk:
- REJECTION_SUMMARY:
  - candidate_id: reason

### TOP_K_SHORTLIST
- LIST:
  - candidate_id + score + 1-line why

---

## 8) FAILURE MODES & FIXES
1) Rankings feel random
- Fix: tighten Track Intent Brief; increase weights for D1/D2; reduce ambiguous candidates.

2) Too many candidates reject
- Fix: expand PD corpus; enrich metadata; adjust policy strictness only in CTL.

3) Candidates fit theme but not cadence
- Fix: raise CADENCE_FIT weight; require “short punch lines” for viral tracks.

4) Overused famous lines keep coming back
- Fix: strengthen Excerpt Collision memory and penalize in D8 or hard-block in HF4.

---

## 9) HANDOFFS (XREF)
Feeds into:
- `13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md`
- `13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md`
- `13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md`

Used by:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
