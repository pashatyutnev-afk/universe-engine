# UNIVERSE ENGINE — ARTIFACT SCHEMA REGISTRY (LAW)
FILE: 01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

SCOPE: Universe Engine
LAYER: SYSTEM LAW
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Закон-реестр артефактов. Фиксирует список допустимых типов артефактов (artifacts) и указывает, где живёт их формат (SoT). Если типа нет в реестре — он не существует.

---

## 0) PURPOSE
Artifact Schema Registry нужен чтобы:
- все процессы говорили на одном языке (одни и те же типы входов/выходов)
- не возникало “двух SCENE_PACK” разного вида
- было понятно, что создаёт ORC/ENG/SPC и куда складывается

---

## 1) EXISTENCE RULE (ABSOLUTE)
> Если артефакт-тип не зарегистрирован в этом реестре — он не считается допустимым типом системы.

Любой новый artifact type:
1) сначала регистрируется здесь
2) затем получает SoT-описание формата в STANDARDS
3) затем начинает использоваться сущностями

---

## 2) ARTIFACT TYPE ID (CANON)
Тип артефакта записывается как:

ART.<GROUP>.<NAME>

Где:
- GROUP: DOC | PRJ | KB | AST | OUT | LOG | DB
- NAME: UPPER_SNAKE_CASE

Примеры:
- ART.PRJ.SCENE_PACK
- ART.OUT.OUT_SCENE
- ART.DOC.SCENE_BRIEF
- ART.LOG.PIPELINE_REPORT

---

## 3) REGISTRY ROW FORMAT (MANDATORY)
Одна строка:

ART_TYPE | PURPOSE | PRODUCED_BY | CONSUMED_BY | SoT_SCHEMA | STORAGE_GROUP | NOTES

Где:
- PRODUCED_BY / CONSUMED_BY: ENG/ORC/SPC/CTL/VAL/QA (или конкретный UID если нужно)
- SoT_SCHEMA: путь на стандарт (без дублей)
- STORAGE_GROUP: KB/PRJ/OUT/AST/LOG/DB

---

## 4) CANON ARTIFACT REGISTRY (START SET)

### A) SCENE PIPELINE ARTIFACTS
ART.PRJ.SCENE_PACK | Сборка сцены в 4 дорожках | ORC | CTL/VAL/QA/ORC | `02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md` | PRJ | input to merge  
ART.OUT.OUT_SCENE | Финальный текст сцены (+опц. заметки) | ORC | OUT consumers | `02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md` | OUT | merged result  
ART.DOC.SCENE_BRIEF | Цель/ограничения сцены | PRJ/KB | ORC/ENG/SPC | `02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md` | PRJ | minimal brief  
ART.LOG.PIPELINE_REPORT | Отчёт прогонов gates | ORC/CTL/VAL/QA | humans/system | `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md` | LOG | pass/fail + issues  

### B) CONTEXT ARTIFACTS (OPTIONAL INPUTS)
ART.KB.WORLD_CONTEXT | Справка о мире | KB | ORC/ENG/SPC | `02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md` | KB | optional  
ART.KB.CHARACTER_CONTEXT | Справка о персонажах | KB | ORC/ENG/SPC | `02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md` | KB | optional  
ART.KB.STYLE_CONTEXT | Справка о стиле/тональности | KB | QA/ORC | `02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md` | KB | optional  

### C) GOVERNANCE / CONTROL ARTIFACTS
ART.DOC.STANDARD | Стандарт SoT документ | SYSTEM | all | `02_STANDARDS/01_SPECIFICATIONS/*` | STD | SoT  
ART.DOC.INDEX | Индекс/реестр | SYSTEM | all | `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md` | STD | navigation  
ART.DOC.ENTITY | ENT файл | SYSTEM | all | `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md` | ENT | must have mini-contract  

---

## 5) NO DUPLICATION RULE
Запрещено:
- создавать новый тип артефакта, если уже есть эквивалентный
- называть один и тот же тип разными именами

Если нужно расширение:
- добавляется версия/поле внутри SoT_SCHEMA, а не новый тип.

---

## 6) FINAL LAW
> Артефакт-тип — это контракт пайплайна.  
> Нет типа в реестре — нет права использовать его в сущностях.

OWNER: Universe Engine  
LOCK: FIXED

---
END.
