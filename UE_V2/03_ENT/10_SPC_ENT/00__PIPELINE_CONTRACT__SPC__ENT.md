# 00__PIPELINE_CONTRACT__SPC__ENT
KIND: ENGINE
ROLE: SPC_CONTRACT
SCOPE: ENT.SPC
STATUS: CANON
VERSION: 1.0.0

## [M] PURPOSE
SPC (специалист) — слой снятия задачи и формализации производства.
SPC обязан превратить любой запрос в:
- BRIEF_TOKEN (что строим + ограничения)
- ENGINE_PLAN_TOKEN (какие движки нужны)
- OUTPUT_CONTRACT (какие артефакты обязаны выйти)
- NO_GO_LIST (что запрещено, чтобы не было мусора)

SPC не производит финальный контент — он задаёт правила и план.

---

## [M] HARD_RULES
1) BRIEF ALWAYS
- BRIEF_TOKEN обязателен для production задач.

2) ENGINE PLAN ALWAYS
- ENGINE_PLAN_TOKEN обязателен если REQUIRED_ROLES содержит SPC.
- Поле required_eng_keys MUST exist (как поле всегда).

3) OUTPUT CONTRACT IS LAW
- OUTPUT_CONTRACT берётся из ROUTE_TOKEN, SPC может только уточнять, но не удалять обязательное.

4) NO-GO IS ENFORCED
- NO_GO_LIST фиксируется и дальше обязателен для CTL/VAL (анти-мусор).

5) DETERMNISM
- Для одинаковой задачи SPC выдаёт одинаковую структуру (не меняет формат).

---

## [M] INPUTS
REQUIRED:
- ROUTE_TOKEN
- TASK_TEXT

OPTIONAL:
- USER_CONSTRAINTS (язык, формат, референсы)
- USER_FILES (если есть)
- RUNTIME_MANIFEST (если есть)

---

## [M] OUTPUTS
REQUIRED (production):
- BRIEF_TOKEN
- ENGINE_PLAN_TOKEN
- SPC_REPORT

OPTIONAL:
- CANON_TOKEN (если есть “ДНК проекта”)

---

## [M] BRIEF_TOKEN (minimum schema)
BRIEF_TOKEN:
  goal: "<one line goal>"
  domain: "<from ROUTE_TOKEN.DOMAIN>"
  audience: "<if known>"
  language: "<RU/EN/OTHER>"
  format: "<artifact format>"
  constraints:
    - "<hard constraint 1>"
    - "<hard constraint 2>"
  success_criteria:
    - "<measurable criterion 1>"
    - "<measurable criterion 2>"
  risks:
    - "<risk 1>"
  notes: "<optional>"

RULE:
- constraints must be short and enforceable
- success_criteria must be checkable by VAL/QA (не “круто”, а “что проверяем”)

---

## [M] ENGINE_PLAN_TOKEN (minimum schema)
ENGINE_PLAN_TOKEN:
  required_eng_keys: ["KEY:ENG.*", "..."]
  allowed_eng_keys:  ["KEY:ENG.*", "..."]   # optional
  no_go_eng_keys:    ["KEY:ENG.*", "..."]   # optional
  expected_outputs:  ["<artifact_name>", "..."] # optional

RULES:
- required_eng_keys field MUST exist always:
  - for SYS patches may be empty []
  - for content production should usually be non-empty
- If allowed_eng_keys is present, it must include all required_eng_keys (otherwise it’s inconsistent).
- no_go_eng_keys must not intersect required_eng_keys.

---

## [M] OUTPUT_CONTRACT (source of truth)
SOURCE:
- ROUTE_TOKEN.REQUIRED_SET.OUTPUT_CONTRACT is the baseline.
SPC may:
- add extra outputs ONLY if profile allows (otherwise NO)
SPC must NOT:
- remove mandatory outputs

---

## [M] NO_GO_LIST (anti-trash)
SOURCE:
- ROUTE_TOKEN.REQUIRED_SET.NO_GO_LIST baseline
SPC may:
- add extra NO_GO items to prevent scope creep

Examples (generic):
- "Do not add unrelated domains"
- "Do not output long lore unless requested"
- "Do not skip required roles"

---

## [M] SPC_REPORT (short)
SPC_REPORT:
  summary: "<what was understood>"
  open_questions: ["<only if truly blocking>"]
  selected_profile: "<ROUTE_TOKEN.PROFILE_KEY>"
  required_roles: "<ROUTE_TOKEN.REQUIRED_SET.REQUIRED_ROLES>"
  required_eng_count: "<len(required_eng_keys)>"

RULE:
- open_questions максимум 1, и только если без него нельзя продолжать.

---

## [M] FAIL / STOP POLICY
- Missing ROUTE_TOKEN or TASK_TEXT -> FAIL: INPUT_ABSENT
- Missing OUTPUT_CONTRACT -> FAIL: MARKER_NOT_CONFIRMED
- ENGINE_PLAN_TOKEN.required_eng_keys field missing -> FAIL: MARKER_NOT_CONFIRMED
- allowed/no-go inconsistency -> FAIL: MARKER_NOT_CONFIRMED

On FAIL:
- provide FIX_LIST minimal:
  - "Provide missing ROUTE_TOKEN"
  - "Add required_eng_keys field"
  - "Remove intersection required vs no_go"

END.
