# XREF MAP — ORC → SPC (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: ORC_TO_SPC
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.ORC_TO_SPC.001
OWNER: SYSTEM
ROLE: Deterministic ownership map: which SPC owns intent/decisions for each ORC pipeline (primary + supporting).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized minimal ORC→SPC ownership map for core routing: doc fixes, entity repair, KB scope runs, and music orchestrators."
- REASON: "Remove ambiguity: ORC must have explicit SPC owners for intent, packaging, and signoff."
- IMPACT: "Handoffs become auditable; routing can select owners deterministically."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.ORC2SPC.001

---

## 0) PURPOSE (LAW)
Эта карта фиксирует владельцев (SPC) для каждого ORC:
- PRIMARY_SPC — владелец намерения и решения
- SUPPORT_SPC — поддержка/пакетирование/стандарты
- SIGNOFF — кто обязан финально подписать

Если ORC не прописан здесь — это GAP.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Использовать только RAW ссылки.

### 1.2 Ownership is mandatory
ORC без PRIMARY_SPC запрещён к использованию.

### 1.3 Finish chain enforced
Для любого ORC:
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

---

## 2) SPC CANON REFS (RAW)

### 2.1 TOP GOVERNANCE SPC
- MACHINE_ARCHITECT_SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md

- GOVERNANCE_OWNER_SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/02__GOVERNANCE_OWNER_SPC.md

- STANDARDS_OWNER_SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md

- DOC_CONTROLLER_SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md

- PIPELINE_ARCHITECT_SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md

- INTEGRATION_PACKER_SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md

---

## 3) ORC REGISTRY (CANON MINIMUM)

### 3.1 CORE ORC — PIPELINE ORCHESTRATOR (generic routing)
ORC_ID: ORC.CORE.PIPELINE_ORCHESTRATOR.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/05__PIPELINE_ORCHESTRATOR_ENG.md

PRIMARY_SPC:
- PIPELINE_ARCHITECT_SPC

SUPPORT_SPC:
- MACHINE_ARCHITECT_SPC
- DOC_CONTROLLER_SPC

SIGNOFF (MANDATORY):
- DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

NOTES:
- Используется как owner-пара для общих пайплайнов, где primary ORC = pipeline orchestrator.

---

### 3.2 MUSIC ORC — GROUP → ALBUM
ORC_ID: ORC.MUSIC.GROUP_TO_ALBUM.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

PRIMARY_SPC:
- INTEGRATION_PACKER_SPC

SUPPORT_SPC:
- STANDARDS_OWNER_SPC
- DOC_CONTROLLER_SPC

SIGNOFF (MANDATORY):
- DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

NOTES:
- Формирование альбомного blueprint требует упаковки + стандартов.

---

### 3.3 MUSIC ORC — ALBUM → TRACK
ORC_ID: ORC.MUSIC.ALBUM_TO_TRACK.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

PRIMARY_SPC:
- INTEGRATION_PACKER_SPC

SUPPORT_SPC:
- STANDARDS_OWNER_SPC
- DOC_CONTROLLER_SPC

SIGNOFF (MANDATORY):
- DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

NOTES:
- Основной производственный маршрут. Primary owner должен держать структуру, naming и конечную сборку.

---

### 3.4 MUSIC ORC — TRACK TEST DOC GATE
ORC_ID: ORC.MUSIC.TRACK_TEST_DOC_GATE.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

PRIMARY_SPC:
- STANDARDS_OWNER_SPC

SUPPORT_SPC:
- INTEGRATION_PACKER_SPC
- DOC_CONTROLLER_SPC

SIGNOFF (MANDATORY):
- DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

NOTES:
- Этот ORC ставит doc-gates и обязан опираться на стандарты/контракты.

---

### 3.5 MUSIC ORC — RELEASE PACK
ORC_ID: ORC.MUSIC.RELEASE_PACK.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

PRIMARY_SPC:
- INTEGRATION_PACKER_SPC

SUPPORT_SPC:
- DOC_CONTROLLER_SPC
- STANDARDS_OWNER_SPC

SIGNOFF (MANDATORY):
- DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

NOTES:
- Упаковка релиза = ответственность packer + doc control.

---

### 3.6 MUSIC ORC — PORTFOLIO PLANNER
ORC_ID: ORC.MUSIC.PORTFOLIO_PLANNER.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

PRIMARY_SPC:
- STANDARDS_OWNER_SPC

SUPPORT_SPC:
- INTEGRATION_PACKER_SPC
- DOC_CONTROLLER_SPC

SIGNOFF (MANDATORY):
- DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

NOTES:
- Планирование портфеля = стандарты + структура выпусков.

---

### 3.7 MUSIC ORC — POET PACK
ORC_ID: ORC.MUSIC.POET_PACK.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

PRIMARY_SPC:
- STANDARDS_OWNER_SPC

SUPPORT_SPC:
- INTEGRATION_PACKER_SPC
- DOC_CONTROLLER_SPC

SIGNOFF (MANDATORY):
- DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC

NOTES:
- Выбор/упаковка поэтов должен жить в стандартах и быть воспроизводимым.

---

## 4) EXTENSION POLICY (STRICT)
Чтобы добавить ORC в карту:
1) иметь RAW на ORC файл
2) назначить PRIMARY_SPC (обязательно)
3) указать SUPPORT_SPC и SIGNOFF
4) внести запись как PATCH

---  
END.
