# VISUAL — READABILITY CHECKLIST (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/07__VISUAL__VISUAL_READABILITY_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: CHECKLIST
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.CHK.READABILITY.007
OWNER: SYSTEM
ROLE: Deterministic checklist to validate visual readability of a single frame/shot plan: focal clarity, separation, edge control, orientation anchors, continuity coherence, and lighting logic. Outputs PASS/REWORK/FAIL.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created visual readability checklist with pass/rework/fail outcomes and fast application order."
- REASON: "Visual quality collapses when readability fails; entities need a measurable-ish checklist to detect and fix quickly."
- IMPACT: "Fewer unreadable frames and fewer orientation/continuity breaks."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.CHK.007

---

## 0) SCOPE (BOUNDARY)
COVERS:
- readability validation for a frame/shot/shotlist entry
- clarity and orientation checks
- lighting/continuity coherence checks

EXCLUDES:
- montage/edit decisions
- fixed color palettes (use contrast/separation principles only)
- performance/acting notes

---

## 1) WHEN TO USE
Use for:
- storyboard frames
- shotlist entries before production
- image generation prompts validation
- QA review of scene visual plans

---

## 2) CHECKLIST (RUN ORDER)
### R1 — PRIMARY SUBJECT CLARITY (CRITICAL)
- [ ] PRIMARY subject is identifiable in ≤ 1 second
- [ ] SECONDARY elements do not compete with PRIMARY
FAIL if: PRIMARY is unclear OR multiple competing focal points exist.

### R2 — SEPARATION (CRITICAL)
- [ ] Subject is separated from background by at least one method:
  - value separation (light/dark)
  - edge/rim separation
  - background simplification
  - detail separation (subject more detailed)
  - geometric silhouette separation
FAIL if: subject merges with background (silhouette unreadable).

### R3 — EDGE CONTROL (IMPORTANT)
- [ ] No unmotivated bright hotspots in corners/edges
- [ ] No accidental tangents (edges touching subject outline in confusing ways)
REWORK if: minor edge attraction exists; FAIL if: edges steal focus consistently.

### R4 — ORIENTATION ANCHOR (CONTEXT-DEPENDENT, CRITICAL WHEN SPACE MATTERS)
If the shot requires spatial understanding:
- [ ] An orientation anchor exists (establishing/master/clear landmark)
- [ ] Axis/eyeline/screen-direction coherence is preserved (or re-established intentionally)
FAIL if: viewer cannot reliably tell who is where / where the action is.

### R5 — LIGHTING LOGIC (IMPORTANT)
- [ ] Local contrast supports PRIMARY readability
- [ ] Key direction / motivation is internally consistent within the moment
REWORK if: lighting is slightly flat or slightly inconsistent; FAIL if: lighting flips direction or makes action unreadable.

### R6 — CONTINUITY VARIABLES (IMPORTANT)
If the shot participates in a sequence:
- [ ] Prop state variables are consistent (location/orientation/held-by)
- [ ] Motion continuity is coherent (gesture/movement direction not resetting)
REWORK if: minor state mismatch; FAIL if: obvious teleport/flip.

### R7 — STYLE CONSISTENCY (OPTIONAL BUT RECOMMENDED)
- [ ] Contrast/texture/camera language is consistent with the sequence intent
REWORK if: mild drift; FAIL if: shot looks like a different project without motivation.

---

## 3) SCORING (FAST)
Count failures by severity:
- CRITICAL fails: R1 or R2 always CRITICAL; R4 becomes CRITICAL when space matters.
- IMPORTANT fails: R3, R5, R6.

RESULT:
- PASS:
  - 0 CRITICAL fails
  - and ≤ 1 IMPORTANT fail (minor)
- REWORK:
  - 0 CRITICAL fails
  - and 2–3 IMPORTANT fails, or issues are noticeable but fixable
- FAIL:
  - any CRITICAL fail
  - or ≥ 4 IMPORTANT fails
  - or viewer likely loses orientation/readability

---

## 4) OUTPUT TEMPLATE (COPY)
VISUAL_READABILITY_RESULT:
- DATE: YYYY-MM-DD
- TARGET: <frame/shot/shotlist id>
- SPACE_MATTERS: YES/NO
- CRITICAL_FAILS:
  - <id> | <note>
- IMPORTANT_FAILS:
  - <id> | <note>
- RESULT: PASS/REWORK/FAIL
- FAST_FIXES:
  - <top 1–3 fixes>

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- checklist is used but result is not declared (pass/rework/fail)
- montage/editing decisions are prescribed as “fix”
- fixed palettes/presets are introduced as rules
- readability failures are ignored and treated as acceptable output

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: hierarchy, edge management, separation principles
- XREF: UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002 | WHY: orientation rules (axis/eyeline/screen direction)
- XREF: UE.KB.VIS.TOPIC.LIGHTING.003 | WHY: contrast + motivated light principles
- XREF: UE.KB.VIS.TOPIC.CONTINUITY.004 | WHY: prop/light/motion continuity variables
- XREF: UE.KB.VIS.TOPIC.CLARITY_FAILS.006 | WHY: symptom→cause→fast fix patterns
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: gate definition standard (if promoted to a full gate)

--- END.
