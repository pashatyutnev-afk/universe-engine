# Core State Engine
FILE: 02__CORE_STATE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines canonical system state model for ENG (current version, active families, locks, open waivers/risks, work mode) and standardizes system state snapshots used by all downstream work

---

## PURPOSE

Core State отвечает на вопрос:

> “В каком состоянии система ENG прямо сейчас?”

Без этого:
- непонятно, какая версия актуальна
- непонятно, какие семейства активны
- непонятно, где есть waivers/риски
- разные агенты начинают работать по разным “состояниям”

---

## NON-GOALS

- не утверждает изменения (Canon Authority)
- не фиксирует историю (Audit Log)
- не версионирует (Versioning & Memory)
Он задаёт **модель состояния** и стандарт “снимка состояния”.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Global registry version from `00__INDEX_ALL_ENGINES.md`
- Governance decisions (CV/AL/RN pointers)
- Waivers (WV) and Risk Register (RR) entries (if used)
- Locks across files (FIXED/UNFIXED)

### PRODUCES
- SYSTEM STATE SNAPSHOT (SS) artifact
- ACTIVE MAP: which families/engines are active
- OPEN ITEMS MAP: waivers/risks/returns

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

### OUTPUT_TARGET
- Used at the beginning of any large work session / integration
- Downstream engines can reference SS_ID to state what system state they assume

---

## SYSTEM STATE MODEL (CANON)

State состоит из 5 частей:

1) **VERSION STATE**
- current ENG system version (from INDEX)
- last release note id (RN)
- last audit id (AL)
- last verdict id (CV)

2) **ACTIVITY STATE**
- active families list
- active engines list (optional if huge)
- deprecated families/engines list

3) **LOCK STATE**
- which families are FIXED
- which are UNFIXED (in-progress)

4) **OPEN GOVERNANCE ITEMS**
- open waivers (WV)
- open risks (RR)
- returned changes (RETURN) that block work

5) **WORK MODE**
- BUILD mode (actively expanding)
- STABILIZE mode (fixing drift/consistency)
- RELEASE mode (preparing lock/version)
- MAINTENANCE mode (patches only)

---

## REQUIRED CANON ARTIFACT: SYSTEM STATE SNAPSHOT (SS)

### SYSTEM_STATE_SNAPSHOT SCHEMA (CANON)

- SS_ID: SS-ENG-0001
- DATE:
- ENG_VERSION:
- MODE:
  - BUILD | STABILIZE | RELEASE | MAINTENANCE
- LAST_GOVERNANCE_POINTERS:
  - RN_ID:
  - AL_ID:
  - CV_ID:
- ACTIVE_FAMILIES:
  - list of family folder names
- FIXED_FAMILIES:
  - list
- UNFIXED_FAMILIES:
  - list
- OPEN_WAIVERS:
  - list of WV IDs (or NONE)
- OPEN_RISKS:
  - list of RR IDs (or NONE)
- BLOCKERS:
  - list of S0/S1 blockers (or NONE)
- NOTES:
  - max 7 bullets

---

## STATUS POLICY (STANDARD)

### File STATUS field meaning
- ACTIVE: usable and part of canon
- DRAFT: exists but not canon-locked yet (still registered if in INDEX)
- DEPRECATED: still referenced but scheduled for replacement
- ARCHIVED: not in active use; cannot be referenced by new work

Rule:
- If STATUS != ACTIVE, it must be visible in INDEX notes (if you add a notes section later).

---

## LOCK POLICY (INTERPRETATION)

- LOCK: FIXED means “stable contract, safe to build on”
- LOCK: UNFIXED means “may change; downstream must expect drift”

Downstream rule:
- if you rely on UNFIXED engine, you must pin SS_ID or version assumption.

---

## PROCEDURE (HOW TO USE CORE STATE)

1) Read current INDEX VERSION
2) Determine mode (BUILD/STABILIZE/RELEASE/MAINTENANCE)
3) List active families for current goal
4) Identify open waivers/risks that affect work
5) Write SS snapshot (optional but recommended for big sessions)
6) Reference SS_ID in big change packets (CHG) and audits

---

## VALIDATION CHECKLIST

- CS1: SS lists current ENG_VERSION
- CS2: SS has mode set
- CS3: SS lists active families explicitly
- CS4: SS lists open waivers/risks or states NONE
- CS5: If system is in RELEASE mode → CR must be planned

---

OWNER: Universe Engine
LOCK: FIXED
