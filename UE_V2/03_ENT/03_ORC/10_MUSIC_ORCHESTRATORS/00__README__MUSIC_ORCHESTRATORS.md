# MUSIC ORCHESTRATORS (ORC) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/00__README__MUSIC_ORCHESTRATORS.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 20_ORC__ORCHESTRATORS
FAMILY: 10_MUSIC_ORCHESTRATORS
DOC_TYPE: README (FAMILY)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUSIC.REALM.README.001
OWNER: SYSTEM
ROLE: Canonical onboarding + navigation for music ORC pipelines. Defines how to route, which maps to consult, and mandatory gates. No guessing.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized music orchestrators README aligned with XREF maps (pipelines, owners, ENG allowlist, validation matrix)."
- REASON: "Make music routing deterministic and auditable. Prevent implicit engine usage and ambiguous ownership."
- IMPACT: "Music runs can reference a stable routing procedure and required gate order."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.MUSIC.README.001

---

## 0) WHAT IS ORC (IN MUSIC)
ORC (Orchestrators) — это пайплайны.
ORC отвечает за:
- порядок шагов (что за чем),
- handoffs между SPC/ENG/CTL/VAL/QA,
- требования к входам/выходам шага,
- привязку к гейтам.

ORC не заменяет:
- SPC (намерение/решения/упаковка),
- ENG (методы),
- CTL (политики и обязательные гейты),
- VAL (проверки соответствия),
- QA (приёмка/скоринг).

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Навигация только по RAW ссылкам.

### 1.2 Determinism via XREF
Любой запуск музыкального маршрута должен ссылаться на XREF карты:
- pipelines (intent → pipeline)
- ORC→SPC (ownership)
- ENG→ORC (allowlist)
- validation matrix (required gates per artifact type)

### 1.3 Mandatory gate order
По умолчанию для любого музыкального ORC:
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

---

## 2) REQUIRED XREF MAPS (RAW)
04 — PIPELINES (intent → pipeline selection)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

02 — ORC → SPC (ownership map)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

01 — ENG → ORC (allowlist)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

03 — VALIDATION MATRIX (required CTL/VAL/QA by artifact type)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

---

## 3) HOW TO RUN MUSIC ROUTE (SHORT PROCEDURE)
1) Определи intent задачи (например: собрать альбом, собрать трек, подготовить релиз-пак).
2) Открой `04__MAP__PIPELINES.md` и выбери PIPELINE_ID.
3) Возьми PRIMARY_ORC и REQUIRED_GATES ORDER из пайплайна.
4) Открой `02__MAP__ORC_to_SPC.md` и зафиксируй PRIMARY_SPC владельца (handoff owners).
5) Открой `01__MAP__ENG_to_ORC.md` и проверь allowlist ENG для выбранного ORC.
6) Применяй `03__MAP__VALIDATION_MATRIX.md` для каждого выпускаемого артефакта (card/prompt/release/pack).
7) Если чего-то не хватает (ORC/ENG/CTL/VAL/QA/Template):
   - фиксируй GAP,
   - создавай недостающее по шаблону,
   - только потом продолжай.

---

## 4) NAVIGATION (CANON LIST, RAW)
Family Path: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/`

01 — GROUP → ALBUM ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

02 — ALBUM → TRACK ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

03 — TRACK TEST DOC GATE ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

04 — RELEASE PACK ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

05 — PORTFOLIO PLANNER ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

06 — POET PACK ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

---

## 5) BOUNDARIES (STRICT)
- ORC не тянет “любой ENG”. Только allowlist через `01__MAP__ENG_to_ORC.md`.
- ORC не назначает владельца “по логике”. Только `02__MAP__ORC_to_SPC.md`.
- ORC не выпускает “голый контент”. Любой выход должен быть артефактом и пройти required gates по `03__MAP__VALIDATION_MATRIX.md`.

---

## 6) CHANGE POLICY (LOCK)
- Любые изменения: только PATCH + CHANGE_NOTE.
- Добавление нового ORC: сначала файл ORC по шаблону, затем регистрация в XREF картах и индексах.

---  
END.
