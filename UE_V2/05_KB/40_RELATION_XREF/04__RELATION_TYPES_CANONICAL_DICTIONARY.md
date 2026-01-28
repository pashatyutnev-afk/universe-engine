# KB — RELATION TYPES (CANONICAL DICTIONARY)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/04__RELATION_TYPES_CANONICAL_DICTIONARY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: DICTIONARY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.DICT.REL_TYPES.004
OWNER: SYSTEM
ROLE: Canonical vocabulary (strict enum) of allowed relation types for KB modules and cross-maps. Prevents relation drift, enables deterministic linking and automated checks.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced canonical dictionary of relation types (REL) with strict meanings, allowed directions, and usage rules."
- REASON: "If relation words drift, maps become non-executable and automation cannot reason about dependencies."
- IMPACT: "All KB modules and maps use the same relation vocabulary; enables audits and dependency graphing."
- CHANGE_ID: UE.CHG.2026-01-14.KB.DICT.004

---

## 0) PURPOSE (KB)
Define the only allowed relation types (REL).
- Strict meanings
- Allowed direction (A → B)
- Recommended usage patterns
- Hard fail conditions for incorrect relations

This DICTIONARY does not contain navigation links.
Navigation is performed via KB master index (RAW-only).

---

## 1) ABSOLUTE RULES
1.1 STRICT ENUM ONLY
- Only relation types listed in Section 2 are allowed.
- Any custom/unknown relation type is invalid.

1.2 DIRECTION MATTERS
- Each relation has a direction: SOURCE → TARGET.
- Inverting direction changes meaning and may be invalid.

1.3 NO URL / NO NAV LINKS
- Relations reference objects by local labels or UID (depending on module standard).
- Do not embed URLs as “relations”.

---

## 2) CANONICAL REL TYPES (ENUM)
### Core dependency relations
REL: depends_on
- Meaning: SOURCE requires TARGET to work correctly.
- Direction: A depends_on B  =>  A requires B
- Use when: method/standard requires another module as prerequisite.

REL: requires
- Meaning: SOURCE must include TARGET as mandatory input/step.
- Direction: A requires B  =>  A cannot run without B
- Note: stronger than depends_on; use sparingly.

REL: complements
- Meaning: TARGET improves SOURCE but is not strictly required.
- Direction: A complements B  =>  B is a useful add-on for A.
- Use when: optional deepening pack.

REL: alternative_to
- Meaning: TARGET can replace SOURCE in a compatible way (mutually exclusive in a run).
- Direction: A alternative_to B  =>  choose A or B, not both.
- Use when: two methods solve the same problem differently.

### Mapping / cross-reference relations
REL: maps_to
- Meaning: SOURCE (label) maps to TARGET (label).
- Direction: A maps_to B
- Use for: scope maps, task maps, label translations.

REL: references
- Meaning: SOURCE mentions TARGET as supporting reference (non-dependency).
- Direction: A references B
- Use when: background material or citation-like pointer.

REL: governed_by
- Meaning: SOURCE is controlled by TARGET rule/policy.
- Direction: A governed_by B
- Use when: a module must comply with a policy.

REL: constrained_by
- Meaning: SOURCE is limited by TARGET constraints (caps, bans, thresholds).
- Direction: A constrained_by B
- Use when: constraints are enforced.

REL: validated_by
- Meaning: SOURCE is evaluated by TARGET validator/QA gate.
- Direction: A validated_by B
- Use when: validator defines pass/fail checks.

REL: produces
- Meaning: SOURCE produces TARGET as an output artifact/module.
- Direction: A produces B
- Use for: pipelines/workflows producing packs or variants.

REL: part_of
- Meaning: SOURCE is a component of TARGET larger system.
- Direction: A part_of B
- Use for: module grouping and hierarchies.

REL: supersedes
- Meaning: SOURCE replaces TARGET (TARGET becomes deprecated).
- Direction: A supersedes B  =>  A is new canon, B deprecated.
- Use for: deprecation workflow.

REL: deprecated_by
- Meaning: SOURCE is deprecated by TARGET (reverse pointer).
- Direction: A deprecated_by B  =>  A is old, B is new.
- Use only when keeping an explicit pointer from old to new.

---

## 3) USAGE RULES (HOW TO CHOOSE)
### Rule A — Prefer depends_on
If the module needs another module to operate, use depends_on.

### Rule B — Use requires only for hard prerequisites
Only when failure is guaranteed without the target.

### Rule C — complements for “nice-to-have”
Do not overuse; keep optional list short.

### Rule D — governed_by for policies
Policies/laws should govern modules that must follow them.

### Rule E — supersedes/deprecated_by pair
When replacing:
- New module: REL: supersedes -> old
- Old module: REL: deprecated_by -> new
(keeps graph navigable)

---

## 4) RELATION FORMAT (STANDARD)
Inside modules:
REL:
- REL: <rel_type> -> <target label or UID> | WHY: <short reason>

Notes:
- Target should be a stable identifier in that module's standard (UID-only if module requires UID-only).
- Keep WHY concise.

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- relation type not in enum
- direction is used with wrong meaning (e.g., “B depends_on A” when A is prerequisite)
- using relations as navigation (URL as relation)
- mixing “alternative_to” with “depends_on” between same pair without explicit reason
- using supersedes without deprecation handling

---

## 6) EXAMPLES
Example 1 (dependency):
- REL: depends_on -> UE.KB.TOPIC.MUSIC.PROMPT_CONTRACT.001 | WHY: prompt contract required to apply phrasebook deltas

Example 2 (governance):
- REL: governed_by -> UE.KB.TOPIC.META.USAGE.001 | WHY: must follow KB usage protocol

Example 3 (deprecation):
- New: REL: supersedes -> UE.KB.TOPIC.MKT.OLD.010 | WHY: replaced by new packaging standard
- Old: REL: deprecated_by -> UE.KB.TOPIC.MKT.NEW.011 | WHY: new canon module

---

## 7) RELATED
- MAP: UE.KB.MAP.TASK_SCOPE.001
- MAP: UE.KB.MAP.ENTITY_SCOPE.002

--- END.
