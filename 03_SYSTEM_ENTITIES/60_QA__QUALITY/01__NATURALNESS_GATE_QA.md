# QA — NATURALNESS GATE
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/01__NATURALNESS_GATE_QA.md

SCOPE: Universe Engine / QA
ENTITY_GROUP: ENT
CATEGORY: QA
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Gate-контроль естественности: анти-ИИ сигнатуры + правила по классу существа (human/robot/animal/spirit).

UID: UE.ENT.QA.NAT.NATURALNESS_GATE

REFERENCES (SoT):
- Naturalness: `02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md`
- Scene 4Track: `02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md`
- QA Rules: `03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md`

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- PRJ: SCENE_PACK or OUT: OUT_SCENE
- NAT_PROFILE (if present)
PRODUCES:
- QA_REPORT (PASS/FAIL + score)
- ISSUES (S0–S3)
- RED_FLAGS (RF_*)
DEPENDS_ON:
- []
OUTPUT_TARGET:
- LOG

---

## REQUIRED CHECKS (MANDATORY)
S0 FAIL if:
- detected strong AI trace red flags (RF_TXT_* etc) that break NAT_PROFILE limits
- entity behavior breaks ENTITY_CLASS rules (e.g., HUMAN acts robotic without reason) in final output

S1 FAIL if:
- multiple red flags present (pattern)
- tone/style inconsistent with STYLE_MODE (if provided)

S2 WARN if:
- minor genericness / minor symmetry / minor over-explaining

---

## REPORT FORMAT (MANDATORY)
RESULT: <PASS|FAIL>
TARGET_UID: <if known else NONE>
SCORE: <0..100>
ISSUES:
- CODE
- SEVERITY
- MESSAGE
- FIX_SUGGESTION
RED_FLAGS:
- <RF_CODE>

---

## RELATIONS (MANDATORY)
CALLS: []
CONSUMES: [PRJ, OUT]
PRODUCES: [LOG]
DEPENDS_ON: [SoT standards]
VALIDATES: []
QUALITY_GATES: [OUT/PRJ]
GOVERNS: []
REFERENCES: []

---
END.
