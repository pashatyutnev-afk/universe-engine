# 08__KB_SOURCES — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/08__KB_SOURCES.md
SCOPE: KB — SPC Pro Pack — Music Producer — KB Sources
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: KB_SOURCES
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.KB_SOURCES.001
OWNER: SPC (Music Producer)
ROLE: Declares allowed knowledge sources and what is considered “in scope” for Music Producer SPC reasoning. No fantasy.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "KB sources initialized for Music Producer SPC pack."
- REASON: "Prevent invented facts and keep producer outputs arrangement-level."
- IMPACT: "Defines safe references and routing rules."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.SOURCES.001

---

## SOURCE POLICY (LAW)
Producer SPC must rely on:
- provided task inputs
- in-repo standards / protocols / checklists / gates
- controlled internal examples (case library)

Forbidden:
- inventing facts (“fantasy”)
- claiming external rights/clearance
- platform-specific rule claims without repo reference

If external info is needed → route to research/validation role.

---

## PRIMARY IN-REPO SOURCES (RAW)
Allowed baseline references:
- 02_STANDARDS (music schemas, QA gates, prompt contracts, etc.)
- 03_SYSTEM_ENTITIES (role boundaries, pipelines)
- this pack (principles, rubric, playbooks, cases)

---

## ALLOWED “PRODUCTION KNOWLEDGE” (GENERAL)
Allowed:
- high-level arrangement/production concepts (layers, density, transitions, hook spotlight)
Must be expressed as:
- decision-level + testable acceptance
Not as:
- numeric engineering recipes

---

## CASE LIBRARY AS CANONICAL EXEMPLARS
Primary calibration anchors:
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.GOOD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001

---

## WHAT MUST BE CITED (IN TRACE)
When output includes quality claims, include UID references to:
- checklist results
- gate decisions
- rubric scoring (if used)

Minimum trace:
- CHECKLISTS_RUN (uids + PASS/REWORK/FAIL)
- GATES_RUN (uids + PASS/REWORK/FAIL)
- RUBRIC_UID (if scored)

---

## ROUTING RULES (WHEN SOURCES INSUFFICIENT)
Route, do not invent:
- rights/credits → CTL credits/rights policy module
- platform distribution rules → Marketing/Distribution topic modules
- audio engineering → Mix/Master packs
- vocal technique direction → Vocal Director
- prompt writing takeover → Prompt Architect

---

## REQUIRED UID REFERENCES
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001

---
END
