# SPC PRO PACK — TOOL (T02) — MUST_HEAR_BUILDER (P0/P1/P2) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/02__T02__MUST_HEAR_BUILDER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T02
TOOL_NAME: MUST_HEAR_BUILDER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T02.MUST_HEAR_BUILDER.001
OWNER: SYSTEM
ROLE: Builds prioritized must-hear word targets (P0/P1/P2) from provided lyrics and hook section. Enforces thresholds and filler exclusion. Does not invent words; only selects from text.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T02 MUST_HEAR_BUILDER for VOCAL_DIRECTOR."
- REASON: "Without correct must-hear priorities, intelligibility work becomes subjective."
- IMPACT: "Deterministic target lists for G2/G3 and downstream packs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T02.001

---

## 0) PURPOSE
Generate stable target blocks:
- MUST_HEAR_WORDS (P0/P1/P2)
- CLARITY_TARGETS

Supports Gate:
- G2 MUST-HEAR

---

## 1) INPUTS (REQUIRED)
- hook/chorus lyrics text (copy-exact)
- HOOK_SECTION_LABEL (from T01)
Optional:
- full song lyrics (for context)
- user-specified must-keep words (if provided)

Rules:
- T02 may only select words that appear in the provided hook text.
- If hook text is not provided → STOP (GAP).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T02 MUST output:

### MUST_HEAR_WORDS
- P0: <comma list>
- P1: <comma list or N/A>
- P2: <comma list or N/A>

### CLARITY_TARGETS
- Target A: "P0 understood on first listen in HOOK"
- Target B (optional): "No breath split inside P0 phrases" (added if phrases exist later)
- Target C (optional): "Hook clarity >= verse baseline" (if verse baseline is available)

---

## 3) THRESHOLDS (STRICT)
- P0 count: 3..8 (default)
  - exception: 2 only if hook is extremely short (must note)
- P1 count: 0..12 (or N/A with reason)
- P2 optional

Filler rule:
- Fillers must NOT be placed in P0.

Filler examples (language-dependent; not exhaustive):
- RU: "я, ты, мы, он, она, они, это, тот, тут, там, как, что, чтобы, и, но, а, на, в, к, с, из, у"
- EN: "I, you, we, he, she, it, this, that, and, but, or, to, of, in, on, at"

Note:
- If a “filler” is semantically critical in context (rare), it may be P1, not P0.

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Tokenize hook words
- Extract candidate words from hook text (strip punctuation)
- Keep original word forms as they appear

Step 2 — Remove obvious fillers from P0 pool
- Filter stopwords/fillers for the given language
- Keep them available for P1/P2 if needed

Step 3 — Score remaining candidates (simple deterministic heuristic)
Prioritize:
- nouns/verbs/adjectives (meaning carriers)
- repeated keywords (appear multiple times in hook)
- title/identity words (if user specified)
Deprioritize:
- short function words
- interjections/fillers

Step 4 — Select P0 (3..8)
- Take top-scored meaning carriers
- If duplicates/near-duplicates: keep only one
- Ensure P0 is not bloated

Step 5 — Select P1 (0..12)
- Add secondary meaning carriers not in P0
- Or set N/A if hook is extremely minimal and P0 already covers meaning

Step 6 — Optional P2
- Only if helpful; keep small

Step 7 — Emit CLARITY_TARGETS
- Always include Target A

---

## 5) STOP / GAP CONDITIONS
Stop and request missing inputs if:
- hook text not provided
- language not specified (do not infer)
- HOOK_SECTION_LABEL missing

GAP response should request:
- hook/chorus lines + language + section label

---

## 6) ANTI-GUESSING RULES
Forbidden:
- inventing words not in hook text
- selecting “synonyms” not present
- bloating P0 beyond 8 “just in case”

---

## 7) TRACE
TRACE:
- TOOL: T02
- OUTPUTS: MUST_HEAR_WORDS, CLARITY_TARGETS
- SUPPORTS_GATE: G2

--- END.
