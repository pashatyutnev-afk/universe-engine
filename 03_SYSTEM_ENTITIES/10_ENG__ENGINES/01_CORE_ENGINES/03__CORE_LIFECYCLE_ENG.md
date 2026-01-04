# Core Lifecycle Engine
FILE: 03__CORE_LIFECYCLE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines canonical lifecycle states and transitions for ENG entities (families/engines/artifacts); standardizes how items move from draft to active to fixed, how deprecation works, and when archiving is allowed

---

## PURPOSE

Lifecycle отвечает на вопрос:

> “Как элемент системы живёт во времени и по каким правилам меняет статус?”

Без этого:
- “черновики” начинают жить как канон
- deprecated остаётся как будто активное
- архивы путаются с актуальной реальностью
- невозможно управлять стабильностью

---

## NON-GOALS

- не утверждает изменения (Canon Authority)
- не ведёт аудит (Audit Log)
- не версионирует релизы (Versioning & Memory)
Он задаёт **стандарт переходов** и критерии каждого состояния.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Change packets (CHG)
- Canon verdicts (CV)
- Consistency reports (CR)
- Release notes (RN) when lifecycle changes are part of release

### PRODUCES
- LIFECYCLE STATE model (canonical)
- TRANSITION RECORD (TR) artifact for meaningful transitions
- DEPRECATION NOTICE (DN) artifact for retirements

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

### OUTPUT_TARGET
- Every family/engine should follow these lifecycle rules
- INDEX and READMEs may reference lifecycle for status meaning

---

## LIFECYCLE STATES (CANON)

### DRAFT
- exists, may be incomplete
- may be registered in INDEX (if you want tracking)
- cannot be LOCK: FIXED
- allowed to change frequently

### ACTIVE
- usable, coherent
- contract exists and is understandable
- may still evolve, but changes must go through governance if canon-impacting

### FIXED (LOCKED CANON)
- status may remain ACTIVE, but LOCK becomes FIXED
- contract is stable
- consumers can safely build on it
- changes require stricter gate (at least D2 when contract changes)

### DEPRECATED
- still exists for backward compatibility
- cannot be used by new work
- must specify replacement pointer and sunset plan

### ARCHIVED
- removed from active navigation
- cannot be referenced by new canon
- may remain as historical artifact

---

## STATUS VS LOCK (IMPORTANT)

- STATUS is about existence/usefulness (ACTIVE/DEPRECATED/ARCHIVED)
- LOCK is about stability (FIXED/UNFIXED)

Allowed combos:
- STATUS: ACTIVE + LOCK: UNFIXED (in-progress but usable)
- STATUS: ACTIVE + LOCK: FIXED (stable canon)
- STATUS: DEPRECATED + LOCK: FIXED (frozen old)
Not allowed:
- STATUS: ARCHIVED + LOCK: UNFIXED (archive must be frozen or irrelevant)

---

## TRANSITION RULES (CANON)

### Allowed transitions
- DRAFT -> ACTIVE
- ACTIVE -> DEPRECATED
- DEPRECATED -> ARCHIVED
- ACTIVE (UNFIXED) -> ACTIVE (FIXED)  (lock transition)

### Discouraged (require MAJOR decision)
- ACTIVE -> DRAFT (rollback) (only with strong reason + audit)
- ARCHIVED -> ACTIVE (resurrection) (treat as new engine + MAJOR)

---

## ENTRY CRITERIA (GATES)

### DRAFT -> ACTIVE
Required:
- coherent ROLE statement
- mini-contract present
- naming/numbering correct
- registered in INDEX
- no S0 blockers in consistency scan

Recommended:
- basic validation checklist present

### ACTIVE (UNFIXED) -> ACTIVE (FIXED)
Required:
- CR verdict PASS
- CV approval
- audit entry exists
- versioning pointers exist (RN at least)
- contract and boundaries explicitly stated

### ACTIVE -> DEPRECATED
Required:
- deprecation notice (DN)
- replacement pointer (REPLACED_BY)
- sunset timeline or condition

### DEPRECATED -> ARCHIVED
Required:
- no active references in INDEX or READMEs
- archive note includes reason and date
- if references remain historically, they must point to replacement

---

## REQUIRED CANON ARTIFACT: TRANSITION RECORD (TR)

### TRANSITION_RECORD SCHEMA (CANON)

- TR_ID: TR-ENG-0001
- DATE:
- ENTITY:
  - family/engine/artifact path
- FROM_STATE:
- TO_STATE:
- REASON:
  - 3–7 bullets
- REQUIRED UPDATES:
  - list of files and what changes
- VALIDATION REQUIRED:
  - CR? yes/no
  - CV? yes/no
  - AL? yes/no
  - RN? yes/no
- REFERENCES:
  - CHG_ID:
  - CV_ID:
  - AL_ID:
  - RN_ID:
- NOTES (optional)

---

## REQUIRED CANON ARTIFACT: DEPRECATION NOTICE (DN)

### DEPRECATION_NOTICE SCHEMA (CANON)

- DN_ID: DN-ENG-0001
- DATE:
- ENTITY:
- STATUS:
  - DEPRECATED
- REPLACED_BY:
  - file pointer
- WHY:
  - short
- SUNSET:
  - date OR condition
- MIGRATION NOTES:
  - how consumers should adapt
- REFERENCES:
  - CV/AL/RN ids

---

## PROCEDURE (HOW TO APPLY LIFECYCLE)

1) Decide target transition (e.g., draft->active)
2) Check entry criteria and required artifacts
3) If canon-impacting, open CHG and attach IR (if needed)
4) Obtain verdict (CV) when required
5) Apply file header updates (STATUS/LOCK)
6) Write TR or DN artifact if required
7) Log in audit and update release notes if part of release

---

## VALIDATION CHECKLIST

- CL1: No entity is FIXED without CR + CV + AL + RN pointers
- CL2: Deprecated items always have REPLACED_BY and SUNSET
- CL3: Archived items are not referenced by new canon
- CL4: Status and lock combinations obey allowed matrix
- CL5: INDEX reflects current lifecycle (no dead links)

---

OWNER: Universe Engine
LOCK: FIXED
