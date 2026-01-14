# CHECKLIST — COMPLIANCE (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/04__CHECKLISTS/03__CHK__COMPLIANCE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CHECKLIST
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CHK.PROMPT_ARCHITECT.COMPLIANCE.001
OWNER: SYSTEM
ROLE: Compliance checklist for PROMPT_ARCHITECT: UID-only authority discipline, no-fantasy, trace completeness, safe prompting, and iteration logs integrity. Produces PASS/REWORK/FAIL.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created compliance checklist for PROMPT_ARCHITECT: UID-only linking, no-fantasy, trace, safe prompting, and log integrity."
- REASON: "Compliance drift breaks deterministic execution and can introduce unsafe or fabricated behavior."
- IMPACT: "More auditable runs and safer output behavior."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.CHK.COMPLIANCE.001

---

## 0) UID-ONLY AUTHORITY DISCIPLINE
- [ ] Any “authority references” are UID-only (no URL/PATH as authority)
- [ ] Topic bindings list uses UID-only entries
- [ ] If a UID is placeholder, it is marked as PLACEHOLDER/UNKNOWN (not claimed real)

If broken → REWORK.

---

## 1) NO-FANTASY / EVIDENCE DISCIPLINE
- [ ] No claims like “rule exists” unless it’s in pack or known KB
- [ ] Missing modules/gates are recorded as GAP (not simulated)
- [ ] Fixes are actionable and tied to checks/gates (not vibes)

If invented claims found → FAIL.

---

## 2) TRACE COMPLETENESS
- [ ] MEMORY_REUSE flag recorded (YES/NO)
- [ ] WEB_LOOKUP_USED flag recorded (YES/NO)
- [ ] Criteria run (UID-only) listed when gates/checklists used
- [ ] Axis changed recorded for patches/variants
- [ ] Loop count and decision recorded (winner/keeper/loser or pass/rework/fail)

If trace fields missing → REWORK.

---

## 3) ITERATION LOG INTEGRITY
- [ ] Baseline prompt is frozen and labeled (when iterating)
- [ ] One-axis discipline followed OR explicitly stated why not
- [ ] Delta described (what changed) for each variant/patch

If multiple axes changed silently → FAIL (discipline breach).

---

## 4) SAFE PROMPTING & IP BOUNDARY
- [ ] No instructions to copy a specific artist “exactly” (use style principles instead)
- [ ] No unsafe or disallowed content instructions
- [ ] No large external text pasted into KB_SOURCES (extraction only)

If “copy exactly” or unsafe instruction present → REWORK/FAIL depending on severity.

---

## 5) RESULT RULE
PASS:
- sections 0–4 all OK
- no invented claims
- trace and logs complete

REWORK:
- minor UID/trace/log omissions fixable quickly

FAIL:
- invented claims (no-fantasy breach)
- silent multi-axis changes
- unsafe prompting or “copy exactly” instructions not corrected

---

## 6) NEXT ACTIONS (IF REWORK/FAIL)
If UID-only broken:
- remove URL/PATH authority usage; replace with UID-only or mark GAP

If no-fantasy breach:
- stop; correct claims; record GAPs explicitly

If trace missing:
- fill trace template and rerun gate 05 (one-axis discipline)

If IP boundary issue:
- rewrite prompt in principles/genre terms (no “exact copy”)

---

## 7) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 | WHY: discipline enforcement gate
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.BINDINGS.DRAFT.001 | WHY: bindings file discipline
- UE.KB.VAL.TPL.VIOLATION.001 | WHY: evidence-first records
- UE.KB.QA.STD.CONNECTOR.001 | WHY: trace discipline

--- END.
