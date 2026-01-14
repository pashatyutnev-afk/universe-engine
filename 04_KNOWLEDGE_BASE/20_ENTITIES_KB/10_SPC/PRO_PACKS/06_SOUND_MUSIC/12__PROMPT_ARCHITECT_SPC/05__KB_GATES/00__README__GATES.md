# SPC PRO PACK — KB GATES (README) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/05__KB_GATES/00__README__GATES.md

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
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.GATES.README.DRAFT.001
OWNER: SYSTEM
ROLE: Gate map for PROMPT_ARCHITECT: what gates exist in this pack, when to run them, and how they connect to playbooks and rework loops. Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gates README for PROMPT_ARCHITECT: gate list, run order, and playbook mapping."
- REASON: "SPC Pro Pack must be testable; gates define PASS/REWORK/FAIL criteria for prompt outputs."
- IMPACT: "More consistent QA convergence and less subjective decisions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.GATES.README.001

---

## 0) PURPOSE
These gates evaluate prompt contracts and iteration discipline:
- detect contradictions and overload early
- enforce structure/hook clarity
- enforce vocal diversity intent
- enforce repetition control intent
- enforce “one-axis change” iteration discipline

Rule:
- Gates are lightweight and operational.
- Domain-level audio QA gates may exist elsewhere; this pack focuses on prompt-level quality.

---

## 1) GATE LIST (FILES IN THIS PACK)
GATE_FILES:
- 01__GATE__PROMPT_CONTRACT_CLARITY.md
  PURPOSE: detect missing blocks, contradictions, overload
  TYPE: KEY-CANDIDATE (pack-level)

- 02__GATE__VOICE_DIVERSITY_INTENT.md
  PURPOSE: ensure vocal roles/contrast are specified sufficiently

- 03__GATE__REPETITION_CONTROL_INTENT.md
  PURPOSE: ensure verse novelty constraints + repetition policy exist

- 04__GATE__STYLE_FINGERPRINT_STABILITY.md
  PURPOSE: ensure anchors + dominance rules (if fusion) and avoid drift

- 05__GATE__ONE_AXIS_CHANGE_DISCIPLINE.md
  PURPOSE: ensure iteration changes only 1 axis per loop and is logged

Notes:
- Start by implementing 01–03 as minimum L3 set.
- 04–05 strengthen pro-level stability.

---

## 2) RUN ORDER (RECOMMENDED)
Default:
1) GATE 01 (clarity) — always
2) GATE 02/03 — if vocals/lyrics constraints in scope (usually yes)
3) GATE 04 — if drift/fusion risk present
4) GATE 05 — when doing variants or rework loops

---

## 3) PLAYBOOK MAPPING (WHEN A GATE FAILS)
If fails:
- Gate 01 → use PB-01 CORE WORKFLOW or PB-04 PATCH MIN
- Gate 02 → use PB-05 VOCAL DIVERSITY BOOST
- Gate 03 → use PB-06 ANTI-REPETITION FIX
- Gate 04 → use PB-07 STYLE STABILIZER
- Gate 05 → use PB-02 ONE-AXIS VARIANTS + PB-03 DIAGNOSE

---

## 4) OUTPUT TYPES CHECKED
- Prompt Contract text (blocks)
- Variant delta logs (when applicable)
- Patch instructions (when applicable)

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- gates are skipped silently in a pipeline that requires them
- gate outcomes are ignored without rework plan
- gate definitions are ambiguous (“looks good”)

---

## 6) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.CORE.001 | WHY: primary method
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal fixes after failures
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001 | WHY: gate-aligned rework loops
- UE.KB.QA.STD.CONNECTOR.001 | WHY: QA discipline reference
- UE.KB.VAL.STD.CONNECTOR.001 | WHY: criterion alignment

--- END.
