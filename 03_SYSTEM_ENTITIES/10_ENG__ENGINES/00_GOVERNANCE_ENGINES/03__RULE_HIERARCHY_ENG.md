# RULE HIERARCHY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

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
UID: UE.ENG.GOV.RULE_HIERARCHY.001
OWNER: SYSTEM
ROLE: Defines strict precedence of rules across layers/files. Detects collisions and produces deterministic resolution records (no silent overrides).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Rule precedence made explicit: sources, strength, scope, override protocol, collision algorithm, required records."
- REASON: "Prevent hidden conflicts, duplicated laws, ambiguous authority."
- IMPACT: "Any rule conflict becomes resolvable and auditable; canon stops drifting."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.HIER.001

---

## 0) PURPOSE (LAW)

Rule Hierarchy Engine фиксирует **кто главнее** и **как решать конфликты**.

Он отвечает на вопросы:
- Если два документа говорят разное — какой действует?
- Какие правила вообще считаются правилами?
- Что допустимо переопределять, а что нельзя?
- Как документировать override (исключение), чтобы не было “тихого канона”?

Non-goals (hard):
- не принимает финальное решение “в канон/не в канон” (это Canon Authority)
- не управляет процессом изменения (это Change Control)
- не проверяет фактическую целостность ссылок/UID (это Consistency), но задаёт порядок их трактовки

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES:
- RULE_SOURCES_LIST                  # список источников правил по слоям + входной контекст
- RULE_CLAIMS                         # 1..N утверждений "X must/should/may"
- CONFLICT_REPORT?                    # если уже найден конфликт (optional)
- CHANGE_CONTEXT?                     # если конфликт возник в рамках change package

PRODUCES:
- RULE_PRECEDENCE_MAP                 # таблица/закон приоритетов (deterministic)
- CONFLICT_RESOLUTION_RECORD          # решение конфликта (какое правило действует и почему)
- OVERRIDE_RECORD?                    # если требуется override (строго по протоколу)

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG
- 00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 2) DEFINITIONS (STRICT)

### 2.1 Rule Claim
Rule claim = утверждение, которое ограничивает систему.
Сигнальные слова:
- MUST / SHALL / REQUIRED  -> HARD rule
- SHOULD / RECOMMENDED     -> SOFT rule
- MAY / OPTIONAL           -> OPTIONAL guidance

### 2.2 Rule Source (where a rule comes from)
Rule sources in Universe Engine:
- SYSTEM LAW layer (законы системы)
- STANDARDS layer (стандарты/регламенты/шаблоны)
- INDEX / REGISTRY docs (канонические реестры и порядок)
- ENGINE docs (правила выполнения конкретных движков)
- PROJECT layer (правила конкретного проекта)
- OUTPUT layer (требования к выпуску)

### 2.3 Scope of a rule
Scope levels:
- GLOBAL: действует на всю систему
- LAYER: действует внутри слоя
- REALM/FAMILY: действует внутри семейства (например ENG family)
- LOCAL: действует в одном документе/артефакте

### 2.4 Authority
Authority = право определять канон и порядок правил.
Rule about authority itself is always HARD and always GLOBAL.

---

## 3) PRECEDENCE AXES (THE ENGINE CORE)

Решение “кто главнее” определяется **не одним фактором**, а строгой формулой:

**A) Authority Tier (главное)**
**B) Canon/Lock status**
**C) Scope**
**D) Rule strength (MUST/SHOULD)**
**E) Specificity (конкретнее > общие)**
**F) Recency (только если одинаковая власть и одинаковый scope и оба canon)**

Если конфликт не разрешается формулой -> требуется OVERRIDE_RECORD или REJECT change (через Canon Authority).

---

## 4) AUTHORITY TIERS (STRICT ORDER)

### 4.1 Tier list (highest -> lowest)

T0 — ROOT CANON INDEXES / EXISTENCE LAWS  
- канонические entrypoints, master indexes, existence rule  
- если T0 сказал “не существует” — оно не существует

