# TEMPLATE — VAL VIOLATION RECORD (COPY) (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/01__TEMPLATE__VAL_VIOLATION_RECORD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 50_VAL
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VAL.TPL.VIOLATION.001
OWNER: SYSTEM
ROLE: Copy-paste template for creating deterministic Validator violation records: criterion UID, evidence, severity, fix guidance, and recheck method (UID-only, evidence-first).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created VAL violation record template: criterion-anchored, evidence-first, actionable fix + recheck."
- REASON: "Validators must produce consistent, actionable reports; template prevents vague 'bad quality' judgments."
- IMPACT: "Faster rework loops and clearer PASS/REWORK/FAIL decisions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VAL.TPL.001

---

## 0) HOW TO USE
- Create one violation record per failed criterion (or group only if same root cause).
- Must reference the failed criterion by UID-only.
- Evidence must be short and observable (quote/snippet/field reference).
- Always include how to recheck.

---

## 1) VIOLATION RECORD (COPY)
VAL_VIOLATION:
- VIOLATION_UID: VAL-YYYYMMDD-001
- DATE: YYYY-MM-DD
- STATUS: OPEN | RESOLVED | WAIVED
- TARGET_OUTPUT_ID:
- TARGET_DOMAIN: NARRATIVE | CHARACTER | WORLD | VISUAL | SOUND_MUSIC | PRODUCTION | MARKETING | META
- SEVERITY: MINOR | MAJOR | CRITICAL

- CRITERION_UID (FAILED) (UID-ONLY):
  - <uid>

- WHAT FAILED (SYMPTOM):
  - <one sentence>

- EVIDENCE (OBSERVABLE):
  - <short quote/snippet/field-id>
  - <optional second evidence>

- WHY IT MATTERS (IMPACT):
  - <clarity/compliance/quality risk in one sentence>

- ROOT CAUSE (OPTIONAL):
  - <likely cause, only if supported>

- FIX (ACTIONABLE):
  - 1) <step>
  - 2) <step>
  - 3) <step>

- RECHECK METHOD:
  - Re-run: <gate/checklist uid(s)>
  - PASS looks like: <observable condition>

- REWORK SCOPE:
  - LOCAL (single section/shot/paragraph) | PARTIAL (submodule) | FULL (entire artifact)

- NOTES (OPTIONAL):
  - <any constraint notes>

- RELATED_UIDS (UID-ONLY):
  - <uid> | WHY

- RUN_TRACE (MINIMUM):
  - KB_SOURCES_USED (UID-ONLY):
    - <uid>
  - MEMORY_REUSE: YES/NO
  - WEB_LOOKUP_USED: YES/NO
  - STATUS_USED: ACTIVE_ONLY/MIXED

---

## 2) SEVERITY GUIDANCE (REFERENCE)
CRITICAL:
- breaks a core gate; output unusable or non-compliant; must stop or full rework

MAJOR:
- strongly degrades clarity/consistency/requirements; rework required

MINOR:
- polish-level; can be fixed without structural rewrite

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- criterion UID missing
- evidence missing or non-observable (“мне кажется”)
- fix guidance is not actionable
- recheck method missing
- URL/PATH used as authority in operational references

---

## 4) RELATED (UID-ONLY)
XREF:
- UE.KB.VAL.STD.CONNECTOR.001 | WHY: validator workflow and rules
- UE.KB.STD.GATE_DEF.088 | WHY: gate criteria structure (often used as criterion)
- UE.KB.QA.STD.CONNECTOR.001 | WHY: QA coordination (when quality gates involved)

--- END.
