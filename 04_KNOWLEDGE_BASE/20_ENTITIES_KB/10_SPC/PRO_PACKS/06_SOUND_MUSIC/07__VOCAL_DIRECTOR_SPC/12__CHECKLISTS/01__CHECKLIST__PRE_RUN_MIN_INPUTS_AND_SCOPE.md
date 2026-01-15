# SPC PRO PACK — CHECKLIST (01) — PRE-RUN: MIN INPUTS + SCOPE (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/12__CHECKLISTS/01__CHECKLIST__PRE_RUN_MIN_INPUTS_AND_SCOPE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CHECKLIST
CHECKLIST_CLASS: PRE_RUN
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CHK.VOCAL_DIRECTOR.PRE_RUN.001
OWNER: SYSTEM
ROLE: Pre-run operational checklist: verify minimum inputs and scope boundaries before starting any VOCAL_DIRECTOR work. Designed to prevent guessing and scope violations.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PRE-RUN checklist for VOCAL_DIRECTOR: min inputs + scope + stop conditions."
- REASON: "Most failures originate from missing inputs or scope drift early in the run."
- IMPACT: "Cleaner pipeline runs; fewer reworks."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CHK.VD.PRE.001

---

## 0) PURPOSE
Before doing anything:
- confirm minimum inputs exist
- confirm scope boundaries
- know exactly when to stop

Next after checklist:
- run T01 intake → evaluate G1.

---

## 1) MIN INPUTS (MUST HAVE)
[ ] Lyrics present:
    - at least HOOK/CHORUS lines (copy-exact)
[ ] Structure present:
    - section list OR loop profile that identifies hook moment
[ ] Language known (RU/EN/etc.)
[ ] Hook section label identifiable (at least 1 candidate)

Optional (nice-to-have):
[ ] BPM / groove
[ ] vocal mode (rap/sing/mixed)
[ ] reference vibe words (3–5)

STOP if any MUST HAVE is missing.

---

## 2) SCOPE BOUNDARIES (ABSOLUTE)
Forbidden:
[ ] Do NOT rewrite lyrics / replace words
[ ] Do NOT give mix/master plugin chains or DAW recipes
[ ] Do NOT claim ownership over structure/arrangement (escalate instead)

Allowed:
[ ] performance constraints (clarity, articulation, breath, stacking placement)
[ ] principle-level “seat” request (only as escalation notes)

---

## 3) HARD STOP CONDITIONS
Stop the run immediately if:
[ ] Missing lyrics or hook not identifiable
[ ] Any plan requires lyric rewrite to solve (must escalate, not rewrite)
[ ] Any solution drifts into mix/master chain instructions
[ ] Required owner change is needed (arrangement/structure) → escalate (T14)

---

## 4) NEXT ACTION
If all MUST HAVE inputs exist:
- Run T01 INTAKE_NORMALIZER
- Then evaluate G1

If inputs are missing:
- Output GAP request (T01 style) and stop.

---

## 5) TRACE
TRACE:
- CHECKLIST: PRE_RUN
- UID: UE.KB.SPC.CHK.VOCAL_DIRECTOR.PRE_RUN.001
- NEXT: T01 → G1

--- END.