T1 — SYSTEM LAW (01_SYSTEM_LAW)  
- абсолютные законы: именование, UID, versioning, canon protocol, constraints

T2 — STANDARDS (02_STANDARDS)  
- стандарты, шаблоны, регламенты (в рамках законов)

T3 — LAYER REALM + RULESETS  
- README/RULES конкретного слоя (ENG/ORC/SPC/…)
- уточняют применение стандартов внутри слоя

T4 — CANON INDEXES внутри слоя/семейства  
- порядок файлов, обязательные поля, навигация, raw-links

T5 — ENGINE SPECS (движки)  
- правила конкретного движка + его mini-contract

T6 — PROJECT RULES (05_PROJECTS)  
- правила конкретного проекта (не могут ломать tier выше)

T7 — OUTPUT FORMATS / DELIVERY RULES  
- требования к выходам (не могут ломать tier выше)

### 4.2 Non-negotiable
- Ни один tier ниже не может отменить tier выше без **explicit override protocol**.
- Любой override на T0/T1 запрещён (кроме emergency waiver с expiry, и то через Canon Authority).

---

## 5) LOCK / STATUS EFFECT (CANON ENFORCEMENT)

### 5.1 LOCK: FIXED
- Если документ FIXED и canon — его правила считаются “active authority” до тех пор, пока не будет change package.
- Прямые изменения FIXED вне pipeline = invalid state (S0 breach).

### 5.2 STATUS: DRAFT
- DRAFT может давать guidance, но не может менять поведение канона.
- Если DRAFT конфликтует с ACTIVE canon — выигрывает canon.

### 5.3 STATUS: DEPRECATED / ARCHIVED
- Не имеет активной силы, кроме исторической справки.
- Используется только для migration links и пояснений.

---

## 6) RULE STRENGTH (MUST/SHOULD)

Strength order:
HARD (MUST) > SOFT (SHOULD) > OPTIONAL (MAY)

Но важнее сначала Authority Tier.
Пример:
- T1 SHOULD > T5 MUST  (потому что tier выше)
- T2 MUST > T2 SHOULD (внутри одного tier)

---

## 7) SPECIFICITY RULE (IMPORTANT)

Если tier одинаковый и сила одинаковая:
- более конкретное правило побеждает более общее.

Specificity ranking:
LOCAL (exact file/path/entity) > REALM/FAMILY > LAYER > GLOBAL

Запрещено писать “общие” правила внизу, которые по факту пытаются отменить “конкретные” выше.
Это считается authority conflict.

---

## 8) RECENCY RULE (LAST RESORT)

Recency разрешено учитывать ТОЛЬКО если:
- одинаковый tier
- одинаковый scope
- одинаковая strength
- оба ACTIVE + canon
- нет явного “LOCK: FIXED prevents change” (то есть изменение прошло pipeline)

Recency proof:
- must be backed by Audit Log + Versioning Memory record

---

## 9) COLLISION DETECTION (WHAT IS A CONFLICT)

Conflict exists if both true:
1) Two active rules apply to same target (same scope intersection)
2) Their requirements are incompatible (cannot both be satisfied)

Examples:
- Naming rule says `NN__NAME_ENG.md`, but a family rule says `NAME__NN.md` (incompatible)
- Existence rule says “only in index exists”, but a local rule says “folder listing is enough”

---

## 10) RESOLUTION ALGORITHM (DETERMINISTIC)

Given conflicting claims A and B:

Step 1 — Determine Tier(A), Tier(B)
- higher tier wins

Step 2 — If same tier, check STATUS/LOCK
- ACTIVE+canon wins over DRAFT
- FIXED canon takes precedence until changed via pipeline

Step 3 — If same tier and both active, evaluate scope specificity
- more specific wins

Step 4 — If same specificity, evaluate strength
- MUST wins

Step 5 — If still tied, evaluate recency
- newer canonical version wins (only with audit/memory evidence)

