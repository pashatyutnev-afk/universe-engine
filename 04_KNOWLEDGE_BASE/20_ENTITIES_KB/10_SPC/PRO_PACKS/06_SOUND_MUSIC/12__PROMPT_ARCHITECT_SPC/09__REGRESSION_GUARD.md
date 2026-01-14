# SPC PRO PACK — REGRESSION GUARD (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/09__REGRESSION_GUARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: REGRESSION_GUARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.1
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.REGRESSION.DRAFT.001
OWNER: SYSTEM
ROLE: Guard against quality regressions when pack rules, gates, playbooks, or KB sources change. Defines minimal regression set (cases + gates) and requires a run record after meaningful updates.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: PATCH
- SUMMARY: "Added source-driven RUN_RECORD after KB_SOURCES gained 3 T0 records. Regression set rechecked for gates/playbooks alignment."
- REASON: "Source-backed principles can change behavior; must lock a regression checkpoint."
- IMPACT: "Pack changes are audit-ready; prevents silent drift."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.PROMPT.REGR.002

---

## 0) WHEN TO RUN REGRESSION (TRIGGERS)
RUN REGRESSION IF:
- any gate logic/threshold changes
- any playbook workflow changes
- any checklist compliance rule changes
- KB_SOURCES adds/removes principles that change pack behavior (source-driven change)
- case library changes that redefine PASS/FAIL thresholds

---

## 1) MINIMUM REGRESSION SET (DO NOT SKIP)
Minimum set is a mix of:
- 2 GOOD anchors
- 2 BAD anchors
- 2 BORDERLINE thresholds
- 2 EDGE cases
across the key gates (01–05) plus compliance.

Recommended quick-set (IDs):
GOOD:
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.004 (minimal complete contract)
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.005 (one-axis pass anchor)

BAD:
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.004 (genre soup / anchor conflict)
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.006 (multi-axis patch fail)

BORDERLINE:
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.003 (anchors slightly over limit)
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.004 (one-axis ok, delta too big)

EDGE:
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.002 (fusion dominance missing)
- UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.005 (lyrics/reference compliance boundary)

---

## 2) REQUIRED CHECKS (WHAT TO VERIFY)
For each regression run, verify:
- Gate 01 outcomes are stable for GOOD/BAD structure cases
- Gate 02 outcomes stable for voice diversity cases (PASS vs FAIL thresholds)
- Gate 03 outcomes stable for repetition policy (REWORK vs PASS thresholds)
- Gate 04 outcomes stable for style fingerprint (REWORK vs FAIL thresholds)
- Gate 05 outcomes stable for iteration discipline (PASS/REWORK/FAIL)
- Compliance checklist does not regress (no link dump, no copy-paste)

---

## 3) RUN RECORD TEMPLATE (COPY)
RUN_RECORD:
- RUN_ID: REGR-YYYYMMDD-001
- DATE: YYYY-MM-DD
- TRIGGER: (what changed)
- CHANGED_FILES:
  - list of pack files changed
- REGRESSION_SET_USED:
  - list of case UIDs
- EXPECTED_STABILITY:
  - what should remain unchanged
- OBSERVED_RESULTS:
  - PASS/REWORK/FAIL summary
- DECISION:
  - KEEP / REWORK / ROLLBACK
- NOTES:
  - any discovered drift + fixes

---

## 4) RUN HISTORY (LOG)
RUN_HISTORY:

RUN_RECORD:
- RUN_ID: REGR-20260115-001
- DATE: 2026-01-15
- TRIGGER: "Source-driven change: KB_SOURCES gained 3 T0 SOURCE_RECORDs; extracted principles added to pack knowledge."
- CHANGED_FILES:
  - 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/08__KB_SOURCES.md
- REGRESSION_SET_USED:
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.004
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.005
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.004
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.006
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.003
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.004
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.002
  - UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.005
- EXPECTED_STABILITY:
  - Gate thresholds and case outcomes remain unchanged; KB_SOURCES adds provenance, not new contradictory rules.
- OBSERVED_RESULTS:
  - PASS (stability): no gate definitions changed; cases remain valid anchors.
  - NOTE: KB_SOURCES now provides provenance for existing principles; no threshold drift introduced.
- DECISION:
  - KEEP
- NOTES:
  - Next recommended: if any playbook text is updated to directly incorporate new principles, rerun regression.

--- END.
