# SPC PRO PACK — GATE (G6) — BREATH / SINGABILITY (P0 PROTECTION) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/06__GATE__BREATH_SINGABILITY.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001
OWNER: SYSTEM
ROLE: Gate G6 verifies breath/singability readiness: P0 phrases are protected from breath splits, explicit allowed/forbidden breath points exist, and density risks are scanned with escalation triggers for unsingable lines. Protects intelligibility under performance pressure.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G6 BREATH/SINGABILITY for VOCAL_DIRECTOR."
- REASON: "Breath splits inside must-hear phrases are a primary cause of hook intelligibility failures."
- IMPACT: "Cleaner phrases, fewer forced splits, deterministic escalation."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G6.001

---

## 0) PURPOSE
Ensure breath placement is explicit and safe:
- protect P0 phrases
- define forbidden splits
- detect density traps
- escalate when unsingable without rewriting lyrics

PASS of G6 is recommended before stacking/take planning.

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G6 requires:
- MUST_HEAR_PROTECTION_RULES
- BREATH_POLICY
- DENSITY_SCAN
- (optional) ESCALATION_TRIGGER / ESCALATION_NOTES

Origin tools:
- T09 BREATH_MAP_BUILDER
- T10 DENSITY_RISK_SCAN
- T14 ESCALATION_NOTE_FORMATTER (if escalation)

Playbook:
- PB-04 BREATH / DENSITY FIX

---

## 2) THRESHOLDS (STRICT)
### MUST_HEAR_PROTECTION_RULES
- must list NEVER_SPLIT_PHRASES for P0 phrases (copy-exact)

### BREATH_POLICY
- must include:
  - allowed list (at least 1 item)
  - forbidden list (at least 1–3 explicit forbidden splits)
- forbidden must include:
  - explicit splits inside P0 phrases
  - forbidden split inside negative constructions (e.g., "не X") when applicable

### DENSITY_SCAN
- every target line has:
  - line_id
  - risk_level (R0/R1/R2)
  - evidence
- if any R2 with F_NO_SAFE_BREATH_POINT → escalation trigger must be evaluated

---

## 3) PASS / REWORK / FAIL
### PASS if ALL are true:
- P0 phrases are protected (NEVER_SPLIT present)
- breath policy has allowed + forbidden points
- density scan present and complete
- if R2 exists:
  - ESCALATION_TRIGGER is set correctly (YES/NO) and, if YES, escalation notes exist

### REWORK if:
- artifacts exist but incomplete:
  - forbidden list too vague or missing explicit splits
  - P0 phrase protection missing 1 phrase
  - density scan missing evidence or line_ids
  - escalation trigger unclear
(Repairable without new inputs.)

### FAIL if ANY is true:
- MUST_HEAR_PROTECTION_RULES missing
- BREATH_POLICY missing forbidden points
- breath policy explicitly permits breath “anywhere”
- density scan missing entirely
- breath split inside P0 is instructed (hard fail)
- R2 unsingable risk exists with no escalation trigger/action

Stop rule:
- If FAIL → do not proceed to G7 until fixed.

---

## 4) OUTPUT (G6 VERDICT BLOCK)
G6_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G7 STACKING SAFE"
  - if REWORK: "Complete breath policy/density scan via T09/T10; rerun G6"
  - if FAIL: "Apply PB-04; if R2 then escalate via T14; rerun G6 (then verify G3)"

---

## 5) FIX ROUTE
Tools:
- T09 BREATH_MAP_BUILDER
- T10 DENSITY_RISK_SCAN

Playbook:
- PB-04 BREATH / DENSITY FIX (A3)

Escalation:
- If R2 + no safe breath → format escalation via T14 (owner Lyricist/Songwriter)
- rerun after owner response

Verification:
- After G6 fixes, verify G3 (intelligibility)

---

## 6) ANTI-SCOPE VIOLATIONS
Forbidden:
- rewriting lyrics to solve density inside this gate
- proposing replacement words
Allowed:
- escalation notes requesting review (principles only)

---

## 7) TRACE
TRACE:
- GATE: G6
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001
- TOOLS: T09, T10 (optional T14)
- PLAYBOOK: PB-04

--- END.
