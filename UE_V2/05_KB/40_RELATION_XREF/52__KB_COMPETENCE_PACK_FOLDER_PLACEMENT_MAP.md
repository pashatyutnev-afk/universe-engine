# KB — COMPETENCE PACK FOLDER PLACEMENT MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/52__KB_COMPETENCE_PACK_FOLDER_PLACEMENT_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.PACK_FOLDER_PLACEMENT.052
OWNER: SYSTEM
ROLE: Orientation map for where competence packs should live in the KB folder structure by domain and role type. This is not navigation and must not include RAW links; it defines placement conventions for consistency.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined folder placement map for competence packs by domain and role type."
- REASON: "Competence packs must be discoverable and consistently organized to support indexing and onboarding."
- IMPACT: "Predictable pack placement; easier master-index registration and audits."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MAP.052

---

## 0) PURPOSE (KB)
Define where competence packs should be stored by convention:
- domain folders
- role focus
- pack type (core/qa/orchestration/control)

This MAP provides orientation only.
Actual navigation to files is via KB master index (RAW-only).

---

## 1) ABSOLUTE RULES
- No URLs/RAW in this map.
- Folders listed are labels for humans; they do not replace the master index.
- Packs must be atomic and domain-consistent.

---

## 2) PLACEMENT CONVENTION (RECOMMENDED)
### Base domains
- SOUND_MUSIC packs → 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/90_PACKS
- NARRATIVE packs   → 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/90_PACKS
- CHARACTER packs   → 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/90_PACKS
- WORLD packs       → 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/90_PACKS
- VISUAL packs      → 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/90_PACKS
- PRODUCTION packs  → 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/90_PACKS
- MARKETING packs   → 04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/90_PACKS
- META packs        → 04_KNOWLEDGE_BASE/10_TOPICS/80_META/90_PACKS

Notes:
- If your repo already uses different folder numbers, keep the idea: each domain has a dedicated `90_PACKS` area.

---

## 3) PACK TYPE SUBFOLDERS (OPTIONAL)
Inside each `90_PACKS`:
- 10_CORE (core competence)
- 20_QA (domain QA/gates packs)
- 30_ORC (orchestration packs, if domain-specific)
- 40_CTL (controller/control packs, if domain-specific)
- 50_VAL (validator rubrics, if domain-specific)

If you prefer flat structure:
- keep consistent filename tokens: `__CORE__`, `__QA__`, `__ORC__`, etc.

---

## 4) SPECIAL CASES
### Cross-domain packs
If a pack truly spans domains:
- place in META or PRODUCTION (prefer PRODUCTION if it’s pipeline-oriented)
- keep scope boundary explicit
- do not mix craft methods across domains; split into sub-packs if needed

### Entity-class packs (non-domain)
- CTL/VAL/QA generic packs can live under META `90_PACKS`
  and reference domain specifics via skill tags and XREF.

---

## 5) VALIDATION RULES
PASS IF:
- pack is placed under the matching domain `90_PACKS`
- pack filename includes domain+role tokens
- pack is registered in master index

FAIL IF:
- pack is stored in unrelated domain folder
- packs are scattered without a domain pack area
- cross-domain pack lacks scope boundary

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- a pack is placed in a folder that implies a different domain
- pack placement makes indexing ambiguous (no domain ownership)
- placement map is used as navigation (URL/RAW introduced)

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.PACK_NAMING_UID.051 | WHY: naming/UID rules must align with folder placement
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: packs must be registered in master index regardless of placement
- XREF: UE.KB.STD.SCOPE_TO_FOLDER.003 | WHY: scope→folder orientation philosophy (non-navigation)

--- END.
