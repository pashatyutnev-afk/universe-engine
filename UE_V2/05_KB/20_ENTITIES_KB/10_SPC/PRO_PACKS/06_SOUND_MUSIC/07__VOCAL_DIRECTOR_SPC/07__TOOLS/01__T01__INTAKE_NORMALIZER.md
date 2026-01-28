# SPC PRO PACK — TOOL (T01) — INTAKE_NORMALIZER (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/01__T01__INTAKE_NORMALIZER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T01
TOOL_NAME: INTAKE_NORMALIZER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T01.INTAKE_NORMALIZER.001
OWNER: SYSTEM
ROLE: Normalizes minimal inputs into stable blocks for downstream gates/tools. Detects missing fields and outputs a deterministic GAP request. Does not invent data.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T01 INTAKE_NORMALIZER for VOCAL_DIRECTOR."
- REASON: "Downstream tools require stable inputs; missing fields must stop the run deterministically."
- IMPACT: "Cleaner pipeline starts; fewer guessing failures."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T01.001

---

## 0) PURPOSE
Convert raw user input into stable intake artifacts:
- MIN_INPUTS_CHECK
- HOOK_SECTION_LABEL
- GAP_REPORT
- NEXT_STEP

This tool supports Gate:
- G1 INPUT READINESS

---

## 1) INPUTS (ACCEPTED)
T01 accepts any subset of:
- lyrics text (full or partial)
- section labels (Verse/Chorus/Bridge) OR a structure description
- language label (RU/EN/…)
- platform prompt text (optional)
- any notes (bpm/genre/vibe)

Rule:
- If an input is not present, mark it as missing (do not guess).

---

## 2) OUTPUT BLOCKS (STABLE NAMES)
T01 MUST output these blocks (always, even on GAP):

### MIN_INPUTS_CHECK
Fields:
- LYRIC_DRAFT_PRESENT: YES/NO
- SECTION_STRUCTURE_PRESENT: YES/NO
- LANGUAGE_PRESENT: YES/NO
- HOOK_SECTION_IDENTIFIABLE: YES/NO

### HOOK_SECTION_LABEL
Fields:
- value: "<label or N/A>"
- why: "<1 line>"
- candidates (optional, max 2):
  - "<candidate 1>"
  - "<candidate 2>"

### GAP_REPORT
Fields:
- STATUS: OK | GAP
- missing_fields:
  - "<field>"
- request_text:
  - "<copy-ready request to user>"
- stop_run: YES/NO

### NEXT_STEP
Fields:
- if GAP: "Request missing fields; rerun T01; then evaluate G1"
- if OK: "Evaluate G1; if PASS proceed to T02/T03"

---

## 3) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Detect lyrics presence
- If any lyric lines exist → LYRIC_DRAFT_PRESENT=YES else NO

Step 2 — Detect structure presence
- If user provides section labels OR a clear structure description → SECTION_STRUCTURE_PRESENT=YES else NO

Step 3 — Detect language presence
- If language label exists OR language is explicitly stated by user → LANGUAGE_PRESENT=YES
- If not explicitly stated, do NOT infer; set NO

Step 4 — Identify hook section
- If user labels a chorus/hook OR structure implies a hook location clearly:
  - HOOK_SECTION_IDENTIFIABLE=YES
  - HOOK_SECTION_LABEL.value = provided label (preferred) OR best candidate
- If ambiguous:
  - HOOK_SECTION_IDENTIFIABLE=NO
  - Provide candidates (max 2) only if derivable from provided structure (no guessing)

Step 5 — Create GAP_REPORT if any MUST HAVE is missing
MUST HAVE fields for OK:
- LYRIC_DRAFT_PRESENT=YES
- SECTION_STRUCTURE_PRESENT=YES
- LANGUAGE_PRESENT=YES
- HOOK_SECTION_IDENTIFIABLE=YES

If any is NO:
- GAP_REPORT.STATUS=GAP
- GAP_REPORT.stop_run=YES
- request_text asks only for missing fields

If all YES:
- GAP_REPORT.STATUS=OK
- GAP_REPORT.stop_run=NO

---

## 4) STOP CONDITIONS (HARD)
Stop_run must be YES if:
- lyrics missing
- structure missing
- language not explicitly provided
- hook cannot be identified from provided structure

---

## 5) EXAMPLE REQUEST_TEXT (TEMPLATE)
Use this exact style (fill missing parts only):

"Нужны минимальные входы для вокального пакета:
1) Текст (хотя бы припев/хук),
2) Структура (Verse/Chorus/Bridge или описание где хук),
3) Язык (RU/EN),
4) Что считать хуком (название секции).
Пришли это — и я соберу пакет."

---

## 6) TRACE
TRACE:
- TOOL: T01
- OUTPUTS: MIN_INPUTS_CHECK, HOOK_SECTION_LABEL, GAP_REPORT, NEXT_STEP
- SUPPORTS_GATE: G1

--- END.
