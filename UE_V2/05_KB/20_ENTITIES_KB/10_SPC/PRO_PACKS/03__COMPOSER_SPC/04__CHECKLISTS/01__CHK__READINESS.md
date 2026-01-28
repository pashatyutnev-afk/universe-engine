# 01__CHK__READINESS — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/04__CHECKLISTS/01__CHK__READINESS.md
SCOPE: KB — SPC Pro Pack — Composer — Checklist (Readiness)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: CHECKLIST
CHECKLIST_TYPE: READINESS
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.CHK.READINESS.001
OWNER: SPC (Composer)
ROLE: Confirm minimum inputs + composition-scope readiness before producing O1/O2.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Readiness checklist initialized for Composer SPC pack."
- REASON: "Prevent guessing when composition inputs are missing."
- IMPACT: "Defines STOP conditions and missing-input routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.CHK.READY.001

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
[ ] R4 Genre/mood intent exists OR is acceptable as "unknown" (explicit)
[ ] R5 Hook requirement exists (explicit or implied):
    - hook motif appears early (<=10–12s) OR task says otherwise
[ ] R6 Scope split is clear:
    - composer decisions only
    - prompt/mix/legal routed if needed

STOP IF ANY OF R1–R3 ARE MISSING.

---

## OPTIONAL BUT RECOMMENDED
[ ] R7 Target duration range provided
[ ] R8 Tonal center preference (or “free”)
[ ] R9 Vocal presence known (yes/no/unknown)
[ ] R10 Variants requested explicitly (yes/no)

---

## AMBIGUITY FLAGS (CAUSE REWORK)
If any is true → REWORK:
[ ] A1 “Make it cool / like usual” with no musical anchors
[ ] A2 Conflicting constraints not acknowledged (e.g., “very complex harmony” + “super simple singable hook”)
[ ] A3 Platform intent missing but asking for “viral hook”
[ ] A4 Hook definition unclear (lyric-only vs musical motif)

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
  - UE.KB.SPC.PACK.COMPOSER.PB.CORE.001

---
END
