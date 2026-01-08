# CORE IDENTITY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/01__CORE_IDENTITY_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.CORE.IDENTITY.001
OWNER: SYSTEM
ROLE: Defines system identity contract + signature + invariants as the single-truth anchor for the whole repo

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Core identity contract finalized: invariants, typed IO, audit binding, cross-layer hooks, strictness matrix, output schemas."
- REASON: "Prevent split canon and make identity deterministic and standards-compatible."
- IMPACT: "Identity becomes stable anchor for Core State/Lifecycle, governance gates, and cross-layer consistency."
- CHANGE_ID: UE.CHG.2026-01-08.CORE.IDENTITY.001

---

## 0) PURPOSE (LAW)

Core Identity Engine фиксирует “кто мы” для Universe Engine на уровне L1.

Он задаёт:
- CORE_IDENTITY_CONTRACT (инварианты + границы)
- SYSTEM_SIGNATURE (минимальные стабильные ключи)
- IDENTITY_ASSERTIONS (проверяемые утверждения)
- IDENTITY_RECORD (audit-compatible запись)

Если контракт отсутствует или нарушен по HARD-инварианту — система считается неинициализированной (BLOCK).

---

## 1) NON-GOALS (HARD)

Этот движок НЕ:
- не заменяет `01_SYSTEM_LAW/*` (подчиняется)
- не определяет процедуры изменений/аппрувов (это governance engines)
- не определяет текущее состояние системы (это `02__CORE_STATE_ENG`)
- не определяет жизненный цикл объектов (это `03__CORE_LIFECYCLE_ENG`)
- не создаёт доменный контент (world/character/narrative)
- не выполняет фактчекинг/языковую валидацию (это validators/QA)
- не хранит историю как закон (логи — журнал, не источник права)

---

## 2) SCOPE (BOUNDARY)

IN SCOPE:
- определение Identity Contract и инвариантов
- определение System Signature (stable keys)
- правило “canon exists only by index”
- требования к навигационным ссылкам (raw-only для канонических карт)
- минимальная карта слоёв и запрет смешивания ролей
- требование audit-фиксации любых identity изменений

OUT OF SCOPE:
- стандарты оформления документов (движок требует соблюдения, но не переписывает)
- управление зависимостями целиком (только declares hooks)
- выполнение проектов/пайплайнов (только anchors и контракты)

---

## 3) COMPLIANCE (LAW OVERRIDE ORDER)

Priority (strict):
1) `01_SYSTEM_LAW/*`
2) `00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG`
3) ENG layer rules (`00__README__ENGINES_REALM.md`, `01__RULES__ENGINES.md`)
4) This engine

UID/Naming/DocControl:
- UID must comply with `01_SYSTEM_LAW/02__UID_RULES.md`
- Naming/paths must comply with `01_SYSTEM_LAW/01__NAMING_RULES.md` + ENG rules
- Single-truth metadata: STATUS/LOCK/VERSION/UID/OWNER/ROLE exist only in header

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- LAWSET (System Law package: naming/uid/canon protocol/versioning)
- LAYER_RULESET (ENG realm + ENG rules)
- CANON_ENTRYPOINT (Root Index definition)
- STRUCTURE_MAP (Repo tree / layer map snapshot)
- OPTIONAL_REGISTRY (Doc/Entity registries if used as mirrors)

PRODUCES:
- CORE_IDENTITY_CONTRACT (CONTRACT)
- SYSTEM_SIGNATURE (SIGNATURE)
- IDENTITY_ASSERTIONS (CONSTRAINTS_SET)
- IDENTITY_RECORD (LOG_RECORD, audit-compatible)

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG

OUTPUT_TARGET:
MANDATORY:
- 00_INDEX/00__ROOT_INDEX.md  (section: SYSTEM_IDENTITY + SYSTEM_SIGNATURE)
- 99_LOGS/LOG__AUDIT.md       (IDENTITY_RECORD entry)

OPTIONAL (assistive mirrors; never override canon):
- 08_DATABASES/DB__DOC_REGISTRY.md
- 08_DATABASES/DB__ENTITY_TYPES.md

---

## 5) DEFINITIONS

- System Identity — стабильный набор утверждений “что такое Universe Engine”.
- Identity Contract — инварианты + допустимые изменения идентичности.
- System Signature — минимальные ключи, которыми система узнаёт себя.
- Canon by Index — сущность существует только если присутствует в каноническом индексе.
- Raw-only Canon Navigation — канонические карты/entrypoints должны быть raw-links.

---

## 6) CORE IDENTITY CONTRACT (INVARIANTS)

C1 (HARD) — Single Canon Entry  
Единственная каноническая точка входа:
- `00_INDEX/00__ROOT_INDEX.md`

