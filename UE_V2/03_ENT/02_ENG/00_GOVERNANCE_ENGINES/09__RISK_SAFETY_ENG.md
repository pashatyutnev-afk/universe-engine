# RISK SAFETY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

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
UID: UE.ENG.GOV.RISK_SAFETY.001
OWNER: SYSTEM
ROLE: Safety gate for canon changes. Converts scope impact + diffs into blockers, risk score, mitigation plan, and safety decision (SAFE/CONDITIONAL/UNSAFE).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Risk Safety upgraded to full canonical safety gate: S0 blockers, risk matrix, mitigation contract, release decision, rollback requirements."
- REASON: "Prevent canon corruption, broken raw navigation, and unsafe structural edits."
- IMPACT: "All high-impact changes become explicitly gated and reversible."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.RISK.001

---

## 0) PURPOSE (LAW)

Risk Safety Engine отвечает:
> “Можно ли безопасно вносить это изменение в канон прямо сейчас?”

Он принимает результаты Scope Impact и факты изменений и выдаёт:
- список **BLOCKERS (S0..S3)**
- **risk score** и категории риска
- **MITIGATION_PLAN** (что обязано быть сделано)
- **SAFETY_DECISION**:
  - SAFE (можно)
  - CONDITIONAL (можно только после mitigations)
  - UNSAFE (нельзя, нужен редизайн/разбиение/откат)

Non-goals:
- не делает индексы и ссылки (это Scope Impact + Change Control)
- не доказывает консистентность всего репо (это Consistency)
- не утверждает канон (это Canon Authority / Decision Approval), но даёт обязательные safety факты

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES:
- SCOPE_IMPACT_REPORT
- DIFF_SUMMARY
- AFFECTED_FILES_LIST
- CHANGE_PROPOSAL
- MIGRATION_MAP?                         # if IC3 present
- REQUIRED_UPDATES_LIST?                 # from Scope Impact
- CONSISTENCY_FINDINGS?                  # optional input

PRODUCES:
- SAFETY_ASSESSMENT_REPORT
- BLOCKERS_LIST
- MITIGATION_PLAN
- SAFETY_DECISION
- ROLLBACK_REQUIREMENTS

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__AUDIT.md

---

## 2) SEVERITY SCALE (STRICT)

Blocker severity uses strict set:

S0 — Hard Blocker
- cannot proceed; change must not be closed/merged into canon
- requires redesign or missing mandatory artifacts

S1 — High Risk / Must Mitigate
- proceed only with mitigation plan + explicit confirmation in governance pipeline

S2 — Medium Risk
- mitigation recommended; can proceed with warnings recorded

S3 — Low Risk
- informational; safe by default

Hard rule:
- if any S0 blocker exists => SAFETY_DECISION must be UNSAFE.

---

## 3) RISK CATEGORIES (CANON)

Each blocker must declare one or more categories:

R1 — Navigation Break
- broken raw-links, broken indexes, missing entrypoints

R2 — Canon Integrity
- violates existence rule, duplicates, hidden canon, stale index mappings

R3 — Identity / UID Corruption
- UID changes without explicit policy, UID collisions, UID drift

R4 — Dependency Graph Damage
- hidden deps, broken deps, cycles without explicit rationale

R5 — Uncontrolled Scope
- IC3/IC6 change without migration/impact, wide blast radius without packaging

R6 — Data Loss / Irreversible Delete
- delete without deprecation/replacement pointer and rollback steps

R7 — Governance Bypass
- changes touching locked docs without proper pipeline, missing audit record

R8 — Cross-layer Conflict
- standards/laws/entities/projects diverge, incompatible schema

---

## 4) HARD BLOCKERS (S0) — EXACT LIST

If any condition holds => create S0 blocker.

S0.B1 — Missing impact classification
- no impact classes / no Scope Impact report

S0.B2 — IC3 without MIGRATION_MAP
- rename/move/delete but no migration map

S0.B3 — Required updates not satisfied (known)
- Scope Impact says UPDATE_* required but plan does not include it

S0.B4 — Broken raw-link guarantee
- canonical index contains raw-links to paths that changed but links not updated

S0.B5 — Existence rule violation
- canonical file exists but not registered in canonical index OR
- index references file that does not exist

S0.B6 — Unsafe delete
- canon file deleted without deprecation + replacement pointer + rollback hints

S0.B7 — Locked canon edited without governance trace
- LOCK: FIXED document changed without explicit Change ID + audit record plan

S0.B8 — UID collision / missing UID in canon doc type that requires it
- duplicates or missing UID in engines/templates/indexes where standard demands

S0.B9 — Dependency registry mismatch (when engines affected)
- engine added/removed/renamed but dependency records not planned

---

## 5) RISK MATRIX (SCORING)

