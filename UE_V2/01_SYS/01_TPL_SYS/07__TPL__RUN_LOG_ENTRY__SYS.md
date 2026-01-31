FILE: 0000-00-00__TPL__RUN_LOG_ENTRY__SYS.md
SCOPE: UE_V2 / SYS
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: RUN_LOG_ENTRY
UID: UE.V2.SYS.TPL.RUN_LOG_ENTRY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
UPDATED: 2026-01-30
OWNER: SYS

---

## [M] RUN_ENTRY
- DATE: 0000-00-00
- RUN_ID: <UNIQUE_RUN_ID>
- MODE: FAST|RELEASE_READY|MASTERPIECE
- TASK_TEXT: <short>
- ROUTE_TOKEN: <if exists>
- WORK_SET_KEYS: [<keys opened/resolved>]

## [M] ACTIONS
- Step: S<n>
- Did:
  - <action>
  - <action>

## [M] OUTPUTS
- Artifacts:
  - <artifact uid or name>
- Tokens:
  - <token>

## [M] GATES
- PASS: [<conditions met>]
- FAIL: [<if failed>]
- GAP: [<if missing>]
- NEXT: "го"
