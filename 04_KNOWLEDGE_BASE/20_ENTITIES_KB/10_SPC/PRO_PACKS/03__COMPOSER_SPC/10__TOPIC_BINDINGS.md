# 10__TOPIC_BINDINGS — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/10__TOPIC_BINDINGS.md
SCOPE: KB — SPC Pro Pack — Music Producer — Topic Bindings (RAW)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC_BINDINGS
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.TOPIC_BINDINGS.001
OWNER: SPC (Music Producer)
ROLE: RAW bindings to KB Topics used by Music Producer SPC. Deterministic navigation (no guessing).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Topic bindings (RAW-only) initialized for Music Producer SPC pack."
- REASON: "RAW is canonical navigation in this repo."
- IMPACT: "Topic loading becomes deterministic and immediate."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.TOPICS.RAW.001

---

## BINDING LAW (RAW)
- Bindings use RAW links only.
- If a topic is not listed here → do not load it by default.
- Use conditional topics only when the task requires it.

---

## CORE TOPICS (DEFAULT LOAD)

### T-SOUND-STRUCTURE (form/sections)
RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/07__SOUND_MUSIC__STRUCTURE_SONG_BLUEPRINTS.md
Use:
- section roles, build/release patterns
- hook placement framing for producer plan

### T-SOUND-HOOK (hook engineering)
RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
Use:
- hook spotlight rules
- recognition-focused arrangement support

### T-SOUND-REPEAT (repeat guard / anti-collision)
RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/04__SOUND_MUSIC__REPEAT_GUARD_ANTI_COLLISION.md
Use:
- repetition control in arrangement
- “variant discipline” framing

### T-SOUND-PROMPT-CONTRACTS (handoff boundaries)
RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
Use:
- prevent prompt takeover
- define handoff block content

---

## OPTIONAL TOPICS (CONDITIONAL LOAD)

### T-SOUND-VOICE (if vocals required)
RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/08__SOUND_MUSIC__VOCAL_PERFORMANCE_DIRECTION.md
Use:
- composition/arrangement-relevant constraints (space, density, register intent)
Limits:
- no vocal technique coaching

### T-SOUND-MIX (if translation intent needed, no numbers)
RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/05__SOUND_MUSIC__MIX_TRANSLATION_QA.md
Use:
- “translation intent” checks (clarity across devices)
Limits:
- no LUFS, no EQ values

### T-PROD-QA (if generic QA formatting needed)
RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/06__PRODUCTION__QA_GATES_RUBRICS.md
Use:
- gate output formatting discipline
- trace minimum set

---

## NON-LOAD RULES (DO NOT LOAD BY DEFAULT)
- marketing topics (unless task explicitly requests packaging)
- distribution topics (unless task explicitly requests release workflow)
- engineering/mix numeric topics (never in producer scope)

---

## TRACE TEMPLATE (MANDATORY)
When topics are used, record:
- TOPICS_LOADED (RAW):
  - <raw link>
  - <raw link>
- EXCERPTS_USED:
  - <what was taken + where applied>

---
END
