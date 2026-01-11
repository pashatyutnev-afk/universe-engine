# REGISTRY — PATH MAP (CANON)
FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/03__REG_PATH_MAP.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: REGISTRIES (REG)
DOC_TYPE: REGISTRY
REGISTRY_TYPE: PATH_MAP
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.PATH.001
OWNER: SYSTEM
ROLE: Canonical path map for Universe Engine repository (where each class/layer lives; prevents misplacement and folder sprawl)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created path map registry: canonical layer paths, entity-class locations, and placement rules."
- REASON: "Stop path drift and make repository deterministic."
- IMPACT: "All artifacts have a single correct home."
- CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

---

## 0) PURPOSE (LAW)
This registry defines:
- canonical paths of main layers
- canonical paths for each entity class in `03_SYSTEM_ENTITIES`
- placement rules: where to create NEW files and where NOT to

If a file is placed outside its canonical home — it is NON-CANON until moved.

---

## 1) CANONICAL LAYERS (TOP-LEVEL)
These are the canonical system layers (high-level):

- `01_SYSTEM_LAW/` — system laws (authority order; no extra laws)
- `02_STANDARDS/` — standards and templates for documentation/format
- `03_SYSTEM_ENTITIES/` — engines/orchestrators/specialists/controllers/validators/qa/xref + registries/templates
- `04_KNOWLEDGE_BASE/` — knowledge base (one-index mode)
- `05_PROJECTS/` — project workspaces and produced artifacts (implementation output)
- `99_MISC/` (if exists) — non-canon scratch only (must not be treated as authority)

Rule:
- Laws live ONLY in `01_SYSTEM_LAW`
- Standards live ONLY in `02_STANDARDS`
- Entities live ONLY in `03_SYSTEM_ENTITIES`
- Production outputs/artifacts live ONLY in `05_PROJECTS`

---

## 2) SYSTEM ENTITIES — CANON CLASS PATHS (STRICT)
All entity classes have fixed homes:

## REG.PATH.ENT.REG — registries path
- KEY: REG.PATH.ENT.REG
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: 03_SYSTEM_ENTITIES registries
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Registries live only in `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/`.
- CHECK: verify registry docs are under 00_REG__REGISTRIES.
- FAIL: registry file found elsewhere.
- FIX: move to canonical folder; update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.TPL — templates path
- KEY: REG.PATH.ENT.TPL
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: entity templates
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Entity templates live only in `03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/`.
- CHECK: scan for `TPL` template docs outside the folder.
- FAIL: templates found outside `01_TPL__TEMPLATES`.
- FIX: move to canonical folder; update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.ENG — engines path
- KEY: REG.PATH.ENT.ENG
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: ENG engines
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Engines live only in `03_SYSTEM_ENTITIES/10_ENG__ENGINES/`.
- CHECK: verify all `*_ENG` are inside the ENG folder tree.
- FAIL: engine file found elsewhere.
- FIX: move to canonical folder; update indexes/XREF; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.ORC — orchestrators path
- KEY: REG.PATH.ENT.ORC
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: ORC orchestrators
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Orchestrators live only in `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/`.
- CHECK: verify all `*_ORC` live inside ORC folder.
- FAIL: orchestrator file found elsewhere.
- FIX: move to canonical folder; update indexes/XREF; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.SPC — specialists path
- KEY: REG.PATH.ENT.SPC
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: SPC specialists
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Specialists live only in `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/`.
- CHECK: verify SPC docs live inside SPC folder.
- FAIL: specialist file found elsewhere.
- FIX: move to canonical folder; update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.CTL — controllers path
- KEY: REG.PATH.ENT.CTL
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: CTL controllers
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Controllers live only in `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/`.
- CHECK: verify CTL docs live inside CTL folder.
- FAIL: controller file found elsewhere.
- FIX: move to canonical folder; update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.VAL — validators path
- KEY: REG.PATH.ENT.VAL
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: VAL validators
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Validators live only in `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/`.
- CHECK: verify VAL docs live inside VAL folder.
- FAIL: validator file found elsewhere.
- FIX: move to canonical folder; update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.QA — quality path
- KEY: REG.PATH.ENT.QA
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: QA checks
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: QA files live only in `03_SYSTEM_ENTITIES/60_QA__QUALITY/`.
- CHECK: verify QA docs live inside QA folder.
- FAIL: QA file found elsewhere.
- FIX: move to canonical folder; update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

## REG.PATH.ENT.XREF — crossref path
- KEY: REG.PATH.ENT.XREF
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: crossref maps
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Crossref maps live only in `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/`.
- CHECK: verify MAP/XREF docs live in xref folder.
- FAIL: xref file found elsewhere.
- FIX: move to canonical folder; update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.PATH.001

---

## 3) WHERE TO PUT "MUSIC FACTORY" WORK
Rule of separation:
- **Entities** (definitions, controllers, validators, QA, orchestrators) → `03_SYSTEM_ENTITIES`
- **Produced content / releases / catalogs / track docs** → `05_PROJECTS`

Meaning:
- `03_SYSTEM_ENTITIES` = “factories and tools”
- `05_PROJECTS` = “products and outputs”

---

## 4) PLACEMENT DECISION QUICK RULE (OPERATOR)
If you are creating a new file, ask:
1) Is it a rule/standard? → `01_SYSTEM_LAW` or `02_STANDARDS`
2) Is it a reusable system entity? → `03_SYSTEM_ENTITIES`
3) Is it a specific album/track/group output artifact? → `05_PROJECTS`
4) Is it just notes and not canon? → keep it out of canon or mark as non-canon (do not index)

---

## FINAL RULE (LOCK)
This path map is authoritative.  
Any relocation/migration must be logged in `90__REG_CHANGELOG.md`.

OWNER: SYSTEM
LOCK: FIXED

--- END.
