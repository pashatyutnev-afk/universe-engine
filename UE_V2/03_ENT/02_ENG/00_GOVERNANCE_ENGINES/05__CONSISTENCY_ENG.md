# CONSISTENCY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

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
UID: UE.ENG.GOV.CONSISTENCY.001
OWNER: SYSTEM
ROLE: Canon integrity inspector. Detects violations across headers/UID/naming/index existence/raw-links/dependencies and produces CONSISTENCY_REPORT with ordered FIX_PLAN.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Consistency Engine upgraded to fully specified canonical inspector (domains, severities, gates, report formats, modes, recovery)."
- REASON: "Prevent broken canon states and hidden drift."
- IMPACT: "Canon changes can be gated and validated deterministically."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.CNS.001

---

## 0) PURPOSE (LAW)

Consistency Engine отвечает за вопрос:
> “Система всё ещё жива и канон не сломан?”

Он выполняет **структурные** проверки:
- шапки (Doc Control) и single-truth метаданных
- UID: наличие/формат/уникальность (на уровне проверяемого scope)
- naming/numbering (там где стандартизировано)
- existence/index coherence (индекс ссылается на то, что реально должно существовать)
- raw-link integrity (когда raw-links обязательны)
- dependency transparency (DEPENDS_ON <-> dependency records)
- authority collision (двойные источники истины)

Non-goals (hard):
- не оценивает художественное качество текста
- не решает approve/reject (это Canon Authority)
- не применяет изменения (это Change Control)
- не заменяет валидаторы фактов/научности (это VAL engines)

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_PACKAGE_RECORD?            # required in post-verify mode
- TARGET_SCOPE                      # what to inspect (layer/family/files)
- AFFECTED_FILES_LIST?              # for delta mode
- CANON_INDEX_REFERENCES?           # canonical entrypoints (raw list or known)
- DEPENDENCY_DECLARATIONS?          # extracted from engines if scope includes ENG
- DEPENDENCY_RECORDS?               # from dependency registry storage

PRODUCES:
- CONSISTENCY_REPORT
- VIOLATION_LIST
- FIX_PLAN

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 2) MODES (MANDATORY)

### Mode P — PRECHECK (before apply)
Goal:
- find blockers before change is applied

Inputs:
- TARGET_SCOPE + AFFECTED_FILES_LIST (recommended)

Output:
- CONSISTENCY_REPORT with RESULT: PASS|WARN|FAIL

### Mode C — POST-VERIFY (after apply, required to close)
Goal:
- certify canon integrity after changes

Inputs:
- CHANGE_PACKAGE_RECORD + AFFECTED_FILES_LIST + TARGET_SCOPE

Output:
- CONSISTENCY_REPORT used by Change Control close gate

Hard rule:
- any canon-impacting change cannot be closed without Mode C PASS (or PASS_WITH_WARN per policy).

---

## 3) SEVERITY MODEL (S0..S3)

S0 — BLOCKER (system broken)
- broken raw-link in canonical entrypoint/index
- index references missing file (existence broken)
- authority collision (two SoT for existence)
- UID duplication in canonical domain (collision)
- FIXED edited outside pipeline evidence
Result:
- FAIL

S1 — HIGH (canon integrity violated)
- missing required header fields
- missing UID in canonical file
- duplicate truth metadata inside file
- missing mini-contract in engine (if engine scope)
- dependency change without dependency record (policy: can be S0 or S1)
Result:
- FAIL or WARN depending on policy; default FAIL for canon-impacting close gate

S2 — MEDIUM (consistency drift)
- naming deviations not breaking tooling
- missing optional sections
- weak cross-links/references
Result:
- WARN

S3 — LOW (cosmetic)
- formatting issues, minor typos
Result:
- WARN

---

## 4) CHECK DOMAINS (D0..D7)

D0 — DOC CONTROL HEADER COMPLIANCE
Checks:
- required fields exist (FILE/SCOPE/LAYER/DOC_TYPE/STATUS/LOCK/VERSION/UID/OWNER/ROLE/CHANGE_NOTE)
- CHANGE_NOTE present and well-formed
- single-truth: no duplicated STATUS/LOCK/VERSION/OWNER blocks outside header

D1 — UID INTEGRITY
Checks:
- UID present where required
- UID format not empty
- UID uniqueness within inspected scope (best-effort)
- UID stability hints (if migration map provided)

D2 — NAMING / NUMBERING INTEGRITY
Checks:
- family numbering rules (NN__ prefix) where used
- README files are 00, engines are 01+
- index ordering matches filename numbering (if index provided)

D3 — EXISTENCE / INDEX COHERENCE
Checks:
- canonical index entries do not point to non-existent paths
- if existence rule says “only indexed exists”, then:
  - file exists but not indexed => flagged as NON-CANON drift (S2) OR S1 if it is referenced as canon elsewhere
