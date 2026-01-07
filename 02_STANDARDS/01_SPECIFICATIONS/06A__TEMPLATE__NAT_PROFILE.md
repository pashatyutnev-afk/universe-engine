# TEMPLATE — NAT PROFILE (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/06A__TEMPLATE__NAT_PROFILE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.TPL.NAT_PROFILE.106A
OWNER: SYSTEM
ROLE: Canonical template for creating a Naturalness (NAT) Profile that configures Naturalness Gates: enabled gates, strictness, scope, and enforcement policy.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Шаблон NAT Profile: включение гейтов, strictness, политики FAIL/WARN, область применения"
- REASON: "Нужен единый копируемый профиль под разные realм/пайплайны"
- IMPACT: "Quality control across authoring pipelines"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.NAT_GATES.106 | implements | this template configures Naturalness Gates | 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header/compliance format | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

# NAT PROFILE — COPY TEMPLATE (INSTANCE)
> Инструкция: скопируй этот блок и настрой профиль под проект/realm/пайплайн.
> Если профиль становится каноном (SoT для пайплайна) — ставь `LOCK: FIXED` и регистрируй в соответствующем индексе/реестре.

---

## DOC CONTROL (INSTANCE HEADER)
FILE: <path-to-your-nat-profile.md>
SCOPE: Universe Engine
LAYER: <your-layer-or-KB-governance>
DOC_TYPE: ARTIFACT
ARTIFACT_TYPE: NAT_PROFILE
LEVEL: L2
STATUS: <DRAFT|ACTIVE>
LOCK: <OPEN|FIXED>
VERSION: 0.1.0
UID: <NAT_PROFILE_DOC_UID>
OWNER: <owner/team>
ROLE: Naturalness profile instance

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

## 1) PROFILE IDENTITY (REQUIRED)
PROFILE_NAME: "<name>"
PROFILE_SCOPE: "<project/realm/pipeline name>"
PROFILE_TARGETS:
- "<Scene Packs>"
- "<Track Events>"
- "<Character docs>"
- "<Other>"

APPLIES_TO:
- NARRATIVE: true|false
- CHARACTER: true|false
- VISUAL: true|false
- SOUND: true|false
- ANY: true|false

DEFAULT_STRICTNESS: <S0|S1|S2|S3>

---

## 2) ENFORCEMENT POLICY (REQUIRED)
FAIL_POLICY: <BLOCK|ALLOW_WITH_FLAG>
WARN_POLICY: <ALLOW_WITH_FLAG|IGNORE>

REQUIRED_MIN_SCORE: <0-100 or null>   # если используешь общий скоринг

OUTPUT_FORMAT:
- RECORD_RESULTS: true
- STORE_COMMENTS: true
- SUMMARY_LINE: true

---

## 3) ENABLED GATES (CONTROLLED SET)
> Включай гейты из списка SoT. Для каждого можно переопределить strictness.

GATES:
- GATE_ID: G-01
  ENABLED: true
  STRICTNESS: <S0|S1|S2|S3 or null>    # null = DEFAULT_STRICTNESS
  NOTES: "<optional>"

- GATE_ID: G-02
  ENABLED: true
  STRICTNESS: <...>
  NOTES: "<optional>"

- GATE_ID: G-03
  ENABLED: true
  STRICTNESS: <...>
  NOTES: "<optional>"

- GATE_ID: G-04
  ENABLED: false
  STRICTNESS: null
  NOTES: "<optional>"

- GATE_ID: G-05
  ENABLED: true
  STRICTNESS: <...>
  NOTES: "<optional>"

- GATE_ID: G-06
  ENABLED: true
  STRICTNESS: <...>
  NOTES: "<optional>"

- GATE_ID: G-07
  ENABLED: false
  STRICTNESS: null
  NOTES: "<optional>"

- GATE_ID: G-08
  ENABLED: true
  STRICTNESS: <...>
  NOTES: "<optional>"

- GATE_ID: G-09
  ENABLED: true
  STRICTNESS: <...>
  NOTES: "<optional>"

---

## 4) RESULT TEMPLATE (OPTIONAL — FOR RECORDING)
> Можно вставлять сюда результаты проверки конкретного объекта (или хранить отдельно).

EVALUATION_SAMPLE:
- TARGET_UID: <UID of scene/event/etc>
  DATE: YYYY-MM-DD
  RESULTS:
    - GATE_ID: G-01 | OUTCOME: PASS|WARN|FAIL | COMMENT: "<short>"
    - GATE_ID: G-02 | OUTCOME: PASS|WARN|FAIL | COMMENT: "<short>"
  NAT_SCORE: <0-100 or null>
  OVERALL: PASS|WARN|FAIL

---

## 5) LINKS / XREF (UID-first)
XREF:
- XREF: <UID_TARGET> | references | "<why>" | <path(optional)>
- XREF: <UID_TARGET> | depends_on | "<why>" | <path(optional)>

--- END OF TEMPLATE
