# FILE: UE_V2/12_LOG/00__LOG_RULES.md
SCOPE: UE_V2
LAYER: 12_LOG
DOC_TYPE: RULES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LOG.RULES.001
OWNER: SYSTEM
TITLE: LOGGING RULES (MINIMAL, USEFUL)

## MARKERS
- [M] PURPOSE
- [M] WHAT_TO_LOG
- [M] WHEN_TO_LOG
- [M] FORMAT_RULES
- [M] RETENTION
- [M] PRIVACY

## [M] PURPOSE
Logs exist to make runs auditable and reproducible with minimum noise.

## [M] WHAT_TO_LOG
- RUN header: timestamp, task id/name, mode, scope
- INPUTS: user task text reference (short), provided RAW links list
- RESOURCES USED: each RAW opened + MARKER FOUND
- ROUTING: selected entities (names only), selected pipeline code (P.*)
- GATES: STOP/GAP/FAIL/OK status with reason codes
- DELIVERABLES: produced artifact ids/names (short)
- DIFF NOTE (optional): what changed vs last run (1–3 lines)

## [M] WHEN_TO_LOG
- always: BOOT completion
- always: any STOP
- always: any GAP creation proposal
- always: any ACCEPT / SIGNOFF
- optional: intermediate drafts (only if needed for audit)

## [M] FORMAT_RULES
- log must be short: prefer codes (LEX) over prose
- never paste full docs into logs
- keep “Resources Used” list deterministic:
  - RAW + marker title exact
- use stable reason codes (see 00_BOOT/07__FAIL_CODES)

## [M] RETENTION
- keep: last 30 runs per domain, last 10 GAP events per family
- keep: all SIGNOFF logs (permanent)

## [M] PRIVACY
- no personal data
- no external account tokens/keys
- no full lyrics or copyrighted long text dumps
