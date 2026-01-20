# ORC — GROUP → ALBUM (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 20_ORC__ORCHESTRATORS
FAMILY: 10_MUSIC_ORCHESTRATORS
LEVEL: L2
DOC_TYPE: ORC (ORCHESTRATOR)
ENTITY_TYPE: ORCHESTRATOR
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUSIC.GROUP_TO_ALBUM.001
OWNER: SYSTEM
ROLE: Deterministic pipeline: group foundation → album blueprint (and minimal album docs) with strict inputs/outputs, XREF dependencies, and mandatory gates.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt GROUP→ALBUM orchestrator as strict contract: inputs/outputs, ownership/allowlist, gate placement, and packaging rules."
- REASON: "Remove ambiguity in how albums are defined before track production. Prevent guessing of owners/engines/templates."
- IMPACT: "Album planning becomes auditable and repeatable; downstream track pipelines get deterministic inputs."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.G2A.001

---

## 0) PURPOSE (LAW)
Этот ORC создаёт фундамент группы и оформляет альбомный blueprint как канонические документы.
Он не генерирует “музыку”, он оформляет структуру и контракт для дальнейшего ALBUM→TRACK.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW ссылки.

### 1.2 Ownership is mandatory
Владельцы берутся только из `ORC → SPC` карты.

### 1.3 Allowlist engines only
ENG допускаются только по `ENG → ORC` allowlist для этого ORC.

### 1.4 Mandatory gate order
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.5 Output artifact rule
Нельзя выпускать “голые списки”.
Выход = документ-артефакт.

---

## 2) REQUIRED XREF (RAW)
PIPELINES (intent → pipeline)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

ENG → ORC allowlist
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

ORC → SPC ownership
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

VALIDATION MATRIX
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

---

## 3) REQUIRED CONTROL (RAW)
READINESS CHECK (mandatory)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 4) INPUTS (MINIMUM)
### 4.1 Required
- Group identity seed (любое из):
  - Group name / working name
  - Brand binding (если есть)
  - Style intent (жанр/настроение/темп/язык) — коротко
- Album intent:
  - Album concept (1–2 строки)
  - Album size target (пример: 7 треков)
  - Album arc (как меняется настроение по трекам) — коротко

### 4.2 Optional
- Reference constraints (что точно нельзя)
- Platform target (Suno/Udio/Universal) — если важно для дальнейшего prompt contract

### 4.3 Stop rule
Если нет ни group seed, ни album intent → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
Минимальный набор:
- ALBUM_BLUEPRINT (как документ-артефакт)
- PACKAGE (если упаковываем как “album blueprint pack”)

Примечание:
- Точные типы файлов альбома зависят от storage map/шаблонов. ORC фиксирует требование “документ-артефакт”, а не придумывает пути.

---

## 6) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (из ORC→SPC map)  
Gate: READINESS_CHECK_CTL  
Input: task + root link base + group/album intent  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — GROUP FOUNDATION (SPC-led)
Owner: PRIMARY_SPC  
Input: group seed + constraints  
Output:
- GROUP_PROFILE_MIN (name, identity notes, style intent)
- NAMING_NOTES (если есть риск конфликтов — фиксируем)

Notes:
- если требуется naming decision — он фиксируется как часть выхода, но без “угадывания путей”.

---

### STEP 2 — ENGINE SELECTION (XREF allowlist)
Owner: ORC (this doc)  
Constraint:
- использовать только allowlisted ENG реалмы из `ENG→ORC` для данного ORC.

Output:
- ALLOWED_ENG_REALMS_USED (RAW ссылки на README реалмов)
Fail:
- если нужного ENG нет в allowlist → STOP: marker not confirmed (GAP)

---

### STEP 3 — ALBUM BLUEPRINT DRAFT (SPC + ENG methods)
Owner: PRIMARY_SPC (решения) + ENG (методы)  
Output draft:
- ALBUM_BLUEPRINT_DRAFT with:
  - tracklist skeleton (T01..Txx)
  - role of each track (intro/peak/bridge/outro)
  - mood/tempo trajectory
  - constraints per track (если нужно)

---

### STEP 4 — VALIDATION + QA (by matrix)
Owner: relevant VAL + relevant QA  
Rule:
- применяем `VALIDATION_MATRIX` к типам артефактов, которые выпускаем (обычно SPEC/PACKAGE).
Output:
- VIOLATIONS (если есть)
- QA_VERDICT

FAIL → вернуть на STEP 3 (исправление)

---

### STEP 5 — PACKAGING (if needed)
Owner: PRIMARY_SPC  
Action:
- оформить blueprint как документ-артефакт
- если требуется пакет: сделать PACKAGE документ с pointers на blueprint и связанные элементы

Output:
- FINAL ALBUM BLUEPRINT
- OPTIONAL: ALBUM BLUEPRINT PACK

---

### STEP 6 — DOC CONTROL + SIGNOFF
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Output:
- signoff подтверждён, версия/UID/статусы корректны

---

## 7) HANDOFFS (CANON)
- PRIMARY_SPC: решение структуры альбома и упаковка
- CTL: readiness и stop-логика
- VAL/QA: приемка по матрице
- DOC_CONTROLLER_SPC: doc control
- MACHINE_ARCHITECT_SPC: финальный signoff

---

## 8) EXTENSION POLICY (STRICT)
Если появляются новые артефакты или требования:
1) сначала правим XREF карты (validation matrix / eng allowlist / owners)
2) затем правим этот ORC (PATCH)

---

END.
