# PLAYBOOK — ANTI-REPETITION FIX (PHRASE/MOTIF) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/06__PLAYBOOK__ANTI_REPETITION_FIX.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.ANTI_REPEAT.001
OWNER: SYSTEM
ROLE: Deterministic method to reduce repetition in generator outputs: diagnose repetition type, apply novelty constraints, targeted negative specs, and minimal-delta patches while preserving hook repetition where desired.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created anti-repetition fix playbook: repetition taxonomy, prompt levers, minimal patch strategy, and recheck."
- REASON: "Repetition is a common failure mode (lyrics/patterns); needs operational control rather than vague requests."
- IMPACT: "Cleaner verses, purposeful chorus repetition, less pattern loops."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.REPEAT.001

---

## 0) INPUTS (REQUIRED)
- BASELINE_PROMPT_CONTRACT (frozen)
- REPETITION_SYMPTOMS (observed):
  - repeated lines/phrases
  - repeated rhyme scheme
  - repeated motif in verses
  - chorus repeated too often / verse turns into chorus
- TARGET REPETITION POLICY:
  - allow chorus/hook repetition (YES/NO)
  - verse repetition tolerance (LOW/MED/HIGH) (default LOW)
- RECHECK (optional gate UIDs)

---

## 1) OUTPUTS
- REPETITION_DIAGNOSIS (type + likely cause)
- NOVELTY_CONSTRAINT_BLOCK (insert/update)
- TARGETED_NEGATIVE_SPECS (repetition)
- PATCH_PROMPT (minimal delta)
- RECHECK_MINI

---

## 2) REPETITION TAXONOMY (DIAG)
Identify type(s). Choose one primary type per patch loop.

R-TYPES:
- R1 LINE REPEAT (same line repeats)
- R2 PHRASE PATTERN (same syntactic pattern repeats)
- R3 RHYME LOOP (same rhyme and cadence repeats)
- R4 MOTIF OVERUSE (same idea/motif repeats outside chorus)
- R5 SECTION COLLAPSE (verse behaves like chorus)

---

## 3) LIKELY CAUSES (PROMPT-LEVEL)
CAUSES:
- C1 prompt too generic (no novelty constraints)
- C2 negative spec missing for repetition
- C3 structure unclear (chorus/verse roles blurred)
- C4 hook constraints too strong and bleed into verses
- C5 lyric seed too short and recycled

Rule:
- Fix structure clarity first if R5.

---

## 4) LEVERS (WHAT TO CHANGE)
Pick 2–4 levers only.

L1 — Verse novelty constraint (strong)
- “Verses must use varied wording; avoid repeating identical lines; each verse introduces new imagery.”

L2 — Allow repetition only where intended
- “Repetition allowed only in chorus/hook; verses must be novel.”

L3 — Vary line length / cadence constraint
- “Verses vary line length and cadence; avoid same rhythmic sentence pattern.”

L4 — Add targeted negative specs
- “avoid repeating the same phrases/lines in verses”
- “avoid recycling chorus lines into verses”
- “avoid repetitive rhyme loops”

L5 — Clarify section roles
- “Chorus repeats; verses develop new content.”

L6 — Provide “variation instruction”
- “Use synonyms / rephrase ideas; avoid repeating keywords across verse lines.”

Keep instructions operational; avoid writing full lyrics here.

---

## 5) NOVELTY_CONSTRAINT_BLOCK (COPY)
NOVELTY_CONSTRAINT_BLOCK:
- REPETITION POLICY:
  - Chorus repetition: ALLOWED (hook)
  - Verse repetition: NOT ALLOWED
- VERSE NOVELTY:
  - Each verse introduces new images/phrases
  - Avoid repeating identical lines
  - Vary cadence/line length
- SECTION ROLE CLARITY:
  - Verses develop; chorus repeats

---

## 6) TARGETED NEGATIVE SPECS (REPETITION)
Choose 4–8 items max.

NEGATIVE_REPEAT:
- avoid repeating the same lines in verses
- avoid repeating the same phrases/keywords line-to-line
- avoid recycling chorus lyrics into verses
- avoid repetitive rhyme loops across verse lines
- avoid identical sentence structures repeatedly
- avoid overusing the same motif outside chorus

---

## 7) PATCH STRATEGY (MINIMAL DELTA)
Delta rule:
- modify only STRUCTURE_BLOCK and/or NEGATIVE_SPEC_BLOCK (and optionally add NOVELTY_CONSTRAINT_BLOCK).
- do not change style/vocals unless required.

Patch prompt (COPY):
PATCH_PROMPT:
- Keep everything else unchanged.
- Add/strengthen NOVELTY_CONSTRAINT_BLOCK.
- Add NEGATIVE_REPEAT items (4–8).
- Clarify verse vs chorus roles in STRUCTURE_BLOCK:
  - “verses must be novel; chorus repeats”

Loop limit:
- 2 attempts on repetition before escalating to DIAGNOSE & REWORK.

---

## 8) RECHECK MINI (POST-GEN)
RECHECK_MINI:
- [ ] Verses do not repeat identical lines
- [ ] Chorus repetition stays mostly within chorus
- [ ] Verse 2 differs from verse 1 (phrasing and imagery)
- [ ] No obvious repeated syntactic template every line
- [ ] Hook still clear (if required)

Result: PASS/REWORK/FAIL

---

## 9) TRACE (MINIMUM)
TRACE_NOTES:
- BASELINE_ID:
- PRIMARY_R_TYPE: R?
- LEVERS_USED: [L1, L4, ...]
- NEGATIVES_ADDED_COUNT:
- RESULT:
- LOOP_COUNT:
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO

---

## 10) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal delta discipline
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001 | WHY: multi-issue cases
- UE.KB.SOUND.TOPIC.REPEAT_GUARD_METHOD.001 (PLACEHOLDER) | WHY: deeper anti-repetition topic module
- UE.KB.QA.STD.CONNECTOR.001 | WHY: recheck discipline

--- END.
