# SPC PRO PACK — CHECKLISTS (README) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/04__CHECKLISTS/00__README__CHECKLISTS.md

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
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.CHK.README.DRAFT.001
OWNER: SYSTEM
ROLE: Checklist map for PROMPT_ARCHITECT: readiness, quality, and compliance checklists; when to run each; and how they relate to gates/playbooks. Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created checklists README for PROMPT_ARCHITECT: checklist list + when-to-use mapping and gate connections."
- REASON: "Checklists provide fast operational checks and reduce gate skipping."
- IMPACT: "More consistent prompt preparation and fewer avoidable failures."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.CHK.README.001

---

## 0) PURPOSE
Checklists provide quick PASS/REWORK/FAIL signals for:
- readiness (inputs present, scope clear)
- quality (contract sanity before generation)
- compliance (no-fantasy, UID-only discipline)

Rule:
- Use checklists early and often.
- Gates remain the more formal criteria; checklists are fast filters.

---

## 1) CHECKLIST LIST (FILES IN THIS PACK)
CHECKLIST_FILES:
- 01__CHK__READINESS.md
  PURPOSE: verify required inputs, baseline freeze, and scope clarity before writing prompts

- 02__CHK__QUALITY.md
  PURPOSE: fast quality sanity before generation (hook/structure/vocals/repetition/style)

- 03__CHK__COMPLIANCE.md
  PURPOSE: ensure UID-only discipline, no-fantasy, and trace fields are present

---

## 2) WHEN TO RUN (RECOMMENDED)
RUN_MAP:
- Before PB-01 CORE WORKFLOW:
  - run CHK READINESS

- Before generating a “final” version:
  - run CHK QUALITY + (optional) gates 01–03

- After producing variants/patches:
  - run CHK COMPLIANCE + gate 05 (one-axis discipline)

- If user demands strict process:
  - run all three checklists + gates

---

## 3) CONNECTION TO GATES / PLAYBOOKS
Mapping:
- CHK QUALITY aligns to:
  - Gate 01 (contract clarity)
  - Gate 02 (voice intent)
  - Gate 03 (repetition intent)
  - Gate 04 (style stability)

- CHK COMPLIANCE aligns to:
  - Gate 05 (one-axis discipline)
  - pack policy (no-fantasy, UID-only)

If checklist fails:
- apply PB-04 PATCH MIN for localized fixes
- or PB-03 DIAGNOSE & REWORK for multi-issue cases

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- checklists are skipped in pipelines that rely on readiness/compliance
- PASS is claimed without marking checklist items

---

## 5) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.CORE.001 | WHY: core workflow depends on readiness
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 | WHY: deeper gate behind quality checklist
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 | WHY: compliance alignment

--- END.
