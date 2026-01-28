# CASE — BORDERLINE (KB_SOURCES LINK DUMP / NO PRINCIPLES EXTRACTED) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/22__CASE__BORDERLINE_005.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.005
OWNER: SYSTEM
ROLE: Borderline case calibrating COMPLIANCE REWORK: KB_SOURCES contains a link dump (many URLs/titles) but no extracted operational principles and no provenance metadata. Should trigger REWORK (not FAIL) because a minimal fix is to convert links into SOURCE_RECORDs with 5–12 extracted principles.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BORDERLINE case #5: KB_SOURCES link dump → compliance REWORK; fix by adding SOURCE_RECORD metadata + extracted principles."
- REASON: "Pack must leverage world knowledge without turning into a link pile; provenance must be operational."
- IMPACT: "Cleaner KB_SOURCES and less hallucination."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BORDERLINE.005

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BL-005
- TYPE: BORDERLINE
- CONTEXT:
  - AREA: KB_SOURCES maintenance
  - RISK: sources recorded without usable extracted principles
- INPUT_INTENT (short):
  - Someone tries to “add sources” by dumping links; pack cannot use them deterministically.

---

## 1) BORDERLINE PROBLEM (EXAMPLE)
BAD_KB_SOURCES_ENTRY:
- "Here are links about prompting, hooks, repetition..."
- URL1, URL2, URL3, URL4...
- (no DATE_ACCESSED)
- (no authority tier)
- (no extracted principles)
- (no where-applied mapping)
- (no copyright note)

This is not an immediate FAIL if:
- no rules were derived yet
- and it can be fixed quickly by adding proper SOURCE_RECORD blocks.

---

## 2) EXPECTED COMPLIANCE OUTCOME (UID-ONLY)
EXPECTED_RESULTS:
- UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001 -> REWORK
  WHY: provenance discipline incomplete (no extracted principles; link dump)

Secondary implication:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.SOURCES.DRAFT.001 -> needs proper SOURCE_RECORD entries (per its own rules)

---

## 3) WHY THIS IS BORDERLINE (NOT FAIL)
WHY_BORDERLINE:
- Problem is structural/procedural, not malicious:
  - links exist but are not operational
- Minimal repair is deterministic:
  - convert each “link” into SOURCE_RECORD
  - extract 5–12 paraphrased operational principles
- No need to rewrite the entire pack; just fix KB_SOURCES entries.

---

## 4) MINIMAL FIX (TO REACH PASS)
Fix steps:
1) Pick 1–3 best sources (do not keep dozens).
2) For each, create SOURCE_RECORD:
   - TITLE, TYPE, AUTHORITY_TIER
   - DATE_ACCESSED, LAST_VERIFIED, REFRESH_INTERVAL
   - EXTRACTED PRINCIPLES (5–12 bullets, actionable)
   - APPLIED_IN_PACK (which playbook/gate it informs)
   - COPYRIGHT NOTE: confirm no large copy
3) Delete raw link dump after conversion.

Result:
- Compliance checklist should PASS (provenance discipline satisfied).

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
