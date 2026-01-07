# QUALITY (QA) — REALM README
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/00__README__QA_REALM.md

SCOPE: Universe Engine / System Entities / Quality
ENTITY_GROUP: ENT
CATEGORY: QA
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Определяет QA: контроль качества результата (естественность/стиль/анти-ИИ следы/согласованность), подключается в ORC как gate.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- ENT Master Index: `03_SYSTEM_ENTITIES/00__INDEX__ALL_ENTITIES.md`

---

## 0) WHAT IS QA
QA (Quality) — сущность оценки результата “как выглядит/звучит/чувствуется”.

QA проверяет:
- naturalness (естественность)
- consistency (консистентность мира/персонажей/тона)
- anti-AI traces (сигнатуры ИИ в речи/тексте)
- style adherence (жанр/тон/стилистические рамки)
- multi-track integrity (если используем 4 дорожки сцены)

QA не валидирует структуру законами (это VAL).
QA не принимает доменных решений (это SPC/ENG).
QA не управляет пайплайном (это ORC/CTL).

---

## 1) EXISTENCE LAW
QA существует только если:
- имеет UID (UE.ENT.QA...)
- зарегистрирован в QA Global Registry

---

## 2) WHAT QA PRODUCES
Типовые выходы QA:
- QA REPORT (PASS/FAIL + score)
- ISSUES LIST (S0–S3)
- FIX SUGGESTIONS (как улучшить)
- OPTIONAL: RED FLAGS (признаки “палево ИИ”)

---

## 3) LINKS
- Rules: `01__RULES__QA.md`
- Registry: `02__INDEX_ALL_QA.md`
- Create Flow: `03__CREATE_FLOW__QA.md`
- Templates: `00__TEMPLATES/`

---
END.
