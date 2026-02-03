FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/01__GVN__ENTRY_GUARD__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.ENTRY_GUARD
UID: UE.V2.ENT.ORC.GVN.ENTRY_GUARD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Entry gatekeeper for governance actions.
Этот модуль — первая точка входа в governance пайплайн:
- проверяет наличие TASK_TEXT
- нормализует MODE_HINT
- формирует GOVN_TASK_TOKEN
- задаёт “границы ответственности” (что governance делает/не делает в MODE REPO)

---

## [M] INPUT
- TASK_TEXT (required): string
- MODE_HINT (optional): FAST|RELEASE_READY|MASTERPIECE|<empty>
- CONSTRAINTS (optional): object
  - platform (optional): string
  - duration (optional): string|number
  - style (optional): string
  - references (optional): string|array
- CONTEXT_TOKEN (optional): object|string (route token / prior decisions)

---

## [M] OUTPUT
On PASS:
- GOVN_TASK_TOKEN: object
  - token_id: string
  - domain: "GVN_ORC_ENT"
  - mode: "FAST"|"RELEASE_READY"|"MASTERPIECE"
  - task_text: string
  - constraints: object (normalized)
  - context_token_present: boolean
  - created_utc: string (YYYY-MM-DD)
  - exec_policy:
      repo_mode: "USAGE-ONLY"
      writes_allowed: false
      raw_navigation: "KEY_ONLY"
      noise_policy: "ANTI_NOISE"
  - run_intent:
      action_class: "governance_run"
      target_realm: "00_GOVERNANCE_ORC_ENT"
      dry_run: true

On FAIL:
- FAIL_CODE
- REQUIRED_FIXES

---

## [M] HARD RULES (enforced here)
1) TASK_TEXT required. No task -> fail.
2) MODE_HINT must be one of allowed values (or empty -> default).
3) MODE REPO (USAGE-ONLY, NO-EDIT):
   - любые попытки “сделай файл/измени файл/запиши в лог” трактуются как dry-run планирование, а не действие записи.
4) Constraints must be lightweight:
   - если constraints огромные/содержат деревья — обрезать до ключевых полей (platform/duration/style/references).
5) No guessing:
   - модуль не “додумывает” отсутствующие факты; только нормализация.

---

## [M] NORMALIZATION

### MODE_HINT normalization
- if MODE_HINT is empty/null -> "RELEASE_READY"
- if MODE_HINT in ["FAST","RELEASE_READY","MASTERPIECE"] -> keep
- else -> FAIL_CODE UE.FAIL.MODE_INVALID

### CONSTRAINTS normalization
Keep only:
- platform
- duration
- style
- references
If missing -> set to empty object {}.
If references is string -> wrap as [string].
If duration is missing -> keep empty (do not assume).

### TASK_TEXT normalization
- trim whitespace
- collapse excessive spaces
- minimum length: >= 3 chars else treat as absent

---

## [M] FAIL CODES emitted by this module
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MODE_INVALID

---

## [M] REQUIRED_FIXES (templates)

### UE.FAIL.INPUT_ABSENT
REQUIRED_FIXES:
- invalid_fields: ["TASK_TEXT"]
- next_step: "Provide TASK_TEXT describing what governance run should do."

### UE.FAIL.MODE_INVALID
REQUIRED_FIXES:
- invalid_fields: ["MODE_HINT"]
- next_step: "Set MODE_HINT to FAST or RELEASE_READY or MASTERPIECE (or omit it)."

---

## [M] DETERMINISTIC TOKEN_ID
token_id format:
GVN-TASK-<YYYYMMDD>-<HASH8>

HASH8 generation rule (deterministic, not cryptographic):
- source = MODE + "|" + normalized TASK_TEXT (first 120 chars) + "|" + normalized constraints summary (first 120 chars)
- hash = first 8 chars of stable hex digest
Note: actual hashing implementation is runtime responsibility; module only defines the rule.

---

## [M] EXAMPLE (PASS)
INPUT:
- TASK_TEXT: "Complete governance ORC_ENT realm docs"
- MODE_HINT: "FAST"
- CONSTRAINTS: {"platform":"md","references":"INDEX_MANIFEST"}

OUTPUT:
- GOVN_TASK_TOKEN.mode = "FAST"
- GOVN_TASK_TOKEN.exec_policy.writes_allowed = false
- GOVN_TASK_TOKEN.run_intent.dry_run = true

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 finalized entry guard (MODE REPO, anti-noise, deterministic token)
