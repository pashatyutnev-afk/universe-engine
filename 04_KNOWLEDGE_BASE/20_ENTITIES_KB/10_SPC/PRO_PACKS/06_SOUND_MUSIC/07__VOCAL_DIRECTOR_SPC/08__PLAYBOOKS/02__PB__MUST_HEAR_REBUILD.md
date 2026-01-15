# SPC PRO PACK — PLAYBOOK (PB-02) — TARGETS_REBUILD_PATCH (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/02__PB-02__TARGETS_REBUILD_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-02
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB02.TARGETS_REBUILD_PATCH.001
OWNER: SYSTEM
ROLE: One-axis repair procedure for must-hear targets: rebuild P0/P1/P2 word targets and copy-exact phrase targets + clarity targets. Uses T02/T03. Rerun G2 then verify G3.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-02 TARGETS_REBUILD_PATCH for VOCAL_DIRECTOR."
- REASON: "Wrong/bloated targets make clarity work untestable and subjective."
- IMPACT: "Deterministic targets that align downstream intelligibility and breath protections."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB02.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A1 (Targets layer)

Fixes:
- missing P0 targets
- bloated P0 (>8)
- fillers inside P0
- missing phrase promotion when meaning is phrase-based
- missing CLARITY_TARGETS

Does NOT fix:
- profile, arc, breath, stacking, take pack, scope

---

## 1) INPUTS REQUIRED
Must have:
- hook/chorus lyrics text (copy-exact)
- language label (RU/EN/etc.)
- HOOK_SECTION_LABEL

Optional:
- user-specified must-keep words/lines (if present)

Tools used:
- T02 MUST_HEAR_BUILDER
- T03 PHRASE_PROMOTION_HELPER

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- MUST_HEAR_WORDS
- MUST_HEAR_PHRASES (if required/available)
- CLARITY_TARGETS

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in PB-02:
- INTELLIGIBILITY_GATES_CHECKLIST / HARD_FAIL_TRIGGERS
- ATTACK_PROTECTION_NOTES
- VOCAL_STYLE_PROFILE / FORBIDDEN_STYLES
- BREATH_POLICY / DENSITY_SCAN
- STACKING_* blocks
- PERFORMANCE_ARC_MAP / CONTRAST_LEVERS
- TAKE_* / SESSION_INTENT
- SCOPE_AUDIT

---

## 4) PROCEDURE (STEPS)
Step 1 — Rebuild MUST_HEAR_WORDS (T02)
- Extract targets only from hook text (no invention)
- Enforce thresholds:
  - P0 count 3..8 (2 only if short hook with explicit note)
  - fillers excluded from P0
- Set P1/P2 as needed (or N/A)

Step 2 — Promote phrases (T03) if required
- Copy-exact phrases only
- Enforce limits:
  - total phrases <=4 (prefer 1..2)
- Promote phrases when meaning is unit-based (negations/slogans)

Step 3 — Ensure CLARITY_TARGETS exist
- Must include:
  - Target A: "P0 understood on first listen in HOOK"

Step 4 — Quick sanity check (G2 readiness)
- P0 not bloated
- no invented words
- phrases (if present) are copy-exact

Step 5 — Apply patch
- Replace only the allowed blocks

---

## 5) RERUN GATES
Required rerun:
- G2

Verification rerun:
- G3 (targets affect intelligibility checks)

---

## 6) HARD STOPS
Stop if:
- hook text missing (request copy-exact hook)
- language missing (do not infer)
- phrases required but exact phrase not provided (request exact line)

---

## 7) SUCCESS CRITERIA
PB-02 successful when:
- MUST_HEAR_WORDS.P0 exists and is within thresholds
- fillers not in P0
- MUST_HEAR_PHRASES are copy-exact (if used)
- CLARITY_TARGETS contains Target A

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-02
- AXIS: A1 (Targets)
- TOOLS: T02, T03
- RERUN: G2 → (verify) G3

--- END.
