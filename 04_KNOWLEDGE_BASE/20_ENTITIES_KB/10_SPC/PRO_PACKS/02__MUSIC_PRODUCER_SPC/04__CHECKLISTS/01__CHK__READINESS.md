# 01__CHK__READINESS — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/04__CHECKLISTS/01__CHK__READINESS.md
SCOPE: KB — SPC Pro Pack — Music Producer — Checklist (Readiness)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: CHECKLIST
CHECKLIST_TYPE: READINESS
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
OWNER: SPC (Music Producer)
ROLE: Confirm minimum inputs + scope readiness before producing O1/O2.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Readiness checklist initialized for Music Producer SPC pack."
- REASON: "Prevent guessing when inputs are missing."
- IMPACT: "Defines STOP conditions and missing-input routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CHK.READY.001

---

## PASS/REWORK/FAIL RULE
- PASS: all mandatory items satisfied
- REWORK: any mandatory item missing or ambiguous
- FAIL: not used here (readiness stops, not fails)

---

## MANDATORY INPUTS (MIN)
[ ] R1 TASK_GOAL is provided (1 sentence)
[ ] R2 PLATFORM_INTENT is provided (shorts / full / clip / etc)
[ ] R3 CONSTRAINTS provided (1–5 bullets)
[ ] R4 “Must-have outcome” defined (1 measurable: hook <=10s / etc) OR derivable from constraints
[ ] R5 Scope split is clear:
    - producer decisions only
    - prompt/mix/legal routed if needed

STOP IF ANY OF R1–R3 ARE MISSING.

---

## OPTIONAL BUT RECOMMENDED
[ ] R6 Reference tracks / vibe words exist
[ ] R7 Target duration range provided
[ ] R8 Vocal presence known (yes/no/unknown)
[ ] R9 Variants requested explicitly (yes/no)

---

## AMBIGUITY FLAGS (CAUSE REWORK)
If any is true → REWORK:
[ ] A1 “Make it cool / like usual” with no measurable anchors
[ ] A2 Conflicting constraints not acknowledged (e.g., “very dense” + “super intelligible”)
[ ] A3 Missing platform intent but asking for “viral”

---

## OUTPUT OF THIS CHECKLIST
Record:
- READINESS_STATUS: <PASS|REWORK>
- MISSING_INPUTS:
  - <list missing>
- AMBIGUITIES:
  - <list flags>
- NEXT_ACTION:
  - if REWORK: request missing inputs (no guessing)
  - if PASS: proceed to PB-01 CORE workflow

---

## REQUIRED UID REFERENCES
- PLAYBOOK:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.CORE.001

---
END
