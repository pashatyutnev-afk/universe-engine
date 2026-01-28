# SPC PRO PACK — TOOL (T03) — PHRASE_PROMOTION_HELPER (COPY-EXACT) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/03__T03__PHRASE_PROMOTION_HELPER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T03
TOOL_NAME: PHRASE_PROMOTION_HELPER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T03.PHRASE_PROMOTION_HELPER.001
OWNER: SYSTEM
ROLE: Promotes copy-exact lyric phrases into MUST_HEAR_PHRASES (P0/P1) when meaning depends on multi-word units. Enforces strict copy-only rule and phrase count limits. Supports G2 and breath protection in G6.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T03 PHRASE_PROMOTION_HELPER for VOCAL_DIRECTOR."
- REASON: "Some meaning is phrase-based; word-only targets fail to protect meaning and breath safety."
- IMPACT: "More reliable hook recognition; stronger breath split protection."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T03.001

---

## 0) PURPOSE
Generate stable phrase targets:
- MUST_HEAR_PHRASES (P0/P1) — copy-exact phrases
Optionally:
- PHRASE_NOTES (internal notes; may be omitted in output packs)

Supports Gates:
- G2 MUST-HEAR (phrase requirement)
- G6 BREATH/SINGABILITY (never split phrases)

---

## 1) INPUTS (REQUIRED)
- hook/chorus lyrics text (copy-exact)
- MUST_HEAR_WORDS (from T02) (recommended)
Optional:
- user-specified “signature line” (if present in lyrics)

Rules:
- T03 may only extract phrases that appear verbatim in the provided hook text.
- No paraphrase, no synonym substitution, no punctuation rewriting that changes words.

---

## 2) OUTPUT BLOCK (STABLE NAME)
T03 MUST output:

### MUST_HEAR_PHRASES
- P0:
  - "<copy-exact phrase>"
- P1:
  - "<copy-exact phrase>" (optional)

Optional helper block (NOT required in output packs):
- PHRASE_NOTES:
  - "<why this phrase matters>"

---

## 3) WHEN PHRASES ARE REQUIRED (DETERMINISTIC RULES)
Promote a phrase if ANY is true:
- negative construction carries meaning:
  - RU: "не X", "без X", "никогда не X"
  - EN: "not X", "no X", "never X"
- signature line / slogan (hook identity) is multi-word
- meaning changes if phrase is split or only one word is heard
- the hook's “message” is expressed as a unit (verb+object, idiom-like)

Do NOT promote phrases when:
- it would create >4 phrases total
- phrases are redundant duplicates
- phrase is too long and contains multiple clauses (use shorter sub-phrase if present verbatim)

---

## 4) LIMITS (STRICT)
- P0 phrases: 1..4 (prefer 1..2)
- P1 phrases: 0..2
- Total phrases (P0+P1): <=4 (hard max)

If more than 4 candidates exist:
- keep only the strongest identity/meaning units (prioritize P0)
- drop the rest

---

## 5) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Scan hook for phrase candidates
- Identify contiguous word spans that match the “required” rules above

Step 2 — Validate copy-exactness
- Ensure candidate phrase appears verbatim in the hook text
- Preserve original spelling/case as in text (copy-exact)

Step 3 — Rank candidates
Prioritize:
- phrase contains P0 words
- phrase is the hook identity line
- phrase is a negative construction
Deprioritize:
- filler-heavy phrases
- very long phrases

Step 4 — Select P0 phrases (1..2 preferred, <=4 max)
- Choose top-ranked phrases
- Ensure no duplicates

Step 5 — Select optional P1 phrase(s)
- Only if needed and within total limit

Step 6 — Emit MUST_HEAR_PHRASES
- P0 first, then P1 (optional)

---

## 6) STOP / GAP CONDITIONS
Stop and request missing inputs if:
- hook text missing
- hook text does not contain any eligible phrases but meaning clearly depends on phrase (requires user confirmation of signature line)
(Do not invent; ask for the exact line.)

---

## 7) ANTI-GUESSING (ABSOLUTE)
Forbidden:
- paraphrasing (“same meaning”) phrases
- merging words across line breaks into a new phrase not present verbatim
- inventing “better” phrase
- exceeding phrase limits

---

## 8) TRACE
TRACE:
- TOOL: T03
- OUTPUTS: MUST_HEAR_PHRASES
- SUPPORTS_GATES: G2, G6

--- END.
