# CONSISTENCY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.CONSISTENCY.001>
OWNER: SYSTEM
ROLE: Canon-wide integrity inspector (structure + index/registry coherence + link/path/UID rules + anti-duplication gates)
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок — **единый инспектор целостности** документации Universe Engine.

Он обязан:
- проверять соответствие **шапкам Doc Control** (STATUS/LOCK/VERSION/UID и т.д.)
- проверять соответствие **Naming/Numbering** (NN совпадает с индексом, корректные имена)
- проверять **EXISTENCE RULE** (что не в индексе — не существует)
- проверять **целостность реестров/индексов** (порядок, ссылки, наличие)
- проверять **anti-duplication** (границы доменов/семейств, отсутствие дублей смыслов)
- формировать **Consistency Report** с уровнями серьёзности и рекомендациями фикса

Primary outcome:
- перед любым “закрытием изменения” (Change Control S5) система получает PASS/FAIL и список нарушений.

Non-goals:
- не решает approve/reject изменений (Canon Authority)
- не заменяет validators по фактам/культуре/языку (это VAL слой)
- не “переписывает контент”, только диагностирует и выдаёт план фикса

---

## 1) BOUNDARY (ANTI-DUPLICATION)

### 1.1 Owned area
- структурные проверки документов (Doc Control, Naming, UID presence)
- проверки индексов/реестров на согласованность
- проверки ссылок и путей (особенно raw-links)
- выявление конфликтов “две сущности делают одно и то же”
- выдача машинно-читаемого отчёта

### 1.2 Forbidden overlap
- не является аудит-логом (только требует ссылку на audit при канон-изменениях)
- не является change control (не управляет стадиями, только проверяет)
- не является dependency registry (но проверяет, что dependency updates записаны)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: TARGET_SCOPE>                 # what to inspect (layer/family/path/list)
- <ARTIFACT: INDEX_SNAPSHOTS?>             # optional pre-collected index views
- <ARTIFACT: CHANGE_PACKAGE_RECORD?>       # if run inside change workflow
- <ARTIFACT: RULESET_REFERENCES?>          # raw-links to relevant laws/standards

PRODUCES:
- <ARTIFACT: CONSISTENCY_REPORT>           # PASS/FAIL + violations
- <ARTIFACT: VIOLATION_LIST>               # normalized records
- <ARTIFACT: FIX_PLAN>                     # ordered actions
- <ARTIFACT: CHECKSUM_SUMMARY?>            # optional (hash list) for reproducibility

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG]
- [00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG]
- [00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]            # for enforcement checks
- [01_SYSTEM_LAW/01__NAMING_RULES]
- [01_SYSTEM_LAW/02__UID_RULES]
- [01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY]
- [01_SYSTEM_LAW/04__CANON_PROTOCOL]

OUTPUT_TARGET:
- `99_LOGS/LOG__CHANGES.md` (refs via Change Control)
- `99_LOGS/LOG__AUDIT.md` (refs via Audit Log)
- optional: `08_DATABASES/DB__DOC_REGISTRY.md` (if used as registry source)

---

## 3) CHECK DOMAINS (WHAT IT CHECKS)

Consistency Engine runs checks in domains. Each domain yields PASS/WARN/FAIL.

### D0 — Doc Control Header Compliance (MANDATORY)
Checks:
- required header fields present: SCOPE/LAYER/STATUS/LOCK/VERSION/UID/OWNER/ROLE
- STATUS is one of allowed set
- LOCK is one of allowed set
- no duplicated STATUS/LOCK/VERSION repeated later as “second truth”
- UID exists and matches UID rules format (as defined in UID law)

### D1 — Naming + Numbering Integrity (MANDATORY)
Checks:
- file names follow naming rules
- family numbering: folder `NN_<FAMILY>_ENGINES` matches index order
- engine numbering: `NN__NAME_ENG.md` starts from 01 in family
- index number equals file number (NN must match)
- README is `00__README__...` and not counted as engine

### D2 — Index / Registry Coherence (MANDATORY)
Checks:
- existence rule: “registered in index = exists; unregistered = ignored”
- index contains raw-links for every registered engine
- index family blocks complete (CLASS/REALM/TEMPLATES/list)
- no references to deleted/renamed non-existing files (stale raw links)

### D3 — Link Integrity (RAW-FIRST)
Checks:
- raw-links are used in indices (no non-raw GitHub UI links)
- internal references do not contradict index paths
- for critical entrypoints: raw link must resolve (if verification method exists)

### D4 — Dependency Transparency
Checks:
- every engine has DEPENDS_ON list (even if [])
- any declared dependency exists in index (registered)
- if dependency changed under change package → dependency registry record required

### D5 — Anti-Duplication Boundaries (Semantic)
Checks (rule-based):
- overlaps between families (e.g. rhythm narrative vs editing rhythm) flagged
- engines with near-identical roles flagged (requires human decision)
- duplicate standards living in multiple places flagged (canonical owner must be defined)

