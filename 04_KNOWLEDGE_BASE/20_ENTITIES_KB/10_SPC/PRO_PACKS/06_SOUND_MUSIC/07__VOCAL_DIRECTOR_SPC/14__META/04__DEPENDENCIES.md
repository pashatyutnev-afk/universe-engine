# SPC PRO PACK — DEPENDENCIES (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/14__META/04__DEPENDENCIES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: DEPENDENCIES
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.DEPENDENCIES.001
OWNER: SYSTEM
ROLE: Notes on operational dependencies for VOCAL_DIRECTOR Pro Pack: what assumptions it relies on (stable block names, gate order, one-axis discipline, escalation format, output pack contracts). Non-authoritative.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Initial dependencies notes created."
- REASON: "Make pack assumptions explicit for maintenance and cross-entity integration."
- IMPACT: "Safer refactors and fewer silent breaks."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.DEPS.001

---

## 0) PURPOSE
This file lists what the VOCAL_DIRECTOR Pro Pack depends on operationally.

It does NOT define new rules. It only records assumptions.

---

## 1) INTERNAL DEPENDENCIES (WITHIN THIS PRO PACK)
- Stable artifact block names (see OUTPUT_PACKS README)
- Canonical assembly order for output packs (MIN/STD/FULL)
- Gate order and definitions (G1..G9)
- Playbook one-axis discipline (PB-01..PB-08)
- Case Library type codes (T1..T9) and mappings

---

## 2) PIPELINE DEPENDENCIES
- Gate sequence is assumed linear:
  - G1 → G2 → G3 → G4 → G5 → G6 → G7 → G8 → G9
- Repairs assume routing tool usage:
  - T15 routes failure type to the correct PB and rerun gates
- Borderline classification assumes:
  - T16 (threshold guide) is used for PASS/REWORK/FAIL consistency

---

## 3) SCOPE / COMPLIANCE DEPENDENCIES
Assumptions:
- No lyric rewrites inside VOCAL_DIRECTOR deliverables
- No mix/master plugin chain prescriptions
- Any ownership-bound issue is escalated (not solved locally)

Remediation dependencies:
- T13 scope audit checklist
- PB-08 compliance one-axis patch

---

## 4) CROSS-ENTITY INTERFACE EXPECTATIONS (NOTES)
When escalation is required (T4/T7/T9 overlaps), the pack expects:
- an owner entity exists for:
  - Lyrics (Lyricist/Songwriter)
  - Arrangement/Seat (Arranger/Producer)
- escalation note format uses:
  - owner
  - section/line_ids
  - problem + evidence
  - request (principles only)
  - must_keep
  - success_criteria
  - next_check (which gate to rerun)

Note:
- This file does not define those owners; it only states the expectation.

---

## 5) PLATFORM PROMPT DEPENDENCIES
Prompt Contracts assume:
- output pack blocks exist to derive constraints from
- platform prompt field model:
  - SUNO/UDIO prompts accept constraints + “avoid” list
  - lyrics are pasted as-is by user (no edits)

---

## 6) MAINTENANCE DEPENDENCIES
Any refactor must preserve:
- stable block names (or provide migration notes)
- gate definitions and pass/fail thresholds
- playbook IDs and filenames (PB-01..PB-08)
- case IDs and type codes (T1..T9)

---

## TRACE
TRACE:
- DOC: DEPENDENCIES
- UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.DEPENDENCIES.001

--- END.
