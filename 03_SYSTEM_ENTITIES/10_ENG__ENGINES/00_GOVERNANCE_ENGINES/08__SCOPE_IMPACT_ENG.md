# SCOPE IMPACT ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.GOV.SCOPE_IMPACT.001
OWNER: SYSTEM
ROLE: Blast-radius analyzer for canon changes. Produces SCOPE_IMPACT_REPORT including required secondary updates, migration map, raw-link impact, dependency impact, and rollback hints.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Scope Impact upgraded to full canonical blast-radius engine (impact classes, required updates, migration law, report format, rename/move/delete checklists)."
- REASON: "Prevent partial renames, stale indexes, and broken raw navigation."
- IMPACT: "Structural changes become predictable and safely packageable."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.SCOPE.001

---

## 0) PURPOSE (LAW)

Scope Impact Engine отвечает:
> “Если мы меняем X — что ещё обязаны обновить, чтобы система осталась живой?”

Он не решает approve/reject, но формирует обязательные “хвосты” изменения:
- какие индексы/реестры нужно поправить
- какие raw-links обновить
- какие dependencies обновить
- где нужен migration map
- какие версии bump’нуть
- какие риски/rollback подсветить

Non-goals:
- не выполняет изменения (это Change Control)
- не валидирует всё состояние (это Consistency)
- не ставит safety blockers (это Risk Safety), но даёт им вход

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_PROPOSAL
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- DIFF_SUMMARY
- DEPENDENCY_DECLARATIONS?               # if engines are affected
- CANON_INDEX_REFERENCES?                # known entrypoints/indexes in scope

PRODUCES:
- SCOPE_IMPACT_REPORT
- REQUIRED_UPDATES_LIST
- MIGRATION_MAP?                         # required for rename/move/delete
- RAW_LINK_IMPACT_LIST
- DEPENDENCY_IMPACT_LIST
- VERSIONING_HINTS
- ROLLBACK_HINTS

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 2) IMPACT CLASSES (STRICT)

Every change must be classified into one or more impact classes:

IC0 — Editorial
- text clarity, typos, formatting, comments
- usually no secondary updates (but still may require version bump if canon)

IC1 — Canon Content Change
- semantic meaning changes inside a canon doc, no path/index changes
- secondary updates: version bump, change note, memory

IC2 — Index / Registry Change
- changes to canonical indexes/registries, reorder/entry add/remove
- secondary updates: raw-links, existence map alignment, post-verify

IC3 — Structure / Navigation Change
- rename/move/delete, folder structure changes, entrypoint changes
- secondary updates: MIGRATION_MAP mandatory + update all impacted indexes + raw links

IC4 — Identity Change
- UID changes, naming rules changes, versioning policy changes
- secondary updates: wide scope impact, risk report likely, strict audit/memory

IC5 — Dependency Graph Change
- DEPENDS_ON changes, new engine added, family order changes
- secondary updates: dependency records + consistency checks

IC6 — Cross-Layer Change
- affects multiple layers (laws/standards/entities/projects)
- secondary updates: risk safety mandatory + broader consistency targets

---

## 3) REQUIRED UPDATES (CANON LAW)

This engine outputs REQUIRED_UPDATES_LIST — this list is binding for Change Control.

Update types (strict set):
- UPDATE_INDEX_ENTRY
- UPDATE_RAW_LINK
- UPDATE_DEPENDENCY_RECORDS
- UPDATE_MIGRATION_MAP
- UPDATE_UID_REFERENCES
- UPDATE_VERSION_BUMP
- UPDATE_MEMORY_RECORDS
- UPDATE_DEPRECATION_POINTER
- UPDATE_REPLACEMENT_POINTER
- UPDATE_CROSSREF_MAP (only if crossref system is used)

Hard rule:
- if REQUIRED_UPDATES_LIST says something is required, closing the change without it is invalid.

---

## 4) MIGRATION LAW (RENAME/MOVE/DELETE)

If DIFF_SUMMARY includes any:
- rename
- move
- delete
Then MIGRATION_MAP is mandatory.

MIGRATION_MAP entry format:
- OLD_PATH:
- NEW_PATH: (or DELETED)
- UID: (should remain same unless explicitly changed)
- CHANGE_ID:
- WHY:
- REQUIRED_UPDATES:
  - indexes to update
  - raw-links to update
  - dependency updates (if any)
- EXPIRY: optional (if temporary dual links allowed)
- NOTES:

Hard rules:
- deleting canon file requires deprecation + replacement pointer (unless non-canon)
- rename/move must update all canonical indexes that reference OLD_PATH

---

## 5) RAW LINK IMPACT LAW

