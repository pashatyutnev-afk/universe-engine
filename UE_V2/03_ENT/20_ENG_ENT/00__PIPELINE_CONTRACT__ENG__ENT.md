# 00__PIPELINE_CONTRACT__ENG__ENT
KIND: ENGINE
ROLE: CONTRACT
SCOPE: ENT.ENG
STATUS: CANON
VERSION: 1.0.0

## 0) PURPOSE
Единый контракт вызова для всех ENG (engine modules) внутри 03_ENT/20_ENG_ENT.
Нужен, чтобы:
- SPC мог планировать вызовы движков (ENGINE_PLAN_TOKEN.required_eng_keys)
- ORC мог запускать движки по ключам и собирать результаты
- VAL мог проверить coverage и output contract

Этот контракт делает ENG “исполняемыми”, а не “просто библиотекой текстов”.

---

## 1) TERMS
- ENG_KEY: ключ движка (KEY:ENG.*) — единственный способ адресации.
- ENGINE_PLAN_TOKEN: план вызовов движков (формирует SPC).
- ENGINE_RUN_LEDGER: факт исполнения (формирует ORC).
- ENG_OUTPUTS_TOKEN: агрегированный результат работы всех движков (формирует ORC).
- OUTPUTS: стандартизированный список артефактов, которые возвращает движок.

---

## 2) REQUIRED TOKENS (INPUT/OUTPUT)
### 2.1 ENGINE_PLAN_TOKEN (input to ORC)
ENGINE_PLAN_TOKEN:
  required_eng_keys: ["KEY:ENG.*", "..."]
  allowed_eng_keys:  ["KEY:ENG.*", "..."]  # optional
  no_go_eng_keys:    ["KEY:ENG.*", "..."]  # optional
  expected_outputs:  ["<artifact_name>", "..."] # optional

Rules:
- required_eng_keys field MUST exist (может быть пустым только для SYS задач).
- If allowed_eng_keys present, ORC must not run engines outside it.
- If no_go_eng_keys present, ORC must never run them.

### 2.2 ENGINE_RUN_LEDGER (output from ORC)
ENGINE_RUN_LEDGER:
  run_id: "<runtime>"
  entries:
    - eng_key: "KEY:ENG...."
      status: "ran|skipped|failed"
      outputs_produced: ["<artifact_name>", "..."]
      notes: "<optional>"

### 2.3 ENG_OUTPUTS_TOKEN (output from ORC)
ENG_OUTPUTS_TOKEN:
  produced_artifacts:
    - name: "<artifact_name>"
      eng_key: "KEY:ENG...."
      payload_ref: "<where stored / summary>"
  summary:
    total_engines_required: <int>
    total_engines_ran: <int>
    total_engines_failed: <int>

---

## 3) ENGINE MODULE INTERFACE (what every ENG must provide)
Each ENG module MUST declare in its header:
- KIND: ENGINE
- ROLE: ENG
- SCOPE: ENT.ENG.<domain>
- ENG_KEY: KEY:ENG....
- INPUTS: (required/optional)
- OUTPUTS: (list)
- GATES: (basic validations for its own outputs)

### 3.1 ENG INPUT CONTRACT (minimum)
Every ENG receives:
- BRIEF_TOKEN (from SPC)
- CANON_TOKEN (if exists)
- PROFILE_KEY (from ROUTE_TOKEN)
- OPTIONAL: KB_TOKEN (rules/checklists if profile requires)

### 3.2 ENG OUTPUT CONTRACT (minimum)
Every ENG returns:
- OUTPUTS (list of named artifacts)
- LOCAL_GATES_REPORT (PASS/FAIL for its own mini-checks)

---

## 4) ORC EXECUTION RULES (how engines are run)
ORC must:
1) Resolve each eng_key via INDEX_MANIFEST__ENG__ENT (KEY → LOCAL_PATH)
2) Validate scope:
   - If eng_key in no_go_eng_keys -> SKIP + ledger entry
   - If allowed_eng_keys present and eng_key not in it -> FAIL:SCOPE_VIOLATION
3) Execute engine:
   - If engine returns FAIL -> mark failed and stop (default)
   - Profile may allow continue-on-fail (only if explicitly set)
4) Append ledger entry for every required_eng_key (ran/skipped/failed)
5) Aggregate outputs into ENG_OUTPUTS_TOKEN

---

## 5) VALIDATION HOOKS (VAL must check)
VAL.ENGINE_COVERAGE_GATE uses:
- ENGINE_PLAN_TOKEN.required_eng_keys
- ENGINE_RUN_LEDGER.entries

PASS conditions:
- Every required_eng_key has a ledger entry
- Every required_eng_key status == ran (unless profile allowed skip)
- No engine ran that violates allowed/no-go constraints

VAL.OUTPUT_CONTRACT_GATE uses:
- ROUTE_TOKEN.OUTPUT_CONTRACT
- OUTPUT_LEDGER / produced_artifacts

---

## 6) FOLDER STANDARD (how ENG packs should be organized)
Inside 03_ENT/20_ENG_ENT:
- Each domain pack has its own folder (MUSICFACTORY, AUDIO, NAMINGIDENTITY, etc.)
- Each engine file must declare ENG_KEY and OUTPUTS.
- Index manifest MUST cover every ENG_KEY.

---

## 7) STOP/FAIL POLICY
If any of these occurs -> STOP_GAP:
- eng_key cannot be resolved -> FAIL:ENTRYPOINT_MISSING
- engine outputs missing required OUTPUTS -> FAIL:MARKER_NOT_CONFIRMED
- engine violates allowed/no-go -> FAIL:SCOPE_VIOLATION

END.
