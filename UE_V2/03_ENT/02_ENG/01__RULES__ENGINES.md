# ENG ENGINES — RULESET (LAW) (CANON)

FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md
SCOPE: Universe Engine (Games volume) / System Entities / ENGINES (ENG)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
ENTITY_GROUP: ENGINES (ENG)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.RULES.001
OWNER: SYSTEM
ROLE: Hard rules + gates for ENG layer. Violations mean INCOMPLETE / NON-CANON behavior.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "DOC CONTROL normalization: structured header + explicit gate list + KB scope + RAW interfaces. No semantic change."
- REASON: "Make enforcement readable and consistent with other realm rulesets."
- IMPACT: "ENG rules become auditable and easy to apply during routing."
- CHANGE_ID: UE.CHG.2026-01-20.ENG.RULES.002

---

## 0) DEFINITIONS (STRICT)
- CANON: только то, что зарегистрировано каноническим индексом.
- INCOMPLETE: файл существует, но нарушает законы (не допускается как рабочий движок).
- RAW-ONLY: ссылки только на `raw.githubusercontent.com`.

---

## 1) HARD RULES (MUST / FORBIDDEN)

### R1 — EXISTENCE MUST (HARD)
MUST:
- любой Engine/README/Template семьи зарегистрирован в каноническом ENG INDEX.

FORBIDDEN:
- считать “файл в папке” каноном без регистрации.

### R2 — RAW-ONLY NAVIGATION MUST (HARD)
MUST:
- индексы/реестры/README дают RAW ссылки.

FORBIDDEN:
- github.com UI ссылки в канонической навигации.

### R3 — NAMING & NUMBERING MUST (HARD)
MUST:
- имя файла `NN__..._ENG.md` и номер в индексе совпадают.
- README семьи всегда `00__README__..._ENGINES.md`.

FORBIDDEN:
- пропуски/двойные номера внутри семьи.

### R4 — STATUS/LOCK STRICT SET MUST (HARD)
MUST:
- STATUS ∈ {DRAFT, ACTIVE, DEPRECATED, ARCHIVED} и встречается ровно один раз.
- LOCK ∈ {OPEN, FIXED} и встречается ровно один раз.

FORBIDDEN:
- второй STATUS/LOCK в конце файла.

### R5 — MINI-CONTRACT LAW MUST (HARD)
MUST:
- каждый Engine содержит MINI-CONTRACT: CONSUMES / PRODUCES / DEPENDS_ON / OUTPUT_TARGET.

FORBIDDEN:
- “вода” вместо артефактов (idea/thing/etc).
Если MINI-CONTRACT расплывчатый → INVALID.

### R6 — BOUNDARIES MUST (HARD)
MUST:
- каждый Engine содержит BOUNDARIES: IN SCOPE / OUT OF SCOPE / COLLISION RULE.

FORBIDDEN:
- дублировать область другого семейства без collision rule.

### R7 — OUTPUT SCHEMAS MUST (HARD)
MUST:
- для каждого PRODUCES артефакта задана минимальная схема:
  - MUST / OPTIONAL / VALIDATION / STORAGE

### R8 — DEPENDENCY VISIBILITY MUST (HARD)
MUST:
- любые зависимости прописаны в DEPENDS_ON.

FORBIDDEN:
- скрытые зависимости.

### R9 — GOVERNANCE COMPATIBILITY MUST (HARD)
MUST:
- canon-impacting изменения проходят governance pipeline
- фиксируются audit записью (append-only)

---

## 2) GATES (FAST ENFORCEMENT)
G0 — Header Gate:
- корректный DOC CONTROL header
- валидные STATUS/LOCK

G1 — Contract Gate:
- MINI-CONTRACT конкретный
- OUTPUT_TARGET заполнен

G2 — Boundary Gate:
- BOUNDARIES не пустые
- collision rule определён

G3 — Schema Gate:
- output schemas существуют на каждый PRODUCES

G4 — Canon Gate:
- зарегистрирован в индексе RAW link
- если canon-impacting — audit запись существует

Если любой gate FAIL → Engine INCOMPLETE.

---

## 3) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- стандарты оформления/контроля (Doc Control, Index Structure)
- правила идентичности (Naming, UID)
- доменные стандарты по тематике движка

KB OUTPUTS:
- none (ENG не является KB модулем)

BOUNDARIES:
- правила/методы и схемы результата — да
- хранение контента и знаний как SoT — нет

---

## 4) REFERENCES (RAW ONLY)
- ENG REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__README__ENGINES_REALM.md
- ENG GLOBAL REGISTRY:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

--- END.
