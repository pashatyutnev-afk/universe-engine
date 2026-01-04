# Consistency Engine
FILE: 05__CONSISTENCY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: System-wide integrity + contradiction detection for ENG engines; prevents role overlap, canon drift, broken dependencies, and incoherent terminology

---

## PURPOSE

Этот движок — “охранник целостности” ENG.

Он нужен, чтобы:
- движки не противоречили друг другу
- роли движков не дублировались
- терминология была единой
- handoff между движками был согласован
- INDEX и файлы не расходились

---

## SCOPE (WHAT IT CHECKS)

Consistency Engine проверяет:

1) **Registry consistency**
- файл существует → он зарегистрирован в INDEX
- номер в имени файла совпадает с номером в INDEX
- README семейства существует и корректно связан

2) **Metadata consistency**
- SCOPE / ENTITY_GROUP / FAMILY / CLASS / LEVEL / STATUS / VERSION присутствуют
- нет двойного STATUS (внизу должен быть LOCK)

3) **Role consistency**
- ROLE движка не пересекается с другим движком без boundary owner
- ясна зона “что движок НЕ делает”

4) **Contract consistency**
- mini-contract заполнен в каждом движке
- CONSUMES ↔ PRODUCES upstream/downstream совпадают (handoff не “придуман”)
- DEPENDS_ON отражает реальные зависимости

5) **Terminology consistency**
- канон-термины совпадают по смыслу и названию
- нет двух терминов для одного и того же
- нет одного термина с разными смыслами

6) **Level/Class consistency**
- CLASS/LEVEL семейства в INDEX соответствует README и движкам внутри
- особенно META (L4) — без “проседаний” до L3

---

## NON-GOALS (WHAT IT DOES NOT DO)

- не утверждает канон (это Canon Authority)
- не управляет изменениями (это Change Control)
- не описывает зависимости как язык (это Dependency Registry)
- не пишет вместо доменных движков их содержание (он только выявляет конфликты)

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- index registry (00__INDEX_ALL_ENGINES.md)
- engine files (all families)
- dependency notes (from Dependency Registry)
- change packet (from Change Control) when auditing a change
- canon terms from README family realm files

### PRODUCES
- CONSISTENCY REPORT (canonical artifact)
- contradiction list + overlap list
- required fixes list (file-by-file)
- severity scoring and stop/go decision

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

### OUTPUT_TARGET
- Used before LOCKing any canon set, and before merging any MAJOR change
- Report is attached to change packet and referenced in audit log

---

## CANON OUTPUT ARTIFACT: CONSISTENCY REPORT (MANDATORY)

Любая проверка должна отдавать отчёт в стандартной форме:

### CONSISTENCY_REPORT (CANON FORMAT)

- REPORT_ID: CR-ENG-0001
- DATE:
- AUDIT_SCOPE:
  - families covered
  - files covered
- TRIGGER:
  - periodic | pre-lock | pre-release | post-change
- SUMMARY:
  - short verdict: PASS | PASS_WITH_FIXES | FAIL
- SEVERITY COUNTS:
  - S0 blockers:
  - S1 critical:
  - S2 major:
  - S3 minor:
- FINDINGS:
  - list of issues (see finding schema)
- REQUIRED FIXES (ORDERED):
  - file-by-file actions
- DEPENDENCY NOTES:
  - edges affected / risk of cycles
- APPROVAL REQUIRED:
  - yes/no + who (canon authority)
- NEXT ACTION:
  - lock / fix / re-audit

### FINDING SCHEMA (EACH ISSUE)

- ID: C-0001
- SEVERITY: S0 | S1 | S2 | S3
- TYPE:
  - INDEX_DRIFT | NAMING_MISMATCH | METADATA_MISSING | LEVEL_MISMATCH
  - ROLE_OVERLAP | CONTRACT_GAP | HANDOFF_MISSING | TERM_CONFLICT
  - DEP_CYCLE | LINK_BROKEN | DUPLICATE_STATUS
- LOCATION:
  - file path(s)
  - section(s)
