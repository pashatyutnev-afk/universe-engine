# Canon Authority Engine
FILE: 02__CANON_AUTHORITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines single source of truth and decision authority for ENG canon; issues canon verdicts for changes, resolves contradictions, assigns ownership, and controls waivers and locks

---

## PURPOSE

Этот движок — “судья канона” ENG.

Он нужен, чтобы:
- существовала **единственная точка истины** о том, что считается каноном
- любые конфликты/противоречия имели финальное решение
- изменения не становились каноном без утверждения
- были правила ownership, waivers и lock decisions

---

## SCOPE (WHAT IT CONTROLS)

Canon Authority контролирует:

1) **Canon truth decisions**
- принять/отклонить/вернуть на доработку изменения
- определить “источник истины” при конфликте

2) **Ownership**
- назначение владельцев (OWNER) зон/семейств/движков
- назначение “OWNER of overlap” когда роли пересекаются

3) **Waivers**
- разрешение временных несоответствий
- условия и сроки waiver’ов

4) **Lock policy**
- когда ставится `LOCK: FIXED`
- когда допускается `LOCK: UNFIXED` и почему

5) **Conflict resolution**
- терминологические конфликты
- role overlap конфликты
- dependency cycle разрешения (через governance break)

---

## NON-GOALS

- не проводит технический аудит целостности (это Consistency Engine)
- не управляет workflow изменений (это Change Control)
- не заменяет dependency language (это Dependency Registry)
- не пишет доменную логику движков

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- CHG packets (from Change Control)
- Consistency Reports (CR)
- Dependency Graph snapshots + Cycle Reports (DG/CY)
- Proposals for new engines/families/index edits
- Any conflict report: terminology/role/dependency

### PRODUCES
- CANON VERDICT (mandatory artifact)
- OWNERSHIP ASSIGNMENTS (when needed)
- WAIVER DECISIONS (when needed)
- LOCK DECISIONS (FIXED/UNFIXED)
- CONFLICT RESOLUTION NOTES (short)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- 00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md

### OUTPUT_TARGET
- Required for any change that touches INDEX, contracts, dependencies, levels, naming, or adds/removes engines
- Verdict is referenced in Audit Log and CHG packet

---

## SINGLE SOURCE OF TRUTH (CANON LAW)

### Truth order (priority)
1) `00__INDEX_ALL_ENGINES.md` — existence + navigation law
2) Governance family (00/*) — process law, formats, gates
3) Family README (realm file) — terminology + boundaries for that family
4) Individual engine file — local rules
5) Notes / drafts / chats — non-canon unless registered and approved

### Existence rule (restate)
Если движка нет в INDEX — он не существует для ENG.
Если файл есть, но не зарегистрирован — он non-canon.

---

## CANON VERDICT (MANDATORY ARTIFACT)

### CANON_VERDICT SCHEMA (CANON)

- VERDICT_ID: CV-ENG-0001
- DATE:
- CHG_ID: (or "NONE" if emergency decision)
- DECISION:
  - APPROVE | REJECT | RETURN | APPROVE_WITH_WAIVER
- SCOPE:
  - families:
  - engines:
- KEY_REASON:
  - 3–7 bullets
- CONDITIONS (if RETURN or APPROVE_WITH_WAIVER):
  - required fixes (ordered)
  - deadlines/expiry (if waiver)
- OWNERSHIP (if assigned/updated):
  - list: {scope -> owner}
- LOCK_DECISION:
  - FIXED | UNFIXED
  - rationale
- REFERENCES:
  - CR: CR-ENG-XXXX (if any)
  - DG: DG-ENG-XXXX (if any)
  - CY: CY-XXXX (if any)
- SIGNATURE:
  - canon_authority: Universe Engine (or named authority if you later formalize)
- NOTES (optional):
  - max 5 bullets

---

## DECISION RULES (WHEN TO APPROVE / REJECT)

### Approve (normal)
- CR verdict is PASS or PASS_WITH_FIXES and fixes are done
- no S0 blockers
- no unresolved role overlap without owner
- dependencies are explicit and cycle-free (or approved cycle)

### Reject
- S0 blockers exist (index drift, naming mismatch, level mismatch, broken links)
- the change removes clarity, increases ambiguity, or breaks contracts
- conflict introduced without resolution plan

### Return (send to fix)
- fix list is clear and bounded
- change intent is valid but implementation incomplete
- missing required artifacts (CHG, CR, DG)

### Approve with waiver
- only when the system needs to move forward
- waiver must include:
  - exact scope of exception
  - expiry date or condition
  - mitigation steps
  - who owns the fix

---

## OWNERSHIP POLICY (CANON)

### OWNER fields
- `OWNER: Universe Engine` is default if nothing else is defined
- Ownership may be refined later (e.g., family owners)

### Overlap owner
Если два движка пересекаются по роли:
- назначается OWNER_OVERLAP (one engine owns decision boundary)
- второй движок получает boundary note: “delegates to owner”

---

## WAIVER POLICY (CANON)

### WAIVER schema
- WAIVER_ID: WV-ENG-0001
- DATE:
- SCOPE:
- RULE_WAIVED:
- WHY:
- EXPIRY:
  - date OR condition
- MITIGATION:
- OWNER:
- STATUS:
  - ACTIVE | EXPIRED | RESOLVED

### Rules
- waiver всегда временный
- waiver не может закрывать S0 blockers (только S1/S2 максимум)
- waiver обязателен в Audit Log и referenced from Canon Verdict

---

## LOCK POLICY (CANON)

### LOCK: FIXED
Ставится, если:
- изменения прошли governance gates
- CR = PASS
- contracts/handoff согласованы
- индекс и ссылки в порядке
- audit запись создана
- canon verdict APPROVE

### LOCK: UNFIXED
Допускается, если:
- эксперимент/черновик внутри canon scope
- явно указан срок/условие перехода в FIXED
- есть waiver или plan
- обозначено: “может измениться”

---

## CONFLICT RESOLUTION TYPES (STANDARD)

1) TERM_CONFLICT
- единый термин/значение выбирается
- остальные варианты помечаются как deprecated

2) ROLE_OVERLAP
- назначается owner engine
- фиксируется boundary + handoff

3) DEP_CYCLE
- по умолчанию запрещён
- разрешается только с governance break + cycle report + подпись

4) INDEX_DRIFT / NAMING_MISMATCH / LEVEL_MISMATCH
- это S0 blockers → только RETURN/REJECT до исправления

---

## PROCEDURE (HOW CANON AUTHORITY WORKS)

1) Receive CHG packet (+ CR/DG if applicable)
2) Check for S0 blockers
3) Check role overlap and boundaries
4) Check dependency risk / cycles
5) Decide: approve / return / reject / approve_with_waiver
6) Issue Canon Verdict (CV)
7) Ensure audit entry references CV
8) Ensure lock decision is applied in touched files (LOCK block)

---

## VALIDATION CHECKLIST (FOR THIS ENGINE)

- CA1: Every approved change has a CV-ENG verdict ID
- CA2: No canon change is merged without audit entry
- CA3: Waivers have expiry and owner
- CA4: S0 blockers cannot be waived
- CA5: Approved cycles have cycle report + governance break

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
