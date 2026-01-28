# CREATOR PANEL — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/04__CREATOR_PANEL_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: CREATOR_PANEL
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.CREATOR_PANEL.001
OWNER: SYSTEM
ROLE: A “creator usability” panel check:
evaluates whether creators can easily use the track for content (edits, captions, duets),
and whether the track provides clear UGC mechanics beyond just sounding good.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Creator Panel QA: checklist for creator usability (clip windows, edit points, caption hooks, duet readiness)."
- REASON: "Tracks often fail because they have no creator use-case even if they sound fine."
- IMPACT: "Higher creator adoption and better platform performance."
- CHANGE_ID: UE.CHG.2026-01-12.QA.CREATOR_PANEL.001

---

## 0) PURPOSE (LAW)
Answer:
**“Would creators actually want to use this?”**

This is a heuristic panel check (not deterministic).

---

## 1) INPUTS
- audio take (candidate)
- best clip window (10–15s) OR pick 1–2 candidate windows
- optional: lyric sheet / Q-line candidate
- optional: duet intent (YES/NO)

---

## 2) PROCEDURE (HOW TO RUN)
1) Choose the most usable 10–15s clip window.
2) Imagine 3 creator use-cases:
   - caption/quote video
   - transition edit / pause-snap
   - duet/stitch (if relevant)
3) Score each item below and output result.

---

## 3) CREATOR USABILITY CHECKLIST
### C1 — Clip window usability
- Does the window stand alone?
- Is there a clear “moment” (hook or drop)?

### C2 — Edit points
- Is there at least one clean cut point (pause/snap) OR drop/switch?

### C3 — Caption hook (lyrical) / sound tag (instrumental)
- Lyrical: does it have a caption-worthy line?
- Instrumental: does it have a signature sound tag?

### C4 — Emotional or comedic payload
- Does it trigger a clear emotion or meme use?

### C5 — Duet readiness (optional)
- Is there space or call/response shape for duets?

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- at least 3 of C1..C4 clearly succeed
- creators have an obvious use-case

WARN when:
- usable but missing one key element (fixable)

FAIL when:
- no clear creator use-case
- clip window feels bland or unusable

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
- ADD_CUT_POINT:
  - add pause/snap or clean drop
- STRENGTHEN_Q_LINE:
  - make quote line clearer and nearer the clip window
- ADD_SIGNATURE_TAG:
  - add S-tag/motif to stamp identity in window
- REFRAME_CLIP_WINDOW:
  - move hook earlier / choose a different moment

---

## 6) OUTPUT TEMPLATE (MANDATORY)
CREATOR_PANEL_QA_RESULT:
- TRACK_UID:
- TAKE_ID:
- CLIP_WINDOW: [start_sec..end_sec]
- RESULT: {PASS | WARN | FAIL}
- NOTES:
  - 3–9 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
Policy context:
- UGC Viral Ruleset CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

Validator alignment:
- UGC Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
