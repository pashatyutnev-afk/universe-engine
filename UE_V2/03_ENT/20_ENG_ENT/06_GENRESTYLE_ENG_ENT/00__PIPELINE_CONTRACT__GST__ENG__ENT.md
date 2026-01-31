# ENGINE TEMPLATE — GENRE & STYLE ENGINES (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENGINE
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.STYLE.ENGINE.001
OWNER: SYSTEM
ROLE: Stamp template for any Engine inside 06_GENRE_STYLE_ENGINES. Enforces ENG ruleset gates: mini-contract, boundaries, output schemas, blockers, integration.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Created canonical engine template for 06_GENRE_STYLE_ENGINES: deterministic structure + gates + schema requirements."
- REASON: "Stamping requires strict uniform file skeleton."
- IMPACT: "All style engines become comparable, auditable, and non-overlapping."
- CHANGE_ID: UE.CHG.2026-01-08.TPL.STYLE.ENGINE.001

---

## HOW TO USE (STAMP RULE)
1) Copy this template into a new engine file:
   `NN__<ENGINE_NAME>_ENG.md` inside `06_GENRE_STYLE_ENGINES/`
2) Replace all `<PLACEHOLDERS>` with concrete values.
3) Ensure MINI-CONTRACT is concrete (no vague artifacts).
4) Ensure BOUNDARIES are explicit (IN/OUT + collision rule).
5) Ensure every PRODUCES has a minimal output schema in section 6.
6) Run Gates mentally: G0..G4. If any FAIL → file is INCOMPLETE.

---

# <ENGINE TITLE> ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/<NN__ENGINE_NAME_ENG.md>
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.ENG.STYLE.<ENGINE>.NNN>
OWNER: <SYSTEM|TEAM|PERSON>
ROLE: <One-sentence: what this engine does deterministically + what primitive it owns.>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|PATCH|HOTFIX>
- SUMMARY: "<What changed>"
- REASON: "<Why>"
- IMPACT: "<System impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) PURPOSE (LAW)
<Define the owned STYLE primitive clearly: what it is, what it is not, and why the system needs it.>
Hard rule:
- MUST be operational and testable: “engine produces X given Y”.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- <List 4–8 explicit exclusions to prevent overlap.>
- <Include collision notes to adjacent engines (tone vs atmosphere vs symbolism etc.).>

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- <1..5 concrete input artifact types, example: EVENT_PACK, SCENE_PACK, CHARACTER_PROFILE, WORLD_LAWSET, STYLE_BRIEF>
- <No vague words like idea/thing>

PRODUCES:
- <1..5 concrete output artifact types, example: TONE_PROFILE, ATMOSPHERE_LAYER_SPEC, SYMBOL_MAP, SENSORY_DETAIL_BANK>
- <Every produced artifact MUST have a schema in section 6>

DEPENDS_ON:
- [<engine pointers or []>]
- <If depends on other families, list them. Hidden dependencies forbidden.>

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/<STYLE|GENRE>/...
OPTIONAL:
- KB/<...> (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- <Term 1>: <strict definition>
- <Term 2>: <strict definition>
- <Include any controlled vocabulary enums you introduce.>

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- <Bullets: what this engine owns>

OUT OF SCOPE (HARD):
- <Bullets: what it never does>

COLLISION RULE:
- If request is <X> → route to <Other Engine>
- If request is <Y> → route to <Other Family>
- <At least 3 collision rules; keep them precise.>

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: <testable rule>
R2 (HARD) MUST: <testable rule>
R3 (HARD) FORBIDDEN: <what is not allowed>
R4 (SOFT) SHOULD: <quality rule>
R5 (HARD) MUST: <validation rule>

Allowed enums (if any):
- <ENUM_NAME>: {<A|B|C>}

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)
> For EACH item in PRODUCES define one artifact schema block.

ARTIFACT: <ARTIFACT_NAME_1>
- MUST:
  - <field>
  - <field>
- OPTIONAL:
  - <field>
- VALIDATION:
  - <checks that make it deterministic>
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/<path>/<file>

---

ARTIFACT: <ARTIFACT_NAME_2>
- MUST:
  - <field>
- OPTIONAL:
  - <field>
- VALIDATION:
  - <checks>
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/<path>/<file>

---

## 7) PIPELINE (DETERMINISTIC)
1) <Step 1: load inputs>
2) <Step 2: transform>
3) <Step 3: validate>
4) <Step 4: emit outputs>

Notes:
- No “magic”: each step must be reproducible from inputs.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: <hard fail condition>
- S0-2: <hard fail condition>
- S0-3: <hard fail condition>
- S0-4: <hard fail condition>
- S0-5: <hard fail condition>

If any S0 triggers → output is INVALID.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream (typical):
- <engines that provide inputs>

Downstream (typical):
- <engines that consume outputs>

Compatibility notes:
- <How to avoid overlap and enforce collision rules.>

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  06_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md
- Family template:
  06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

--- END.

LOCK: <OPEN|FIXED>