Risk score is computed as:
- BASE from impact classes:
  - IC0: +0
  - IC1: +1
  - IC2: +2
  - IC3: +4
  - IC4: +5
  - IC5: +3
  - IC6: +4
- ADDERS (if present):
  - touches LOCK: FIXED files: +2
  - delete operation: +3
  - rename/move of entrypoints/indexes: +3
  - raw-link heavy index touched: +2
  - multi-layer impact: +2
- SUBTRACTORS (if mitigation ready):
  - complete MIGRATION_MAP: -1
  - complete REQUIRED_UPDATES_LIST satisfied: -2
  - rollback plan exists: -1

Interpretation:
- 0–2: LOW (usually SAFE)
- 3–6: MEDIUM (SAFE or CONDITIONAL)
- 7–10: HIGH (usually CONDITIONAL)
- 11+: CRITICAL (often UNSAFE unless split)

Note:
- scoring never overrides S0 blockers.

---

## 6) MITIGATION PLAN (MANDATORY FOR S1+)

MITIGATION_PLAN is a binding list of steps, each must be verifiable.

Mitigation step format:
- MID: UE.MIT.YYYY-MM-DD.NNN
- TYPE: UPDATE_INDEX_ENTRY | UPDATE_RAW_LINK | UPDATE_DEPENDENCY_RECORDS | UPDATE_MIGRATION_MAP | VERSION_BUMP | AUDIT_LOG | CONSISTENCY_POST_VERIFY | DEPRECATION_POINTER | ROLLBACK_PLAN
- TARGET:
- DONE_BY: (role/entity)
- PROOF: (what evidence confirms it)
- STATUS: PENDING|DONE

Hard rules:
- if S1 blockers exist => mitigation plan must exist.
- if IC3 exists => mitigation must include MIGRATION_MAP + raw-link updates.

---

## 7) ROLLBACK REQUIREMENTS (MANDATORY FOR IC3/IC4/IC6)

If change includes IC3 or IC4 or IC6:
- must output ROLLBACK_REQUIREMENTS.

Rollback requirement format:
- RR_ID: UE.RR.YYYY-MM-DD.NNN
- TRIGGER: what failure forces rollback
- ACTIONS: minimal revert steps
- RESTORE: which indexes/links must be restored
- DATA_LOSS: YES|NO (and what)

---

## 8) SAFETY DECISION (STRICT)

SAFETY_DECISION is computed:

If any S0 blocker => UNSAFE

Else if any S1 blocker => CONDITIONAL
- proceed only if all mitigations are DONE

Else => SAFE

Decision must include:
- DECISION: SAFE|CONDITIONAL|UNSAFE
- RISK_SCORE:
- REASONS: list
- REQUIRED_MITIGATIONS: list (empty only for SAFE)

---

## 9) OUTPUT FORMAT — SAFETY_ASSESSMENT_REPORT (CANON)

SAFETY_ASSESSMENT_REPORT:
- REPORT_ID: UE.SAFETY.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- TIME: HH:MM (or NA)
- CHANGE_ID:
- IMPACT_CLASSES: [IC0..IC6]
- RISK_SCORE: N
- DECISION: SAFE|CONDITIONAL|UNSAFE
- BLOCKERS_LIST:
  - BLK_ID: UE.BLK.YYYY-MM-DD.NNN
    SEVERITY: S0|S1|S2|S3
    CODE: S0.B1 .. (or custom)
    CATEGORY: R1..R8
    WHAT:
    WHY:
    FIX:
    PROOF_REQUIRED:
- MITIGATION_PLAN: none | list
- ROLLBACK_REQUIREMENTS: none | list
- NOTES:

---

## 10) CHECKLISTS (PRACTICAL)

### 10.1 Safety checklist for structural edits (IC3)
- [ ] MIGRATION_MAP exists and complete
- [ ] REQUIRED_UPDATES_LIST fully covered by mitigations
- [ ] raw-link impact list covered
- [ ] rollback requirements defined
- [ ] audit log entry planned

### 10.2 Safety checklist for locked canon edits
- [ ] explicit CHANGE_ID in change note
- [ ] version bump defined
- [ ] audit entry required
- [ ] consistency post-verify planned

---

## 11) EXAMPLES

### Example A — rename engine file (IC3 + IC5)
Blockers:
- S0 if MIGRATION_MAP missing
- S1 if dependency updates not yet done
Decision:
- CONDITIONAL until mitigations done

### Example B — index reorder (IC2)
Blockers:
- S1 if reorder breaks numbering rules
- S0 if index references missing file

### Example C — delete canon doc (IC3)
Blockers:
- S0 unless deprecation + replacement pointer + rollback exist

---

## 12) REFERENCES (RAW ONLY)

Scope Impact:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md

Rule Hierarchy:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

Audit Log (target):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md

--- END.
