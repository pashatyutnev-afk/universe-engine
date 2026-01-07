# NATURALNESS GATES (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/07__NATURALNESS_GATES.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.NAT_GATES.607
OWNER: SYSTEM
ROLE: Marking module providing conventions for recording Naturalness Gates evaluations (PASS/WARN/FAIL), where to place NAT results, how to link results to targets, and optional NAT scoring. Extends Naturalness Gates SoT.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль NAT: разметка результатов гейтов, формат записи, привязка к UID целей, политика хранения и score"
- REASON: "Чтобы NAT проверки были одинаково записаны и читались везде"
- IMPACT: "Scene Packs, Track Events, Character docs, pipelines"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.NAT_GATES.106 | extends | marking details for NAT results | 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md
XREF: UE.STD.TPL.NAT_PROFILE.106A | references | NAT Profile instance structure | 02_STANDARDS/01_SPECIFICATIONS/06A__TEMPLATE__NAT_PROFILE.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first links to targets | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот модуль задаёт:
- где хранить результаты NAT проверок
- как оформлять записи PASS/WARN/FAIL
- как ссылать результаты на конкретную цель (scene/event/entity) через UID
- как (опционально) считать NAT_SCORE

---

## 1) WHERE TO STORE NAT RESULTS (RECOMMENDED)
Варианты (по приоритету):

1) **Внутри целевого документа** (если результат важен для чтения)
   - пример: Scene Pack включает блок NAT_EVALUATION
2) **В отдельном артефакте “NAT Evaluation”** (если проверок много)
   - рекомендуется для массовых проверок пайплайна
3) **Внутри NAT Profile как “sample”** (только примеры, не как основное хранилище)

---

## 2) NAT EVALUATION BLOCK (STANDARD)
Рекомендуемый блок для вставки в документ:

`## NAT_EVALUATION`
- PROFILE_UID: <NAT_PROFILE_UID or null>
- DATE: YYYY-MM-DD
- TARGET_UID: <UID of scene/event/entity>
- RESULTS:
  - GATE_ID: G-01 | OUTCOME: PASS|WARN|FAIL | COMMENT: "<short>"
  - GATE_ID: G-02 | OUTCOME: PASS|WARN|FAIL | COMMENT: "<short>"
- NAT_SCORE: <0-100 or null>
- OVERALL: PASS|WARN|FAIL
- NOTES: "<optional>"

---

## 3) OUTCOME RULES (PRACTICAL)
- PASS: гейт удовлетворён
- WARN: допустимо, но нужен комментарий (почему ок/что поправить)
- FAIL: блокер в зависимости от политики профиля

Правило:
- WARN/FAIL обязаны иметь `COMMENT` (не пустой).

---

## 4) LINKING RULES (UID-FIRST)
`TARGET_UID` обязателен.
Если цель имеет путь:
- допускается `TARGET_PATH` как доп. поле, но не вместо UID.

Если проверяется сцена:
- `TARGET_UID = SCENE_UID` (сущность)
Если проверяется документ:
- `TARGET_UID = DOC_UID` (документ)
(Выбирай один режим и держи консистентно в области.)

---

## 5) OPTIONAL NAT SCORE (STANDARDIZED IF USED)
Если считаешь score:
- `NAT_SCORE = 100 - (FAIL*20 + WARN*5)` (min 0)

Если не считаешь:
- `NAT_SCORE: null`

---

## 6) OVERALL DECISION RULE (SIMPLE)
Если включена строгая политика:
- если есть FAIL → OVERALL = FAIL
- иначе если есть WARN → OVERALL = WARN
- иначе PASS

Если политика профиля разрешает FAIL:
- OVERALL всё равно отражает факт FAIL, даже если пайплайн не блокируется.

---

## 7) PRIORITY VS STRICTNESS (DO NOT CONFUSE)
- `PRIORITY S0–S3` — критичность проблемы (см. Priority module)
- `NAT_STRICTNESS S0–S3` — строгость профиля NAT

Если нужно писать оба:
- `PRIORITY: S1`
- `NAT_STRICTNESS: S2`

---

## 8) COMMON PATTERNS
### 8.1 Scene Pack inline
В конце Scene Pack:
- вставить `## NAT_EVALUATION` для важной сцены

### 8.2 Pipeline batch
Создать отдельный документ:
- `ARTIFACT_TYPE: NAT_EVALUATION_REPORT`
- таблица по TARGET_UID + результаты

---

## 9) MIGRATION NOTES
S0:
- привести все NAT записи к единому блоку NAT_EVALUATION
S1:
- внедрить обязательные комментарии для WARN/FAIL

---

## FINAL RULE (LOCK)
Этот модуль расширяет NAT Gates SoT и задаёт стандарт записи результатов.
Изменение формата NAT_EVALUATION блока = MAJOR по умолчанию.
--- END.
