# UGC VIRAL RULESET — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: UGC_VIRAL_RULESET
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.UGC_VIRAL_RULESET.001
OWNER: SYSTEM
ROLE: Defines platform-native UGC constraints for music output:
clip window requirements, cut/edit points, hook timing expectations, duet readiness patterns, and prohibited anti-UGC artifacts.
Used by Trend/Genre engines, Prompt Compiler, Track Factory, and TEST→DOC gate.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created UGC Viral Ruleset CTL: deterministic UGC constraints, moment requirements, and prohibitions for short-form performance."
- REASON: "Virality fails when outputs lack clip windows, edit points, and early recognition."
- IMPACT: "Higher creator adoption, better loop metrics, cleaner UGC gating."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.UGC.RULESET.001

---

## 0) PURPOSE (LAW)
This controller defines **UGC readiness rules** for short-form platforms.
It does NOT create content — it defines constraints and pass/fail expectations.

---

## 1) DEFINITIONS
- CLIP WINDOW: a 8–15 second segment that works standalone.
- HARD CUT POINT: a clean pause/snap/stop or clear transition suitable for edits.
- DROP/SWITCH: a noticeable energy/texture change that creates an edit peak.
- QUOTE HOOK: a short lyric line suitable for captions/comments.
- SOUND TAG (S-TAG): a signature sound/vocal tag that stamps identity.
- DUET READY: structure leaves space for response / call-response formatting.

---

## 2) UGC REQUIREMENTS (MANDATORY)
A track variant intended for UGC must satisfy:

R1 — PRIMARY CLIP WINDOW EXISTS
- At least 1 primary clip window must exist.
- Recommended length: 8–15 seconds.

R2 — SECONDARY CLIP WINDOW (RECOMMENDED)
- At least 1 additional clip window is recommended for reuse.

R3 — AT LEAST ONE EDIT POINT
Must contain at least one of:
- HARD CUT POINT (pause/snap/stop)
- DROP/SWITCH peak

R4 — EARLY RECOGNITION SUPPORT
- The “identity stamp” must appear early (hook cue, signature tag, or obvious genre anchor).
- No long “ambient intro” for UGC variant.

R5 — QUOTE OR TAG
- If lyrical: include a Quote Hook candidate (Q-line) near a clip window.
- If instrumental: include a clear S-tag near a clip window.

R6 — LOOP IMPRINT
- Ending should support looping (short loopable outro or clear end-stamp).

---

## 3) DUET / REMIX RULES (OPTIONAL, WHEN REQUESTED)
If DUET_READY is required:
- Include call/response possibility:
  - CALL line with space
  - RESPONSE line or open slot
- Provide at least one moment where creators can “enter” without being masked.

---

## 4) PROHIBITED ANTI-UGC ARTIFACTS (HARD BLOCKERS)
The UGC variant must NOT include:
- long intro before identity stamp
- muddy or unintelligible lead vocal (if lyrical RU)
- excessive chant spam / identical phrase loops
- overly complex structure with no clean clip windows
- no clear drop/cut points anywhere
- chaotic genre switching without fusion rules

---

## 5) DURATION ALIGNMENT (COHERENCE)
UGC rules must not contradict Duration Policy.
If Duration Policy enforces a short variant:
- prioritize early hook and clip windows
- compress verse content and reduce “slow build”

Dependency:
- Duration Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

---

## 6) OUTPUT EXPECTATIONS (WHAT OTHER ENTITIES MUST PRODUCE)
Engines/SPC that implement UGC mode must output (at least in notes):
- PRIMARY_CLIP_WINDOW: [t..t]
- SECONDARY_CLIP_WINDOWS: [t..t]...
- EDIT_POINTS: (pause/snap/drop)
- QUOTE_HOOK or S_TAG: (what and where)
- LOOP_IMPRINT_NOTE: (how the ending loops)

---

## 7) PASS/FAIL CRITERIA (FOR GATES)
PASS when:
- R1 + R3 + R4 + R5 are satisfied
- prohibited artifacts absent

WARN when:
- R1 satisfied but R2 missing OR edit points weak
- still fixable with one knob (insert pause/snap or create clearer drop)

FAIL when:
- no clip windows (R1 fail)
- no edit points (R3 fail)
- identity stamp late (R4 fail)
- chant spam / muddy vocals / chaotic structure (blockers)

---

## 8) REFERENCES (RAW)
Used by:
- UGC Moment Map ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md
- Viral Hook Blueprint ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md

Validator alignment:
- UGC Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
