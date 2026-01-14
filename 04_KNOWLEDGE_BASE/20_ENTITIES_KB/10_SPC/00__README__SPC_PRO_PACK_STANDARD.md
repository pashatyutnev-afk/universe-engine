# SPC — PRO PACK STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/00__README__SPC_PRO_PACK_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.SPC.STD.PRO_PACK.001
OWNER: SYSTEM
ROLE: Defines the canonical structure and minimum content requirements for SPC Pro Packs (specialist competence packs): folder/file layout, required artifacts, linkage to Topics via UID-only XREF, gates/cases/rubrics, provenance discipline, and readiness criteria.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created SPC Pro Pack standard: pack structure, required artifacts, topic linkage rules, and readiness gates aligned to SPC proficiency matrix."
- REASON: "SPC is the 'quality backbone' of entity work; packs must be deep, testable, and deterministic."
- IMPACT: "Consistent SPC competence, easier QA, safer certification readiness."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.STD.001

---

## 0) PURPOSE (KB)
Standardize SPC packs so that any SPC specialist:
- is a real “pro” at their craft
- has deterministic methods and constraints
- can be evaluated by gates/rubrics
- uses Topics correctly (no domain duplication inside packs)

---

## 1) SCOPE (BOUNDARY)
COVERS:
- SPC competence pack internal structure and minimum requirements
- how SPC packs reference Topics and Reference modules
- evaluation, gates, cases, regression discipline

EXCLUDES:
- universal domain topics themselves (live in `10_TOPICS`)
- shared generic assets (live in `30_SHARED_LIBRARIES`)

---

## 2) ABSOLUTE RULES
R1 — No domain topics inside SPC packs
- Domain craft knowledge must remain in `10_TOPICS`.
- SPC packs may only reference domain topics via UID-only XREF.

R2 — Pack must be executable
- Every major capability must have:
  - a method/playbook
  - a checklist or gate
  - examples/cases
  - rubric anchors (for PRO level)

R3 — UID-only crossrefs
- Operational linking is UID-only.
- URLs/PATH are not allowed as authority inside pack XREF blocks.

R4 — Provenance when derived externally
- If a method/rule is derived from external sources, it must be documented in KB_SOURCES.

---

## 3) CANON PACK STRUCTURE (FOLDER/FILE LAYOUT)
A SPC Pro Pack is a folder with the following canonical subfolders/files.

PACK_ROOT:
- 00__PACK_PASSPORT.md
- 01__SCOPE_AND_SKILL_TREE.md
- 02__GOLDEN_PRINCIPLES_AND_LIMITS.md
- 03__METHOD_PLAYBOOKS/
- 04__CHECKLISTS/
- 05__KB_GATES/
- 06__CASE_LIBRARY/
- 07__EVALUATION_RUBRIC.md
- 08__KB_SOURCES.md
- 09__REGRESSION_GUARD.md
- 10__TOPIC_BINDINGS.md

Notes:
- If a folder is not needed, keep it but mark EMPTY with a placeholder note (do not delete layout).
- Aliases/pointers allowed only if they contain no new rules.

---

## 4) REQUIRED CONTENT (MINIMUM)
### 00__PACK_PASSPORT.md (required)
Must include:
- pack UID
- owner entity UID (SPC)
- scope boundary (covers/excludes)
- status, version, lock
- target proficiency level (L1..L4)
- dependencies (UID-only)

### 01__SCOPE_AND_SKILL_TREE.md (required)
Must include:
- responsibilities (what SPC must do)
- forbidden actions (what SPC must not do)
- skill tree with leaf skills (observable outcomes)

### 02__GOLDEN_PRINCIPLES_AND_LIMITS.md (required)
Must include:
- core principles (what to optimize for)
- constraints and safety boundaries
- anti-patterns (what NOT to do)

### 03__METHOD_PLAYBOOKS/ (required)
Must include:
- at least 3 playbooks for L2+
- for L3+ include diagnosis and rework strategy playbooks

