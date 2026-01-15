# SPC PRO PACK — GATE (G8) — TAKE PACK REPEATABILITY (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/08__GATE__TAKE_PACK.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001
OWNER: SYSTEM
ROLE: Gate G8 verifies that the Take Direction Pack is complete, executable, and repeatable: goals per section are limited, repeatability rules exist, QC hard fails are explicit (tied to P0), and comp notes prevent artifacts.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G8 TAKE PACK REPEATABILITY for VOCAL_DIRECTOR."
- REASON: "Without a disciplined take plan, sessions drift and comps become inconsistent."
- IMPACT: "More usable takes, faster convergence, less redo."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G8.001

---

## 0) PURPOSE
Ensure recording and comping are repeatable:
- 2–4 goals per section
- >=3 repeatability rules
- QC hard fails (P0)
- comp notes

PASS of G8 is required before final scope audit (G9).

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G8 requires:
- SESSION_INTENT
- TAKE_GOALS_BY_SECTION
- REPEATABILITY_RULES
- QC_HARD_FAILS
- COMP_NOTES
Recommended:
- RISK_LINES
- QC_SOFT_FAILS

Origin tool:
- T12 TAKE_PACK_BUILDER

Playbook:
- PB-06 TAKE PACK FIX

---

## 2) THRESHOLDS (STRICT)
### TAKE_GOALS_BY_SECTION
- each section: 2..4 goals
- goals must be executable (not vibe-only)
- chorus/hook section must include P0 clarity goal

### REPEATABILITY_RULES
- count: >=3
- must include:
  - fixed pronunciation for P0 across takes
  - stable hook articulation policy
  - stable chorus intensity band (if arc uses intensity lever)

### QC_HARD_FAILS
Must include:
- HF-1: P0 not understood on first listen in hook
- HF-2: breath split inside P0 phrase
- HF-3: masking reduces P0 clarity (delivery/stacking)

### COMP_NOTES
Must include:
- no comp across different pronunciations of P0
- splice only outside P0 phrases
- avoid mixing different vocal characters in comp

---

## 3) PASS / REWORK / FAIL
### PASS if ALL are true:
- take goals per section are 2..4
- repeatability rules >=3
- QC hard fails include HF-1..HF-3
- comp notes present

### REWORK if:
- pack exists but incomplete:
  - one section has >4 goals OR
  - rules count is 1–2 OR
  - hard fails missing 1 item OR
  - comp notes missing 1 item
(Fixable by pruning/adding.)

### FAIL if ANY is true:
- take pack missing entirely
- QC hard fails missing entirely
- goals are primarily vibe-only and not executable
- repeatability rules missing entirely (<1)

Stop rule:
- If FAIL → do not proceed to G9 until fixed.

---

## 4) OUTPUT (G8 VERDICT BLOCK)
G8_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G9 SCOPE COMPLIANCE"
  - if REWORK: "Prune/complete take pack via T12; rerun G8"
  - if FAIL: "Apply PB-06; rerun G8"

---

## 5) FIX ROUTE
Tool:
- T12 TAKE_PACK_BUILDER

Playbook:
- PB-06 TAKE PACK FIX (A6)

After fix:
- rerun G8.

---

## 6) ANTI-SCOPE VIOLATIONS
Forbidden:
- lyric rewrites inside take pack
- mix/master chain prescriptions
Allowed:
- performer goals, QC rules, comp rules

---

## 7) TRACE
TRACE:
- GATE: G8
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001
- TOOL: T12
- PLAYBOOK: PB-06

--- END.
