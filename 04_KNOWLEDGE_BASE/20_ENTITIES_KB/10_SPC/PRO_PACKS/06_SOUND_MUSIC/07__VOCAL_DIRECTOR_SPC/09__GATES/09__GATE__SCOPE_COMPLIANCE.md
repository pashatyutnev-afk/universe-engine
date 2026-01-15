# SPC PRO PACK — GATE (G9) — SCOPE COMPLIANCE (F1..F5) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/09__GATE__SCOPE_COMPLIANCE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001
OWNER: SYSTEM
ROLE: Gate G9 enforces strict scope/ownership compliance for VOCAL_DIRECTOR outputs. It detects forbidden actions (lyric rewrites, structure/arrangement ownership, mix/master chain prescriptions, guessing) and defines hard-fail rules and remediation paths. This is the final gate before READY.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G9 SCOPE COMPLIANCE (F1..F5) for VOCAL_DIRECTOR."
- REASON: "Forbidden content breaks auditability and entity boundaries; must be stopped deterministically."
- IMPACT: "Prevents lyric rewrites and mix-chain advice; enforces escalation instead."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G9.001

---

## 0) PURPOSE
Ensure the output is scope-safe and ownership-safe.

This is the final gate:
- PASS → pack can be considered READY (subject to project-level approvals).
- FAIL → forbidden content must be removed before any use.

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G9 requires:
- SCOPE_AUDIT
Optional (when violations exist):
- VIOLATIONS_FOUND
- REMEDIATION
- ESCALATION_NOTES (if converted)

Origin tool:
- T13 SCOPE_AUDIT_CHECKLIST

Related tools:
- T14 ESCALATION_NOTE_FORMATTER
- T15 REPAIR_ROUTER

Playbook:
- PB-08 COMPLIANCE / ONE-AXIS PATCH

---

## 2) FORBIDDEN CLASSES (F1..F5)
G9 audits these classes:

F1 — LYRIC REWRITE / REPLACEMENT
- providing replacement words or rewritten lines (automatic FAIL)

F2 — STRUCTURE OWNERSHIP
- directing section changes as if VOCAL_DIRECTOR owns structure
- allowed only as escalation notes to owner

F3 — ARRANGEMENT OWNERSHIP
- prescriptive arrangement decisions as ownership
- allowed only as escalation notes to owner

F4 — MIX/MASTER CHAIN PRESCRIPTIONS
- plugin chains, EQ/compressor settings, DAW recipes (automatic FAIL)

F5 — GUESSING / UNSUPPORTED FACT CLAIMS
- asserting details not present in inputs/knowledge (must convert to GAP or note uncertainty)

---

## 3) PASS / REWORK / FAIL
### PASS if ALL are true:
- lyric_rewrite_present (F1) = NO
- structure_edit_present (F2) = NO (or only as escalation notes)
- arrangement_ownership_present (F3) = NO (or only as escalation notes)
- mix_chain_present (F4) = NO
- guessing_present (F5) = NO

### REWORK if:
- minor wording implies ownership but can be rewritten into escalation/principles
- no direct lyric rewrites or mix chains are present
- violations are limited and easily removed without rebuilding content

### FAIL (HARD FAIL) if ANY is true:
- F1 YES (lyric rewrite present) → automatic FAIL
- F4 YES (mix/master chain present) → automatic FAIL
- repeated/strong ownership claims (F2/F3) present and not in escalation format
- F5 guessing is used to justify decisions beyond inputs (must stop)

Hard stop rule:
- If FAIL → do not consider pack usable until cleaned.

---

## 4) OUTPUT (G9 VERDICT BLOCK)
G9_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "READY (scope-compliant)."
  - if REWORK: "Rewrite violating lines into escalation/principles; rerun G9."
  - if FAIL: "Remove forbidden content (F1/F4) and apply PB-08; rerun G9."

---

## 5) REMEDIATION / FIX ROUTE
Tool:
- T13 SCOPE_AUDIT_CHECKLIST (detect + list violations)

If violations:
- convert F2/F3 into ESCALATION_NOTES via T14 (no solutions)
- remove F1/F4 content entirely
- convert F5 into GAP request + stop

Playbook:
- PB-08 COMPLIANCE / ONE-AXIS PATCH (A7 by default)

After fix:
- rerun G9.

---

## 6) COMPLIANCE REMINDERS (ABSOLUTE)
- No lyric rewrite in VOCAL_DIRECTOR pack output.
- No plugin chain / mix/master recipe advice.
- Escalate to owners with principle-level requests only.

---

## 7) TRACE
TRACE:
- GATE: G9
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001
- TOOL: T13
- PLAYBOOK: PB-08
- ESCALATION: T14 (when needed)

--- END.
