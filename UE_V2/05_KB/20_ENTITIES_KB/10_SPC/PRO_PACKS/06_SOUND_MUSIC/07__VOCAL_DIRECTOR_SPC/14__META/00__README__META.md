# SPC PRO PACK — META (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/14__META/00__README__META.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: README
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.META.README.DRAFT.001
OWNER: SYSTEM
ROLE: Defines the META folder for VOCAL_DIRECTOR Pro Pack: changelog, roadmap, known gaps, and dependency notes. META is operational bookkeeping only; it must not introduce new rules that override Gates/Tools/Playbooks.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created META README for VOCAL_DIRECTOR: purpose + non-authority rule + file roadmap."
- REASON: "Need a clean place for maintenance notes without polluting operational laws."
- IMPACT: "Safer evolution and clearer maintenance."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.META.README.001

---

## 0) PURPOSE
This folder contains maintenance metadata for the VOCAL_DIRECTOR Pro Pack:
- change history for this pack
- roadmap for future additions
- known gaps and TODOs (non-authoritative)
- dependency notes (what this pack relies on)

---

## 1) NON-AUTHORITY RULE (ABSOLUTE)
META files are NOT operational authority.

META MUST NOT:
- introduce new gates/tools/playbook rules
- override thresholds or change pass/fail logic
- define new scope permissions

META MAY:
- record what changed, why, and when
- list future work items
- list known gaps and risks
- list dependencies and references (as notes)

Authority lives in:
- 07__TOOLS
- 08__PLAYBOOKS
- 09__GATES
- 10__OUTPUT_PACKS
- 11__PROMPT_CONTRACTS
- 12__CHECKLISTS
- 13__CASE_LIBRARY

---

## 2) WHAT BELONGS HERE
### A) CHANGELOG
- log of edits made to this pro pack (file additions, schema changes)
- concise entries

### B) ROADMAP
- planned additions (new tools, new cases, better templates)
- no rules inside; only plan items

### C) KNOWN GAPS
- what is missing, unclear, or needs research
- link to where the fix should be applied (tool/gate/etc.)

### D) DEPENDENCIES
- what this pack depends on (e.g., stable block names, gate order)
- any cross-pack assumptions (notes only)

---

## 3) SCOPE REMINDER (ALWAYS)
Even in META notes:
- No lyric rewrites allowed in VOCAL_DIRECTOR outputs
- No mix/master plugin chains allowed
- Ownership issues → escalation notes (T14)

---

## 4) NEXT FILES (ORDER)
Proceed in numeric order (one file per step):
- 01__CHANGELOG.md
- 02__ROADMAP.md
- 03__KNOWN_GAPS.md
- 04__DEPENDENCIES.md

--- END.
