FILE: UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md
SCOPE: UE_V2 / 14_LOG
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: LOG
UID: UE.V2.LOG.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: KEY-only; resolve RAW via UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

---

## [M] PURPOSE
Step-run contract for LOG realm.
Provides deterministic write/append targets for runtime logs using KEYS only.

## [M] HARD_RULES
- This contract references targets by KEY only.
- Any open is performed via INDEX_MANIFEST resolution (RAW lives there).
- Append-only discipline: no rewriting history, only new entries.

## [M] REQUIRED INDEX
- IDX.KEY = INDEX_MANIFEST  (UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md)

## [M] TARGET KEYS (must exist in IDX)
- LOG.RUN_LOG
- LOG.CHANGE_LOG
- LOG.TOKEN_ARCHIVE
- LOG.DECISION_LOG
- LOG.START_POINT_LOG

## [M] STEP-RUN (CANON)

S0) LOG_INIT
- Ensure targets resolvable by KEY (all TARGET KEYS).
- If any target missing -> GAP.

S1) WRITE_START_POINT
- Append record to LOG.START_POINT_LOG:
  - timestamp
  - TASK_TEXT hash/short
  - ROUTE_TOKEN pointer (if exists)
  - run_id (generated)

S2) WRITE_RUN_STEP
- Append record to LOG.RUN_LOG for each step:
  - run_id
  - step_id
  - status (OK|GAP|STOP)
  - produced artifacts pointers (if any)

S3) WRITE_DECISION
- Append record to LOG.DECISION_LOG when a gate/approval happens:
  - run_id
  - gate_id
  - decision (PASS|FAIL|GAP|STOP)
  - rationale pointer(s)

S4) ARCHIVE_TOKENS
- Append record to LOG.TOKEN_ARCHIVE:
  - run_id
  - ROUTE_TOKEN / START_OUTPUT pointers
  - resume pointer(s) if emitted

S5) WRITE_CHANGE (optional)
- Append record to LOG.CHANGE_LOG only if canon/system changed:
  - change_id
  - affected keys
  - patch pointer(s)

## [M] STOP / GAP
STOP only if:
- IDX missing RAW for required keys (cannot resolve)
- marker not confirmed for MUST_LOAD targets
GAP if:
- any TARGET KEY missing in IDX or file absent

## [M] OUTPUT
- LOG_TOKEN:
  - run_id
  - pointers to latest appended entries (per target)
- NEXT: "го"
