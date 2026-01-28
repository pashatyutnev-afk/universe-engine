# SPC PRO PACK — TOOL (T13) — SCOPE_AUDIT_CHECKLIST (F1..F5) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/13__T13__SCOPE_AUDIT_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T13
TOOL_NAME: SCOPE_AUDIT_CHECKLIST
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T13.SCOPE_AUDIT_CHECKLIST.001
OWNER: SYSTEM
ROLE: Audits VOCAL_DIRECTOR outputs for scope/ownership violations using fixed forbidden classes (F1..F5). Produces a binary SCOPE_AUDIT and optional violation list/remediation notes. Hard-fails on F1 (lyric rewrite) and F4 (mix/master chains).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T13 SCOPE_AUDIT_CHECKLIST for VOCAL_DIRECTOR."
- REASON: "Compliance must be enforced deterministically; forbidden content cannot pass."
- IMPACT: "Prevents illegal lyric edits and production/mix advice from entering packs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T13.001

---

## 0) PURPOSE
Audit any deliverable text for scope compliance and output:
- SCOPE_AUDIT
Optional:
- VIOLATIONS_FOUND
- REMEDIATION

Supports Gate:
- G9 SCOPE COMPLIANCE

---

## 1) INPUTS (REQUIRED)
- candidate output text (any draft pack, prompt contract, notes)

Rule:
- This tool evaluates presence/absence of forbidden classes.
- It does not “fix” content; it flags.

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T13 MUST output:

### SCOPE_AUDIT
- lyric_rewrite_present (F1): YES/NO
- structure_edit_present (F2): YES/NO
- arrangement_ownership_present (F3): YES/NO
- mix_chain_present (F4): YES/NO
- guessing_present (F5): YES/NO

Optional helper blocks:
### VIOLATIONS_FOUND
- V-1:
- V-2: (optional)

### REMEDIATION
- action:
- convert_to_escalation: YES/NO
- remove_content: YES/NO
- rerun_gate: G9

---

## 3) FORBIDDEN CLASSES (DETERMINISTIC DEFINITIONS)
F1 — LYRIC REWRITE / REPLACEMENT
Flag YES if output includes:
- rewritten lines
- replacement word suggestions
- “use this line instead” type content

F2 — STRUCTURE OWNERSHIP
Flag YES if output includes:
- directives to change section structure as owned decision
- “remove chorus / add bridge” without escalation framing

F3 — ARRANGEMENT OWNERSHIP
Flag YES if output includes:
- prescriptive instrumentation edits as owned decisions
- “add/remove guitar/synth” without escalation framing

F4 — MIX/MASTER CHAIN PRESCRIPTIONS
Flag YES if output includes:
- plugin chain advice (EQ/compressor/distortion settings)
- DAW recipes for mixing/mastering

F5 — GUESSING / UNSUPPORTED FACT CLAIMS
Flag YES if output includes:
- asserting details not present in user inputs
- fabricated specifics (“the singer is X”) without source

Hard-fail classes:
- F1 and F4 are automatic FAIL in G9.

---

## 4) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Scan for F1 patterns
- Look for alternative text lines, “replace word”, “rewrite” indications

Step 2 — Scan for F4 patterns
- Look for mixing/mastering terms used as prescriptions (EQ/compressor/plugin chain)

Step 3 — Scan for F2/F3
- Look for structure/arrangement decisions stated as direct actions
- If content is framed as escalation request (owner + request + success criteria), do NOT count as F2/F3

Step 4 — Scan for F5
- Identify claims that are not grounded in provided inputs

Step 5 — Output SCOPE_AUDIT
- Set YES/NO per class

Step 6 — If any YES, output VIOLATIONS_FOUND + REMEDIATION
- Remediation is only procedural (remove/convert to escalation), not creative solutions.

---

## 5) REMEDIATION RULES (PROCEDURAL ONLY)
If F1=YES:
- remove rewritten/replacement text (mandatory)
If F4=YES:
- remove mix/master chain prescriptions (mandatory)
If F2/F3=YES:
- convert to ESCALATION_NOTES (via T14) OR remove
If F5=YES:
- convert to GAP request / uncertainty; stop if it affects decisions

Then rerun:
- G9

---

## 6) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- providing new creative content as remediation inside the audit
Allowed:
- listing violations and procedural cleanup steps

---

## 7) TRACE
TRACE:
- TOOL: T13
- OUTPUTS: SCOPE_AUDIT (+ optional VIOLATIONS_FOUND, REMEDIATION)
- SUPPORTS_GATE: G9

--- END.
