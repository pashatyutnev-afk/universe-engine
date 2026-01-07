# ORC ENTITY — TEMPLATE
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_ENTITY.md

SCOPE: Universe Engine / ORC Template
ENTITY_GROUP: ENT
CATEGORY: ORC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Шаблон оркестратора: контракт + пайплайн шагов + checkpoint’ы.

---

## 0) HEADER (REQUIRED)
UID: <UE.ENT.ORC.<FAMILY>.<NAME>>
FAMILY: <GEN|PROD|GOV|QLT>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <1.0>
OWNER: <SYSTEM|YOU>
ROLE: <что оркестратор делает одним предложением>

---

## 1) PURPOSE (REQUIRED)
Кратко:
- что именно он оркестрирует
- какой продукт/слой обслуживает (PRJ/OUT/AST/KB)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- []
PRODUCES:
- []
DEPENDS_ON:
- []
OUTPUT_TARGET:
- <PRJ|OUT|AST|KB>

---

## 3) PIPELINE (MANDATORY)
### STEPS
1) STEP_ID: 01
    NAME: <...>
    EXECUTOR_UID: <UE.ENT.ENG... | UE.ENT.SPC... | UE.ENT.CTL... | UE.ENT.VAL... | UE.ENT.QA...>
    CONSUMES: []
    PRODUCES: []
    GATE: <NONE|VAL|QA|CTL>
    FAIL_SEVERITY: <S0|S1|S2|S3>
    HANDOFF_TARGET: <KB|PRJ|AST|OUT>
    NOTES: ""

(добавляй шаги по аналогии)

---

## 4) CHECKPOINTS (REQUIRED)
- CHECKPOINT_01: <описание точки, где нужно остановиться>
- CHECKPOINT_02: ...

---

## 5) FAIL POLICY (REQUIRED)
- S0: стоп пайплайна
- S1: разрешено продолжать, но фиксировать
- S2: предупреждение
- S3: заметка

---

## 6) NOTES (OPTIONAL)

---
END.
