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
ROLE: Compiles all creative + control constraints into a deterministic, platform-native prompt pack (Suno/Udio) with minimal ambiguity and maximal fidelity.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created a deterministic prompt compiler: Suno-native fields, negative spec enforcement, phrasebook usage, and fidelity/QA hooks."
- REASON: "We need compatibility: model executes exactly what we ask, with minimal 'from itself'."
- IMPACT: "Higher consistency, fewer rerolls, stronger control over style/voices/hooks."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.PROMPT.COMPILER.001

---

## 0) PURPOSE (LAW)
This engine produces a **PROMPT PACK** that:
- is **platform-native** (Suno/Udio formats)
- is **deterministic** (clear constraints, no vague adjectives alone)
- enforces **controls** (negative spec, policy gates, duration)
- embeds **hook strategy** and **UGC moments**
- supports **repeatable series identity** (style fingerprint + naming)

---

## 1) INPUTS (CONSUMES)
- Style Fingerprint (identity anchors)
- Fusion Recipe (genre blend constraints)
- Viral Hook Blueprint (hook role + placement)
- Earworm Hook Stack (primary/secondary microhooks)
- UGC Moment Map (clip windows and quote lines)
- Duration Strategy + Duration Policy
- Prompt Contract (what must/ must not happen)
- Platform Phrasebooks (Suno/Udio)
- Negative Spec Library (anti-artifacts)
- Release Variants plan (short/long/alt intro)
- Credits/Metadata Policy (credits field discipline if used)

---

## 2) OUTPUTS (PRODUCES)
- PROMPT PACK (Suno):
  - Lyrics (RU) OR instrument-only instruction
  - Styles string (comma-separated, platform-native)
  - Advanced Options notes (structure, vibe constraints)
  - Negative constraints (integrated safely)
  - Variant prompts (Short/Long/Alt intro)
- PROMPT PACK (Udio):
  - Tags / descriptors (native ordering)
  - Structure hints (intro/verse/chorus/bridge)
  - Negative constraints pack
  - Variant prompts
- Prompt Fidelity Checklist (for validator)
- Prompt Diff (what changed from last attempt)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Style Fingerprint",
  "Fusion Recipe",
  "Viral Hook Blueprint",
  "Earworm Hook Stack",
  "UGC Moment Map",
  "Duration Policy",
  "Prompt Contract",
  "Suno Phrasebook",
  "Udio Phrasebook",
  "Negative Spec Library",
  "Release Variants plan",
  "Credits/Metadata Policy"
]
PRODUCES: [
  "Suno Prompt Pack",
  "Udio Prompt Pack",
  "Prompt Fidelity Checklist",
  "Prompt Diff"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/PROMPT_PACKS/"

---

## 4) CORE LAW: COMPILATION PRINCIPLES
### 4.1 Determinism rule
- Never rely on single vague adjectives (e.g., “крутой”, “эпичный”) alone.
- Every descriptor must be anchored by **observable audio traits**:
  - tempo feel, groove type, instrumentation, vocal character, mix traits, structure notes.

### 4.2 Minimal ambiguity rule
- Prefer short, platform-native tags over paragraphs in style field.
- Put “what to avoid” into a **negative pack**, not scattered text.

### 4.3 Identity-first rule
- Style Fingerprint is the anchor.
- Fusion recipe may only modify within allowed blend bounds.

### 4.4 Hook-first rule
- Hook requirements must be explicit:
  - “recognizable hook by 0:10–0:15”
  - “main hook repeats 2–3 times but not copy-paste”
  - “one pause/snap moment before hook hit”

---

## 5) OUTPUT FORMAT — SUNO PROMPT PACK (STANDARD)
The Suno pack is always delivered as:

### 5.1 SUNO.LYRICS (RU)
- If lyrical: provide full lyrics with clear section labels.
- If instrumental: write “Instrumental” and move constraints to SUNO.INSTRUCTION.

**Allowed section labels:**
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Bridge]
[Final Chorus]
[Outro]