C2 (HARD) — Canon Exists Only By Index  
Если сущности/движка нет в каноническом INDEX — он не существует (ignored / non-canon).

C3 (HARD) — Raw-only Canon Navigation  
Канонические карты (entrypoints/registries/index links) должны быть raw-links. Не-raw не считается навигационной гарантией.

C4 (HARD) — Layer Separation  
00_INDEX / 01_SYSTEM_LAW / 02_STANDARDS / 03_SYSTEM_ENTITIES / 04_KNOWLEDGE_BASE / 05_PROJECTS / 06_ASSETS / 08_DATABASES / 99_LOGS  
Смешивание ролей слоёв запрещено.

C5 (HARD) — Single-Truth Metadata  
STATUS/LOCK/VERSION/UID/OWNER/ROLE — одна истина в шапке. Дубли запрещены.

C6 (HARD) — Governance Compatibility  
Любое canon-impact изменение identity keys/invariants:
- фиксируется в audit log
- при конфликтах решается через Rule Hierarchy + Canon Authority

C7 (SOFT→HARD by impact) — Cross-layer Anchor Consistency  
Identity не должна ломать:
- канонические индексы (hard)
- структуру слоёв (hard)
- проектные выходы/пайпы (soft unless breaks canon outputs)

---

## 7) SYSTEM SIGNATURE (STABLE KEYS)

MUST:
- SYSTEM_NAME: Universe Engine
- REPO_ROOT: UNIVERSE_ENGINE/
- CANON_ROOT_INDEX: 00_INDEX/00__ROOT_INDEX.md
- ENG_BASE_PATH: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/
- EXISTENCE_RULE: "If not in canon index — does not exist."

Изменение любого ключа подписи = identity change (audit mandatory; usually MAJOR by meaning).

---

## 8) OUTPUT SCHEMAS (MINIMUM FORMS)

CORE_IDENTITY_CONTRACT:
- invariants list (C1..Cn) with HARD/SOFT
- scope boundaries (in/out)
- system signature keys
- strictness notes (WARN/BLOCK mapping)

SYSTEM_SIGNATURE:
- stable keys list
- date + version + owner
- short change note (if changed)

IDENTITY_ASSERTIONS:
- assertion_id
- statement
- severity: WARN|BLOCK
- anchor_ref (path/section)

IDENTITY_RECORD (audit-compatible):
- DATE
- CHANGE_TYPE (MAJOR|MINOR|PATCH|HOTFIX)  # semantic label
- SUMMARY
- REASON
- IMPACT
- REFERENCES (optional raw pointers)

NOTE:
Если формат audit-записи конфликтует — побеждает Audit Log Engine spec (через Rule Hierarchy).

---

## 9) STRICTNESS MATRIX (DECISION LAW)

- HARD invariant violated → BLOCK
- SOFT invariant violated → WARN (может быть эскалировано governance)

Authority:
- conflicts: Rule Hierarchy + Canon Authority
- audit format: Audit Log Engine

---

## 10) INTERFACES (CROSS-LAYER HOOKS)

PROJECTS (05_PROJECTS):
- проектные документы могут ссылаться на SYSTEM_SIGNATURE keys
- existence-by-index правило должно соблюдаться внутри проектных индексов

DATABASES (08_DATABASES):
- базы могут быть зеркалом/справочником, но не authority
- любые DB mirrors должны отмечаться как assistive

KNOWLEDGE_BASE (04_KNOWLEDGE_BASE):
- KB не определяет identity, но обязана соблюдать existence-by-index и raw-only в канонических картах

---

## 11) PROCESS (DETERMINISTIC)

1) Gather anchors: Root Index + System Law + ENG rules + structure map
2) Validate invariants C1–C7
3) Emit outputs: contract + signature + assertions + audit record
4) Publish: update root identity section + append audit record
5) If BLOCK: stop and escalate to Canon Authority

---

## 12) FAILURE MODES (BLOCKERS)

BLOCK:
- Duplicate root (C1)
- Canon-by-index broken (C2)
- Raw-only canon navigation broken (C3)
- Metadata double-truth (C5)
- Layer mixing (C4)

WARN:
- Optional registry mirrors diverge (allowed, but note drift)
- Soft anchor drift (C7)

---

## 13) READY CHECK (FAST)

- [ ] Single canon entry exists (C1)
- [ ] Existence-by-index enforced (C2)
- [ ] Raw-only canon navigation used (C3)
- [ ] Header single-truth metadata only (C5)
- [ ] Identity changes produce audit record (C6)

---

## 14) REFERENCES (RAW ONLY)

ROOT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX.md

SYSTEM LAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

ENG:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__README__ENGINES_REALM.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

GOVERNANCE:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

CORE SIBLINGS:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/02__CORE_STATE_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/03__CORE_LIFECYCLE_ENG.md

--- END.
