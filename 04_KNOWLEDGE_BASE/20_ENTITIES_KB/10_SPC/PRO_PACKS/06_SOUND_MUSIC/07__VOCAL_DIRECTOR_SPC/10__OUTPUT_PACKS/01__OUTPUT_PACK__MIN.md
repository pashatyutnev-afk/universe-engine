# SPC PRO PACK — OUTPUT PACK (MIN) — VOCAL_DIRECTOR (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/10__OUTPUT_PACKS/01__OUTPUT_PACK__MIN.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: OUTPUT_PACK
PACK_TIER: MIN
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.OUTPUT.MIN.001
OWNER: SYSTEM
ROLE: Minimal output contract for VOCAL_DIRECTOR: fastest usable pack for quick generation runs. Must be scope-safe and contain minimum must-hear targeting.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created OUTPUT PACK MIN template for VOCAL_DIRECTOR."
- REASON: "Need a minimal, consistent deliverable shape for fast iteration."
- IMPACT: "Faster runs with deterministic must-hear targets and compliance."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.OUTPUT.MIN.001

---

## 0) PURPOSE
MIN pack is a “fast draft” contract:
- includes minimum blocks to run safely
- prioritizes must-hear targeting and scope compliance
- avoids deep arc/take planning unless requested

---

## 1) REQUIRED GATES (MIN)
Must PASS:
- G1 INPUT READINESS
- G2 MUST-HEAR
- G9 SCOPE COMPLIANCE

Should PASS (recommended):
- G3 INTELLIGIBILITY (lightweight check)

---

## 2) REQUIRED BLOCKS (STABLE NAMES ONLY)
MIN pack must include exactly these blocks (in order):

1) MIN_INPUTS_CHECK
2) HOOK_SECTION_LABEL
3) MUST_HEAR_WORDS
4) MUST_HEAR_PHRASES (recommended; include if phrases required)
5) CLARITY_TARGETS
6) SCOPE_AUDIT
7) ESCALATION_NOTES (only if needed)

Rule:
- Do not include mixing chains or lyric replacements.
- Use copy-exact phrases only (no paraphrase).

---

## 3) TEMPLATE (FILL-IN)
### MIN_INPUTS_CHECK
MIN_INPUTS_CHECK:
- LYRIC_DRAFT_PRESENT: YES/NO
- SECTION_STRUCTURE_PRESENT: YES/NO
- LANGUAGE_PRESENT: YES/NO
- HOOK_SECTION_IDENTIFIABLE: YES/NO

### HOOK_SECTION_LABEL
HOOK_SECTION_LABEL:
- value: "<e.g., Chorus 1 (HOOK)>"
- why: "<1 line>"

### MUST_HEAR_WORDS
MUST_HEAR_WORDS:
- P0: <comma list>
- P1: <comma list or N/A>
- P2: <comma list or N/A>

### MUST_HEAR_PHRASES (optional but recommended)
MUST_HEAR_PHRASES:
- P0:
  - "<copy-exact phrase>"
- P1:
  - "<copy-exact phrase>" (optional)

### CLARITY_TARGETS
CLARITY_TARGETS:
- Target A: "P0 understood on first listen in HOOK"
- Target B (optional): "No breath split inside P0 phrases"

### SCOPE_AUDIT
SCOPE_AUDIT:
- lyric_rewrite_present (F1): NO
- structure_edit_present (F2): NO
- arrangement_ownership_present (F3): NO
- mix_chain_present (F4): NO
- guessing_present (F5): NO

### ESCALATION_NOTES (only if needed)
ESCALATION_NOTES:
- owner:
- section:
- problem:
- request (principles only):
  - 1)
- must_keep:
  - 1)
- forbidden (scope):
  - 1)
- success_criteria:
  - 1)
- next_check:
  - "Rerun G1/G2/G9" (as appropriate)

---

## 4) VALIDATION RULES (MIN)
- If MIN_INPUTS_CHECK has any NO → stop; request missing inputs (do not produce targets).
- P0 must be present (3..8, or 2 if hook is extremely short with note).
- If phrases are required (meaning unit) but absent → treat as REWORK; add phrases.
- Scope audit must remain clean (F1/F4 always NO).

---

## 5) NEXT PACK
If MIN pack is insufficient (needs full execution):
- upgrade to STD output pack.

--- END.
