# SYSTEM LAW INDEX — MASTER REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: INDEX
INDEX_TYPE: MASTER_LAW_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.1
UID: UE.DOC.IDX.LAW.MASTER
OWNER: SYSTEM
ROLE: Canonical navigation law + registry for all system-level laws (mandatory entrypoint)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "Doc Control compliance + PATH/RAW canon map."
- REASON: "Единый формат индексов по системе."
- IMPACT: "Слой 01_SYSTEM_LAW полностью совместим."

---

## PURPOSE (LAW)
Этот INDEX — единая точка истины для слоя `01_SYSTEM_LAW`.

### EXISTENCE RULE (ABSOLUTE)
Если закона нет в этом INDEX — он не существует для слоя SYSTEM LAW.
Если файл есть, но не зарегистрирован здесь — NON-CANON (ignored).

---

## HOW TO USE (MANDATORY FLOW)
1) Любой спор по системе сначала сверяется с `00__SYSTEM_LAW.md`.
2) Затем открывается нужный LAW по номеру (01..07).
3) Любые новые LAW:
   - сначала добавляются в этот INDEX,
   - потом создаётся файл,
   - потом фиксируется по `03__VERSIONING_CHANGE_POLICY.md` и `04__CANON_PROTOCOL.md`.

---

## ORDER OF AUTHORITY (PRIORITY)
0) `00__SYSTEM_LAW.md`
1) `04__CANON_PROTOCOL.md`
2) `03__VERSIONING_CHANGE_POLICY.md`
3) `02__UID_RULES.md`
4) `01__NAMING_RULES.md`
5) `06__CONSTRAINTS_REGISTRY.md`
6) `05__ARTIFACT_SCHEMA_REGISTRY.md`
7) `07__PIPELINE_REGISTRY.md`

---

## CANON MAP — SYSTEM LAW FILES (REGISTERED)

00 — System Law (Core)
PATH: `01_SYSTEM_LAW/00__SYSTEM_LAW.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

01 — Naming Rules
PATH: `01_SYSTEM_LAW/01__NAMING_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

02 — UID Rules
PATH: `01_SYSTEM_LAW/02__UID_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

03 — Versioning & Change Policy
PATH: `01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

04 — Canon Protocol
PATH: `01_SYSTEM_LAW/04__CANON_PROTOCOL.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

05 — Artifact Schema Registry
PATH: `01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

06 — Constraints Registry
PATH: `01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

07 — Pipeline Registry
PATH: `01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

--- END.
