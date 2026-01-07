# REQUIREMENTS / TZ INDEX (CANON)
FILE: 02_STANDARDS/05_REQUIREMENTS_TZ/00__INDEX.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: INDEX
INDEX_TYPE: REQUIREMENTS_ROOT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.IDX.REQ_TZ.500
OWNER: SYSTEM
ROLE: Canonical entrypoint + registry index for the Requirements/TZ realm inside STANDARDS. Defines how requirements live, how they are registered, and how they relate to SoT specs without replacing them.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован индекс требований/TZ: отделение требований от SoT, правила хранения, регистрация, ссылки UID-first"
- REASON: "ТЗ должно быть управляемым и не подменять стандарты"
- IMPACT: "All requirements docs under 02_STANDARDS/05_REQUIREMENTS_TZ"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | doc header & compliance | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.SPEC.DOC_REGISTRY.107 | references | registry/compliance model | 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md
XREF: UE.STD.SPEC.STORAGE_MAP.102 | references | placement rules | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для области `02_STANDARDS/05_REQUIREMENTS_TZ/`.

Он фиксирует:
- состав требований/ТЗ (requirements artifacts)
- правила “что такое requirement и что оно НЕ такое”
- порядок навигации (by number/folder)
- правило существования требований

---

## 1) EXISTENCE RULE (ABSOLUTE)
> Если требования/ТЗ нет в этом INDEX — оно **не существует** в области REQUIREMENTS/TZ.  
> Если файл лежит в папке, но не зарегистрирован здесь — **ignored / non-canon**.

---

## 2) REQUIREMENTS ≠ SoT (CRITICAL RULE)
### 2.1 Что такое requirement/TZ
Requirement/TZ — это постановка цели/ограничений/ожиданий:
- что нужно получить
- по каким критериям считается “готово”
- какие ограничения/риски/зависимости

### 2.2 Что requirement НЕ делает
Requirement НЕ является SoT:
- не переопределяет стандарты
- не вводит новые “законы”
- не заменяет спецификации

Если в requirement появляется “как должно быть по системе” — это выносится в SPEC/MODULE и регистрируется в `01_SPECIFICATIONS` или `06_MARKING_STANDARDS`.

---

## 3) HOW TO USE (MANDATORY FLOW)
1) Сначала определить: это requirement или стандарт.
2) Если requirement:
   - создать файл в этой папке (или подпапке),
   - добавить в этот INDEX,
   - сделать XREF на связанные спеки/протоколы (UID-first).
3) Если requirement приводит к необходимости нового стандарта:
   - открыть Change Management Protocol (STANDARDS)
   - создать/обновить SPEC/MODULE
   - requirement остаётся “заявкой/основанием”, но не заменяет SoT.

---

## 4) REQUIREMENTS FILE FORMAT (RECOMMENDED)
Каждое требование/ТЗ рекомендуется оформлять как:
- DOC_TYPE: REQUIREMENTS
- ARTIFACT_TYPE: TZ | REQUIREMENT
- обязательно:
  - GOAL
  - SCOPE
  - ACCEPTANCE_CRITERIA
  - CONSTRAINTS
  - DEPENDENCIES (XREF UID-first)
  - RISKS
  - OUT_OF_SCOPE

---

## 5) CANON MAP — REQUIREMENTS TREE

# 00 — ROOT INDEX (THIS FILE)
00 — Requirements/TZ Index (THIS FILE)  
PATH: `02_STANDARDS/05_REQUIREMENTS_TZ/00__INDEX.md`  
UID: `UE.STD.IDX.REQ_TZ.500`

---

# 01 — ACTIVE REQUIREMENTS (REGISTER BELOW)
> Ниже регистрируются требования/ТЗ.  
> Формат строки:  
> `NN — <Title> — PATH: <path> — UID: <uid> — STATUS: <...>`

(EMPTY — add entries here)

---

## 6) NO-DUPLICATION RULE (REQUIREMENTS)
- Один goal → одно основное requirement (SoT для требований по этой задаче).
- Дробить можно на sub-requirements, но они должны ссылаться на родителя (UID-first).
- Дубли требований запрещены без явной причины (например разные версии требований) — тогда используется SemVer + deprecation flow.

---

## 7) CHANGE RULE (CANON)
Любая правка этого INDEX меняет состав REQUIREMENTS/TZ и считается изменением канона:
- проходит Canon Protocol
- требует SemVer bump (обычно PATCH/MINOR)

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины для `05_REQUIREMENTS_TZ`.
Любая правка состава/порядка = изменение канона.
--- END.
