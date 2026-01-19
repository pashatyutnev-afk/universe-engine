# PIPELINE REGISTRY (SYSTEM LAW)

FILE: 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md
SCOPE: Universe Engine (All volumes)
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY
REGISTRY_TYPE: PIPELINE
LEVEL: L1
MODE: REPO (USAGE-ONLY, NO-EDIT)
ROLE: Canonical registry of pipeline identifiers, pipeline purposes, and allowed invocation patterns. Defines how pipelines are referenced and validated across the system.
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.1
UID: UE.LAW.PIPELINE.REG.001
OWNER: SYSTEM

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "DOC CONTROL compliance: added LEVEL, normalized DOC_TYPE, kept semantics; header aligned for auditable registry."
- REASON: "Mandatory base fields must exist; DOC_TYPE must be unambiguous for tooling."
- IMPACT: "Registry becomes parse-stable and consistent with System Law and Standards."
- CHANGE_ID: UE.CHG.2026-01-20.LAW.PIPELINE.REG.001

---

## 0) PURPOSE (LAW)
This document is the canonical **PIPELINE REGISTRY** for Universe Engine.

It defines:
- what a pipeline is in this system;
- how pipelines are referenced (ID/UID);
- minimal fields a pipeline definition must expose;
- enforcement rules and stop conditions for pipeline execution and referencing.

---

## 1) DEFINITIONS (LAW)

### 1.1 Pipeline
A **pipeline** is a deterministic, ordered set of steps that:
- starts from a declared entrypoint (usually SPC/ORC),
- produces one or more artifacts,
- includes mandatory gates (CTL/VAL/QA),
- ends with signoff (DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC).

### 1.2 Registry role
This registry is **not** the pipeline executor.
It is the source of truth for:
- pipeline identifiers and their meaning,
- the minimal interface contract required for any pipeline document.

---

## 2) PIPELINE IDENTIFIERS (LAW)

### 2.1 ID format
A pipeline can be referenced by:
- `PIPELINE_ID` (human-readable stable ID), and/or
- `UID` (system-level canonical identifier).

Recommended `PIPELINE_ID` pattern (stable, ASCII):
- `PL.<DOMAIN>.<NAME>.<NNN>`
Examples:
- `PL.CORE.BOOT.001`
- `PL.SCENE.PIPELINE.001`
- `PL.MUSIC.ALBUM_TO_TRACK.001`

### 2.2 UID format
Pipeline entities/documents MUST also follow global UID rules.
This registry uses:
- `UE.LAW.PIPELINE.REG.001` for the registry itself,
and pipeline documents should use their own UIDs under the system UID policy.

---

## 3) MINIMUM PIPELINE CONTRACT (LAW)

Any pipeline document (usually an ORC, sometimes SPC/ENG) MUST expose:

### 3.1 Purpose
- One paragraph: what it does and for what outputs.

### 3.2 Inputs (minimum)
- task text / user intent
- required links / required entities
- scope boundaries

### 3.3 Steps (ordered)
- numbered steps with clear handoffs:
  - SPC → ORC → ENG → CTL/VAL → QA → PACKAGING → SIGNOFF

### 3.4 Gates
- explicit placement of:
  - `READINESS_CHECK_CTL`
  - relevant `VAL`
  - relevant `QA`
  - `DOC_CONTROLLER_SPC` signoff

### 3.5 Outputs
- artifact types produced
- naming rules
- storage placement rules (where applicable)

### 3.6 Stop conditions
Only:
- RAW missing
- marker not confirmed
- input absent

---

## 4) ENFORCEMENT RULES (LAW)

### 4.1 No guessing
Pipelines must not reference non-RAW paths as authoritative.
Navigation must follow RAW-only constraints.

### 4.2 Single entrypoint
No pipeline runs outside the single runtime entrypoint:
- `START_UNIVERSE_ENGINE` (entrypoint runbook)

### 4.3 Deterministic routing
If routing is ambiguous:
- default to Top Governance SPC routing and select minimal sufficient ORC.

### 4.4 Missing entity duty
If a pipeline requires a missing entity/template:
- log GAP
- propose creation
- provide full entity file via template
- only then continue.

---

## 5) REGISTRY CONTENT — PIPELINES (CATALOG)
This section records known pipeline families and their intent.
(Individual pipeline documents live in their respective realms.)

### 5.1 Core runtime pipelines
- BOOT sequence (startup gating and law loading)
- Canon change management flow
- Index integrity checks

### 5.2 Production pipelines (examples)
- Scene pipeline (scene pack + gates)
- Music factory pipeline (group → album → tracks → release pack)
- KB ingestion pipeline (sources → modules → connectors → QA)

### 5.3 Governance pipelines
- Audit logging pipeline
- Dependency registry updates
- Release note compilation

---

## 6) CHANGE CONTROL (LAW)
Any modification of pipeline definitions or this registry must:
- follow the Canon Protocol and Change Management Protocol,
- preserve stable IDs,
- update CHANGE_NOTE and CHANGE_ID.

--- END.
