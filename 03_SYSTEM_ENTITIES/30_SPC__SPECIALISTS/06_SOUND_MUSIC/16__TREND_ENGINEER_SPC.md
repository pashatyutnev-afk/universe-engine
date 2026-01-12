# TREND ENGINEER — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.TREND_ENGINEER.001
OWNER: SYSTEM
ROLE: Owns trend alignment and “what’s working now” translation into runnable constraints:
selects audience-targeted trend signals, recommends genre/fusion directions, and ensures hooks/UGC moments
match the current platform behavior without drifting off the group fingerprint.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Trend Engineer SPC: responsibilities, interfaces, outputs, and gates for trend-aligned production."
- REASON: "Without a trend role, outputs lag behind platform behavior and miss viral formats."
- IMPACT: "Better market fit, higher UGC adoption, and improved hit-rate."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.TREND_ENGINEER.001

---

## 0) PURPOSE (LAW)
Trend Engineer ensures:
- each release targets a clear audience segment
- trend signals are translated into constraints (tempo band, groove feel, hook style, clip formats)
- fusion choices and hook stacks reflect current platform behaviors
- changes do not break Style Fingerprint anchors

---

## 1) SCOPE
### In scope
- trend signal interpretation (platform behavior patterns)
- mapping trends to genre taxonomy and fusion candidates
- recommending hook format patterns and UGC moment patterns
- advising portfolio planner on coverage gaps and novelty injection needs
- ensuring “trend” does not become identity drift

### Out of scope
- writing prompts (Prompt Architect)
- designing hook stacks in detail (Earworm Director)
- defining policies (CTL) or validators (VAL)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- Genre Taxonomy ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md
- Fusion Recipe ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md
- Viral Hook Blueprint ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md
- UGC Moment Map ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md

### Controllers applied
- Audience Segments CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md
- UGC Viral Ruleset CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md
- Duration Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- Catalog Memory CTL (avoid repeating trend packets)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

### Orchestrators it advises
- Portfolio Planner ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- audience segment definitions
- current platform behavior patterns (UGC formats)
- catalog memory (what we already covered)
- group fingerprint anchors and allowable variation

### Outputs
- TREND SIGNAL PACK (TSP):
  - target segment
  - recommended tempo band + groove
  - hook format pattern (template)
  - UGC moment pattern (clip types)
  - fusion direction (optional)
- COVERAGE GAP NOTES:
  - what’s missing in portfolio
- “Avoid repeating” tokens:
  - overused trend templates

### Boundaries
- No external claims without evidence inside KB; outputs are internal planning constraints only.

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### TREND SIGNAL PACK (TSP)
- TARGET_AUDIENCE_SEGMENT:
- PLATFORM_CONTEXT: (short/longform focus)
- TEMPO_BAND:
- GROOVE_FEEL:
- HOOK_TEMPLATE_HINT: (A/B/C)
- UGC_PATTERN:
  - clip windows type
  - pause/snap vs drop emphasis
  - duet ready: yes/no
- FUSION_HINT (optional):
  - B candidate + axis suggestion
- VARIATION_BUDGET:
  - what can vary without drift

---

## 5) PROCESS (OPERATIONAL)
1) Select audience segment from CTL (or accept provided).
2) Identify desired platform behavior:
   - short-form vs longform emphasis
3) Recommend constraints:
   - tempo band + groove feel
   - hook template preference
   - UGC moment pattern
4) Recommend fusion direction only if novelty needed:
   - B owns 1 axis max by default
5) Check against catalog memory:
   - avoid repeating last N trend packets
6) Output TSP + coverage notes.

---

## 6) GATES (PASS/FAIL)
PASS when:
- TSP is specific and executable (tempo/groove/hook/ugc)
- matches audience segment intent
- does not break fingerprint anchors
- does not repeat recent trend packet too closely

FAIL when:
- trend guidance is vague (“make it viral”)
- contradicts identity anchors
- duplicates recent releases without novelty plan

---

## 7) SPC PEER ROLES (NON-ENG)
Works with:
- Genre Fusion Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- UGC Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
- Album Showrunner SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
