# PRJ PASSPORT — TEMPLATE (UNIVERSAL)
FILE: 05_PROJECTS/00_PRJ_GOVERNANCE/06__TEMPLATE__PRJ_PASSPORT.md

SCOPE: Universe Engine / Projects
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Универсальный шаблон паспорта PRJ-объекта (PACK/EP/SCENE/SHOT). Без дублей. Только UID.

SOURCE OF TRUTH:
- UID: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- PRJ Rules: `05_PROJECTS/00_PRJ_GOVERNANCE/01__RULES__PRJ.md`
- REL/XREF: `02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md`
- Scene Link Law: `05_PROJECTS/00_PRJ_GOVERNANCE/05__SCENE_LINK_LAW.md`

---

## 0) HEADER (REQUIRED)
UID: <UE.PRJ.<CATEGORY>.<FAMILY>.<NAME>>
CATEGORY: <PACK|EP|SCENE|SHOT>
FAMILY: <GEN|NAR|WORLD|...>
STATUS: <DRAFT|ACTIVE|ARCHIVED|DEPRECATED>
LOCK: <OPEN|FIXED>
VERSION: <1.0>
OWNER: <SYSTEM|YOU>

---

## 1) SUMMARY (REQUIRED)
1–5 строк: что это за объект и зачем существует.

---

## 2) PARENT REF (REQUIRED)
(строго один родитель, кроме PACK)

PACK_REF: <UID or NONE>     # обязателен для EP/SCENE/SHOT
EP_REF: <UID or NONE>       # обязателен для SCENE/SHOT
SCENE_REF: <UID or NONE>    # обязателен для SHOT

---

## 3) OBJECTIVE / OUTPUT TARGET (REQUIRED)
OBJECTIVE:
- кратко: что должно получиться на выходе

OUTPUT_TARGETS:
- OUT_STACK: <UID or TBD>   # для SCENE желательно заполнять как TBD до создания STACK
- OUT_VIDEO: <UID or TBD>
- OUT_AUDIO: <UID or TBD>
- OUT_SCRIPT: <UID or TBD>

---

## 4) KB REFERENCES (OPTIONAL)
(персонажи/локации/объекты/правила мира)

KB_REFS: []
XREFS: []
DEPENDS_ON: []

---

## 5) REL POLICY (OPTIONAL)
REL_POLICY:
  - TARGET: "UE.KB.*.*.*"
    MODE: "SOMETIMES"
    CONDITIONS: "only if used in this unit"
    REASON: "context"
  - TARGET: "UE.OUT.*.*.*"
    MODE: "ALWAYS"
    CONDITIONS: "scene outputs"
    REASON: "production chain"

---

## 6) CHECKLIST (OPTIONAL, RECOMMENDED)
- [ ] UID valid
- [ ] registered in PRJ Global Registry
- [ ] parents set
- [ ] outputs planned (TBD ok)
- [ ] scene has STACK_REF after stack exists

---

## 7) NOTES (OPTIONAL)
- любые уточнения

---
END.
