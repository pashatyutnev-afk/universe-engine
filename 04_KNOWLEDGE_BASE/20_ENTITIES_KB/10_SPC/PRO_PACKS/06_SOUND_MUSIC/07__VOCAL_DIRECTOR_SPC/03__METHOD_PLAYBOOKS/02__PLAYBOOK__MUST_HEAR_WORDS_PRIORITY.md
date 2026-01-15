# SPC PRO PACK — PLAYBOOK (PB-02) — MUST-HEAR WORDS PRIORITY (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/02__PLAYBOOK__MUST_HEAR_WORDS_PRIORITY.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PB.MUST_HEAR.001
OWNER: SYSTEM
ROLE: Deterministic method to extract, rank, and validate MUST-HEAR words (hook + meaning carriers). Produces a prioritized list (P0/P1/P2), pronunciation risk notes, and intelligibility targets for gates and take direction.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PB-02 must-hear words extraction + priority method."
- REASON: "Intelligibility-first requires explicit targets; this playbook makes targets testable and stable."
- IMPACT: "Faster convergence: vocalist focuses on the words that must land; QC becomes pass/fail."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB02.001

---

## 0) PURPOSE
Use this playbook when:
- hook clarity is critical
- you need a ranked must-hear target list BEFORE take direction
- you’re diagnosing why lyrics are not understood

Primary objective:
- Define WHAT MUST be understood (targets) before prescribing HOW to sing it.

---

## 1) REQUIRED INPUTS (MINIMUM)
STOP/GAP if missing:
- LYRIC_DRAFT with at least:
  - Chorus/Hook lines (or the “main message” lines)
  - Language

Recommended:
- SECTION STRUCTURE (to locate hook sections)
- Lyric variants (if available)
- Known pronunciation risks (names, slang, stress ambiguities)

---

## 2) REQUIRED OUTPUTS (MANDATORY)
This playbook MUST produce:
- MUST_HEAR_WORDS (ranked P0/P1/P2)
- MUST_HEAR_PHRASES (if single words are insufficient)
- PRONUNCIATION_RISK_NOTES (stress/cluster/foreign names)
- CLARITY_TARGETS (what “PASS” means)
- ESCALATION_NOTES (if targets cannot be made intelligible without lyric changes)
- TRACE (memory/web + gaps)

NOT READY rule:
- If no P0 targets exist → STOP (no intelligibility target).

---

## 3) PRIORITY MODEL (STRICT)
Define priorities:

P0 (ABSOLUTE):
- Hook signature words and the main message carriers:
  - the phrase people quote
  - the title line (if present)
  - the key emotional “turn” words
Rule:
- P0 must be short (3–8 items) and testable.

P1 (IMPORTANT):
- Meaning carriers that support P0:
  - key nouns/verbs that define scene/action
  - names/places (if critical)
Rule:
- P1 should be limited (5–12 items).

P2 (NICE-TO-HAVE):
- Decorative/support words:
  - adjectives, fillers, secondary images
Rule:
- P2 can be larger; it is not a hard fail target.

---

## 4) EXTRACTION METHOD (DETERMINISTIC STEPS)
### STEP 1 — Locate hook sections
1) Identify Chorus/Hook lines (or the repeated refrain).
2) If structure labels exist, map them to CHORUS sections.
3) If no chorus label exists:
   - infer “main message lines” but mark as WEAK STRUCTURE (recommend PB-01 intake fixes).

### STEP 2 — Candidate list
1) Extract candidates from hook lines:
   - nouns/verbs + unique words (avoid stop-words)
2) Extract candidates from “meaning lines” outside hook:
   - the plot/scene driver words

### STEP 3 — Remove noise
Remove from P0/P1:
- generic fillers (e.g., “и”, “но”, “это”)
- repeated function words
- words that do not change meaning if missed

### STEP 4 — Rank into P0/P1/P2
Rules:
- If word appears in hook and changes meaning → P0
- If word is title line / quote line → P0
- If word carries scene/action but not hook → P1
- If decorative/support → P2

### STEP 5 — Phrase promotion rule
If meaning depends on multi-word unit:
- promote phrase into MUST_HEAR_PHRASES (P0/P1)
Examples (pattern):
- “я возвращаюсь к своему”
- “помехи в голове” (phrase, not single word)

### STEP 6 — Pronunciation risk scan
Flag for each P0/P1 item:
- stress ambiguity (multiple stresses)
- consonant clusters that blur at tempo
- foreign names / acronyms
- repeated similar-sounding words

Output PRONUNCIATION_RISK_NOTES:
- what is risky + why + minimal non-meaning-changing fix options (phonetic spacing, syllable split).

### STEP 7 — Define CLARITY TARGETS (PASS conditions)
Define what PASS means:
- Target A: P0 words/phrases understood on first listen
- Target B: P1 understood by second listen
- Target C: P0 in chorus clearer than verses

---

## 5) ESCALATION RULES
Escalate to Lyricist/Songwriter if:
- hook phrase is unsingable at tempo without changing words
- P0 targets are too dense (too many hard consonants)
- meaning depends on long clause that cannot be articulated clearly

Escalate note must include:
- what to change (minimal)
- why (clarity/breath/stress)
- what stays fixed (meaning intent)

---

## 6) COMMON FAIL MODES
- P0 list too long (un-testable).
- P0 contains filler words.
- No phrase promotion (single words lose meaning).
- Pronunciation risks ignored (stress ambiguity not flagged).
- Targets defined, but no PASS criteria.

---

## 7) OUTPUT TEMPLATE (COPY)
### MUST_HEAR_WORDS
- P0:
- P1:
- P2:

### MUST_HEAR_PHRASES
- P0:
- P1:

### PRONUNCIATION_RISK_NOTES
- item:
  - risk:
  - why:
  - non-meaning-changing fixes:

### CLARITY_TARGETS (PASS)
- Target A:
- Target B:
- Target C:

### ESCALATION_NOTES
- to Lyricist/Songwriter:
- to Arranger/Producer (seat):

### TRACE
- MEMORY_REUSE:
- WEB_LOOKUP_USED:
- GAPS:

--- END.
