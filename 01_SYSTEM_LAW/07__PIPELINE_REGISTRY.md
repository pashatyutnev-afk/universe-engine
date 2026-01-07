# UNIVERSE ENGINE — PIPELINE REGISTRY (LAW)
FILE: 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

SCOPE: Universe Engine
LAYER: SYSTEM LAW
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Закон-реестр пайплайнов. Фиксирует какие пайплайны существуют, их входы/выходы, gates и канонических исполнителей (ORC/CTL/VAL/QA). Если пайплайна нет в реестре — он не считается каноническим.

---

## 0) PURPOSE
Pipeline Registry нужен чтобы:
- у системы были “официальные конвейеры”
- все сущности понимали, какой pipeline является каноном
- входы/выходы и quality gates были стандартными и повторяемыми

---

## 1) PIPELINE ID (CANON)
Каждый пайплайн имеет ID:

PL.<DOMAIN>.<NAME>

DOMAIN:
- NAR (нарратив/сцены/сюжет)
- VIS (визуал)
- SND (звук)
- PRD (production)
- SYS (системный пайплайн)

NAME: UPPER_SNAKE_CASE

Пример:
- PL.PRD.SCENE_PIPELINE

---

## 2) REGISTRY ROW FORMAT (MANDATORY)
Одна запись:

PIPELINE_ID | STATUS | OWNER | ORCHESTRATOR_UID | INPUTS | OUTPUTS | GATES | SoT | NOTES

Где:
- ORCHESTRATOR_UID: UID ORC, который управляет пайплайном
- INPUTS/OUTPUTS: artifact types из Artifact Schema Registry (ART.*)
- GATES: список UID gates (CTL/VAL/QA)
- SoT: ссылка на pipeline spec (если есть отдельный стандарт)
- NOTES: кратко

---

## 3) PIPELINE EXISTENCE RULE (ABSOLUTE)
> Если pipeline не зарегистрирован здесь — он не считается существующим для системы.

---

## 4) CANON PIPELINES (START SET)

### A) PRODUCTION PIPELINES
PL.PRD.SCENE_PIPELINE | ACTIVE | SYSTEM | UE.ENT.ORC.PRD.SCENE_PIPELINE | [ART.PRJ.SCENE_PACK, ART.DOC.SCENE_BRIEF] | [ART.OUT.OUT_SCENE, ART.LOG.PIPELINE_REPORT] | [UE.ENT.CTL.GEN.READINESS_CHECK, UE.ENT.VAL.DOC.SCENE_PACK_FORMAT, UE.ENT.QA.NAT.NATURALNESS_GATE] | (optional) | Canon scene production line

---

## 5) PIPELINE CHANGE RULE
Любое изменение пайплайна (inputs/outputs/gates/order):
- считается минимум MINOR
- а если ломает совместимость — MAJOR (breaking)
- проходит Canon Protocol

---

## 6) GATE ORDER RULE (RECOMMENDED)
Рекомендуемый порядок gates:
1) CTL readiness (есть ли всё)
2) VAL format (валидность структуры)
3) QA quality (естественность/стиль)

Нарушение порядка допускается только при явной причине.

---

## 7) FINAL LAW
> Pipeline — это контракт производства.  
> Реестр пайплайнов определяет, что считается “официальной линией” системы.

OWNER: Universe Engine  
LOCK: FIXED

---
END.
