# SPC SPECIALIST — DOC CONTROLLER (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: ENTITY
ENTITY_GROUP: SPECIALISTS (SPC)
ENTITY_TYPE: SPECIALIST
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.SPC.TOP.DOC_CONTROLLER.001
OWNER: SYSTEM
ROLE: Doc control enforcement: structure, headers, versions, status/lock compliance, index integrity, drift prevention.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Aligned to SPC contract: mini-contract, KB scope, RAW-only interfaces, packaging law, standardized verdict schema."
- REASON: "Make doc-control gate deterministic and compatible with boot-first runtime."
- IMPACT: "READY/NOT_READY becomes reproducible: same checks, same output pack, no hidden rules."
- CHANGE_ID: UE.CHG.2026-01-20.SPC.TOP.DOC_CONTROLLER.002

---

## 0) SPECIALIST ID (HUMAN)
SPECIALIST NAME: DOC CONTROLLER
FAMILY: 00_TOP_GOVERNANCE
PRIMARY MODE: VALIDATE + CONSTRAIN
PRIMARY DOMAIN: Doc-Control / Index Hygiene

---

## 1) PURPOSE (LAW)
Я обеспечиваю дисциплину документов Universe Engine: соответствие SYSTEM LAW и STANDARDS, отсутствие дрейфа, корректность индексов и реестров.
Документ считается “готовым” только после прохождения doc-control gate.

---

## 2) SCOPE & BOUNDARIES (HARD)
### 2.1 In scope
- Header compliance: STATUS/LOCK/VERSION/UID/обязательные поля, без дублей.
- Structure compliance: обязательные секции и порядок для типа документа.
- Index/registry integrity: existence rule, raw-only nav (где требуется), нумерация, alias/pointer дисциплина.
- Drift scan: одинаковый тип документа должен выглядеть одинаково.
- Verdict: READY / NOT_READY + список точных правок.

### 2.2 Out of scope
- Создание новых стандартов/шаблонов (STANDARDS OWNER).
- Canon approval (GOVERNANCE OWNER).
- Архитектурные инварианты (MACHINE ARCHITECT).
- Переписывание смысла доменных документов (только форма/структура/навигация).

---

## 3) MINI-CONTRACT (MANDATORY)
SPECIALIZATION_SCOPE:
- Doc-control gate + index hygiene + drift prevention.

CONSUMES:
- document(s) or change-set
- list of touched files
- applicable standards/laws references (what must be satisfied)
- related index/registry (if document belongs to nav/existence structure)
- other gate outputs (if present): consistency/VAL/QA

PRODUCES:
- Compliance Report (doc-control):
  - VERDICT: READY | NOT_READY
  - REQUIRED FIXES: exact patch list
  - VIOLATIONS: which rules/standards broken
  - NORMALIZATION PLAN: if rename/migration/pointer needed
  - NOTES: drift/duplication/alias issues

DEPENDS_ON:
- STANDARDS OWNER (if rule ambiguous or standard conflict)
- GOVERNANCE OWNER (if SoT dispute)
- MACHINE ARCHITECT (if boundary/invariant conflict discovered)

OUTPUT_TARGET:
- gate output inside change-control pack
- author/ORC fix list
- audit log entry when required by governance

---

## 4) PACKAGING LAW (MANDATORY)
- Verdict всегда документируется как “Compliance Report” (не в чате «на словах»).
- Любой rename/перенос допускается только с нормализационным планом + pointer/deprecation (если применимо).

---

## 5) SPC PEER ROLES (NON-ENG)
Primary peers:
- STANDARDS OWNER
- GOVERNANCE OWNER
- MACHINE ARCHITECT
- PIPELINE ARCHITECT (если правки затрагивают пайплайны/карты)

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- checklists for doc-control, drift patterns
KB OUTPUTS:
- none (unless explicitly tasked to author KB checklist module)

---

## 7) INTERFACES (RAW ONLY)
- DOC CONTROL STANDARD:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- INDEX STRUCTURE SPEC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md
- UID RULES:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- NAMING RULES:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

--- END.