- index path mismatches => S0/S1 depending on impact

D4 — RAW-LINK INTEGRITY
Checks:
- for canonical entrypoints/indexes: raw-links must be present and valid syntax
- if raw-only policy is enforced: any non-raw link where raw is mandatory => S1
- missing raw in index entry => S1 (or S0 if it breaks navigation requirement)

D5 — DEPENDENCY TRANSPARENCY
Scope: ENG engines
Checks:
- each engine has mini-contract including DEPENDS_ON
- DEPENDS_ON references are consistent with dependency records storage (policy)
- no dependency record references unknown engine

D6 — AUTHORITY COLLISION (DOUBLE-SoT)
Checks:
- two indexes claiming existence for same domain
- a “sub-index” pretending to be SoT where law says forbidden
- conflicting “single index law” statements across docs
Result:
- S0

D7 — CROSS-LAYER DRIFT (optional)
Checks:
- cross-layer entrypoints referenced but absent
- standards referenced but missing
Result:
- S1/S2 depending on scope

---

## 5) HARD GATES (CLOSE-GATE ENFORCEMENT)

The following rules are non-negotiable for POST-VERIFY close:

- G1 No S0 violations
- G2 No S1 violations (default policy)
- G3 Index/existence coherence must hold for affected indexes
- G4 Raw-links required by canon entrypoints must be valid
- G5 Any dependency drift must be resolved (DEPENDS_ON and dependency records aligned)

If any gate fails -> RESULT: FAIL -> Change Control must not close the package.

---

## 6) OUTPUT FORMATS (CANON)

### 6.1 CONSISTENCY_REPORT (required)
CONSISTENCY_REPORT:
- REPORT_ID: UE.CNS.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- TIME: HH:MM (or NA)
- MODE: PRECHECK|POST-VERIFY
- TARGET_SCOPE: <string>
- CHANGE_ID: <optional>
- RESULT: PASS|PASS_WITH_WARN|WARN|FAIL
- COUNTS:
  - S0:
  - S1:
  - S2:
  - S3:
- VIOLATIONS:
  - VID: UE.VIO.YYYY-MM-DD.NNN
    SEVERITY: S0|S1|S2|S3
    DOMAIN: D0..D7
    RULE: <short id>
    PATH: <file path>
    UID: <optional>
    MESSAGE: <human readable>
    EVIDENCE: <short excerpt or pointer>
    FIX: <one-line fix>
- FIX_PLAN:
  - ORDER: 1..N
    ACTION: <short>
    TARGET: <path>
    WHY:
    SEVERITY:

### 6.2 VIOLATION_LIST (normalized)
VIOLATION:
- SEVERITY
- DOMAIN
- PATH
- MESSAGE
- FIX

---

## 7) DECISION RULES (RESULT CALCULATION)

Default (strict) mapping:
- If any S0 -> FAIL
- Else if any S1 -> FAIL in POST-VERIFY; WARN in PRECHECK
- Else if any S2 -> WARN
- Else if only S3 -> PASS_WITH_WARN
- Else -> PASS

Policy can be tightened but never loosened for S0.

---

## 8) EXAMPLES (GOOD / BAD)

### 8.1 GOOD — PASS
- all files have full header + UID
- indexes reference existing files
- required raw links exist in canonical entrypoints
- deps consistent

Result:
- PASS

### 8.2 BAD — S0: broken index existence
- canonical index references path that does not exist
Result:
- FAIL
Violation:
- SEVERITY: S0
- DOMAIN: D3
- RULE: IDX_PATH_MISSING
Fix:
- update index or restore file

### 8.3 BAD — S1: missing UID in canonical engine
Result:
- FAIL (post-verify)
Fix:
- add UID

### 8.4 BAD — authority collision
Two docs claim “only source of truth” for same domain
Result:
- FAIL (S0)
Fix:
- delete/convert one to pointer, keep single SoT

---

## 9) RECOVERY / FIX STRATEGY (ORDER)

Fix order:
1) S0 blockers first (existence/raw/authority)
2) S1 (UID/header/mini-contract)
3) S2 drift
4) S3 cosmetic

Never waste time on S3 if S0/S1 exist.

---

## 10) EDGE CASES

### 10.1 Intentional non-canon files
Files that exist but are not in index:
- should not be treated as canon
- but if referenced from canon docs as if canon -> flag S1/S0 depending on claim

### 10.2 Migration in progress
During renames/moves:
- require migration map
- temporarily allow dual references only if explicitly documented in change package and expires

### 10.3 Partial scope scanning
If TARGET_SCOPE is narrow:
- UID uniqueness check is best-effort (only within scope)
- do not claim global uniqueness

---

## 11) REFERENCES (RAW ONLY)

Rule Hierarchy:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

Dependency Registry:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

Change Control:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

Canon Authority:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

Logs:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md

--- END.
