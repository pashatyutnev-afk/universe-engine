# SPC PRO PACK — PLAYBOOKS (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/00__README__PLAYBOOKS.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PLAYBOOKS.README.DRAFT.001
OWNER: SYSTEM
ROLE: Map of Playbooks (PB-01..PB-08) for VOCAL_DIRECTOR Pro Pack: what each PB fixes (one axis only), required inputs, expected artifacts, and rerun gates. Playbooks are repair procedures; Tools generate artifacts; Gates validate.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PLAYBOOKS README for VOCAL_DIRECTOR: PB catalog + axis mapping + rerun gates + file order."
- REASON: "Repairs must be deterministic and non-regressive; playbooks encode one-axis patches."
- IMPACT: "Faster triage and fewer loops."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.PB.README.001

---

## 0) PURPOSE
Playbooks (PB) are deterministic repair procedures applied AFTER a failure is identified.

They:
- fix ONE axis only (one-axis discipline)
- define what to change / what NOT to change
- define which gates must be rerun

They do NOT:
- rewrite lyrics
- prescribe mix/master plugin chains

---

## 1) ONE-AXIS RULE (ABSOLUTE)
- One PB per patch iteration.
- Do not mix PBs in one patch.
- After patch, rerun required gates and verify G3 if clarity could be affected.

Routing is done by:
- T15 REPAIR_ROUTER (type_code → axis → PB → rerun gates)

---

## 2) PB CATALOG (PB-01..PB-08)
PB-01 — PROFILE_COHERENCE_PATCH
- axis: A4
- fixes: contradictory/vague delivery profile; overload
- primary gates: G4 (verify G3)

PB-02 — TARGETS_REBUILD_PATCH
- axis: A1
- fixes: P0 missing/bloat; phrase promotion missing
- primary gates: G2 → (verify) G3

PB-03 — ATTACK_CLARITY_PATCH
- axis: A1
- fixes: swallowed consonant attacks; delivery masking on P0
- primary gates: G3

PB-04 — BREATH_DENSITY_PATCH
- axis: A3
- fixes: breath split inside P0; density risk; R2 escalation trigger
- primary gates: G6 → G3

PB-05 — ARC_LEVER_PATCH
- axis: A2
- fixes: flat arc or lever overload; prune to <=3 levers
- primary gates: G5 → (verify) G3

PB-06 — TAKE_PACK_PATCH
- axis: A6
- fixes: missing/weak take plan; repeatability rules; QC hard fails
- primary gates: G8

PB-07 — STACKING_SAFE_PATCH
- axis: A5
- fixes: stacking masking; missing protected zones/QC rules
- primary gates: G7 → G3

PB-08 — COMPLIANCE_ONE_AXIS_PATCH
- axis: A7
- fixes: scope violations (F1..F5); convert ownership to escalation
- primary gates: G9

---

## 3) PB ↔ TOOLS ↔ GATES (SUMMARY)
PB-01:
- tools: T06/T07
- rerun: G4 → (verify) G3

PB-02:
- tools: T02/T03
- rerun: G2 → G3

PB-03:
- tools: T05 (+ T04 if checklist missing)
- rerun: G3

PB-04:
- tools: T09/T10 (+ T14 if escalation)
- rerun: G6 → G3

PB-05:
- tools: T08
- rerun: G5 → (verify) G3

PB-06:
- tools: T12
- rerun: G8

PB-07:
- tools: T11
- rerun: G7 → G3

PB-08:
- tools: T13 (+ T14 if conversion)
- rerun: G9

---

## 4) PLAYBOOK OUTPUT CONTRACT (COMMON)
Every PB file must include:
- PURPOSE
- INPUTS REQUIRED
- PATCH SCOPE (what to change)
- DO NOT CHANGE (protected blocks)
- PROCEDURE (steps)
- RERUN GATES
- HARD STOPS (scope)
- TRACE

---

## 5) NEXT FILES (ORDER)
Proceed in numeric order:
- 01__PB-01__PROFILE_COHERENCE_PATCH.md
- 02__PB-02__TARGETS_REBUILD_PATCH.md
- 03__PB-03__ATTACK_CLARITY_PATCH.md
- 04__PB-04__BREATH_DENSITY_PATCH.md
- 05__PB-05__ARC_LEVER_PATCH.md
- 06__PB-06__TAKE_PACK_PATCH.md
- 07__PB-07__STACKING_SAFE_PATCH.md
- 08__PB-08__COMPLIANCE_ONE_AXIS_PATCH.md

--- END.