### 5.2 SUNO.STYLES (comma-separated)
Rules:
- 5–12 tags max
- order: genre → era → instrumentation → vocal → mood → mix traits
- avoid contradictions (no “lofi” + “stadium anthem” together unless fusion recipe allows)

### 5.3 SUNO.INSTRUCTION (1 short paragraph)
Must include:
- hook timing intent (early recognition)
- structure intent (e.g., verse→chorus fast)
- UGC moment hint (pause/snap, drop/switch)
- duration target (short/long variant)

### 5.4 SUNO.NEGATIVE (compact)
Use Negative Spec Library:
- anti-artifacts (muddy vocals, clipped highs, messy structure, random key changes, etc.)
- anti-style drift (no jazz scat, no opera vibrato, etc.) as applicable

### 5.5 SUNO.VARIANTS (if requested)
- V1: Short (UGC)
- V2: Full (album)
- V3: Alt Intro (0–7s grab)

---

## 6) OUTPUT FORMAT — UDIO PROMPT PACK (STANDARD)
Udio pack is always delivered as:

- UDIO.TAGS (comma-separated, 8–15)
- UDIO.STRUCTURE (very short: Intro/Verse/Chorus/Bridge notes)
- UDIO.VOCAL (voice constraints, delivery, language)
- UDIO.MIX (mix & master intent)
- UDIO.NEGATIVE (compact)
- UDIO.VARIANTS (short/full/alt intro)

---

## 7) VOICE + INSTRUMENT STYLE MODEL (GROUP CAST)
This engine supports **group cast** (not only singer):
- VOCAL role: lead / backing / chant / call-response
- INSTRUMENT roles: guitar lead, synth lead, bass pocket, drum signature, fx moments

Rule:
- at least **one signature element** must be declared:
  - signature riff / signature drum fill / signature synth motif / chant tag

---

## 8) DURATION COMPILATION (ANTI-CHAOS)
Input: Duration Policy.
Compiler outputs:
- Target total length range (e.g., 2:10–2:40 short; 2:50–3:30 full)
- Mandatory: hook appears by a specified second
- Mandatory: no “empty intro” longer than allowed

If platform cannot guarantee exact seconds:
- Compiler uses relative constraints (early hook, short intro, loopable outro).

---

## 9) UGC MOMENT INJECTION (FROM UMM)
At least 3 of these must appear in compiled instructions:
- intro grab (0–7s)
- pause/snap moment
- drop/switch moment
- quote line / caption hook (for lyrical)
- loopable outro hint

---

## 10) NEGATIVE SPEC — SAFE INTEGRATION RULES
- Negative pack must be short and technical.
- Avoid “don’t be bad” language.
- Prefer “avoid: <artifact> / no: <behavior>”.

Examples (pattern only, not final list):
- avoid: muddy vocals, harsh sibilance
- no: random genre shift, spoken skits (unless requested)
- avoid: too many repeats, monotone melody

---

## 11) PROMPT DIFF (MANDATORY)
Every iteration outputs:
- What changed vs previous prompt (3–8 bullets)
- Why changed (tie to QA or validator fail)

---

## 12) FAIL MODES & FIX
1) Model invents too much
- Fix: tighten prompt contract, reduce adjectives, increase anchors.

2) Wrong vibe / drift
- Fix: reinforce Style Fingerprint + negative anti-drift.

3) Hook weak / late
- Fix: explicit early-hook requirement + intro compression.

4) Repetitive chorus
- Fix: add variation rule: “chorus repeats with small melodic/rhythmic variation”.

5) Vocals unclear (RU)
- Fix: add diction/clarity constraints + reduce dense instrumentation under vocal.

---

## 13) VALIDATION HANDOFFS
Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md`
- `60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md`
- `60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md`

Controlled by:
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
