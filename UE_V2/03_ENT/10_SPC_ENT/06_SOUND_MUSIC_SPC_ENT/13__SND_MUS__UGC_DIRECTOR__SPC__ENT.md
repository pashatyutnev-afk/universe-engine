# UGC DIRECTOR — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.UGC_DIRECTOR.001
OWNER: SYSTEM
ROLE: Owns UGC performance design: ensures every track has creator-usable moments (clip windows, pause/snap cuts, duets),
and that hooks are positioned and engineered for scroll-stop, recognition, and loopability.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created UGC Director SPC: responsibilities, interfaces, UGC moment standards, and gates."
- REASON: "Virality fails when there are no clean edit points, quote lines, or duet-ready structures."
- IMPACT: "Higher creator adoption, better retention, stronger loop behavior."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.UGC_DIRECTOR.001

---

## 0) PURPOSE (LAW)
UGC Director ensures each track is **creator-native**:
- at least one primary clip window (8–15s)
- at least one hard cut point (pause/snap) or a clear drop/switch
- at least one quote/caption hook (if lyrical) or signature sound tag (if instrumental)
- duet-ready structure when planned

---

## 1) SCOPE
### In scope
- UGC moment planning (clip windows, cut points, duet patterns)
- edit-peak placement (drop/switch, pause/snap)
- quote-line clarity requirements (for captions)
- loop imprint requirements (ending behavior)
- UGC readiness precheck before QA/VAL gates

### Out of scope
- writing lyrics content (Lyricist / Poet editors)
- composing music (Composer/Arranger)
- enforcing policy thresholds (CTL/VAL owns)
- naming/titles (Naming engines)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- UGC Moment Map ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md
- Viral Hook Blueprint ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md
- Earworm Hook Stack ENG (Q-line / S-tag source)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md
- Duration Strategy ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md
- Prompt Compiler ENG (UGC encoding)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md

### Controllers applied
- UGC Viral Ruleset CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md
- Duration Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- Negative Spec Library CTL (anti-UGC artifacts)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

### Validators / QA gates referenced
- UGC Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md
- Scroll Stop 5s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md
- Loop 15s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md
- Recognition 10s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- audience segment intent (what creators do with it)
- UGC ruleset constraints (platform-native)
- hook timing + clip windows
- quote line (lyrical) OR sound tag (instrumental)

### Outputs
- UGC Moment Spec (primary/secondary windows + cut points)
- Duet/Remix readiness notes
- Prompt-ready UGC instruction lines (short)

### Boundaries
- no “montage decisions”: only UGC constraints and risks (not exact edits)

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### UGC MOMENT SPEC (for each variant)
- PRIMARY_CLIP_WINDOW: [t..t]
- SECONDARY_CLIP_WINDOWS: [t..t], ...
- HARD_CUT_POINTS: (pause/snap/drop)
- QUOTE_HOOK (lyrical): (short line + placement)
- SOUND_TAG (instrumental): (tag + placement)
- DUET_READY: YES/NO
- CREATOR_ACTION_HINT: (what creators can do)

---

## 5) PROCESS (OPERATIONAL)
1) Load UGC ruleset + duration policy.
2) Ensure at least 1 primary clip window exists.
3) Ensure at least 1 hard cut point exists (pause/snap OR strong drop/switch).
4) Ensure recognition in first 10s is supported (identity stamp).
5) Ensure loop imprint at the end (loopable outro).
6) Encode all of the above into short prompt instruction lines (no essays).
7) Precheck: confirm UGC Ready VAL criteria will pass.

---

## 6) GATES (PASS/FAIL)
PASS when:
- primary clip window exists (8–15s)
- at least 1 hard cut point exists
- quote hook or sound tag is clear and placed near a window
- no long intro that kills scroll-stop
- loop behavior supports reuse

FAIL when:
- no clip windows
- no edit points
- quote line is muddy/unclear
- hook timing is too late for UGC mode
- ending is dead/no loop imprint

---

## 7) SPC PEER ROLES (NON-ENG)
Works with:
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- Album Showrunner SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md
- Group Creative Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
