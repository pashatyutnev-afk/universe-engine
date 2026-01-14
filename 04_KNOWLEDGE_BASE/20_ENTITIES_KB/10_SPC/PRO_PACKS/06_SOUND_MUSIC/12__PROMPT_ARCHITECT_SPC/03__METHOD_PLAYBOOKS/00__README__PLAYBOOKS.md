# SPC PRO PACK — PLAYBOOKS (README) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/00__README__PLAYBOOKS.md

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
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PLAYBOOKS.README.DRAFT.001
OWNER: SYSTEM
ROLE: Playbook index for PROMPT_ARCHITECT: what each playbook does and when to use it. Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created playbooks README for PROMPT_ARCHITECT: execution map + when-to-use guidance."
- REASON: "SPC needs deterministic selection of methods; README maps scenarios to playbooks."
- IMPACT: "Faster correct method choice and fewer random rewrites."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.README.001

---

## 0) PURPOSE
Playbooks define repeatable execution methods:
- build prompt contracts
- generate controlled variants
- diagnose failures
- patch with minimal change
- prepare QA recheck

Rule:
- Use the correct playbook instead of improvising.

---

## 1) PLAYBOOK LIST (CANON FOR THIS PACK)
### PB-01 — CORE WORKFLOW (BUILD CONTRACT)
FILE: 01__PLAYBOOK__CORE_WORKFLOW.md
WHEN:
- you need a prompt from scratch
- you need to convert intent into a full contract (sections + vocals + negatives)
OUTPUT:
- prompt contract + initial variant set (optional)

### PB-02 — ONE-AXIS VARIANTS (A/B LEARNING)
FILE: 02__PLAYBOOK__ONE_AXIS_VARIANTS.md
WHEN:
- you need controlled experimentation
- you want to isolate what changes affect the output
OUTPUT:
- 2–5 variants, each changing only one axis

### PB-03 — DIAGNOSE & REWORK (GATE-ALIGNED)
FILE: 03__PLAYBOOK__DIAGNOSE_AND_REWORK.md
WHEN:
- QA/VAL returns REWORK/FAIL
- you need to map failure → minimal fix
OUTPUT:
- diagnosis + patch plan + recheck method

### PB-04 — PATCH PROMPT (MINIMAL CHANGE)
FILE: 04__PLAYBOOK__PATCH_PROMPT_MINIMAL_CHANGE.md
WHEN:
- the output is close but fails one key dimension (voice sameness, repetition, muddy)
- you must preserve identity
OUTPUT:
- patch prompt instructions (change 1–2 axes)

### PB-05 — VOCAL DIVERSITY BOOST (ANTI “SAME SINGER”)
FILE: 05__PLAYBOOK__VOCAL_DIVERSITY_BOOST.md
WHEN:
- voices are too similar across sections or tracks
- you need explicit role separation and contrast levers
OUTPUT:
- vocal intent block + targeted negatives + section role map

### PB-06 — ANTI-REPETITION FIX (PHRASE/MOTIF)
FILE: 06__PLAYBOOK__ANTI_REPETITION_FIX.md
WHEN:
- repeated lines/patterns appear
- chorus repetition bleeds into verses
OUTPUT:
- variation constraints + targeted negatives + recheck checklist

### PB-07 — STYLE FINGERPRINT STABILIZER (DRIFT CONTROL)
FILE: 07__PLAYBOOK__STYLE_FINGERPRINT_STABILIZER.md
WHEN:
- genre identity drifts
- output becomes “random mix”
OUTPUT:
- anchor markers + dominance rules + simplified instrument roles

### PB-08 — FINAL QA PRECHECK (BEFORE SUBMIT)
FILE: 08__PLAYBOOK__FINAL_QA_PRECHECK.md
WHEN:
- before generating final version / before “release-ready” step
OUTPUT:
- precheck result + minimal last patch (if needed)

Notes:
- This pack starts with README + PB-01 next. Other playbooks can be stubbed and filled later.

---

## 2) PLAYBOOK SELECTION RULE (FAST)
If:
- building from scratch → PB-01
- need learning/experimentation → PB-02
- gate failed → PB-03
- near-pass but one issue → PB-04
- voice sameness → PB-05
- repetition → PB-06
- style drift → PB-07
- final pass attempt → PB-08

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- playbooks are used without defining outputs
- rework happens without one-axis change discipline
- playbook selection is random and not scenario-based

---

## 4) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.POLICY.DRAFT.001 | WHY: principles constrain playbook behavior
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.SKILLTREE.DRAFT.001 | WHY: skills map to playbooks
- UE.KB.QA.STD.CONNECTOR.001 | WHY: QA-first tuning alignment

--- END.
