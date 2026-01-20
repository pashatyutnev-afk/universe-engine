# ORC — ALBUM → TRACK (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
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
UID: UE.ORC.MUSIC.ALBUM_TO_TRACK.001
OWNER: SYSTEM
ROLE: Primary production pipeline: converts an album blueprint into track document set (CARD + PROMPT + RELEASE metadata). Matrix-driven CTL/VAL/QA, allowlisted ENG only, deterministic iteration loop.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt ALBUM_TO_TRACK as strict deterministic producer: inputs/outputs per track, one-axis iteration, matrix-driven gates, and explicit handoff to DOC-GATE and RELEASE_PACK."
- REASON: "Prevent ad-hoc generation, missing docs, and uncontrolled changes across iterations."
- IMPACT: "Track production becomes auditable, repeatable, and compatible with packaging and validation."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.A2T.001

---

## 0) PURPOSE (LAW)
Этот ORC создаёт документальный набор трека из альбомного плана:
- MUSIC_TRACK_CARD
- MUSIC_TRACK_PROMPT
- MUSIC_TRACK_RELEASE

Аудио может быть сгенерировано вне документов, но этот ORC отвечает за документы (как вход в генерацию/публикацию).
Финальная готовность подтверждается через DOC-GATE и затем RELEASE_PACK.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW.

### 1.2 Ownership is mandatory
PRIMARY_SPC берётся только из `ORC → SPC`.

### 1.3 Allowlist engines only
ENG разрешены только по `ENG → ORC`.

### 1.4 Matrix-driven gates only
Обязательные CTL/VAL/QA берутся из `VALIDATION_MATRIX` по ARTIFACT_TYPE.

### 1.5 One-axis iteration discipline
В одном цикле правки меняется только ОДНА ось:
- либо структура (sections/arrangement)
- либо хук (hook)
- либо вокальная подача (delivery)
- либо лирика/слова (lyrics)
- либо негативные ограничения (negative spec)
Иначе → FAIL (процессный).

### 1.6 Stop conditions
Только:
- RAW missing
- marker not confirmed
- input absent

---

## 2) REQUIRED XREF (RAW)
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
- Album blueprint (track list + intent per track) — RAW link if exists, else user text
- Group style / master style — RAW link if exists, else user text
- Track targets:
  - number of tracks to produce (N)
  - language constraint (if any)
  - mood/genre intent (short)

### 4.2 Optional
- Poet pack spec (если используем поэзию/мозаику)
- Catalog memory snapshot (что уже было, чтобы не повторяться)

### 4.3 Stop rule
Если нет album blueprint / track targets → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET) — PER TRACK
Для каждого трека i:
- MUSIC_TRACK_CARD (ARTIFACT_TYPE: MUSIC_TRACK_CARD)
- MUSIC_TRACK_PROMPT (ARTIFACT_TYPE: MUSIC_TRACK_PROMPT)
- MUSIC_TRACK_RELEASE (ARTIFACT_TYPE: MUSIC_TRACK_RELEASE)

Дополнительно:
- ITERATION_LOG (короткий трейс: что меняли по one-axis)

---

## 6) TRACK DOC MINIMUM CONTENT (DETERMINISTIC)
### 6.1 CARD minimum
- UID/Title
- role in album (slot)
- mood/genre tags
- differentiation note (чем отличается от соседних)
- pointers to prompt/release docs (или planned names)

### 6.2 PROMPT minimum
- prompt contract fields (structure)
- negative specs
- duration target / hook timing intent
- optional: voice diversity intent

### 6.3 RELEASE minimum
- credits/metadata block
- rights notes (если есть)
- collision/fingerprint note (intent-level)

---

## 7) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (from ORC→SPC map)  
Gate: READINESS_CHECK_CTL  
Input: blueprint + targets  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — PLAN TRACK SLOTS
Owner: PRIMARY_SPC  
Action:
- зафиксировать N слотов (T01..TN)
- для каждого: intent + differentiation tag
Output:
- TRACK_SLOT_TABLE

---

### STEP 2 — DRAFT DOCS (CARD/PROMPT/RELEASE)
Owner: PRIMARY_SPC + allowlisted ENG methods  
Constraint:
- использовать только allowlisted ENG (см. ENG→ORC запись для ALBUM→TRACK)
Output per track:
- CARD_DRAFT
- PROMPT_DRAFT
- RELEASE_DRAFT
- ITERATION_LOG entry (axis = NEW, first draft)

---

### STEP 3 — APPLY MATRIX GATES (PER ARTIFACT)
Owner: ORC (this doc)  
Action:
Для каждого артефакта (CARD, PROMPT, RELEASE):
- определить ARTIFACT_TYPE
- получить REQUIRED_CTL/VAL/QA из `VALIDATION_MATRIX`
- применить в каноническом порядке
Outputs:
- CTL_VERDICT per artifact
- VIOLATION_RECORDS per artifact (VAL)
- QA_VERDICT per artifact

If any FAIL:
- перейти к STEP 4 (repair loop)

---

### STEP 4 — REPAIR LOOP (ONE-AXIS)
Owner: PRIMARY_SPC  
Action:
- выбрать ОДНУ ось изменения
- внести минимальную правку
- обновить ITERATION_LOG
- повторить STEP 3 только для затронутых артефактов

Stop:
- если попытка изменить >1 оси за цикл → STOP: marker not confirmed (process violation)

---

### STEP 5 — HANDOFF TO DOC-GATE
Owner: PRIMARY_SPC  
Action:
- после PASS по всем артефактам трека — отправить набор в TRACK_TEST_DOC_GATE_ORC
Output:
- DOC_GATE_INPUT_SET

DOC-GATE ORC:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

### STEP 6 — READY FOR PACKAGING
Owner: PRIMARY_SPC  
Action:
- если DOC-GATE PASS — трек готов к упаковке
Output:
- READY_TRACK_SET (card+prompt+release)

Packaging ORC:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

---

### STEP 7 — DOC CONTROL + SIGNOFF (PER RUN)
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Action:
- подтверждение что produced docs соответствуют стандартам и матрице
Output:
- SIGNOFF_NOTE (run-level)

---

## 8) FAILOVER (STRICT)
- FAIL on CARD/PROMPT/RELEASE gates → repair loop (STEP 4)
- FAIL on DOC-GATE → repair loop, затем снова DOC-GATE
- Repeated catalog collision → use allowed collision/novelty engines; если не хватает — GAP (allowlist/matrix)

---

## 9) EXTENSION POLICY (STRICT)
- Новый тип артефакта → PATCH Validation Matrix
- Новый ENG нужен → PATCH ENG→ORC allowlist
- Новый ownership нужен → PATCH ORC→SPC map
Иначе STOP.

---

END.
