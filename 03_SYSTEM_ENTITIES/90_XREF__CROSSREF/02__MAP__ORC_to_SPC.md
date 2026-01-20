# XREF MAP — ORC → SPC (OWNERSHIP) (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: ORC_TO_SPC_OWNERSHIP
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.ORC_TO_SPC.001
OWNER: SYSTEM
ROLE: Deterministic ownership map: assigns PRIMARY_SPC and SUPPORT roles for each ORC pipeline. Prevents guessing who owns decisions/packaging/signoff.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized minimal working ORC→SPC ownership map for MUSIC orchestrators + mandatory signoff roles."
- REASON: "Make runtime routing deterministic and auditable; eliminate implicit ownership."
- IMPACT: "Every ORC has an explicit primary owner and required governance signoff chain."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.ORC2SPC.001

---

## 0) PURPOSE (LAW)
Эта карта говорит: кто владелец пайплайна (PRIMARY_SPC) и кто обязан участвовать (SUPPORT_SPC).
ORC не имеет права “назначать” специалистов сам.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Только RAW ссылки.

### 1.2 Ownership is explicit
Если ORC не имеет записи в этой карте → STOP: marker not confirmed (ownership missing).

### 1.3 Mandatory governance signoff (always)
Независимо от PRIMARY_SPC, финальная цепочка всегда включает:
DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

### 1.4 Separation of concerns
- PRIMARY_SPC: владелец решения и финальной упаковки результата пайплайна
- SUPPORT_SPC: участвуют только в своей зоне (standards/pipeline/integration)

---

## 2) TOP GOVERNANCE SPC (RAW)
MACHINE_ARCHITECT_SPC
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md

DOC_CONTROLLER_SPC
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md

PIPELINE_ARCHITECT_SPC
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md

INTEGRATION_PACKER_SPC
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md

STANDARDS_OWNER_SPC
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md

---

## 3) RECORD SCHEMA (CANON)
Каждая запись обязана иметь:
- ORC_UID
- ORC_RAW
- PRIMARY_SPC_RAW
- SUPPORT_SPC_RAW (0..n)
- REQUIRED_SIGNOFF_SPC_RAW (always includes DOC_CONTROLLER + MACHINE_ARCHITECT)
- NOTES

---

# 4) OWNERSHIP — MUSIC ORCHESTRATORS (MINIMUM WORKING SET)

## 4.1 ORC: GROUP → ALBUM
ORC_UID: UE.ORC.MUSIC.GROUP_TO_ALBUM.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
PRIMARY_SPC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
SUPPORT_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
REQUIRED_SIGNOFF_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
NOTES: Until a dedicated MUSIC domain SPC owner exists, Machine Architect owns the pipeline decisions.

---

## 4.2 ORC: ALBUM → TRACK
ORC_UID: UE.ORC.MUSIC.ALBUM_TO_TRACK.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
PRIMARY_SPC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
SUPPORT_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
REQUIRED_SIGNOFF_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
NOTES: Track artifacts must pass CTL/VAL/QA before signoff.

---

## 4.3 ORC: TRACK TEST DOC GATE
ORC_UID: UE.ORC.MUSIC.TRACK_TEST_DOC_GATE.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
PRIMARY_SPC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
SUPPORT_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
REQUIRED_SIGNOFF_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
NOTES: Doc-gate is primarily doc-control owned; it enforces readiness and blocks invalid docs.

---

## 4.4 ORC: RELEASE PACK
ORC_UID: UE.ORC.MUSIC.RELEASE_PACK.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
PRIMARY_SPC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md
SUPPORT_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md
REQUIRED_SIGNOFF_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
NOTES: Packaging is integration-owned. Must enforce pointer completeness and compliance gates.

---

## 4.5 ORC: PORTFOLIO PLANNER
ORC_UID: UE.ORC.MUSIC.PORTFOLIO_PLANNER.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md
PRIMARY_SPC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md
SUPPORT_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
REQUIRED_SIGNOFF_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
NOTES: Portfolio planning is pipeline-owned (routing/scheduling).

---

## 4.6 ORC: POET PACK
ORC_UID: UE.ORC.MUSIC.POET_PACK.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md
PRIMARY_SPC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
SUPPORT_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md
REQUIRED_SIGNOFF_SPC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
NOTES: Poet pack is standards/policy owned because rights boundary and corpus selection are governance-sensitive.

---

## 5) EXTENSION POLICY (STRICT)
- Добавление нового ORC = добавить запись сюда (PATCH), иначе STOP.
- Если появляется dedicated MUSIC domain SPC owner:
  - обновить PRIMARY_SPC для соответствующих ORC (PATCH)
  - сохранить signoff chain.

---

END.
