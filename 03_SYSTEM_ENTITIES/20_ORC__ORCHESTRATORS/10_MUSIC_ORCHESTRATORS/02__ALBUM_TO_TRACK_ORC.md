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
ROLE: Deterministic pipeline: album blueprint → track artifacts (card/prompt/release) with mandatory gates, ownership, and allowlisted engines.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt ALBUM→TRACK orchestrator as a strict contract: inputs/outputs, handoffs, XREF dependencies, mandatory gate order."
- REASON: "Remove ambiguity: ORC must not guess engines, owners, or gate placement."
- IMPACT: "Music production becomes auditable and repeatable across runs."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.A2T.001

---

## 0) PURPOSE (LAW)
Этот ORC определяет порядок шагов для преобразования альбомного blueprint в комплект трек-артефактов.
ORC не генерирует контент сам, а управляет:
- шагами,
- handoffs,
- применением CTL/VAL/QA гейтов,
- упаковкой результатов в канонические документы.

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Использовать только RAW ссылки из ROOT LINK BASE или присланные пользователем.

### 1.2 Ownership is mandatory
ORC обязан опираться на карту владельцев `ORC → SPC`.
Нельзя назначать владельцев “по логике”.

### 1.3 Allowlist engines only
ORC обязан опираться на карту `ENG → ORC`.
Нельзя использовать ENG вне allowlist.

### 1.4 Mandatory gate order
По умолчанию для каждого артефакта в этом пайплайне:
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.5 Output artifact rule
Запрещён “голый контент”. Каждый результат оформляется как документ-артефакт.

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

MUSIC CTL FAMILY (policies)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/00__README__MUSIC_CONTROLLERS.md

---

## 4) INPUTS (MINIMUM)
### 4.1 Required
- Album context (минимум один из):
  - `00__ALBUM__PASSPORT.md`
  - `01__ALBUM__BLUEPRINT.md`
- Group context (если доступно):
  - `00__GROUP__PASSPORT.md`
  - `01__GROUP__STYLE.md`

### 4.2 Task inputs
- Target: какой трек делаем (T01..Txx) или список треков
- Format intent: какой тип трека/настроение/роль в альбоме (из blueprint)
- Platform target: Suno/Udio/Universal (если применимо)

### 4.3 Stop rule
Если нет альбомного blueprint и невозможно определить цель трека → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
Минимальный набор на 1 трек (строго как документы):
- MUSIC_TRACK_CARD
- MUSIC_TRACK_PROMPT
- MUSIC_TRACK_RELEASE (когда есть релизный результат или релиз-пак стадия)

Матрица гейтов для каждого типа берётся из `VALIDATION_MATRIX`.

---

## 6) PIPELINE STEPS (DETERMINISTIC)
Каждый шаг должен оставлять trace: что принято, что выдано, кто владелец.

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (из ORC→SPC map)  
Gate: READINESS_CHECK_CTL  
Input: TASK + album blueprint + root link base context  
Output: READINESS_VERDICT PASS/FAIL

Fail → STOP по причине из CTL.

---

### STEP 1 — TRACK SELECTION (SPC handoff)
Owner: PRIMARY_SPC  
Input: album blueprint + task target  
Output:
- TRACK_TARGET (Txx)
- TRACK_ROLE_IN_ALBUM (hook/bridge/intro/outro/peak etc)
- REQUIRED_ARTIFACTS (card/prompt/release)

Notes:
- Не допускается выбор “примерно такой трек”. Нужна явная фиксация TRACK_TARGET.

---

### STEP 2 — ENGINE SELECTION (ORC + XREF)
Owner: ORC (this file)  
Constraint:
- использовать только allowlisted ENG реалмы из `ENG→ORC` для данного ORC.

Output:
- ALLOWED_ENG_REALMS_USED (список реалмов, ссылками на README реалмов)
- OPTIONAL_ENGINE_NOTES (что для чего)

Fail:
- если для нужного действия нет allowlisted ENG реалма → STOP: marker not confirmed (это GAP)

---

### STEP 3 — PROMPT CONTRACT APPLICATION (CTL)
Owner: PRIMARY_SPC + CTL policy application  
Apply CTL policies (по необходимости):
- PROMPT_CONTRACT_CTL
- DURATION_POLICY_CTL
- RELEASE_VARIANTS_CTL (если нужен вариант)
- NEGATIVE_SPEC_LIBRARY_CTL (если применимо)

Output:
- PROMPT_CONTRACT_STATE (кратко: что применили)
- CONSTRAINTS_APPLIED (список)

Notes:
- Контроллеры не создают текст за ORC. Они ограничивают форму и требования.

---

### STEP 4 — DRAFT ARTIFACTS (ENG execution via ORC)
Owner: PRIMARY_SPC (решения) + ENG (методы)  
Produces drafts:
- TRACK_CARD_DRAFT
- TRACK_PROMPT_DRAFT

Output target:
- оформляется как документы (не как “в чат текстом без шапки”)

---

### STEP 5 — VALIDATION + QA (by matrix)
Owner: relevant VAL + relevant QA  
Input: drafts  
Rules:
- REQUIRED_VAL и REQUIRED_QA берутся из `VALIDATION_MATRIX` по ARTIFACT_TYPE.

Output:
- VIOLATIONS (если есть)
- QA_VERDICT (PASS/WARN/FAIL по доменным правилам QA, если определены)

Fail handling:
- FAIL → возврат на STEP 3/4 (исправление) без выхода из allowlist и без смены владельцев.

---

### STEP 6 — DOC CONTROL + SIGNOFF
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Action:
- проверка doc control полей, UID, version, naming consistency
- финальная подпись цепочки

Output:
- FINAL_ARTIFACTS (card/prompt/release) готовые

---

## 7) HANDOFFS (CANON)
- ORC owner (this doc) управляет шагами и обязательными картами.
- PRIMARY_SPC владеет решениями и упаковкой результата.
- CTL применяет политики и readiness gate.
- VAL фиксирует нарушения соответствия.
- QA фиксирует приемку/скоринг.
- DOC_CONTROLLER_SPC проверяет doc control и корректность упаковки.
- MACHINE_ARCHITECT_SPC закрывает ран.

---

## 8) EXTENSION POLICY (STRICT)
Если нужно добавить:
- новый тип артефакта
- новый обязательный гейт
- новый ENG реалм для этого ORC

Сначала:
1) обновить XREF карты (validation matrix / eng→orc / orc→spc) как PATCH
2) затем обновить этот ORC как PATCH

---

END.
