# ORC — PORTFOLIO PLANNER (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md
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
UID: UE.ORC.MUSIC.PORTFOLIO_PLANNER.001
OWNER: SYSTEM
ROLE: Planning-only pipeline: build a deterministic release portfolio plan (calendar/sequence/rules) without producing audio. Outputs are SPEC/PACKAGE only.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt PORTFOLIO_PLANNER as strict planning-only contract: inputs/outputs, XREF dependencies, gate placement, and signoff chain."
- REASON: "Prevent mixing planning with generation; make portfolio planning auditable and reproducible."
- IMPACT: "Portfolio plans become consistent inputs for release scheduling and pipeline selection."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.PORTFOLIO.001

---

## 0) PURPOSE (LAW)
Этот ORC строит план портфеля выпусков:
- что и в каком порядке выпускать,
- какие серии/темы/жанры покрываем,
- какие ограничения и правила соблюдаем,
- какой “следующий шаг” (какой pipeline запускать дальше).

Здесь не создаются аудио-выходы. Только плановые документы.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW.

### 1.2 Ownership is mandatory
Владельцы берутся только из `ORC → SPC` карты.

### 1.3 Allowlist engines only
ENG допускаются только по `ENG → ORC` allowlist для этого ORC.

### 1.4 Mandatory gate order
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.5 Planning-only scope
Запрещено выпускать:
- MUSIC_TRACK_* артефакты
- MUSIC_RELEASE_* артефакты
Этот ORC выпускает только SPEC/PACKAGE.

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
- Portfolio horizon (например: 4 недели / 3 месяца / 20 релизов)
- Portfolio goals (охват жанров/настроений/аудиторий) — кратко
- Constraints:
  - frequency (как часто выпускать)
  - variety (минимальная дифференциация между релизами)
  - platform focus (YouTube/streaming/etc) — как intent, без внешних ссылок

### 4.2 Optional
- Existing catalog snapshot (список уже готовых релизов/треков)
- Brand constraints (если портфель под брендом)

### 4.3 Stop rule
Если нет horizon или goals → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
- PORTFOLIO_PLAN (SPEC doc) — основной документ плана
- OPTIONAL: PORTFOLIO_PACK (PACKAGE doc) — если нужно упаковать план с приложениями

Validation gates берём из `VALIDATION_MATRIX` для типов SPEC/PACKAGE.

---

## 6) PLANNING RULES (DETERMINISTIC)
План обязан содержать минимум:
- Release slots (S01..SNN) или календарные точки (W01..WNN)
- Для каждого слота:
  - intent (что выпускаем: single track / album pack / poet pack / etc)
  - recommended pipeline (PIPELINE_ID из `PIPELINES` map)
  - ownership note (primary ORC owner is resolved via ORC→SPC during execution)
  - differentiation tag (почему это отличается от соседнего)
- Risk notes (если есть риск однообразия / коллизий / перегруза)

---

## 7) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (from ORC→SPC map)  
Gate: READINESS_CHECK_CTL  
Input: horizon + goals + constraints  
Output: PASS/FAIL  
Fail → STOP

---

### STEP 1 — SLOT GRID BUILD (SPC)
Owner: PRIMARY_SPC  
Output:
- SLOT_GRID (N слотов) с частотой и распределением

---

### STEP 2 — INTENT ASSIGNMENT (SPC)
Owner: PRIMARY_SPC  
Action:
- назначить intent каждому слоту
- отметить разнообразие (variety)

Output:
- SLOT_INTENTS

---

### STEP 3 — PIPELINE RESOLUTION (XREF)
Owner: ORC (this doc)  
Action:
- для каждого intent подобрать PIPELINE_ID по `PIPELINES` map
Output:
- SLOT_PIPELINE_MAP (slot → pipeline_id → primary_orc_raw)

Fail:
- если intent не маппится → STOP: marker not confirmed (need new pipeline record)

---

### STEP 4 — VALIDATION + QA (by matrix)
Owner: relevant VAL + relevant QA  
Action:
- применить матрицу к типу SPEC (и PACKAGE если делаем pack)
Output:
- VIOLATIONS / QA_VERDICT

FAIL → возврат на STEP 1–3

---

### STEP 5 — DOC CONTROL + SIGNOFF
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Output:
- FINAL PORTFOLIO_PLAN (и optional pack)

---

## 8) EXTENSION POLICY (STRICT)
Если нужно добавить новый тип слота/intent:
1) обновить `PIPELINES` map (PATCH)
2) при необходимости обновить `VALIDATION_MATRIX` (PATCH)
3) затем обновить этот ORC (PATCH)

---

END.