### D6 — Project/KB/DB Bridge Coherence (Optional but recommended)
Checks:
- entity types referenced across layers have a single canonical registry
- project storage maps do not contradict system storage map standards
- DB artifacts (lists) do not redefine canon laws; only store enumerations

---

## 4) SEVERITY MODEL (S0–S3)

Violation severity:
- S0 (BLOCKER): breaks navigation/canon existence rule, or corrupts indexes, or missing core header fields
- S1 (HIGH): inconsistent naming/numbering, broken raw-links in canonical index, missing DEPENDS_ON
- S2 (MED): duplicated info, weak boundaries, missing optional but recommended artifacts
- S3 (LOW): style drift, minor formatting, small clarity issues

Rule:
- Any S0 → overall FAIL
- Any S1 with canon-impact change → FAIL (unless explicitly waived by Canon Authority decision)
- S2/S3 → WARN, must be planned but can pass depending on policy

---

## 5) RUN MODES (WHEN IT RUNS)

### Mode A — Full Canon Audit
Input:
- TARGET_SCOPE = whole repo (all canonical layers)
Output:
- CONSISTENCY_REPORT (global)

### Mode B — Layer/Family Audit
Input:
- TARGET_SCOPE = specific family (e.g. 10_ENG__ENGINES/00_GOVERNANCE_ENGINES)
Output:
- focused report

### Mode C — Change Workflow Gate (DEFAULT)
Triggered by Change Control at stage S5 (POST-VERIFY):
Input:
- CHANGE_PACKAGE_RECORD + AFFECTED_FILES_LIST
Output:
- pass/fail gate + fix plan

---

## 6) STANDARD OUTPUTS (FORMATS)

### 6.1 CONSISTENCY_REPORT (REQUIRED)
FORMAT:

- REPORT_ID: <UE.CNS.YYYY-MM-DD.NNN>
- DATE:
- MODE: <FULL|LAYER|CHANGE_GATE>
- TARGET_SCOPE:
- SUMMARY:
  - RESULT: <PASS|WARN|FAIL>
  - COUNTS: S0=<n> S1=<n> S2=<n> S3=<n>
- VIOLATIONS:
  - [list of VIOLATION records]
- FIX_PLAN:
  - [ordered actions]
- NOTES:
- REFERENCES:
  - raw links to the laws/standards used

### 6.2 VIOLATION record (REQUIRED)
FORMAT:

- VID: <UE.VIO.YYYY-MM-DD.NNN>
- SEVERITY: <S0|S1|S2|S3>
- DOMAIN: <D0..D6>
- TYPE: <HEADER_MISSING|STATUS_INVALID|LOCK_DUP|NAMING_MISMATCH|INDEX_STALE|RAW_LINK_BROKEN|DEPENDS_MISSING|DUPLICATION_RISK|...>
- PATH:
- EXPECTED:
- FOUND:
- WHY_IT_MATTERS:
- FIX:
- OWNER_HINT: <which law/owner should handle>

### 6.3 FIX_PLAN (REQUIRED)
Ordered list:
1) fix S0
2) fix S1
3) align indexes/raw-links
4) update dependency registry
5) resolve duplication risks (requires decision if semantic)

---

## 7) HARD ENFORCEMENT RULES

- R1: If file is referenced as canonical entrypoint and raw-link is broken → S0
- R2: If canonical index references a file not present / renamed → S0
- R3: If engine lacks MINI-CONTRACT block → S1
- R4: If engine lacks DEPENDS_ON or OUTPUT_TARGET → S1
- R5: If STATUS not in allowed set → S1
- R6: If duplicate STATUS/LOCK/VERSION “second truth” appears → S1
- R7: If file exists but is not in canonical index where it should be → S2 (unless it is explicitly non-canon storage)
- R8: If semantic overlap found → S2 (unless it causes direct conflict → S1)

---

## 8) INTEGRATION POINTS

### 8.1 With Change Control (mandatory gate)
- Change Control S5 MUST request Consistency report
- Close change is forbidden if RESULT=FAIL (or if S0 exists)

### 8.2 With Canon Authority
- Canon Authority can waive S1/S2 issues only via explicit decision record
- Waivers must be included into report NOTES (decision ref)

### 8.3 With Dependency Registry
- If report finds dependency mismatch → requires dependency registry update record

---

## 9) REFERENCES (RAW-LINKS)

SYSTEM LAW:
- Core Law — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- Naming Rules — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md
- UID Rules — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- Versioning & Change Policy — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Canon Protocol — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

ENG (GOVERNANCE):
- Audit Log Engine — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- Canon Authority Engine — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- Rule Hierarchy Engine — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
- Change Control Engine — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- Dependency Registry Engine — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

--- END.
