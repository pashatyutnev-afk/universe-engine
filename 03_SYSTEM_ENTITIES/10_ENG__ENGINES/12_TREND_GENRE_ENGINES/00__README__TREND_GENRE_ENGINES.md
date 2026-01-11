# Prompt Compiler Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md

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
UID: UE.ENG.TG.PROMPT_COMPILER.001
OWNER: SYSTEM
ROLE: Converts internal specs (group DNA, style fingerprint, hook blueprint, UGC moment map, duration policy, PD/lyrics) into generator-ready prompts (SUNO/UDIO), with strict compression + negative specs + fidelity guard.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Prompt Compiler Engine: compiler contract, prompt layers, compression rules, and platform phrasebooks integration."
- REASON: "Models misinterpret long/ambiguous prompts; we need deterministic compilation."
- IMPACT: "Higher prompt fidelity, less 'model improvisation', predictable outputs."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.PROMPT_COMPILER.001

---

## 0) PURPOSE (LAW)
This engine is the **compatibility bridge** between Universe Engine and music generators.

It ensures:
- the prompt is short enough to be respected
- the most important constraints are expressed in the model’s “native dialect”
- negative constraints are explicit
- outputs are reproducible and controllable

---

## 1) INPUTS (CONSUMES)
- Group DNA Spec (identity anchors, promises, forbiddens)
- Style Fingerprint (core anchors + variable anchors)
- Fusion Recipe (if any)
- Viral Hook Blueprint + Earworm Hook Stack
- UGC Moment Map (where “clip moments” should appear)
- Duration Policy (target length + tolerance)
- Lyrics source (PD mosaic pack OR original lyric brief OR instrumental)
- Release Variant plan (if multiple versions are required)
- Platform choice: SUNO or UDIO

---

## 2) OUTPUTS (PRODUCES)
- Prompt Package (platform-ready)
  - STYLE TAGS LINE (short)
  - LYRICS BLOCK (optional)
  - ADVANCED NOTES (optional, if platform supports)
  - NEGATIVE SPECS (must-not list)
  - VERSION TAGS (V1/V2… for controlled variants)
- Prompt Delta Notes (what changed vs previous attempt)
- Fidelity Checklist (what to verify after generation)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group DNA Spec",
  "Style Fingerprint",
  "Hook Blueprint / Earworm Stack",
  "UGC Moment Map",
  "Duration Policy",
  "Lyrics source (PD/original/none)",
  "Platform phrasebook",
  "Negative Spec Library"
]
PRODUCES: [
  "Prompt Package (Suno/Udio ready)",
  "Prompt Delta Notes",
  "Fidelity Checklist"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/PROMPTS/"

---

## 4) COMPILER PRINCIPLES (STRICT)
1) **Short > long**: limit to the minimum needed to control output.
2) **Priority encoding**: top 3 constraints must be obvious.
3) **No ambiguous metaphors** in the prompt. Only concrete audio terms.
4) **Avoid internal jargon**. Convert to platform language (phrasebooks).
5) **Negative specs always present** (what must NOT happen).
6) **Variant discipline**: each variant changes 1–2 axes only.

---

## 5) PROMPT LAYERS (OUTPUT FORMAT)
The compiled output must be structured:

### L1) STYLE TAGS LINE (max 12–20 tags)
- genre, era references, vocal type, groove, instrumentation, mood, mix style
- 1–2 “signature anchors” from fingerprint
- 0–1 fusion spice tag (if used)

### L2) STRUCTURE NOTES (max 4 bullets)
- hook timing / hook form
- intro signature
- energy curve (A/B/Drop)
- UGC moment windows (timestamps as intent, not exact)

### L3) DURATION TARGET (single line)
- target length + tolerance

### L4) LYRICS BLOCK (optional)
- if PD/original lyrics: keep clean, not huge
- if instrumental: explicit “instrumental” directive

### L5) NEGATIVE SPECS (max 8–12 items)
- “no …”, “avoid …”, “do not …”
- remove typical model drift patterns

### L6) VARIANT TAG
- V1/V2 + “delta” note

---

## 6) COMPRESSION RULES (ANTI-MISUNDERSTANDING)
- Replace long explanations with **short tags**
- Prefer “adjectives + instrument + era” format:
  - “dry punchy drums”, “bright synth lead”, “warm tape bass”
- If conflict between tags:
  - keep the ones tied to identity anchors, drop the rest
- Never exceed “human readable” density:
  - style tags line must be scannable

---

## 7) PLATFORM DIALECTS (SUNO vs UDIO)
### 7.1 SUNO DIALECT (priority)
- Style tags are primary control surface.
- Avoid long paragraphs.
- If lyrics present: keep tight, clear section markers.
- Explicitly state language: “русский язык”.

### 7.2 UDIO DIALECT
- Often tolerates richer instruction, but still compress.
- Put structure notes in short bullets.

The compiler must output two formats when requested:
- SUNO_PROMPT
- UDIO_PROMPT
(Otherwise only the chosen platform.)

---

## 8) VARIANT GENERATION STANDARD (V1..V4)
To create multiple options without chaos:
- V1: baseline (core fingerprint + hook blueprint)
- V2: change 1 axis (hook grammar or intro)
- V3: change 1 axis (groove or timbre palette)
- V4: change 1 axis (vocal delivery or mix vibe)

Never change more than 2 axes per variant.

---

## 9) FIDELITY CHECKLIST (POST-GEN)
After generation, check:
1) Language correct (RU)
2) Hook appears where intended
3) Signature anchors audible
4) Forbidden items absent (negative specs)
5) Duration within tolerance
6) No obvious reuse of prior take fingerprint (if known)

If fail → send “Prompt Delta Notes” to Track Factory for regen.

---

## 10) FAILURE MODES & FIX
1) Model ignores prompt
- Fix: shorten tags, move identity anchors to the beginning, reduce count.

2) Model invents extra stuff (improvisation)
- Fix: strengthen negative specs; reduce ambiguity; add “no improvisational genre shifts”.

3) Output too generic
- Fix: add 1 signature anchor + 1 hook blueprint directive; remove generic mood spam.

4) Output collides with catalog
- Fix: call Novelty Injection Engine; then recompile.

---

## 11) HANDOFFS (XREF)
NEXT:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` (generation variants)
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md` (validation)
- `60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md` (anti-repeat)

USES:
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md`

---

## 12) OUTPUT PACK (MANDATORY LIST)
1) SUNO_PROMPT (if target Suno)
2) UDIO_PROMPT (if target Udio)
3) Variant Set (V1..V4) if requested
4) Prompt Delta Notes
5) Fidelity Checklist

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
