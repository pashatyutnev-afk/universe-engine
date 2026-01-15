# SPC PRO PACK — KNOWN GAPS (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/14__META/03__KNOWN_GAPS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: KNOWN_GAPS
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.KNOWN_GAPS.001
OWNER: SYSTEM
ROLE: Maintenance list of known gaps/weaknesses in VOCAL_DIRECTOR Pro Pack coverage, including where to patch and the risk if not addressed. Non-authoritative.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Initial known gaps list created."
- REASON: "Track weaknesses without mixing into operational rules."
- IMPACT: "Improves future iterations and test coverage."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.GAPS.001

---

## 0) GAP LIST (NON-AUTHORITY)
Each gap includes:
- GAP_ID
- description
- patch_location (where to fix)
- risk_if_unfixed

---

## G-01 — NO FILLED EXAMPLE PACKS
description:
- No fully filled MIN/STD/FULL examples exist yet; only templates.
patch_location:
- 10__OUTPUT_PACKS (add example docs) + 11__PROMPT_CONTRACTS (example prompts)
risk_if_unfixed:
- Operators may misfill blocks or change block names/order accidentally.

---

## G-02 — LIMITED “STRESS HOTSPOTS” GUIDANCE (RU PRONUNCIATION)
description:
- Russian stress and consonant cluster hotspot notes are not formalized (notes-only desired).
patch_location:
- 07__TOOLS (add a notes-only analyzer tool) + 13__CASE_LIBRARY (add RU cluster subcases)
risk_if_unfixed:
- Higher rate of consonant loss (T1/T5) in fast lines; repeated trial-and-error.

---

## G-03 — PLATFORM LENGTH/FORMAT LIMITS NOT ENCODED
description:
- SUNO/UDIO prompt length limits and formatting preferences are not encoded beyond templates.
patch_location:
- 11__PROMPT_CONTRACTS (add platform variants / compact versions)
risk_if_unfixed:
- Prompts may be too long or poorly formatted; reduced compliance with platform behavior.

---

## G-04 — NO “LISTEN TEST PROTOCOL” PACK
description:
- No dedicated short listening test protocol (10s/15s/first-listen scoring) besides gates/checklists.
patch_location:
- 12__CHECKLISTS (add listen-test checklist) or 07__TOOLS (add test harness tool)
risk_if_unfixed:
- Subjective “sounds ok” decisions; inconsistent gate verdicts across runs.

---

## G-05 — LIMITED CROSS-ENTITY HANDOFF STANDARD
description:
- Escalation notes exist as a concept but cross-entity fields are not standardized beyond T14 mention.
patch_location:
- 07__TOOLS (expand escalation skeleton) + 14__DEPENDENCIES (note interface expectations)
risk_if_unfixed:
- Escalations lack actionable structure; slow resolution of T4/T7 cases.

---

## G-06 — SUB-CASES FOR HYBRID VOCALS NOT WRITTEN
description:
- No sub-cases for rap+melodic hybrid transitions (common masking points).
patch_location:
- 13__CASE_LIBRARY (add additional case files)
risk_if_unfixed:
- Repeated confusion between T5 (delivery masking) and T8 (arc leverage) in hybrids.

---

## G-07 — “REGRESSION GUARD” NOT EXPLICIT
description:
- One-axis discipline exists, but explicit regression guard checklist is not present.
patch_location:
- 12__CHECKLISTS (add small regression guard checklist)
risk_if_unfixed:
- Fixing one issue accidentally breaks P0 clarity elsewhere; more loops.

---

## TRACE
TRACE:
- DOC: KNOWN_GAPS
- UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.KNOWN_GAPS.001

--- END.
