# XREF — MAP: PIPELINES (ORC ROUTES ↔ GATES) (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP (XREF)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.PIPELINES.004
OWNER: SYSTEM
ROLE: Single canonical map that ties each allowed PIPELINE_ID to its ENTRY_ORC and mandatory gate set (CTL/VAL/QA) + KB consumption flag. Must match PIPELINE_REGISTRY. Used for deterministic routing and for validation matrix alignment.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Synced pipeline map with PIPELINE_REGISTRY: ORC entrypoints, KB flags, required gates, outputs, default returns."
- REASON: "Prevent invisible routes and gate drift between ORC/CTL/VAL/QA."
- IMPACT: "Routing and enforcement become auditable and consistent across the system."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.PIPEMAP.004

---

## 0) PURPOSE (LAW)
Эта карта отвечает на вопрос:
какой ORC маршрут разрешён и какие гейты обязаны быть пройдены.

Карта обязана:
- 1:1 соответствовать `01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md`
- использовать RAW ссылки
- явно указывать KB_CONSUMPTION

Если карта расходится с реестром пайплайнов → FAIL_CLASS: marker not confirmed (до синхронизации).

---

## 1) REQUIRED REFERENCES (RAW)
PIPELINE REGISTRY (LAW)  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

MUSIC ORC REALM README (context)  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/00__README__MUSIC_ORCHESTRATORS.md

---

## 2) MAP RECORD FORMAT (CANON)
Each MAP record must contain:

- PIPELINE_ID
- DOMAIN
- ENTRY_ORC_RAW (or NONE if gate-only)
- KB_CONSUMPTION: TRUE | FALSE | CONDITIONAL
- REQUIRED_GATES:
  - CTL: list of RAW
  - VAL: list of RAW
  - QA:  list of RAW
- OUTPUTS: list (artifact names)
- DEFAULT_RETURN_RAW

---

## 3) PIPELINE MAP (ALLOWED)

### UE.PIPE.SYSTEM.READINESS.000
DOMAIN: SYSTEM  
ENTRY_ORC_RAW: NONE  
KB_CONSUMPTION: CONDITIONAL  
REQUIRED_GATES:  
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: NONE
- QA:  NONE  
OUTPUTS:
- READINESS_TRACE (PASS/FAIL)  
DEFAULT_RETURN_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md

---

### UE.PIPE.MUSIC.GROUP_TO_ALBUM.101
DOMAIN: MUSIC  
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md  
KB_CONSUMPTION: FALSE  
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- VAL: NONE
- QA:  NONE  
OUTPUTS:
- ALBUM_BLUEPRINT  
DEFAULT_RETURN_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

---

### UE.PIPE.MUSIC.ALBUM_TO_TRACK.102
DOMAIN: MUSIC  
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md  
KB_CONSUMPTION: CONDITIONAL  
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- QA:  NONE  
OUTPUTS:
- TRACK_CARD
- TRACK_PROMPT  
DEFAULT_RETURN_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

### UE.PIPE.MUSIC.TRACK_TEST_GATE.103
DOMAIN: MUSIC  
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md  
KB_CONSUMPTION: CONDITIONAL  
REQUIRED_GATES:
- CTL: MATRIX_SELECTED
- VAL: MATRIX_SELECTED
- QA:  MATRIX_SELECTED  
OUTPUTS:
- TEST_GATE_VERDICT
- REQUIRED_FIXES_LIST  
DEFAULT_RETURN_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

### UE.PIPE.MUSIC.RELEASE_PACK.104
DOMAIN: MUSIC  
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md  
KB_CONSUMPTION: CONDITIONAL  
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md
- QA:  NONE  
OUTPUTS:
- MUSIC_RELEASE_PACK  
DEFAULT_RETURN_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

---

### UE.PIPE.MUSIC.POET_PACK.105
DOMAIN: MUSIC  
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md  
KB_CONSUMPTION: TRUE  
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
- QA:  NONE  
OUTPUTS:
- POET_PACK (with provenance + excerpt policy + handoff block)  
DEFAULT_RETURN_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

---

## 4) SYNC RULE (LAW)
Эта карта обязана быть синхронизирована с PIPELINE REGISTRY:
- если пайплайн добавлен/изменён в реестре — он должен появиться здесь в тот же change pack
- если пайплайн deprecated — запись остаётся, но помечается в NOTES (если вводится блок NOTES)

---

## 5) STOP CONDITIONS (MAP AUDIT)
Если при аудите карты найдено:
- пайплайн есть тут, но нет в реестре (или наоборот)
- ссылка не RAW
- обязательные гейты не совпадают
→ STOP: marker not confirmed

---

END.
