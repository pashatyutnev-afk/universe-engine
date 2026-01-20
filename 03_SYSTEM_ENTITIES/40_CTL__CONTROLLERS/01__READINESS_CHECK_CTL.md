# 01__READINESS_CHECK_CTL

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
SCOPE: Universe Engine / Controllers (CTL) / Default Readiness Gate
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: CTL (CONTROLLER)
LEVEL: L2 (ENTITY)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.ENT.CTL.GEN.READINESS_CHECK.001
OWNER: SYSTEM
ROLE: Default readiness controller. Provides universal readiness gate with profiles. Includes SCENE_PACK profile as baseline.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Converted readiness check from single SCENE_PACK-only gate into universal readiness controller with profiles."
- REASON: "START requires readiness gate in finish chain for any task; single-type gate caused routing ambiguity."
- IMPACT: "One readiness controller can be reused across domains; profiles keep checks explicit."

---

## 0) PURPOSE (LAW)
Этот контроллер — базовый gate готовности.
Он не оценивает качество (QA) и не валидирует канон (VAL).
Он проверяет минимальную готовность входного артефакта к продвижению по пайплайну.

---

## 1) MINI-CONTRACT (MANDATORY)
CONSUMES:
- artifact_candidate (любой тип)
- artifact_type (string)
- expected_minimum (optional)

PRODUCES:
- READINESS_REPORT (PASS/FAIL)
- MISSING_LIST (what is missing)
- BLOCKERS_LIST (if FAIL)

DEPENDS_ON:
- []

OUTPUT_TARGET:
- LOG

---

## 2) UNIVERSAL BASE CHECKS (MANDATORY)
Эти проверки применяются ко всем типам артефактов.

S0 FAIL if any:
- отсутствует DOC CONTROL header (FILE/SCOPE/LAYER/DOC_TYPE/STATUS/LOCK/VERSION/UID/OWNER/ROLE)
- UID пустой
- VERSION пустой
- STATUS/LOCK отсутствуют

S1 FAIL (или BLOCKED) if any:
- отсутствует PURPOSE
- отсутствует MINI-CONTRACT (если это сущность-исполнитель: CTL/ORC/ENG/SPC/VAL/QA)
- отсутствуют ссылки на SoT стандарты, если контроллер явно ссылается на стандарты

---

## 3) PROFILES (EXPLICIT CHECKSETS)
Профили применяются по `artifact_type`.
Если профиль не найден, применяется только UNIVERSAL BASE CHECKS.

### PROFILE: SCENE_PACK (4TRACK)  (baseline)
S0 FAIL if any:
- missing TRACK NAR
- missing TRACK VIS
- missing TRACK SND
- missing TRACK MOT
- any track exists but has 0 events
- missing META.GOAL

S1 WARN (can be BLOCKED if policy requires):
- META.TONE empty
- CONSTRAINTS empty (warn if финальный прогон)
- LINKS missing when required by brief

SoT references for this profile:
- MARKING: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md
- SCENE 4TRACK: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md
- STORAGE MAP: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

### PROFILE: MUSIC_TRACK (placeholder)
(добавлять проверки по мере появления стандартов, без угадывания)

### PROFILE: INDEX_DOC (placeholder)
(минимум: doc control + наличие списка RAW ссылок или явной политики индекса)

### PROFILE: ENTITY_DOC (SPC/ORC/ENG/CTL/VAL/QA) (placeholder)
(минимум: doc control + purpose + mini-contract + interfaces raw)

---

## 4) OUTPUT FORMAT (MANDATORY)
RESULT: PASS|FAIL
TARGET: <artifact_type>
MISSING:
- <items>
BLOCKERS:
- (если FAIL) blockers list
NOTES: ""

---

## 5) RELATIONS (MANDATORY)
CALLS: []
CONSUMES: [artifact_candidate]
PRODUCES: [LOG]
DEPENDS_ON: [SoT standards when profile requires]

---

## 6) INTERFACES (RAW)
- UID RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- CTL RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md

---

## 7) KNOWLEDGE BASE (KB) SCOPE
KB Inputs:
- optional примеры readiness отчётов и типовые missing-листы

KB Outputs:
- none

Boundaries:
- readiness не делает доменные решения и не заменяет QA/VAL

--- END.
