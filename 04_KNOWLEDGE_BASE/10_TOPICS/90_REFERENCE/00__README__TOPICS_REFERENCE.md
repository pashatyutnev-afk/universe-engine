# TOPICS — REFERENCE (README) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/00__README__TOPICS_REFERENCE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 90_REFERENCE
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.REF.001
OWNER: SYSTEM
ROLE: Orientation for REFERENCE topics scope: what reference modules live here (glossary, dictionaries, quick refs), how they are used, and what must NOT be stored here (no navigation authority, no raw link dumps).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created REFERENCE topics realm README: scope boundaries, usage patterns, and roadmap to populate the folder with high-signal reference modules."
- REASON: "Folder was empty; reference realm must be structured to prevent turning into a link dump."
- IMPACT: "Reference knowledge becomes accessible and reusable across domains."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.REF.README.001

---

## 0) PURPOSE (KB)
This realm contains universal “reference” knowledge modules that support all domains:
- glossaries and controlled vocabularies
- quick reference tables and checklists (when they are reference-style)
- naming/format conventions for domain artifacts (not governance laws)
- micro-dictionaries for recurring terms (audio, camera, narrative)

Reference modules are:
- compact
- stable
- reusable across many packs and topics

---

## 1) WHAT BELONGS HERE / WHAT DOES NOT
### BELONGS (IN-SCOPE)
- Glossary: term → definition → usage notes
- Dictionaries: controlled vocabulary sets (domain terms)
- Quick refs: compact tables (shot types, common mix issues, etc.)
- “Cheat sheets”: short high-signal reminders
- Canonical “term disambiguation” (avoid confusion between similar terms)

### DOES NOT BELONG (OUT-OF-SCOPE)
- RAW link registries / navigation maps (master index only)
- long tutorials (belongs to domain TOPIC/PLAYBOOK)
- governance laws/policies (belongs to 00_KB_GOVERNANCE)
- random web links without ingestion/provenance
- opinion dumps (“best of internet”) without structure

---

## 2) HOW ENTITIES USE REFERENCE TOPICS (DETERMINISTIC)
Use reference modules when:
- you need consistent term meanings
- you need a quick lookup for a repeated decision
- you need to avoid vocabulary drift across entities/packs

Do not use reference modules as:
- rules that override governance
- replacements for measurable gates

Always:
- load minimal set
- emit RUN_TRACE with UID-only sources

---

## 3) FILL PLAN (ROADMAP: WHAT FILES WE MUST CREATE)
Roadmap list (not navigation authority):

### P1 — Universal glossaries
- GLOSSARY__AUDIO_MIX_MASTER_TERMS
- GLOSSARY__CINEMATOGRAPHY_SHOT_TERMS
- GLOSSARY__NARRATIVE_STRUCTURE_TERMS

### P1 — Quick refs used constantly
- QUICKREF__COMMON_FAILURE_MODES (cross-domain)
- QUICKREF__PASS_REWORK_FAIL_INTERPRETATION
- QUICKREF__QUALITY_SIGNAL_HEURISTICS (labeled as HEURISTIC)

### P2 — Controlled vocab for prompts/labels
- DICT__PROMPT_TOKENS_STYLE (labeled; not “truth”)
- DICT__GENRE_LABELS (where allowed)

### P2/P3 — Domain disambiguation
- DISAMBIG__HOOK_VS_CHORUS_VS_DROP
- DISAMBIG__SCENE_BEAT_VS_TURNING_POINT

---

## 4) STRUCTURE RULES FOR REFERENCE MODULES
- Prefer DICTIONARY / TOPIC (reference-style) / CHECKLIST (reference-style).
- Keep entries short and consistent.
- If derived from web sources:
  - use provenance/source record discipline (do not paste large text).
- Use canonical tags when applicable.

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- this realm becomes a link dump
- this realm becomes a second navigation index (RAW registries)
- reference modules turn into long tutorials without split
- external content is copied in large chunks without provenance

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: KB governance rules apply everywhere
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: trace discipline for any KB-driven run
- XREF: UE.KB.PROC.GAP_HANDLING.066 | WHY: missing reference knowledge should trigger gap handling, not invention

--- END.