### 04__CHECKLISTS/ (required)
Must include:
- readiness checklist
- quality checklist
- compliance checklist when applicable

### 05__KB_GATES/ (required)
Must include:
- at least 1 measurable gate for L1
- at least 3 gates for L3 (including a key-gate candidate)
- gate definitions should follow gate standard where applicable

### 06__CASE_LIBRARY/ (required)
Must include:
- good/bad/borderline cases
- edge cases for L3+
- cases must reference which gate/checklist they calibrate

### 07__EVALUATION_RUBRIC.md (required for SPC)
Must include:
- axes and scoring anchors
- mapping to PASS/REWORK/FAIL
- examples for score anchors for L3+

### 08__KB_SOURCES.md (required when applicable)
Must include:
- provenance records for external-derived methods
- refresh discipline notes if needed

### 09__REGRESSION_GUARD.md (required for L2+ recommended; L4 mandatory)
Must include:
- sample runs
- expected outcomes
- what must not regress after updates

### 10__TOPIC_BINDINGS.md (required)
Must include:
- UID-only bindings to domain topics used by this SPC
- minimal-load recommendation (what to load for which tasks)
- preferred reference glossaries (UID-only)

---

## 5) TOPIC BINDINGS RULES
- Bind only by UID-only.
- For each binding include WHY:
  - what competence this topic supports
- Keep minimal set:
  - do not link the entire universe “just in case”.

---

## 6) READINESS CRITERIA (PASS/REWORK/FAIL)
PASS:
- pack follows layout
- passport + skill tree + principles exist
- playbooks exist for core tasks
- gates + checklists exist
- case library exists and maps to gates
- rubric exists (SPC)
- topic bindings exist (UID-only)

REWORK:
- layout exists but one major block is weak (few cases, weak gates, no rubric anchors)

FAIL:
- missing passport/skill tree/principles
- no gates/cases
- domain topics duplicated inside pack
- no topic bindings
- UID-only rule violated

---

## 7) QUICK PACK AUDIT TEMPLATE (COPY)
SPC_PACK_AUDIT:
- DATE: YYYY-MM-DD
- PACK_UID:
- TARGET_LEVEL: L1/L2/L3/L4
- STRUCTURE_OK: YES/NO
- PASSPORT_OK: PASS/REWORK/FAIL
- SKILL_TREE_OK: PASS/REWORK/FAIL
- PRINCIPLES_OK: PASS/REWORK/FAIL
- PLAYBOOKS_OK: PASS/REWORK/FAIL
- CHECKLISTS_OK: PASS/REWORK/FAIL
- GATES_OK: PASS/REWORK/FAIL
- CASES_OK: PASS/REWORK/FAIL
- RUBRIC_OK: PASS/REWORK/FAIL
- SOURCES_OK: PASS/REWORK/FAIL (if required)
- REGRESSION_OK: PASS/REWORK/FAIL (if required)
- TOPIC_BINDINGS_OK: PASS/REWORK/FAIL
- RESULT: PASS/REWORK/FAIL
- NEXT_ACTIONS:
  - <action>

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- pack contains domain topic content instead of referencing Topics realm
- lacks gates or case calibration
- violates UID-only linking discipline
- claims pro-level without rubric anchors and edge cases
- external-derived rules present without provenance record

---

## 9) RELATED (UID-ONLY)
XREF:
- UE.KB.RULE.ENTITIES.001 | WHY: entity pack minimum and boundaries
- UE.KB.COV.SPC_PROFICIENCY.004 | WHY: proficiency level requirements
- UE.KB.STD.QA_RUBRIC.096 | WHY: rubric standard for scoring
- UE.KB.STD.GATE_DEF.088 | WHY: gate definition standard
- UE.KB.POL.GATE_LIBRARY.092 | WHY: key gate discipline

--- END.
