# KB — KB_SCOPE → TOPIC FOLDER MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/03__KB_SCOPE_TO_TOPIC_FOLDER_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.SCOPE_TO_FOLDER.003
OWNER: SYSTEM
ROLE: Deterministic mapping from KB_SCOPE labels (used in scope maps) to the canonical topic folders inside 04_KNOWLEDGE_BASE. This MAP provides orientation without embedding navigation links (no URL/PATH-as-navigation).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced canonical KB_SCOPE→folder map to connect scope labels with the KB folder layout."
- REASON: "Entities need a stable orientation from abstract scopes to concrete KB areas; prevents confusion and wrong folder assumptions."
- IMPACT: "Scope selection becomes actionable while keeping navigation centralized in KB master index (RAW-only)."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MAP.003

---

## 0) PURPOSE (KB)
This MAP translates KB_SCOPE labels into canonical KB areas (folders).
It is NOT a navigation index and MUST NOT contain URLs or RAW links.

Navigation rule:
- Use the KB master index to open documents (RAW-only).
This MAP only tells where topics live conceptually.

---

## 1) ABSOLUTE RULES
1.1 NO URL / NO RAW / NO NAV LINKS
- This MAP must not embed URLs/RAW.
- It may include folder labels as orientation only.

1.2 MASTER INDEX IS NAV
- Any opening of a document must be done via the KB master index.

1.3 SCOPE LABELS ARE STABLE
- KB_SCOPE labels should remain stable even if folder numbering changes (if restructured, update this map + master index).

---

## 2) DEFINITIONS
### KB_SCOPE
Abstract scope label used by entities/maps.

### Topic folder
A canonical KB area that contains topic modules for a domain.

---

## 3) CANONICAL MAPPING (SCOPE → FOLDER LABEL)

### 3.1 Governance & Maps
KB_SCOPE.GOVERNANCE
→ FOLDER: 04_KNOWLEDGE_BASE (governance modules + master index + rules)

KB_SCOPE.MAPS.TASK_SCOPE
→ FOLDER: 04_KNOWLEDGE_BASE/40_RELATION_XREF (maps live here)

KB_SCOPE.MAPS.ENTITY_SCOPE
→ FOLDER: 04_KNOWLEDGE_BASE/40_RELATION_XREF (maps live here)

KB_SCOPE.MAPS.PIPELINES
→ FOLDER: 04_KNOWLEDGE_BASE/40_RELATION_XREF (if/when pipeline maps exist)

---

### 3.2 Topic Domains (Primary)
KB_SCOPE.TOPICS.NARRATIVE
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE

KB_SCOPE.TOPICS.CHARACTER
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER

KB_SCOPE.TOPICS.WORLD
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD

KB_SCOPE.TOPICS.VISUAL
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL

KB_SCOPE.TOPICS.SOUND_MUSIC
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC

KB_SCOPE.TOPICS.PRODUCTION
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION

KB_SCOPE.TOPICS.MARKETING
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING

KB_SCOPE.TOPICS.META
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/80_META

KB_SCOPE.TOPICS.REFERENCE
→ FOLDER: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE

---

## 4) SELECTION BEHAVIOR (HOW ENTITIES USE THIS)
Step 1: Entity selects KB_SCOPE via TASK_SCOPE_MAP or ENTITY_SCOPE_MAP.  
Step 2: Entity uses this MAP to identify the correct KB area.  
Step 3: Entity returns to KB master index to open specific modules (RAW-only).  
Step 4: Entity applies the module and emits KB_SOURCES trace.

---

## 5) FAIL CONDITIONS
- Using this MAP as navigation (e.g., “open folder directly” without master index)
- Embedding URLs/RAW links inside this MAP
- Scope label without folder mapping (must be added here)

---

## 6) EXAMPLES
Example A — Task: “Write hook engineering rules”
- Selected scope: KB_SCOPE.TOPICS.SOUND_MUSIC
- Folder label: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC
- Then open actual module via KB master index.

Example B — Entity: “Marketing SPC”
- Selected scope: KB_SCOPE.TOPICS.MARKETING
- Folder label: 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING
- Then open packaging/distribution modules via KB master index.

---

## 7) RELATED (MAPS ONLY)
- MAP: UE.KB.MAP.TASK_SCOPE.001
- MAP: UE.KB.MAP.ENTITY_SCOPE.002
- MAP: UE.KB.MAP.SCOPE_TO_FOLDER.003

--- END.
