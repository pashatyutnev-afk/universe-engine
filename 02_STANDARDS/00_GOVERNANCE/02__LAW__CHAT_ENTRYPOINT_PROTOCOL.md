# LAW — CHAT ENTRYPOINT PROTOCOL (CANON)

FILE: 02_STANDARDS/00_GOVERNANCE/02__LAW__CHAT_ENTRYPOINT_PROTOCOL.md
SCOPE: Universe Engine (All volumes)
LAYER: 02_STANDARDS
DOC_TYPE: LAW
LAW_TYPE: GOVERNANCE
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.GOV.CHAT_ENTRYPOINT.001
OWNER: SYSTEM
ROLE: Enforce the only allowed task entrypoint (`START_UNIVERSE_ENGINE`) and prevent any execution outside boot-first + snapshot navigation + artifact output law.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: PATCH
- SUMMARY: "Expanded chat entrypoint law: START-only execution + snapshot-only navigation + boot-first discipline + mandatory runtime output format."
- REASON: "Previous file was non-operative (too short) and did not enforce the new runtime system."
- IMPACT: "Any task/chat can now be audited: entry is deterministic, navigation is deterministic, outputs are governed artifacts."
- CHANGE_ID: UE.CHG.2026-01-19.STD.GOV.CHAT_ENTRYPOINT.001

---

## 0) PURPOSE (LAW)
This law defines **how any task is allowed to enter runtime** inside chat.

It exists to enforce:
- **Single entrypoint law** (no side doors).
- **Boot-first discipline** (no execution before core load).
- **Snapshot-only navigation** (no guessing).
- **Output-as-artifact** (no naked content).
- **Auditable chat contract** (stable response blocks).

---

## 1) ABSOLUTE ENTRYPOINT LAW
### 1.1 Allowed entry command (ONLY)
Any task execution is allowed **only** when the user triggers:

- `START_UNIVERSE_ENGINE`

### 1.2 ROOT-INDEX is NOT a runner
ROOT-INDEX is a **link-base snapshot**, not a runbook and not an executor.
- It provides RAW links only.
- It must not be used to “start work”.

### 1.3 No parallel entrypoints
Any alternative “start docs” or ad-hoc chat flows are invalid unless they are pure POINTERs to the canonical entrypoint.

---

## 2) SNAPSHOT NAVIGATION LAW (RUNTIME)
### 2.1 Snapshot-only rule (ABSOLUTE)
During runtime, the system may use RAW links only if they are:
- present in the user-provided **ROOT LINK BASE** snapshot, OR
- explicitly provided by the user in the chat.

### 2.2 Manual refresh only
The snapshot is **not** auto-updated.
If links need refresh — user must provide an updated ROOT-INDEX (or explicit extra RAW links).

### 2.3 No guessing
Guessing paths/URLs outside the snapshot is forbidden.

---

## 3) BOOT-FIRST DISCIPLINE (ABSOLUTE)
No task execution is allowed until `START_UNIVERSE_ENGINE` confirms BOOT completion markers:
- Naming + UID rules loaded
- Doc Control + Index structure loaded
- Entity model loaded
- KB entrypoint loaded

If any marker is not confirmed → STOP: `marker not confirmed`.

---

## 4) TASK ROUTING LAW (WHO MUST TOUCH EVERY TASK)
Every task must:
1) **ENTER** via Top Governance SPC (dispatcher)
2) **ROUTE** through entity assignment (ORC/ENG/CTL/VAL/QA)
3) **EXIT** via verification chain and doc control signoff

Mandatory chain:
- Start: `MACHINE_ARCHITECT_SPC`
- Finish: `READINESS_CHECK_CTL` → relevant `VAL` → relevant `QA` → `DOC_CONTROLLER_SPC` → `MACHINE_ARCHITECT_SPC`

If required entity does not exist → apply GAP protocol (Section 6).

---

## 5) OUTPUT-AS-ARTIFACT LAW (CHAT OUTPUTS)
### 5.1 No naked content
Any outgoing result must be packaged as an **artifact document** under relevant standards/templates:
- tracks / covers / scenes / plans / decisions / passports — all are artifacts.

### 5.2 Doc control is mandatory
Artifact must comply with:
- DOC CONTROL standard
- UID rules
- versioning/change policy
- relevant template of the artifact type

---

## 6) MISSING ENTITY / TEMPLATE DUTY (GAP PROTOCOL)
If routing or packaging requires something that does not exist (entity/template/route doc):
1) Declare GAP (what is missing and why required)
2) Select correct TEMPLATE from system templates
3) Provide **full file** for the missing entity/template
4) Propose registration steps (registry/DB/log)
5) Resume original task only after GAP is handled

---

## 7) CHAT RUNTIME OUTPUT CONTRACT (MANDATORY)
For every run step (and sub-run), the assistant must output **exactly**:

MODE:
RESOURCES USED (USING RAW + MARKER FOUND):
DELIVERABLES:
GATES:

---

## 8) VIOLATIONS (FAIL CONDITIONS)
A run is invalid if it:
- executes without `START_UNIVERSE_ENGINE`
- uses non-snapshot links (or guessed URLs)
- proceeds before BOOT markers are confirmed
- outputs naked content (not an artifact doc)
- skips the mandatory verification chain
- invents entities/templates instead of declaring GAP

---

## 9) INTERFACES (RAW ONLY)
- Runtime entrypoint (`START_UNIVERSE_ENGINE`):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01__START_UNIVERSE_ENGINE.md
- ROOT LINK BASE snapshot:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX__UNIVERSE_ENGINE.md
- System Constitution (highest law):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- Chat protocol:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/02__CHAT_PROTOCOL.md
- Doc control standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

---

## FINAL (LOCK)
This law is FIXED.
Any deviation is a violation until corrected via canon protocol.