Step 6 — If still tied
- produce CONFLICT_RESOLUTION_RECORD with status UNRESOLVED
- escalate: Canon Authority must REJECT or require OVERRIDE_RECORD

No other steps allowed.

---

## 11) OVERRIDE PROTOCOL (NO SILENT OVERRIDES)

Override allowed only when:
- lower tier must deviate due to project constraints OR transitional migration
- deviation does not break T0/T1
- deviation is explicitly time-bounded OR narrowly scoped

Override MUST produce OVERRIDE_RECORD including:
- OVERRIDE_ID: UE.OVR.YYYY-MM-DD.NNN
- TARGET_SCOPE: exact paths/entities
- RULE_OVERRIDDEN: reference (file + section)
- NEW_RULE: explicit requirement text
- WHY: short reason
- IMPACT: what breaks / what changes
- EXPIRY: date or "NONE" (NONE allowed only for project-local overrides)
- APPROVER: role (recommended: governance owner)
- AUDIT_REF: required

If override affects canon indexes or FIXED docs:
- must also pass Canon Authority decision and be recorded in Audit Log.

---

## 12) ABSOLUTE BLOCKERS (S0) — HIERARCHY BREACH

S0-1 Two sources claim “single source of truth” for same area
S0-2 Lower-tier rule attempts to cancel T0/T1 (without emergency waiver)
S0-3 FIXED canon modified outside pipeline
S0-4 Conflict is unresolved but change attempts to proceed anyway
S0-5 Override without OVERRIDE_RECORD

Any S0 should trigger:
- Canon Authority -> REJECT (or emergency waiver with expiry)

---

## 13) OUTPUT FORMATS (CANON)

### 13.1 RULE_PRECEDENCE_MAP (required, stable)
RULE_PRECEDENCE_MAP:
- VERSION:
- TIERS: list T0..T7 with paths
- AXES: authority/lock/scope/strength/specificity/recency
- EXAMPLES: 3-5 short examples
- NOTES: anti-duplication boundaries

### 13.2 CONFLICT_RESOLUTION_RECORD (required on conflict)
CONFLICT_RESOLUTION_RECORD:
- CR_ID: UE.CRF.YYYY-MM-DD.NNN
- DATE:
- CONTEXT: change_id or "runtime"
- CLAIM_A: (source + short quote)
- CLAIM_B:
- TARGET: what is affected
- APPLIES_TO: scope
- RESOLUTION: A_WINS | B_WINS | UNRESOLVED
- WHY: (tier/scope/strength steps)
- REQUIRED_ACTIONS: [] | list
- ESCALATE_TO_CANON_AUTHORITY: YES/NO
- AUDIT_REQUIRED: YES

---

## 14) INTEGRATION WITH OTHER GOVERNANCE ENGINES

### With Canon Authority
- Any UNRESOLVED conflict => Canon Authority must decide (usually reject or require override).

### With Change Control
- If change introduces a conflict (even if “works”), it must include conflict resolution record or override record.

### With Consistency
- Consistency engine validates that applied resolution matches repo state:
  - indexes match existence rules
  - file naming matches standards/laws
  - no duplicate authority sources

### With Risk Safety
- Broad override (layer-wide or cross-layer) requires risk report.

---

## 15) SYSTEM PRECEDENCE QUICK MAP (PRACTICAL)

When in doubt, assume the order:
00_INDEX (existence) >
01_SYSTEM_LAW >
02_STANDARDS >
Layer README/RULES >
Layer INDEXES >
Engines >
Projects >
Outputs

But if a canonical INDEX defines existence/order for its domain — it behaves like Tier T0/T4 within that domain.

---

## 16) REFERENCES (RAW ONLY)

Canon Authority:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

Audit Log:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

Change Control:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

Consistency:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

Risk Safety:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

Root / Laws / Standards:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__INDEX__STANDARDS.md

Logs:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md

--- END.
