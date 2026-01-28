# ORC — SCENE PIPELINE
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__SCENE_PIPELINE_ORC.md

SCOPE: Universe Engine / ORC
ENTITY_GROUP: ENT
CATEGORY: ORC
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Боевой оркестратор сцены: собирает SCENE_PACK (4TRACK), прогоняет gates (CTL→VAL→QA), собирает финальный OUT_SCENE.

UID: UE.ENT.ORC.PRD.SCENE_PIPELINE

REFERENCES (SoT):
- Marking: `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`
- Rel/Xref: `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md`
- Storage Map: `02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md`
- Scene 4Track: `02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md`
- Naturalness: `02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md`
- VAL Rules: `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/01__RULES__VAL.md`
- QA Rules:  `03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md`

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- SCENE_BRIEF (goal/constraints)
- WORLD_CONTEXT (optional)
- CHARACTER_CONTEXT (optional)
PRODUCES:
- SCENE_PACK (4TRACK)
- OUT_SCENE (final merged scene)
- LOG: pipeline report
DEPENDS_ON:
- UE.ENT.VAL.* (doc/format validation)
- UE.ENT.QA.* (naturalness/style quality)
OUTPUT_TARGET:
- OUT (final)
- PRJ (scene pack)
- LOG (reports)

---

## PIPELINE OVERVIEW
S1) Build SCENE_PACK (4TRACK)  -> PRJ
S2) CTL Gate: readiness check  -> PASS/FAIL
S3) VAL Gate: structure/marking -> PASS/FAIL
S4) QA Gate: naturalness/quality -> PASS/FAIL
S5) Merge -> OUT_SCENE          -> OUT
S6) Log results                 -> LOG

---

## STEPS (CANON ORDER)

### STEP S1 — SCENE_PACK BUILD (4TRACK)
INPUT:
- SCENE_BRIEF + constraints
ACTION:
- produce SCENE_PACK with NAR/VIS/SND/MOT tracks (see 4TRACK standard)
OUTPUT:
- PRJ: SCENE_PACK v1

GATE: NONE

---

### STEP S2 — CTL READINESS GATE
ACTION:
- check that all 4 tracks exist and have >=1 EVENT
- check mandatory META fields present
OUTPUT:
- readiness PASS/FAIL + missing list
GATE:
- CTL (readiness)

FAIL RULE:
- missing any track => S0 FAIL

---

### STEP S3 — VAL STRUCTURE GATE
ACTION:
- validate SCENE_PACK format + required headers if stored as doc
- validate XREF format rules if links exist
OUTPUT:
- VAL report PASS/FAIL
GATE:
- VAL (format/doc-control)

FAIL RULE:
- invalid format/marking => S0 FAIL

---

### STEP S4 — QA NATURALNESS/QUALITY GATE
ACTION:
- apply NATURALNESS_GATES (anti-ai traces + class rules)
- apply style/consistency checks as configured
OUTPUT:
- QA report PASS/FAIL + score
GATE:
- QA (naturalness)

FAIL RULE:
- S0 FAIL if red flags break class/style

---

### STEP S5 — MERGE TO OUT_SCENE
ACTION:
- merge order: NAR -> VIS -> MOT -> SND
OUTPUT:
- OUT: OUT_SCENE (final)
REQUIRED CONTENT:
- readable scene text
- optional shot notes / sound cues / motion cues

GATE: NONE

---

### STEP S6 — PIPELINE LOG
ACTION:
- write short summary:
  - what passed/failed
  - links to reports
OUTPUT:
- LOG: pipeline report

---

## RELATIONS (MANDATORY)
CALLS: [ENG, SPC, CTL, VAL, QA]
CONSUMES: [PRJ inputs, KB context]
PRODUCES: [PRJ SCENE_PACK, OUT OUT_SCENE, LOG]
DEPENDS_ON: [SoT standards]
VALIDATES: []
QUALITY_GATES: []
GOVERNS: []
REFERENCES: []

---
END.