If any canonical index/entrypoint includes raw-links:
- every affected path rename/move implies raw-link update is mandatory.

RAW_LINK_IMPACT_LIST entry format:
- SOURCE_PATH: (file containing the raw link)
- TARGET_OLD: raw link URL
- TARGET_NEW: raw link URL
- WHY:
- REQUIRED: YES

If raw-links are required and not updated -> S0 blocker in Risk Safety / Consistency.

---

## 6) DEPENDENCY IMPACT LAW

If any engine file is added/removed/renamed or DEPENDS_ON changed:
- dependency records must be updated (Dependency Registry Engine).
- required update: UPDATE_DEPENDENCY_RECORDS

DEP_IMPACT entry format:
- FROM_ENGINE:
- TO_ENGINE:
- TYPE: HARD|SOFT
- CHANGE_ID:
- WHY:

---

## 7) VERSIONING HINTS

Scope Impact does not bump versions itself, but outputs hints:
- list of files that must bump VERSION
- suggested bump level: PATCH/MINOR/MAJOR
- why (impact class, lock, index touched)

Versioning hints become binding when Canon Authority / Versioning Memory confirms.

---

## 8) ROLLBACK HINTS (MINIMAL)

If impact classes include IC2/IC3/IC4/IC6:
- rollback hints must exist.

Rollback hint includes:
- what would break if change fails
- minimal revert steps
- which indexes must be restored

---

## 9) HARD GATES (ENFORCEMENT)

- G1 Every change must have at least one impact class.
- G2 If IC3 present => MIGRATION_MAP mandatory.
- G3 If IC2 present => UPDATE_INDEX_ENTRY mandatory.
- G4 If raw-links exist in affected indexes => UPDATE_RAW_LINK mandatory.
- G5 If IC5 present => UPDATE_DEPENDENCY_RECORDS mandatory.
- G6 If IC4 present => treat as high-risk (flag for Risk Safety).
- G7 Required updates list cannot be empty for IC2/IC3/IC5/IC6 changes.

---

## 10) OUTPUT FORMAT — SCOPE_IMPACT_REPORT (CANON)

SCOPE_IMPACT_REPORT:
- REPORT_ID: UE.SCOPE.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- TIME: HH:MM (or NA)
- CHANGE_ID:
- IMPACT_CLASSES: [IC0..IC6]
- PRIMARY_AFFECTED:
  - ITEM: DOC|INDEX|ENGINE|TEMPLATE|REGISTRY|MAP
    PATH:
    UID:
- REQUIRED_UPDATES_LIST:
  - RU_ID: UE.RU.YYYY-MM-DD.NNN
    TYPE: <from strict set>
    TARGET: <path or record target>
    WHY:
    SEVERITY: S0|S1|S2|S3
- MIGRATION_MAP: none | list
- RAW_LINK_IMPACT_LIST: none | list
- DEPENDENCY_IMPACT_LIST: none | list
- VERSIONING_HINTS: list
- ROLLBACK_HINTS: list
- NOTES:

---

## 11) CHECKLISTS (PRACTICAL)

### 11.1 Rename / Move checklist (IC3)
- [ ] MIGRATION_MAP entry created
- [ ] all canonical indexes referencing OLD_PATH updated
- [ ] raw-links updated
- [ ] dependency records updated if engine file moved/renamed
- [ ] version bump planned for touched canon files
- [ ] consistency post-verify required

### 11.2 Delete checklist (IC3)
- [ ] deprecate + replacement pointer OR explicit allowed delete
- [ ] MIGRATION_MAP entry with NEW_PATH: DELETED
- [ ] indexes updated (remove entry or point to replacement)
- [ ] raw-links removed/updated
- [ ] consistency post-verify

### 11.3 Index change checklist (IC2)
- [ ] entry list matches real files
- [ ] raw-links present where required
- [ ] ordering rules maintained (NN)
- [ ] consistency post-verify required

---

## 12) EXAMPLES

### Example A — simple patch (IC1)
- Edit text in one engine
Required updates:
- version bump + memory + audit
No migration map.

### Example B — rename engine file (IC3 + IC5)
- Rename 05__CONSISTENCY_ENG.md -> 05__CONSISTENCY_ENGINE.md
Required updates:
- migration map
- update ENG index raw-link
- update any references/raw links
- update dependency records for any edges pointing to old filename
- post-verify

### Example C — add new engine (IC5)
Required updates:
- register in ENG index
- add dependency records
- version bump for index
- post-verify

---

## 13) REFERENCES (RAW ONLY)

Dependency Registry:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

Rule Hierarchy:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

Change log storage:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md

--- END.
