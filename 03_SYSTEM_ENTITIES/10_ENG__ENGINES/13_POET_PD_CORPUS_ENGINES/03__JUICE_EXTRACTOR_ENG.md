# Juice Extractor Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md

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
UID: UE.ENG.PD.JUICE_EXTRACTOR.001
OWNER: SYSTEM
ROLE: Extracts the strongest PD fragments (“juice”) from top-ranked poems: hook-worthy lines,
quote lines, rhythmic/cadence-ready phrases, and imagery kernels.

Produces a Juice Pack used by Mosaic Composer and Track Factory (Q-line/H1/H2 support).

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Juice Extractor: extraction rubric, fragment types, cadence tagging, and output schema for mosaic lyrics."
- REASON: "We must avoid dumping whole poems and instead extract high-impact hook material."
- IMPACT: "Stronger lyrical hooks, better quoteability, less repetition, cleaner prompts."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.PD.JUICE_EXTRACTOR.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Which fragments of this PD text are worth using for hooks and mosaics?”**

It must:
- work only on PD-eligible sources
- output a compact, ranked set of fragments
- tag fragments by function (hook/quote/bridge/imagery)
- tag cadence/rhythm traits for music fitting
- never output full poem dumps; only fragments

---

## 1) INPUTS (CONSUMES)
- Top-K shortlist from Fit Scoring (FRANK)
- Selected candidate poem(s) metadata and text (PD-eligible)
- Track Intent Brief (role + mood + theme)
- Hook Stack needs (Q-line / slogan / call-response)
- Duration Strategy (short/full; density constraints)
- PD Policy CTL (fragment size limits)
- Excerpt Collision memory (optional)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- JUICE_PACK (JP): ranked fragments with tags

Secondary:
- FRAGMENT TOKENS:
  - short tokens used for collision tracking later
- “DO NOT USE” list:
  - weak / off-brand / too-long fragments
- Cadence Profile Summary:
  - what type of lines dominate (short punch / long lyrical)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Fit Ranking (Top-K shortlist)",
  "Selected PD poem texts (eligible)",
  "Track Intent Brief",
  "Hook Stack needs",
  "Duration Strategy",
  "PD Policy CTL",
  "Excerpt Collision memory (optional)"
]
PRODUCES: [
  "Juice Pack (JP)",
  "Fragment Tokens",
  "Do-Not-Use list",
  "Cadence Profile Summary"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS//PD_CORPUS/JUICE/"

---

## 4) FRAGMENT TYPES (STANDARD)
Each extracted fragment must be tagged as one (or more) of:

F1 — Q_LINE (quote/caption line)
F2 — HOOK_LINE (chorus/hook nucleus)
F3 — SETUP_LINE (sets up the hook)
F4 — CALL_LINE (call-response first half)
F5 — RESPONSE_LINE (call-response answer)
F6 — IMAGERY_KERNEL (strong image/metaphor)
F7 — BRIDGE_MATERIAL (contrast tone, but on theme)
F8 — TAGLINE / SLOGAN (short, repeatable)

---

## 5) EXTRACTION RUBRIC (SCORING)
Each fragment gets a 0–10 score in dimensions:

E1 PUNCH (weight 2.0)
- short impact, “hit” quality

E2 QUOTEABILITY (weight 2.0)
- can be captioned and repeated

E3 CADENCE_FIT (weight 2.0)
- rhythm and syllable flow suitable for hooks

E4 IMAGERY_POWER (weight 1.0)
- vividness, metaphor density

E5 THEME_MATCH (weight 1.5)
- fits track role and mood

E6 ORIGINALITY_RISK (weight 0.5, negative)
- famous/overused line risk (penalize if flagged by collision memory)

Fragment Score:
- FRAG_SCORE = weighted sum normalized to 0–100

---

## 6) HARD LIMITS (POLICY-DRIVEN)
This engine must respect PD policy:
- fragment length cap (lines count or character count) — set by CTL
- no full poem output
- output must be fragments only

If a candidate text is too long:
- extract only top fragments, never paste full text.

---

## 7) PROCEDURE (DETERMINISTIC)
1) Select 1–3 top candidates from Fit Ranking.
2) For each candidate:
   a) segment into units: lines / couplets / short stanzas
   b) propose fragment candidates (short units)
   c) score each fragment with rubric E1..E6
   d) tag fragment types (F1..F8)
   e) tag cadence profile:
      - SHORT_PUNCH / MEDIUM_FLOW / LONG_LYRICAL
3) Sort fragments by FRAG_SCORE.
4) Output Juice Pack:
   - top 6–20 fragments max
   - ensure diversity of fragment types (not all imagery, not all quotes)
5) Generate tokens for collision tracking:
   - author/work id + fragment hash/label
6) Emit “Do not use” list:
   - fragments that are off-theme, too long, or risky

---

## 8) OUTPUT SCHEMA (MANDATORY)

### JUICE_PACK (JP)
- TRACK_UID:
- DATE:
- SOURCE_CANDIDATES:
  - candidate_id + author + work + fit_score
- FRAGMENTS (ranked):
  - rank:
    fragment_id:
    source_candidate_id:
    fragment_text: (short fragment only; no full poem)
    fragment_type_tags: [F1..F8]
    frag_score_0_100:
    cadence_tag: {SHORT_PUNCH | MEDIUM_FLOW | LONG_LYRICAL}
    usage_hint:
      - where to place (hook/setup/bridge/ugc window)
      - why it works (1 line)
    risk_notes:
      - famous_line_risk: low/med/high
      - collision_risk: low/med/high
- CADENCE_PROFILE_SUMMARY:
  - dominant cadence types + recommendation for hook usage
- DO_NOT_USE:
  - list of fragment_ids + reason
- TOKENS:
  - list of compact tokens for collision guard

---

## 9) FAILURE MODES & FIXES
1) Extracted fragments are long and un-singable
- Fix: raise cadence weight; enforce SHORT_PUNCH for hook/Q-line.

2) Fragments are poetic but not viral
- Fix: increase punch/quoteability weights; require at least 2 Q_LINE.

3) Too many famous lines
- Fix: strengthen collision memory; penalize E6; pick alternative fragments.

4) Too few usable fragments
- Fix: widen candidate selection to top 5; use mosaic across 2–3 works.

---

## 10) HANDOFFS (XREF)
Feeds into:
- `13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md`
- `13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md`
Used by:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` (Q-line/hook material)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
