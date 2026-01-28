# SPC PRO PACK — TOOL (T09) — BREATH_MAP_BUILDER (NEVER_SPLIT + POLICY) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/09__T09__BREATH_MAP_BUILDER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T09
TOOL_NAME: BREATH_MAP_BUILDER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T09.BREATH_MAP_BUILDER.001
OWNER: SYSTEM
ROLE: Builds breath safety artifacts: protects P0 phrases from splits (NEVER_SPLIT_PHRASES) and defines explicit breath policy (allowed/forbidden). Does not rewrite lyrics; derives phrases copy-exact from MUST_HEAR_PHRASES.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T09 BREATH_MAP_BUILDER for VOCAL_DIRECTOR."
- REASON: "Breath splits inside must-hear phrases are hard fails; policy must be explicit."
- IMPACT: "Deterministic breath placement constraints and fewer clarity breaks."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T09.001

---

## 0) PURPOSE
Generate breath safety blocks:
- MUST_HEAR_PROTECTION_RULES
- BREATH_POLICY

Supports Gate:
- G6 BREATH / SINGABILITY

---

## 1) INPUTS (REQUIRED)
- MUST_HEAR_PHRASES.P0 (from T03) OR explicit signature phrases provided by user
- HOOK_SECTION_LABEL (recommended)
Optional:
- MUST_HEAR_WORDS.P0 (context)
- section text with line breaks

Rules:
- Phrases must be copy-exact from provided lyrics.
- If no phrases exist, tool can still output breath policy, but MUST_HEAR_PROTECTION_RULES will be minimal (N/A note inside list is NOT allowed; instead omit phrase list and rely on word-level guidance).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T09 MUST output:

### MUST_HEAR_PROTECTION_RULES
- NEVER_SPLIT_PHRASES:
  - "<copy-exact P0 phrase>"
  - "<copy-exact P0 phrase>" (optional)

### BREATH_POLICY
- allowed:
  - "<allowed breath point / principle>"
- forbidden:
  - "<explicit forbidden split>"

---

## 3) THRESHOLDS (STRICT)
- NEVER_SPLIT_PHRASES: include 1..4 phrases if available
- BREATH_POLICY must include:
  - allowed: at least 1 item
  - forbidden: at least 1 item (prefer 1..3)
- forbidden must explicitly reference:
  - splitting inside P0 phrases (primary)
  - splitting inside negative constructions when applicable (e.g., "не X")

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Build NEVER_SPLIT_PHRASES
- If MUST_HEAR_PHRASES.P0 exists:
  - copy phrases verbatim into NEVER_SPLIT_PHRASES
- If phrases do not exist:
  - do not invent phrases; keep NEVER_SPLIT_PHRASES empty (no placeholders)
  - breath protection will be expressed via forbidden rules referencing “P0 phrase units” only if user provided them

Step 2 — Create BREATH_POLICY.allowed
- Provide 1–3 concise allowed points:
  - between lines
  - after complete phrase units
  - before P0 phrase onset (micro-prep)

Step 3 — Create BREATH_POLICY.forbidden
- Provide explicit forbidden splits:
  - "inside any NEVER_SPLIT_PHRASES item"
  - if negative constructions exist in phrases: "between 'не' and the negated word" (only if that exact construction exists in text)

Step 4 — Output stable blocks

---

## 5) STOP / GAP CONDITIONS
Stop and request missing inputs if:
- phrases are required (meaning depends on them) but MUST_HEAR_PHRASES is missing and user did not provide exact phrases
Request:
- “Provide exact hook line(s) / signature phrase(s) copy-exact.”

---

## 6) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- rewriting phrases or suggesting replacements
- inventing phrases not present
- prescribing mix chain to “fix breath”

Allowed:
- performer breath placement constraints

---

## 7) TRACE
TRACE:
- TOOL: T09
- OUTPUTS: MUST_HEAR_PROTECTION_RULES, BREATH_POLICY
- SUPPORTS_GATE: G6

--- END.