- DESCRIPTION:
  - what is wrong
- WHY_IT_MATTERS:
  - impact explanation
- FIX:
  - exact fix steps (minimum)
- OWNER:
  - who must change it
- STATUS:
  - OPEN | FIXED | WAIVED
- WAIVER_RULE (optional):
  - if waived, explain why and for how long

---

## SEVERITY STANDARD (CANON)

### S0 — BLOCKER (STOP SHIP)
- index drift (file exists but not in INDEX, or INDEX points to missing file)
- naming/number mismatch
- level mismatch on family (e.g., META L4 vs files L3)
- broken dependency cycles without explicit governance breaks
- contradictions that break downstream pipeline (handoff impossible)

### S1 — CRITICAL
- role overlap without boundary owner
- mini-contract missing or clearly wrong
- handoff missing when produces/consumes exists
- terminology collision (same term different meaning)

### S2 — MAJOR
- weak/unclear boundaries leading to likely duplication
- missing required sections (procedure/validation)
- inconsistent output artifact definitions

### S3 — MINOR
- formatting inconsistencies
- small wording drift
- missing integration notes but contract exists

---

## CONSISTENCY DOMAINS (WHAT WE MUST KEEP CLEAN)

### 1) ROLE MAP (NO OVERLAP WITHOUT OWNER)
If overlap exists:
- designate OWNER engine
- add boundary notes in both engines
- add handoff mapping
- log in audit

### 2) CONTRACT MAP (CONSUME/PRODUCE MUST MATCH)
If engine says it consumes X, upstream must produce X.
If it doesn’t exist → mark as CONTRACT_GAP (S1/S0 depending).

### 3) TERMINOLOGY MAP
Canonical terms must live in:
- family README realm file
- or global glossary (if exists)
If term defined in two places differently → TERM_CONFLICT (S1).

### 4) LEVEL MAP
Family class/level must be consistent:
- INDEX ↔ README ↔ all engines
Mismatch is S0.

---

## PROCEDURE (HOW TO RUN A CONSISTENCY AUDIT)

1) Load audit scope
- full system OR selected families OR change packet touched files

2) Registry scan
- INDEX entries exist and links point to real files
- files in repo are registered (or marked non-canon)

3) Metadata scan
- mandatory header fields present
- bottom lock block present
- no duplicate STATUS

4) Role scan
- compare ROLE + purpose across engines in same layer
- flag overlaps and missing boundaries

5) Contract scan
- verify mini-contract is present
- map produces→consumes across engines
- verify depends_on edges are coherent

6) Terminology scan
- list core terms per family README
- detect collisions / drift

7) Dependency risk scan
- detect cycles and hidden couplings (with Dependency Registry)
- classify cycle type: forbidden by default

8) Produce Consistency Report
- severity list + ordered fix plan
- stop/go verdict

9) Route to Change Control (if fixes needed)
- create CHG packet(s) for the required fixes
- after fixes, rerun audit

---

## QUICK CHECKLIST (FAST MODE)

- K1: INDEX ↔ files match (no drift)
- K2: naming/numbering correct
- K3: no duplicate STATUS; use LOCK
- K4: mini-contract exists everywhere
- K5: handoff described where outputs feed downstream
- K6: no role overlap without OWNER/boundary
- K7: family LEVEL consistent (INDEX/README/engines)

---

## INTEGRATION (GOVERNANCE PIPELINE)

- Triggered by:
  - Change Control gate G3 (consistency)
  - Pre-lock releases
  - Periodic maintenance

- Feeds into:
  - Canon Authority (approve/waive)
  - Audit Log (record report + verdict)
  - Dependency Registry (edge fixes / cycle fixes)

---

## FAILURE MODES (COMMON)

- “Система кажется логичной”, но отсутствует contract/handoff → downstream ломается
- Индекс красивый, но ссылки/номера расходятся → навигация становится ложной
- Движки дублируют роли → разные агенты будут принимать разные решения
- META уровень не совпадает → мета-слой начинает “конкурировать” с L3

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
