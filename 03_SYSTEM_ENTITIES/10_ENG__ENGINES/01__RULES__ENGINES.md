# ENG ENGINES — RULESET (LAW) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: RULESET
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.RULES.001
OWNER: SYSTEM
ROLE: Hard rules + gates for ENG layer. Violations mean incomplete / non-canon behavior.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "ENG ruleset created: existence, raw-only, numbering, mini-contract, boundaries, governance compatibility."
- REASON: "Root ENG rules were empty; stamping requires hard enforcement."
- IMPACT: "ENG can be executed deterministically and audited."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.RULES.001

---

## 0) DEFINITIONS (STRICT)
- CANON: только то, что зарегистрировано каноническим индексом/реестром.
- INCOMPLETE: файл существует, но не удовлетворяет законам (не допускается как рабочий движок).
- RAW-ONLY: ссылки только на raw.githubusercontent.com.

---

## 1) HARD RULES (MUST / FORBIDDEN)

### R1 (HARD) — EXISTENCE
MUST: любой Engine/README/Template семьи должен быть зарегистрирован в каноническом ENG INDEX.
FORBIDDEN: использовать “файл в папке” как канон без регистрации.

### R2 (HARD) — RAW-ONLY NAVIGATION
MUST: индексы/реестры/README обязаны давать raw-links.
FORBIDDEN: github.com UI ссылки в канонической навигации.

### R3 (HARD) — NAMING & NUMBERING
MUST: имя файла `NN__NAME_ENG.md` и номер в индексе совпадают.
MUST: README семьи всегда `00__README__...`.
FORBIDDEN: пропуски/двойные номера внутри семьи.

### R4 (HARD) — STATUS/LOCK STRICT SET
MUST: STATUS ∈ {DRAFT, ACTIVE, DEPRECATED, ARCHIVED} и встречается ровно один раз.
MUST: LOCK ∈ {OPEN, FIXED} и встречается ровно один раз.
FORBIDDEN: второй STATUS/LOCK в конце файла.

### R5 (HARD) — MINI-CONTRACT LAW
MUST: каждый Engine содержит MINI-CONTRACT:
CONSUMES / PRODUCES / DEPENDS_ON / OUTPUT_TARGET.
FORBIDDEN: “вода” вместо артефактов (idea/thing/etc).
Если MINI-CONTRACT vague → INVALID.

### R6 (HARD) — BOUNDARIES
MUST: каждый Engine содержит BOUNDARIES:
IN SCOPE / OUT OF SCOPE / COLLISION RULE.
FORBIDDEN: дублирование области другого семейства без collision rule.

### R7 (HARD) — OUTPUT SCHEMAS
MUST: для каждого PRODUCES артефакта задана минимальная схема:
MUST / OPTIONAL / VALIDATION / STORAGE.

### R8 (HARD) — DEPENDENCY VISIBILITY
MUST: любые зависимости прописаны в DEPENDS_ON.
MUST: если существует governance dependency registry — зависимость отражена там.
FORBIDDEN: скрытые зависимости.

### R9 (HARD) — GOVERNANCE PIPELINE COMPATIBILITY
MUST: любые canon-impacting изменения проходят governance pipeline.
MUST: canon-impacting изменения фиксируются audit записью (append-only).

---

## 2) GATES (FAST ENFORCEMENT)
G0 — Header Gate:
- корректный CANON FILE path
- корректные FAMILY/CLASS/LEVEL
- STATUS/LOCK валидны

G1 — Contract Gate:
- MINI-CONTRACT конкретный
- OUTPUT_TARGET заполнен (хотя бы MANDATORY)

G2 — Boundary Gate:
- BOUNDARIES не пустой
- collision rule определён

G3 — Schema Gate:
- output schemas существуют на каждый PRODUCES

G4 — Canon Gate:
- зарегистрирован в индексе raw-link
- если canon-impacting — audit record существует

Если любой Gate FAIL → файл считается INCOMPLETE.

---
## LINK RESOLUTION RULE (OPERATIONAL)
- RAW links are the only navigation mechanism.
- When a user provides an operational index (or subset), it becomes the only allowed link library.
- No link guessing is allowed.

## 3) REFERENCES (RAW ONLY)
- ENG REALM README:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__README__ENGINES_REALM.md
- ENG INDEX_ALL_ENGINES:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

--- END.
