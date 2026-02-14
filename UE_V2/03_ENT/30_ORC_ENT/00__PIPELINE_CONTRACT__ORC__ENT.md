# 00__PIPELINE_CONTRACT__ORC__ENT
KIND: ENGINE
ROLE: ORC_CONTRACT
SCOPE: ENT.ORC
STATUS: CANON
VERSION: 1.0.0

## [M] PURPOSE
ORC (оркестратор) — исполнительный слой между SPC и ENG.
ORC превращает план (ENGINE_PLAN_TOKEN) в факт исполнения:
- резолвит движки по KEY
- запускает их по контракту ENG
- собирает выходы
- ведёт доказательные леджеры

Главная задача ORC: НЕ “писать текст”, а ОРКЕСТРИРОВАТЬ движки и собирать артефакты.

---

## [M] HARD_RULES
1) ORC runs engines ONLY by KEY (KEY-first).
2) ORC must produce ENGINE_RUN_LEDGER always (если ORC required).
3) ORC must not invent missing modules:
   - если eng_key не резолвится → STOP_GAP (FAIL: ENTRYPOINT_MISSING)
4) ORC must follow constraints:
   - allowed_eng_keys (если есть)
   - no_go_eng_keys (если есть)
5) ORC must output only artifacts in OUTPUT_CONTRACT (лишнее не добавлять).

---

## [M] INPUTS (TOKENS)
REQUIRED:
- ROUTE_TOKEN
- BRIEF_TOKEN
- ENGINE_PLAN_TOKEN

OPTIONAL:
- CANON_TOKEN
- KB_TOKEN (если профиль требует)
- NO_GO_LIST (из ROUTE_TOKEN/PROFILE)
- POLICY_REPORT (если CTL раньше ORC — редко)

---

## [M] OUTPUTS (TOKENS)
REQUIRED:
- ENGINE_RUN_LEDGER
- ENG_OUTPUTS_TOKEN
- ORC_REPORT (короткий отчёт)

OPTIONAL:
- DRAFT_ARTIFACTS (если ORC собирает черновики для CTL)

---

## [M] ENGINE_PLAN_TOKEN (minimum expected)
ENGINE_PLAN_TOKEN:
- required_eng_keys: ["KEY:ENG.*", "..."]
- allowed_eng_keys:  ["KEY:ENG.*", "..."] (optional)
- no_go_eng_keys:    ["KEY:ENG.*", "..."] (optional)
- expected_outputs:  ["<artifact_name>", "..."] (optional)

RULE:
- field required_eng_keys MUST exist as field (even if empty for SYS tasks).
- For content production it should usually be non-empty.

---

## [M] EXECUTION STEPS (CANON)
### STEP 0 — PRECHECK
- validate ENGINE_PLAN_TOKEN schema exists
- validate required_eng_keys field exists
If missing → FAIL: MARKER_NOT_CONFIRMED

### STEP 1 — RESOLVE ENGINES
For each eng_key in required_eng_keys:
- if no_go_eng_keys contains eng_key → mark SKIPPED in ledger, continue
- if allowed_eng_keys exists and eng_key not in it → FAIL: SCOPE_VIOLATION
- resolve eng_key via ENG index manifest:
  - KEY → LOCAL_PATH
If cannot resolve → FAIL: ENTRYPOINT_MISSING

### STEP 2 — RUN ENGINES
For each resolved engine:
- execute engine per ENG pipeline contract:
  inputs: BRIEF_TOKEN + (CANON_TOKEN) + (KB_TOKEN) + PROFILE_KEY
  outputs: named artifacts + local gates report
- append ENGINE_RUN_LEDGER entry:
  - eng_key, status, outputs_produced, notes
- collect outputs into ENG_OUTPUTS_TOKEN

Default rule:
- if any required engine fails → STOP and return FAIL (unless profile explicitly allows continue)

### STEP 3 — OUTPUT CONTRACT FILTER
- if ROUTE_TOKEN.REQUIRED_SET.OUTPUT_CONTRACT exists:
  keep only artifacts relevant to contract (or mark extras as ignored)
- ORC_REPORT should summarize:
  - engines ran/skipped/failed
  - key outputs produced

---

## [M] ENGINE_RUN_LEDGER (required format)
ENGINE_RUN_LEDGER:
  run_id: "<runtime>"
  entries:
    - eng_key: "KEY:ENG...."
      status: "ran|skipped|failed"
      outputs_produced: ["<artifact_name>", "..."]
      notes: "<optional>"

---

## [M] ENG_OUTPUTS_TOKEN (required format)
ENG_OUTPUTS_TOKEN:
  produced_artifacts:
    - name: "<artifact_name>"
      eng_key: "KEY:ENG...."
      payload_ref: "<summary/ref>"
  summary:
    total_engines_required: <int>
    total_engines_ran: <int>
    total_engines_failed: <int>

---

## [M] FAIL / STOP POLICY
- Missing required token → FAIL: MARKER_NOT_CONFIRMED
- Unresolvable eng_key → FAIL: ENTRYPOINT_MISSING
- Allowed/no-go violation → FAIL: SCOPE_VIOLATION
- Engine execution failure (required) → FAIL: MARKER_NOT_CONFIRMED (or propagate)

On FAIL:
- Provide minimal FIX_LIST:
  - "Add eng_key mapping to ENG index manifest"
  - "Remove forbidden eng_key from plan"
  - "Provide missing token <...>"

END.
